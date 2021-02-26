---
description: "MSsync_states (Transact-SQL)"
title: "MSsync_states (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: replication
ms.topic: "reference"
f1_keywords: 
  - "MSsync_states"
  - "MSsync_states_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "MSsync_states system table"
ms.assetid: b25e17e1-7718-432e-a442-c4946741d474
author: cawrites
ms.author: chadam
---
# MSsync_states (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  The **MSsync_states** table tracks which publication is still in concurrent snapshot mode. This table is stored in the distribution database.  
  
|Column name|Data type|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|The ID of the publisher.|  
|**publisher_db**|**sysname**|The Name of the publication database.|  
|**publication_id**|**int**|The ID of the publication.|  
  
## See Also  
 [Mapping System Tables to System Views &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Integration Services Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)   
 [Backup and Restore Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [Log Shipping Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
