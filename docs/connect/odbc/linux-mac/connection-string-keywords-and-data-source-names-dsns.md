---
title: "Connecting using ODBC"
description: "Learn how to create a connection to a database from Linux or macOS using the Microsoft ODBC Driver for SQL Server."
ms.custom: ""
ms.date: 09/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords: 
  - "data source names"
  - "connection string keywords"
  - "DSNs"
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
author: David-Engel
ms.author: v-daenge
---

# Connecting to SQL Server

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

This topic discusses how you can create a connection to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.  
  
## Connection Properties  

See [DSN and Connection String Keywords and Attributes](../dsn-connection-string-attribute.md) for all the connection string keywords and attributes supported on Linux and macOS.

> [!IMPORTANT]  
> When connecting to a database that uses database mirroring (has a failover partner), do not specify the database name in the connection string. Instead, send a **use** _database_name_ command to connect to the database before executing your queries.  
  
The value passed to the **Driver** keyword can be one of the following:  
  
- The name you used when you installed the driver.

- The path to the driver library, which was specified in the template .ini file used to install the driver.  

DSNs are optional. You can use a DSN to define connection string keywords under a `DSN` name that you can then reference in the connection string. To create a DSN, create (if necessary) and edit the file **~/.odbc.ini** (`.odbc.ini` in your home directory) for a User DSN only accessible to the current user, or `/etc/odbc.ini` for a System DSN (administrative privileges required.) The following is a sample file that shows the minimal required entries for a DSN:  

```ini
# [DSN name]
[MSSQLTest]  
Driver = ODBC Driver 17 for SQL Server  
# Server = [protocol:]server[,port]  
Server = tcp:localhost,1433
#
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

To connect using the above DSN in a connection string, you would specify the `DSN` keyword like: `DSN=MSSQLTest;UID=my_username;PWD=my_password`  
The above connection string would be the equivalent of specifying a connection string without the `DSN` keyword like: `Driver=ODBC Driver 17 for SQL Server;Server=tcp:localhost,1433;UID=my_username;PWD=my_password`

You can optionally specify the protocol and port to connect to the server. For example, **Server=tcp:**_servername_**,12345**. Note that the only protocol supported by the Linux and macOS drivers is `tcp`.

To connect to a named instance on a static port, use <b>Server=</b>*servername*,**port_number**. Connecting to a dynamic port is not supported before version 17.4.

Alternatively, you can add the DSN information to a template file, and execute the following command to add it to `~/.odbc.ini` :
 - **odbcinst -i -s -f** _template_file_  

For complete documentation on ini files and `odbcinst`, see the [unixODBC documention](http://www.unixodbc.org/odbcinst.html). For entries in the `odbc.ini` file specific to the ODBC Driver for SQL Server, see [DSN and Connection String Keywords and Attributes](../dsn-connection-string-attribute.md) for ones supported on Linux and macOS.

You can verify that your driver is working by using `isql` to test the connection, or you can use this command:
 - **bcp master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> -U <name> -P <password>**  

## Using TLS/SSL  

You can use Transport Layer Security (TLS), previously known as Secure Sockets Layer (SSL), to encrypt connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. TLS protects [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] user names and passwords over the network. TLS also verifies the identity of the server to protect against man-in-the-middle (MITM) attacks.  

Enabling encryption increases security at the expense of performance.

For more information, see [Encrypting Connections to SQL Server](/previous-versions/sql/sql-server-2008-r2/ms189067(v=sql.105)) and [Using Encryption Without Validation](../../../relational-databases/native-client/features/using-encryption-without-validation.md).

Regardless of the settings for **Encrypt** and **TrustServerCertificate**, the server login credentials (user name and password) are always encrypted. The following table shows the effect of the **Encrypt** and **TrustServerCertificate** settings.  

||**TrustServerCertificate=no**|**TrustServerCertificate=yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Server certificate is not checked.<br /><br />Data sent between client and server is not encrypted.|Server certificate is not checked.<br /><br />Data sent between client and server is not encrypted.|  
|**Encrypt=yes**|Server certificate is checked.<br /><br />Data sent between client and server is encrypted.<br /><br />The name (or IP address) in a Subject Common Name (CN) or Subject Alternative Name (SAN) in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] TLS/SSL certificate should exactly match the server name (or IP address) specified in the connection string.|Server certificate is not checked.<br /><br />Data sent between client and server is encrypted.|  

By default, encrypted connections always verify the server's certificate. However, if you connect to a server that has a self-signed certificate, also add the `TrustServerCertificate` option to bypass checking the certificate against the list of trusted certificate authorities:  

```
Driver={ODBC Driver 17 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
TLS uses the OpenSSL library. The following table shows the minimum supported versions of OpenSSL and the default Certificate Trust Store locations for each platform:

|Platform|Minimum OpenSSL Version|Default Certificate Trust Store Location|  
|------------|---------------------------|--------------------------------------------|
|Debian 10|1.1.1|/etc/ssl/certs|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71|1.0.1|/etc/ssl/certs|
|OS X 10.11, macOS 10.12-10.15|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 8|1.1.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SUSE Linux Enterprise 15|1.1.0|/etc/ssl/certs|
|SUSE Linux Enterprise 11, 12|1.0.1|/etc/ssl/certs|
|Ubuntu 18.10, 19.04, 19.10, 20.04|1.1.1|/etc/ssl/certs|
|Ubuntu 18.04|1.1.0|/etc/ssl/certs|
|Ubuntu 16.04, 16.10, 17.10|1.0.2|/etc/ssl/certs|
|Ubuntu 14.04|1.0.1|/etc/ssl/certs|

You can also specify encryption in the connection string using the `Encrypt` option when using **SQLDriverConnect** to connect.

## Adjusting the TCP Keep-Alive Settings

Starting in ODBC Driver 17.4, how often the driver sends keep-alive packets and retransmits them when a response is not received is configurable.
To configure, add the following settings to either the driver's section in `odbcinst.ini`, or the DSN's section in `odbc.ini`. When connecting
with a DSN, the driver will use the settings in the DSN's section if present; otherwise, or if connecting with a connection string only, it will use the
settings in the driver's section in `odbcinst.ini`. If the setting is not present in either location, the driver uses the default value.

- `KeepAlive=<integer>` controls how often TCP attempts to verify that an idle connection is still intact by sending a keep-alive packet. The default is **30** seconds.

- `KeepAliveInterval=<integer>` determines the interval separating keep-alive retransmissions until a response is received.  The default is **1** second.

## See Also

- [Installing the Microsoft ODBC Driver for SQL Server on Linux](installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installing the Microsoft ODBC Driver for SQL Server on macOS](install-microsoft-odbc-driver-sql-server-macos.md)
- [Programming Guidelines](programming-guidelines.md)