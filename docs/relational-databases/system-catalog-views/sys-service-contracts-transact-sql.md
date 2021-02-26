---
description: "sys.service_contracts (Transact-SQL)"
title: "sys.service_contracts (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "06/10/2016"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: system-objects
ms.topic: "reference"
f1_keywords: 
  - "service_contracts_TSQL"
  - "sys.service_contracts_TSQL"
  - "sys.service_contracts"
  - "service_contracts"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sys.service_contracts catalog view"
ms.assetid: 787dd47e-4210-439d-9c4a-57a727a0dbd8
author: WilliamDAssafMSFT
ms.author: wiassaf
---
# sys.service_contracts (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  This catalog view contains a row for each contract in the database.  
  
|Column name|Data type|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name of the contract, unique within the database. Not NULLABLE.|  
|**service_contract_id**|**int**|Identifier of the contract. Not NULLABLE.|  
|**principal_id**|**int**|Identifier for the database principal that owns this contract. NULLABLE.|  
  
## Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] For more information, see [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
