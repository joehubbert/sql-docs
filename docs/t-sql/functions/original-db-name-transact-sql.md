---
description: "ORIGINAL_DB_NAME (Transact-SQL)"
title: "ORIGINAL_DB_NAME (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: sql
ms.prod_service: "sql-database"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "ORIGINAL_DB_NAME"
  - "ORIGINAL_DB_NAME_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "ORIGINAL_DB_NAME function"
ms.assetid: 7dadc40a-1287-4f31-8487-434ee477144d
author: VanMSFT
ms.author: vanto
---
# ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Returns the database name specified by the user in the database connection string. This database is specified by using the **sqlcmd-d** option (USE *database*). It can also be specified with the Open Database Connectivity (ODBC) data source expression (initial catalog =*databasename*).  
  
 This database is different from the default user database.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```syntaxsql
ORIGINAL_DB_NAME ()  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Remarks  
 If the initial database isn't specified, the function returns an empty string.  
  
## See Also  
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [osql Utility](../../tools/osql-utility.md)   
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
