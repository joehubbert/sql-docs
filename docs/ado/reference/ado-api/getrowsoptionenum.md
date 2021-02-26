---
description: "GetRowsOptionEnum"
title: "GetRowsOptionEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "GetRowsOptionEnum"
helpviewer_keywords: 
  - "GetRowsOptionEnum enumeration [ADO]"
ms.assetid: adc109b9-79f4-4946-a5eb-658e22e9a8a5
author: rothja
ms.author: jroth
---
# GetRowsOptionEnum
Specifies how many records to retrieve from a [Recordset](./recordset-object-ado.md).  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adGetRowsRest**|-1|Retrieves the rest of the records in the **Recordset**, from either the current position or a bookmark specified by the *Start* parameter of the [GetRows](./getrows-method-ado.md) method.|  
  
## ADO/WFC Equivalent  
 Package: **com.ms.wfc.data**  
  
|Constant|  
|--------------|  
|AdoEnums.GetRowsOption.REST|  
  
## Applies To  
 [GetRows Method (ADO)](./getrows-method-ado.md)