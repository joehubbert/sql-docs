---
description: "Partitioned Tables and Indexes"
title: "Partitioned Tables and Indexes | Microsoft Docs"
ms.custom: ""
ms.date: "1/5/2021"
ms.prod: sql
ms.reviewer: ""
ms.technology: 
ms.topic: conceptual
helpviewer_keywords: 
  - "partitioned tables [SQL Server], about partitioned tables"
  - "partitioned indexes [SQL Server], architecture"
  - "partitioned tables [SQL Server], architecture"
  - "partitioned indexes [SQL Server], about partitioned indexes"
  - "index partitions"
ms.assetid: cc5bf181-18a0-44d5-8bd7-8060d227c927
author: julieMSFT
ms.author: jrasnick
monikerRange: "=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# Partitioned Tables and Indexes
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports table and index partitioning. The data of partitioned tables and indexes is divided into units that may optionally be spread across more than one filegroup in a database. The data is partitioned horizontally, so that groups of rows are mapped into individual partitions. All partitions of a single index or table must reside in the same database. The table or index is treated as a single logical entity when queries or updates are performed on the data. Prior to [!INCLUDE[ssSQL15_md](../../includes/sssql16-md.md)] SP1, partitioned tables and indexes were not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
> [!IMPORTANT]  
> [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] supports up to 15,000 partitions by default. In versions earlier than [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the number of partitions was limited to 1,000 by default.  
  
## Benefits of Partitioning  
 Partitioning large tables or indexes can have the following manageability and performance benefits.  
  
-   You can transfer or access subsets of data quickly and efficiently, while maintaining the integrity of a data collection. For example, an operation such as loading data from an OLTP to an OLAP system takes only seconds, instead of the minutes and hours the operation takes when the data is not partitioned.  
  
-   You can perform maintenance operations on one or more partitions more quickly. The operations are more efficient because they target only these data subsets, instead of the whole table. For example, you can choose to compress data in one or more partitions or rebuild one or more partitions of an index.  
  
-   You may improve query performance, based on the types of queries you frequently run and on your hardware configuration. For example, the query optimizer can process equi-join queries between two or more partitioned tables faster when the partitioning columns are the same as the columns on which the tables are joined. See [Queries](#queries) below for further information.
  
When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs data sorting for I/O operations, it sorts the data first by partition. To improve data sorting performance, stripe the data files of your partitions across more than one disk by setting up a RAID. In this way, although [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] still sorts data by partition, it can access all the drives of each partition at the same time.  
  
In addition, you can improve performance by enabling lock escalation at the partition level instead of a whole table. This can reduce lock contention on the table. To reduce lock contention by allowing lock escalation to the partition, set the `LOCK_ESCALATION` option of the `ALTER TABLE` statement to AUTO. 

> [!TIP]
> Partitions of a table or index can be placed on one filegroup, for example the `PRIMARY` filegroup, or on multiple filegroups. When using tiered storage, using multiple filegroups lets you assign specific partitions to specific storage tiers. All other partitioning benefits apply regardless of the number of filegroups used or partition placement on specific filegroups.
  
## Components and Concepts  
The following terms are applicable to table and index partitioning.  
  
### Partition function  
A database object that defines how the rows of a table or index are mapped to a set of partitions based on the values of a certain column, called a partitioning column. Each value in the partitioning column is an input to the partitioning function, which returns a partition value. The partition function defines the number of partitions and the partition boundaries that the table will have. For example, given a table that contains sales order data, you may want to partition the table into twelve (monthly) partitions based on a **datetime** column such as a sales date.  
  
### Partition scheme 
A database object that maps the partitions of a partition function to a set of filegroups. The primary reason for placing your partitions on separate filegroups is to make sure that you can independently perform backup operations on partitions. This is because you can perform backups on individual filegroups.  

> [!NOTE]
> In Azure [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] only primary filegroups are supported.  
  
### Partitioning column  
The column of a table or index that a partition function uses to partition the table or index. Computed columns that participate in a partition function must be explicitly marked PERSISTED. All data types that are valid for use as index columns can be used as a partitioning column, except **timestamp**. The **ntext**, **text**, **image**, **xml**, **varchar(max)**, **nvarchar(max)**, or **varbinary(max)** data types cannot be specified. Also, Microsoft .NET Framework common language runtime (CLR) user-defined type and alias data type columns cannot be specified.  
  
### Aligned index  
An index that is built on the same partition scheme as its corresponding table. When a table and its indexes are in alignment, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can switch partitions quickly and efficiently while maintaining the partition structure of both the table and its indexes. An index does not have to participate in the same named partition function to be aligned with its base table. However, the partition function of the index and the base table must be essentially the same, in that:
 1. The arguments of the partition functions have the same data type.
 2. They define the same number of partitions.
 3. They define the same boundary values for partitions.  

#### Partitioning Clustered Indexes
When partitioning a clustered index, the clustering key must contain the partitioning column. When partitioning a nonunique clustered index, and the partitioning column is not explicitly specified in the clustering key, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adds the partitioning column by default to the list of clustered index keys. If the clustered index is unique, you must explicitly specify that the clustered index key contain the partitioning column. For more information on clustered indexes and index architecture, see [Clustered Index Design Guidelines](../../relational-databases/sql-server-index-design-guide.md#Clustered).       

#### Partitioning NonClustered Indexes
When partitioning a unique nonclustered index, the index key must contain the partitioning column. When partitioning a nonunique, nonclustered index, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adds the partitioning column by default as a nonkey (included) column of the index to make sure the index is aligned with the base table. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not add the partitioning column to the index if it is already present in the index. For more information on nonclustered indexes and index architecture, see [Nonclustered Index Design Guidelines](../../relational-databases/sql-server-index-design-guide.md#Nonclustered).

### Non-aligned index  
An index partitioned independently from its corresponding table. That is, the index has a different partition scheme or is placed on a separate filegroup from the base table. Designing a non-aligned partitioned index can be useful in the following cases:  
-   The base table has not been partitioned.  
-   The index key is unique and it does not contain the partitioning column of the table.  
-   You want the base table to participate in collocated joins with more tables using different join columns.  

### Partition elimination
The process by which the query optimizer accesses only the relevant partitions to satisfy the filter criteria of the query.  

## Performance Guidelines  
 The new, higher limit of 15,000 partitions affects memory, partitioned index operations, DBCC commands, and queries. This section describes the performance implications of increasing the number of partitions above 1,000 and provides workarounds as needed. With the limit on the maximum number of partitions being increased to 15,000, you can store data for a longer time. However, you should retain data only for as long as it is needed and maintain a balance between performance and number of partitions.  
  
### Processor Cores and Number of Partitions Guidelines  
 To maximize performance with parallel operations, we recommend that you use the same number of partitions as processor cores, up to a maximum of 64 (which is the maximum number of parallel processors that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can utilize).  
  
### Memory Usage and Guidelines  
 We recommend that you use at least 16 GB of RAM if a large number of partitions are in use. If the system does not have enough memory, Data Manipulation Language (DML) statements, Data Definition Language (DDL) statements and other operations can fail due to insufficient memory. Systems with 16 GB of RAM that run many memory-intensive processes may run out of memory on operations that run on a large number of partitions. Therefore, the more memory you have over 16 GB, the less likely you are to encounter performance and memory issues.  
  
 Memory limitations can affect the performance or ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to build a partitioned index. This is especially the case when the index is not aligned with its base table or is not aligned with its clustered index, if the table already has a clustered index applied to it. In this case, it may be useful to increase the index create memory Server Configuration Option. For more information, refer to [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md). 
  
### Partitioned Index Operations  
Creating and rebuilding non-aligned indexes on a table with more than 1,000 partitions is possible, but is not supported. Doing so may cause degraded performance or excessive memory consumption during these operations.  
  
Creating and rebuilding aligned indexes could take longer to execute as the number of partitions increases. We recommend that you do not run multiple create and rebuild index commands at the same time as you may run into performance and memory issues.  
  
 When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs sorting to build partitioned indexes, it first builds one sort table for each partition. It then builds the sort tables either in the respective filegroup of each partition or in **tempdb** if the SORT_IN_TEMPDB index option is specified. Each sort table requires a minimum amount of memory to build. When you are building a partitioned index that is aligned with its base table, sort tables are built one at a time, using less memory. However, when you are building a nonaligned partitioned index, the sort tables are built at the same time. As a result, there must be sufficient memory to handle these concurrent sorts. The larger the number of partitions, the more memory required. The minimum size for each sort table, for each partition, is 40 pages, with 8 kilobytes per page. For example, a nonaligned partitioned index with 100 partitions requires sufficient memory to serially sort 4,000 (40 * 100) pages at the same time. If this memory is available, the build operation will succeed, but performance may suffer. If this memory is not available, the build operation will fail. Alternatively, an aligned partitioned index with 100 partitions requires only sufficient memory to sort 40 pages, because the sorts are not performed at the same time.  
  
 For both aligned and non-aligned indexes, the memory requirement can be greater if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is applying degrees of parallelism to the build operation on a multiprocessor computer. This is because the greater the degrees of parallelism, the greater the memory requirement. For example, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sets degrees of parallelism to 4, a nonaligned partitioned index with 100 partitions requires sufficient memory for four processors to sort 4,000 pages at the same time, or 16,000 pages. If the partitioned index is aligned, the memory requirement is reduced to four processors sorting 40 pages, or 160 (4 * 40) pages. You can use the MAXDOP index option to manually reduce the degrees of parallelism.  

### DBCC Commands  
With a larger number of partitions, DBCC commands could take longer to execute as the number of partitions increases.  
  
### Queries  
Queries that use partition elimination could have comparable or improved performance with larger number of partitions. Queries that do not use partition elimination could take longer to execute as the number of partitions increases.  
  
For example, assume a table has 100 million rows and columns `A`, `B`, and `C`. 
-  In scenario 1, the table is divided into 1000 partitions on column `A`. 
-  In scenario 2, the table is divided into 10,000 partitions on column `A`. 
A query on the table that has a `WHERE` clause filtering on column `A` will perform partition elimination and scan one partition. That same query may run faster in scenario 2 as there are fewer rows to scan in a partition. A query that has a `WHERE` clause filtering on column B will scan all partitions. The query may run faster in scenario 1 than in scenario 2 as there are fewer partitions to scan.  

Queries that use operators such as TOP or MAX/MIN on columns other than the partitioning column may experience reduced performance with partitioning because all partitions must be evaluated.  

If you frequently run queries that involve an equi-join between two or more partitioned tables, their partitioning columns should be the same as the columns on which the tables are joined. Additionally, the tables, or their indexes, should be collocated. This means that they either use the same named partition function, or they use different ones that are essentially the same, in that they:
-  Have the same number of parameters that are used for partitioning, and the corresponding parameters are the same data types.
-  Define the same number of partitions.
-  Define the same boundary values for partitions.
In this way, the query optimizer can process the join faster, because the partitions themselves can be joined. If a query joins two tables that are not collocated or are not partitioned on the join field, the presence of partitions may actually slow down query processing instead of accelerate it.

For more information about partition handling in query processing, see [Query Processing Enhancements on Partitioned Tables and Indexes](../../relational-databases/query-processing-architecture-guide.md#query-processing-enhancements-on-partitioned-tables-and-indexes).

## Behavior changes in statistics computation during partitioned index operations  
 Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], statistics are not created by scanning all the rows in the table when a partitioned index is created or rebuilt. Instead, the query optimizer uses the default sampling algorithm to generate statistics. After upgrading a database with partitioned indexes, you may notice a difference in the histogram data for these indexes. This change in behavior may not affect query performance. To obtain statistics on partitioned indexes by scanning all the rows in the table, use `CREATE STATISTICS` or `UPDATE STATISTICS` with the `FULLSCAN` clause.  
  
## Related Tasks  
  
|Tasks|Topic|  
|-|-|   
|Describes how to create partition functions and partition schemes and then apply these to a table and index.|[Create Partitioned Tables and Indexes](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md)|  
|||  
  
## Related Content  
 You may find the following white papers on partitioned table and index strategies and implementations useful.  
-   [Partitioned Table and Index Strategies Using SQL Server 2008](https://msdn.microsoft.com/library/dd578580\(SQL.100\).aspx)    
-   [How to Implement an Automatic Sliding Window](https://msdn.microsoft.com/library/aa964122\(SQL.90\).aspx)    
-   [Bulk Loading into a Partitioned Table](/previous-versions/sql/sql-server-2005/administrator/cc966380(v=technet.10))    
-   [Project REAL: Data Lifecycle -- Partitioning](/previous-versions/sql/sql-server-2005/administrator/cc966424(v=technet.10))    
-   [Query Processing Enhancements on Partitioned Tables and Indexes](/previous-versions/sql/sql-server-2008-r2/ms345599(v=sql.105))    
-   [Top 10 Best Practices for Building a Large Scale Relational Data Warehouse](https://download.microsoft.com/download/0/F/B/0FBFAA46-2BFD-478F-8E56-7BF3C672DF9D/SQLCAT's%20Guide%20to%20Relational%20Engine.pdf) in _SQLCAT's Guide to: Relational Engineering_
  
