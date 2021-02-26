---
description: "DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)"
title: DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)
ms.custom: ""
ms.date: "07/03/2019"
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ""
ms.topic: "language-reference"
dev_langs: 
  - "TSQL"
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: XiaoyuMSFT 
ms.author: xiaoyul
monikerRange: "= azure-sqldw-latest"
---

# DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Shows the storage space used result set caching for an Azure [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] database.
  
![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## Syntax  
  
```syntaxsql
DBCC SHOWRESULTCACHESPACEUSED  
[;]  
```  

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

## Remarks

The `DBCC SHOWRESULTCACHESPACEUSED` command doesn't take any parameters and returns the space used by the database where the command is run.

## Permissions

Requires VIEW SERVER STATE permission.
  
## Result Sets  
  
|Column|Data Type|Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Total space used for the database, in KB. This number will change as the cached result set increases.|  
|data_space|bigint|Space used for data, in KB.|  
|index_space|bigint|Space used for indexes, in KB.|  
|unused_space|bigint|Space that is part of the reserved space and not used, in KB.|  

## See also

[Performance tuning with result set caching](/azure/sql-data-warehouse/performance-tuning-result-set-caching)</br>
[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../statements/alter-database-transact-sql-set-options.md?view=azure-sqldw-latest&preserve-view=true)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](../statements/alter-database-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)</br>
[SET RESULT SET CACHING &#40;Transact-SQL&#41;](../statements/set-result-set-caching-transact-sql.md)</br>
[DBCC DROPRESULTSETCACHE  &#40;Transact-SQL&#41;](./dbcc-dropresultsetcache-transact-sql.md)