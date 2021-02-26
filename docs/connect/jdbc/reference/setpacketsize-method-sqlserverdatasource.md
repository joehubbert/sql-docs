---
description: "setPacketSize Method (SQLServerDataSource)"
title: "setPacketSize Method (SQLServerDataSource) | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: reference
apiname: 
  - "SQLServerDataSource.setPacketSize"
apilocation: 
  - "sqljdbc.jar"
apitype: "Assembly"
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: David-Engel
ms.author: v-daenge
---
# setPacketSize Method (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sets the current network packet size used to communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], specified in bytes.  
  
## Syntax  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### Parameters  
 *packetSize*  
  
 An **int** value containing the network packet size.  
  
## Remarks  
 The acceptable range of values of this property is [-1 | 0 | 512..32767]. If this property is set to a value outside the acceptable range, an exception will occur.  
  
 The application might want to set the packetSize property while connecting with Transport Layer Security (TLS), previously known as Secure Sockets Layer (SSL), encryption. The [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] negotiates the packet size with the server. If the encrypt property is set to "**true**" and the negotiated packet size is larger than the Java Virtual Machine (JVM)'s default security provider's TLS record size, the driver will raise an error and terminate the connection.  
  
 In addition, the application might want to set the packetSize property without requesting the TLS encryption. In this case, if the server requires the client to support TLS encryption, the driver checks the JVM's default security provider's TLS record size. If the packetSize property is larger than the JVM's default security provider's TLS record size, the driver will raise an error and terminate the connection.  
  
 For more information about using TLS, see [Using encryption](../../../connect/jdbc/using-ssl-encryption.md).  
  
## See Also  
 [SQLServerDataSource Members](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource Class](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
