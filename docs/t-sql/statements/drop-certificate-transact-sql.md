---
description: "DROP CERTIFICATE (Transact-SQL)"
title: "DROP CERTIFICATE (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "06/18/2018"
ms.prod: sql
ms.prod_service: "database-engine, sql-database, sql-data-warehouse, pdw"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "DROP CERTIFICATE"
  - "DROP_CERTIFICATE_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "certificates [SQL Server], removing"
  - "removing certificates"
  - "dropping certificates"
  - "DROP CERTIFICATE statement"
  - "deleting certificates"
ms.assetid: 5704aa04-68a3-4b29-b62b-8868af487817
author: VanMSFT
ms.author: vanto
monikerRange: ">=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# DROP CERTIFICATE (Transact-SQL)
[!INCLUDE [sql-asdb-pdw](../../includes/applies-to-version/sql-asdb-pdw.md)]

  Removes a certificate from the database.  
  
> [!IMPORTANT]  
>  A backup of the certificate used for database encryption should be retained even if the encryption is no longer enabled on a database. Even though the database is not encrypted anymore, parts of the transaction log may still remain protected, and the certificate may be needed for some operations until the full backup of the database is performed. The certificate is also needed to be able to restore from the backups created at the time the database was encrypted.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md) 

  
 
## Syntax  
  
```synaxsql  
DROP CERTIFICATE certificate_name  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Arguments
 *certificate_name*  
 Is the unique name by which the certificate is known in the database.  
  
## Remarks  
 Certificates can only be dropped if no entities are associated with them.  
  
## Permissions  
 Requires CONTROL permission on the certificate.  
  
## Examples  
 The following example drops the certificate `Shipping04` from the `AdventureWorks` database.  
  
```sql  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## Examples: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 The following example drops the certificate `Shipping04`.  
  
```sql
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## See Also  
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [Encryption Hierarchy](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)
