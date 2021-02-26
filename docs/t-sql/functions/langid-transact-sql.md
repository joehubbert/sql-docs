---
description: "&#x40;&#x40;LANGID (Transact-SQL)"
title: "@@LANGID (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "09/18/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "@@LANGID"
  - "@@LANGID_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "languages [SQL Server], current in use"
  - "@@LANGID function"
  - "current language in use"
  - "ID for language in use"
  - "local language IDs [SQL Server]"
ms.assetid: 7a0fc089-2a48-4a81-9d78-2aaedb540d37
author: cawrites
ms.author: chadam
---
# &#x40;&#x40;LANGID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Returns the local language identifier (ID) of the language that is currently being used.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```syntaxsql  
@@LANGID  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Return Types
 **smallint**  
  
## Remarks  
 To view information about language settings, including language ID numbers, run **sp_helplanguage** without a parameter specified.  
  
## Examples  
 The following example sets the language for the current session to `Italian`, and then uses `@@LANGID` to return the ID for Italian.  
  
```sql  
SET LANGUAGE 'Italian'  
SELECT @@LANGID AS 'Language ID'  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Changed language setting to Italiano.  
Language ID  
-----------  
6            
```  
  
## See Also  
 [Configuration Functions &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  
