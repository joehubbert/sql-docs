---
description: "COS (Transact-SQL)"
title: "COS (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "07/24/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database, sql-data-warehouse, pdw"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "COS"
  - "COS_TSQL"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "cosine"
  - "COS function"
ms.assetid: c9fa8ae1-3373-4f3e-9b97-fa05077c1040
author: cawrites
ms.author: chadam
monikerRange: ">=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# COS (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

A mathematical function that returns the trigonometric cosine of the specified angle - measured in radians - in the specified expression.
  
![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## Syntax  
  
```syntaxsql
COS ( float_expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Arguments
*float_expression*  
An [expression](../../t-sql/language-elements/expressions-transact-sql.md) of type **float**.
  
## Return types
**float**
  
## Examples  
This example returns the `COS` value of the specified angle:
  
```sql
  DECLARE @angle FLOAT;  
SET @angle = 14.78;  
SELECT 'The COS of the angle is: ' + CONVERT(VARCHAR,COS(@angle));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
The COS of the angle is: -0.599465                        
  
(1 row(s) affected)  
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] and [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  


This example returns the COS values of the specified angles:
  
```sql
SELECT COS(14.76) AS cosCalc1, COS(-0.1472738) AS cosCalc2;   
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
cosCalc1  cosCalc2
--------  --------
-0.58     0.99
```
  
## See also
[Mathematical Functions &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  

