---
title: "PDO::commit"
description: "API reference for the PDO::commit function in the Microsoft PDO_SQLSRV Driver for PHP for SQL Server."
ms.custom: ""
ms.date: "08/10/2020"
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: reference
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: David-Engel
ms.author: v-daenge
---
# PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Sends commands to the database that were issued after calling [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) and returns the connection to auto commit mode.  
  
## Syntax  
  
```  
  
bool PDO::commit();  
```  
  
## Return Value  
true if the method call succeeded, false otherwise.  
  
## Remarks  
PDO::commit is not affected by (and does not affect) the value of PDO::ATTR_AUTOCOMMIT.  
  
See [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) for an example that uses PDO::commit.  
  
Support for PDO was added in version 2.0 of the [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## See Also  
[PDO Class](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
