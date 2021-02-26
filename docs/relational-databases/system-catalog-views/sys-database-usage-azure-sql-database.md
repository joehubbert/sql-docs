---
description: "sys.database_usage (Azure SQL Database)"
title: "sys.database_usage (Azure SQL Database) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.service: sql-database
ms.prod_service: "sql-database"
ms.reviewer: ""
ms.topic: "reference"
f1_keywords: 
  - "database_usage"
  - "database_usage_TSQL"
  - "sys.database_usage_TSQL"
  - "sys.database_usage"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "database_usage"
  - "sys.database_usage"
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: julieMSFT
ms.author: jrasnick
monikerRange: "= azuresqldb-current"
---
# sys.database_usage (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **Note: This applies only to Azure SQL Database V11.**  
  
 Lists the number, type, and duration of databases on the [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server.  
  
 The **sys.database_usage** view contains the following columns.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|time|The date when the usage events occurred.|  
|sku|The type of service tier for the database: **Web**, **Business**, **Basic**, **Standard**, **Premium**|  
|quantity|The maximum number of databases of an SKU type that existed during that day.|  
  
## Permissions  
 Read-only access to this view is available to all users with permissions to connect to the **master** database.  
  
## Remarks  
 The **sys.database_usage** view returns one row for each day of your subscription.  
  
## See Also  
 [SQL Database Pricing Details](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Accounts and Billing in Azure SQL Database](/previous-versions/azure/ee621788(v=azure.100))  
  
