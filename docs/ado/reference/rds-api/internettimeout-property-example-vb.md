---
description: "InternetTimeout Property Example (VB)"
title: "InternetTimeout Property Example (VB) | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "InternetTimeout property [ADO], Visual Basic example"
ms.assetid: b35d2f4a-449c-4170-aab6-9ff88c890043
author: rothja
ms.author: jroth
---
# InternetTimeout Property Example (VB)
> [!IMPORTANT]
>  Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to [WCF Data Service](/dotnet/framework/wcf/).  
  
 This example demonstrates the [InternetTimeout](./internettimeout-property-rds.md) property, which exists on the [DataControl](./datacontrol-object-rds.md) and [DataSpace](./dataspace-object-rds.md) objects. This example uses the **DataControl** object and sets the timeout to 20 seconds.  
  
```  
'BeginInternetTimeoutVB  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As RDS.DataControl  
    Dim rst As ADODB.Recordset  
    Set dc = New RDS.DataControl  
  
    dc.Server = "https://MyServer"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Connect = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    dc.SQL = "SELECT * FROM Authors"  
     ' Wait at least 20 seconds  
    dc.InternetTimeout = 200  
  
    dc.Refresh  
     ' Use another Recordset as a convenience  
    Set rst = dc.Recordset  
    Do While Not rst.EOF  
       Debug.Print rst!au_fname & " " & rst!au_lname  
       rst.MoveNext  
    Loop  
  
    If rst.State = adStateOpen Then rst.Close  
    Set rst = Nothing  
    Set dc = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
    Set dc = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndInternetTimeoutVB  
```  
  
## See Also  
 [DataControl Object (RDS)](./datacontrol-object-rds.md)   
 [DataSpace Object (RDS)](./dataspace-object-rds.md)   
 [InternetTimeout Property (RDS)](./internettimeout-property-rds.md)