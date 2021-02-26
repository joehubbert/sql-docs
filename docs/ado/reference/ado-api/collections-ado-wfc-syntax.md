---
description: "Collections (ADO - WFC Syntax)"
title: "Collections (ADO - WFC Syntax) | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
helpviewer_keywords: 
  - "syntax indexes [ADO], ADO/WFC"
  - "collections [ADO], ADO/WFC syntax"
  - "ADO/WFC syntax index [ADO]"
ms.assetid: 073f9a0e-c755-42dd-9f71-4647d68e331a
author: rothja
ms.author: jroth
---
# Collections (ADO - WFC Syntax)
**package com.ms.wfc.data**  
  
## Parameters  
  
### Methods  
  
```  
public void append(com.ms.wfc.data.Parameter param)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public Parameter getItem(int n)  
public Parameter getItem(String s)  
```  
  
### Properties  
  
```  
public int getCount()  
```  
  
## Fields  
  
### Methods  
  
```  
public void append(String name, int type)  
public void append(String name, int type, int definedSize)  
public void append(String name, int type, int definedSize, int attrib)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public com.ms.wfc.data.Field getItem(int n)  
public com.ms.wfc.data.Field getItem(String s)  
```  
  
### Properties  
  
```  
public int getCount()  
```  
  
## Errors  
  
### Methods  
  
```  
public void clear()  
public void refresh()  
public com.ms.wfc.data.Error getItem(int n)  
public com.ms.wfc.data.Error getItem(String s)  
```  
  
### Properties  
  
```  
public int getCount()  
```  
  
## See Also  
 [Errors Collection (ADO)](./errors-collection-ado.md)   
 [Fields Collection (ADO)](./fields-collection-ado.md)   
 [Parameters Collection (ADO)](./parameters-collection-ado.md)