---
description: "sys.dm_os_memory_pools (Transact-SQL)"
title: "sys.dm_os_memory_pools (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database, sql-data-warehouse, pdw"
ms.reviewer: ""
ms.technology: system-objects
ms.topic: "reference"
f1_keywords: 
  - "sys.dm_os_memory_pools_TSQL"
  - "dm_os_memory_pools"
  - "dm_os_memory_pools_TSQL"
  - "sys.dm_os_memory_pools"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sys.dm_os_memory_pools dynamic management view"
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: WilliamDAssafMSFT
ms.author: wiassaf
monikerRange: ">=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Returns a row for each object store in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. You can use this view to monitor cache memory use and to identify bad caching behavior  
  
> [!NOTE]  
>  To call this from [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] or [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use the name **sys.dm_pdw_nodes_os_memory_pools**.  
  
|Column name|Data type|Description|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|Memory address of the entry that represents the memory pool. Is not nullable.|  
|**pool_id**|**int**|ID of a specific pool within a set of pools. Is not nullable.|  
|**type**|**nvarchar(60)**|Type of object pool. Is not nullable. For more information, see [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|System-assigned name of this memory object. Is not nullable.|  
|**max_free_entries_count**|**bigint**|Maximum number of free entries that a pool can have. Is not nullable.|  
|**free_entries_count**|**bigint**|Number of free entries currently in the pool. Is not nullable.|  
|**removed_in_all_rounds_count**|**bigint**|Number of entries removed from the pool since the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was started. Is not nullable.|  
|**pdw_node_id**|**int**|**Applies to**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> The identifier for the node that this distribution is on.|  
  
## Permissions

On [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requires `VIEW SERVER STATE` permission.   
On SQL Database Basic, S0, and S1 service objectives, and for databases in elastic pools, the [server admin](https://docs.microsoft.com/azure/azure-sql/database/logins-create-manage#existing-logins-and-user-accounts-after-creating-a-new-database) account or the [Azure Active Directory admin](https://docs.microsoft.com/azure/azure-sql/database/authentication-aad-overview#administrator-structure) account is required. On all other SQL Database service objectives, the `VIEW DATABASE STATE` permission is required in the database.   

## Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components sometimes use a common pool framework to cache homogeneous, stateless types of data. The pool framework is simpler than cache framework. All entries in the pools are considered equal. Internally, pools are memory clerks and can be used in places where memory clerks are used.  
  
## See Also  
 
  [SQL Server Operating System Related Dynamic Management Views &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


