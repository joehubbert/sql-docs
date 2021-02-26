---
description: "Deprecated database engine features in [!INCLUDE[sssql19-md](../includes/sssql19-md.md)]"
title: "Deprecated database engine features in SQL Server 2019 | Microsoft Docs"
titleSuffix: "SQL Server 2019"
ms.custom: "seo-lt-2019"
ms.date: "02/12/2021"
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ""
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords: 
  - "deprecated changes 2019 [SQL Server]"
ms.assetid: 
author: MikeRayMSFT
ms.author: mikeray
monikerRange: ">=sql-server-ver15||>=sql-server-linux-ver15"
---

# Deprecated database engine features in SQL Server 2019 (15.x)

[!INCLUDE[sqlserver2019](../includes/applies-to-version/sqlserver2019.md)]

[!INCLUDE [sssql19-md](../includes/sssql19-md.md)] does not deprecate any features beyond those deprecated in prior releases:

- [[!INCLUDE [sssql17-md](../includes/sssql17-md.md)]](deprecated-database-engine-features-in-sql-server-2017.md)
- [[!INCLUDE [sssql16-md](../includes/sssql16-md.md)]](deprecated-database-engine-features-in-sql-server-2016.md)

## Deprecation guidelines

When a feature is marked deprecated, it means:

- The feature is in maintenance mode only. No new changes will be done, including those related to inter-operability with new features.
- We strive not to remove a deprecated feature from future releases to make upgrades easier. However, under rare situations, we may choose to permanently remove the feature from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] if it limits future innovations.
- For new development work, we do not recommend using deprecated features.      

You can monitor the use of deprecated features by using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Deprecated Features Object performance counter, or the `deprecation_announcement`  and `deprecation_final_support` extended events. For more information, see [Use SQL Server Objects](../relational-databases/performance-monitor/use-sql-server-objects.md).  

## Query deprecated features

The values of these counters are also available by executing the following statement:  

```sql
SELECT * FROM sys.dm_os_performance_counters
WHERE object_name = 'SQLServer:Deprecated Features';
```

### See also

- [Breaking changes to database engine features in SQL Server 2019](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-version-15.md)
- [Discontinued database engine functionality in SQL Server](../database-engine/discontinued-database-engine-functionality-in-sql-server.md)
- [SQL Server database engine backward compatibility](./discontinued-database-engine-functionality-in-sql-server.md)