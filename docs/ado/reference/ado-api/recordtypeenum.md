---
description: "RecordTypeEnum"
title: "RecordTypeEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "RecordTypeEnum"
helpviewer_keywords: 
  - "RecordTypeEnum enumeration [ADO]"
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: rothja
ms.author: jroth
---
# RecordTypeEnum
Specifies the type of [Record](./record-object-ado.md) object.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Indicates a *simple* record (does not contain child nodes).|  
|**adCollectionRecord**|1|Indicates a *collection* record (contains child nodes).|  
|**adRecordUnknown**|-1|Indicates that the type of this **Record** is unknown.|  
|**adStructDoc**|2|Indicates a special kind of *collection* record that represents COM structured documents.|  
  
## ADO/WFC Equivalent  
 These constants do not have ADO/WFC equivalents.  
  
## Applies To  
 [RecordType Property (ADO)](./recordtype-property-ado.md)