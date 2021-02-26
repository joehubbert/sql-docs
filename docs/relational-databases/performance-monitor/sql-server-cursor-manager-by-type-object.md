---
title: "SQL Server, Cursor Manager by Type Object | Microsoft Docs"
description: Learn about the SQLServer:Cursor Manager by Type object, which provides counters to monitor cursors, grouped by type.
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: 
  - "Cursor Manager by Type object"
  - "SQLServer:Cursor Manager by Type"
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: WilliamDAssafMSFT
ms.author: wiassaf
---
# SQL Server, Cursor Manager by Type Object
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  The **SQLServer:Cursor Manager by Type** object provides counters to monitor cursors, grouped by type.  
  
 This table describes the SQL Server **Cursor Manager by Type** counters.  
  
|Cursor Manager by Type counters|Description|  
|-------------------------------------|-----------------|  
|**Active cursors**|Number of active cursors.|  
|**Cache Hit Ratio**|Ratio between cache hits and lookups.|  
|**Cache Hit Ratio Base**|For internal use only.| 
|**Cached Cursor Counts**|Number of cursors of a given type in the cache.|  
|**Cursor Cache Use Count/sec**|Times each type of cached cursor has been used.|  
|**Cursor memory usage**|Amount of memory consumed by cursors in kilobytes (KB).|  
|**Cursor Requests/sec**|Number of SQL cursor requests received by server.|  
|**Cursor worktable usage**|Number of worktables used by cursors.|  
|**Number of active cursor plans**|Number of cursor plans.|  
  
 Each counter in the object contains the following instances:  
  
|Cursor Manager instance|Description|  
|-----------------------------|-----------------|  
|**_Total**|Information for all cursors.|  
|**API Cursor**|Only the API cursor information.|  
|**TSQL Global Cursor**|Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] global cursor information.|  
|**TSQL Local Cursor**|Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] local cursor information.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
