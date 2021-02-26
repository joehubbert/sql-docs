---
description: "Create Method Example (VB)"
title: "Create Method Example (VB) | Microsoft Docs"
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
  - "Create method [ADOX], Visual Basic example"
ms.assetid: d7ea0244-596a-404e-8f30-71cadab8d8fc
author: rothja
ms.author: jroth
---
# Create Method Example (VB)
The following code shows how to create a new Microsoft Jet database with the [Create](./create-method-adox.md) method.  
  
```  
Attribute VB_Name = "Create"  
Option Explicit  
  
' BeginCreateDatabaseVB  
Sub CreateDatabase()  
    On Error GoTo CreateDatabaseError  
  
    Dim cat As New ADOX.Catalog  
    cat.Create "Provider='Microsoft.Jet.OLEDB.4.0';Data Source='new.mdb'"  
  
    'Clean up  
    Set cat = Nothing  
    Exit Sub  
  
CreateDatabaseError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateDatabaseVB  
```  
  
## See Also  
 [Catalog Object (ADOX)](./catalog-object-adox.md)   
 [Create Method (ADOX)](./create-method-adox.md)