---
title: "Accessing diagnostic information in the extended events log"
description: "Learn how to access extended events on the server that are related to events from the Microsoft JDBC Driver for SQL Server."
ms.custom: ""
ms.date: "05/06/2020"
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ""
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a79e9468-2257-4536-91f1-73b008c376c3
author: David-Engel
ms.author: v-daenge
---
# Accessing diagnostic information in the extended events log
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In the [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], tracing ([Tracing driver operation](../../connect/jdbc/tracing-driver-operation.md)) has been updated to make it easier to correlate client events with diagnostic information, such as connection failures, from the server's connectivity ring buffer and application performance information in the extended events log. For information about reading the extended events log, see [Extended Events](../../relational-databases/extended-events/extended-events.md).  
  
## Details  
 For connection operations, the [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] will send a client connection ID. If the connection fails, you can access the connectivity ring buffer ([Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer](/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)) and find the **ClientConnectionID** field and get diagnostic information about the connection failure. Client connection IDs are logged in the ring buffer only if an error occurs. (If a connection fails before sending the prelogin packet, a client connection ID won't be generated.) The client connection ID is a 16-byte GUID. You can also find the client connection ID in the extended events target output, if the **client_connection_id** action is added to events in an extended events session. If you need further client driver diagnostic assistance, you can enable tracing and rerun the connection command to observe the **ClientConnectionID** field in the trace.  
  
 You can get the client connection ID programmatically by using [ISQLServerConnection Interface](../../connect/jdbc/reference/isqlserverconnection-interface.md). The connection ID will also be present in any connection-related exceptions.  
  
 When there's a connection error, the client connection ID in the server's Built In Diagnostics (BID) trace information and in the connectivity ring buffer can help correlate the client connections to connections on the server. For more information about BID traces on the server, see [Data Access Tracing](/previous-versions/sql/sql-server-2008/cc765421(v=sql.100)). Note, the data access tracing article also contains information about data access trace, which doesn't apply to the [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]; see [Tracing driver operation](../../connect/jdbc/tracing-driver-operation.md) for information on doing a data access trace using the [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 The JDBC Driver also sends a thread-specific activity ID. The activity ID is captured in the extended events sessions if the sessions are started with the TRACK_CAUSAILITY option enabled. For performance issues with an active connection, you can get the activity ID from the client's trace (ActivityID field) and then locate the activity ID in the extended events output. The activity ID in extended events is a 16-byte GUID (not the same as the GUID for the client connection ID) appended with a 4-byte sequence number. The sequence number represents the order of a request within a thread. The ActivityId is sent for SQL batch statements and RPC requests. To enable sending ActivityId to the server, you first need to specify the following key-value pair in the Logging.Properties file:  
  
```
com.microsoft.sqlserver.jdbc.traceactivity = on  
```  
  
 Any value other than `on` (case sensitive) will disable sending the ActivityId.  
  
 For more information, see [Tracing driver operation](../../connect/jdbc/tracing-driver-operation.md). This trace flag is used with corresponding JDBC object loggers to decide whether to trace and send the ActivityId in the JDBC driver. In addition to updating the Logging.Properties file, the logger com.microsoft.sqlserver.jdbc needs to be enabled at FINER or higher. If you want to send ActivityId to the server for requests that are made by a particular class, the corresponding class logger needs to be enabled at FINER or FINEST. For example, if the class is, SQLServerStatement, enable the logger com.microsoft.sqlserver.jdbc.SQLServerStatement.  
  
 The following sample uses [!INCLUDE[tsql](../../includes/tsql-md.md)] to start an extended events session that will be stored in a ring buffer and will record the activity ID sent from a client on RPC and batch operations:  
  
```sql
create event session MySession on server  
add event connectivity_ring_buffer_recorded,  
add event sql_statement_starting (action (client_connection_id)),  
add event sql_statement_completed (action (client_connection_id)),  
add event rpc_starting (action (client_connection_id)),  
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## See also

[Diagnosing problems with the JDBC driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)