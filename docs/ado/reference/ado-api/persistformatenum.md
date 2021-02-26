---
description: "PersistFormatEnum"
title: "PersistFormatEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "PersistFormatEnum"
helpviewer_keywords: 
  - "PersistFormatEnum enumeration [ADO]"
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: rothja
ms.author: jroth
---
# PersistFormatEnum
Specifies the format in which to save a [Recordset](./recordset-object-ado.md).  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indicates Microsoft Advanced Data TableGram (ADTG) format.|  
|**adPersistADO**|1|Indicates that ADO's own Extensible Markup Language (XML) format will be used. This value is the same as adPersistXML and is included for backwards compatibility.|  
|**adPersistXML**|1|Indicates Extensible Markup Language (XML) format.|  
|**adPersistProviderSpecific**|2|Indicates that the provider will persist the **Recordset** using its own format.|  
  
## ADO/WFC Equivalent  
 Package: **com.ms.wfc.data**  
  
|Constant|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## Applies To  
 [Save Method](./save-method.md)