---
description: "DROP REMOTE SERVICE BINDING (Transact-SQL)"
title: "DROP REMOTE SERVICE BINDING (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: sql
ms.prod_service: "sql-database"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "DROP REMOTE SERVICE BINDING"
  - "DROP_REMOTE_SERVICE_BINDING_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "dropping remote service bindings"
  - "removing remote service bindings"
  - "deleting remote service bindings"
  - "remote service bindings [Service Broker], dropping"
  - "DROP REMOTE SERVICE BINDING statement"
ms.assetid: 377789b4-bf94-488f-8c20-687d0bae447a
author: WilliamDAssafMSFT
ms.author: wiassaf
---
# DROP REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Drops a remote service binding.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```syntaxsql
DROP REMOTE SERVICE BINDING binding_name  
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Arguments
 *binding_name*  
 Is the name of the remote service binding to drop. Server, database, and schema names cannot be specified.  
  
## Permissions  
 Permission for dropping a remote service binding defaults to the owner of the remote service binding, members of the db_owner fixed database role, and members of the sysadmin fixed server role.  
  
## Examples  
 The following example deletes the remote service binding `APBinding` from the database.  
  
```sql 
DROP REMOTE SERVICE BINDING APBinding ;  
```  
  
## See Also  
 [CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](../../t-sql/statements/create-remote-service-binding-transact-sql.md)   
 [ALTER REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
