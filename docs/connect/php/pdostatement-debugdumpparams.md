---
title: "PDOStatement::debugDumpParams"
description: "API reference for the PDOStatement::debugDumpParams function in the Microsoft PDO_SQLSRV Driver for PHP for SQL Server."
ms.custom: ""
ms.date: "08/10/2020"
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: reference
ms.assetid: cf156d65-d933-4235-b89a-18e172d61c15
author: David-Engel
ms.author: v-daenge
---
# PDOStatement::debugDumpParams
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Displays a prepared statement.  
  
## Syntax  
  
```  
  
bool PDOStatement::debugDumpParams();  
```  
  
## Remarks  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## Example  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = "Owner";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = :param");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
  
echo "\n\n";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
?>  
```  
  
## See Also  
[PDOStatement Class](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
