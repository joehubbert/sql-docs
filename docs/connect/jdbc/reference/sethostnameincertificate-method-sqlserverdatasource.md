---
description: "setHostNameInCertificate Method (SQLServerDataSource)"
title: "setHostNameInCertificate Method (SQLServerDataSource) | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: reference
apiname: 
  - "setHostNameInCertificate Method (SQLServerDataSource)"
apilocation: 
  - "setHostNameInCertificate Method (SQLServerDataSource)"
apitype: "Assembly"
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: David-Engel
ms.author: v-daenge
---
# setHostNameInCertificate Method (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sets the host name to be used in validating the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Transport Layer Security (TLS), previously known as Secure Sockets Layer (SSL), certificate.  
  
## Syntax  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### Parameters  
 *hostNameInCertificate*  
  
 A **String** that contains the host name.  
  
## Remarks  
 The hostNameInCertificate value is used to validate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] TLS/SSL certificate when the communication layer is encrypted by using TLS. The default value is null.  
  
 If the hostNameInCertificate property is set to null or unspecified, the [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] will use the serverName property value to validate against the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] TLS/SSL certificate. If the hostNameInCertificate property is set to a string or an empty string "", the driver will use that value to validate the server TLS/SSL certificate.  
  
## See Also  
 [SQLServerDataSource Members](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource Class](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
