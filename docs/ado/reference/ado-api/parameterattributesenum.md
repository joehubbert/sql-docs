---
description: "ParameterAttributesEnum"
title: "ParameterAttributesEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "ParameterAttributesEnum"
helpviewer_keywords: 
  - "ParameterAttributesEnum enumeration [ADO]"
ms.assetid: 7ef6c728-5eda-4bde-8052-02d2db1d2cfe
author: rothja
ms.author: jroth
---
# ParameterAttributesEnum
Specifies the attributes of a [Parameter](./parameter-object.md) object.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adParamSigned**|16|Indicates that the parameter accepts signed values.|  
|**adParamNullable**|64|Indicates that the parameter accepts null values.|  
|**adParamLong**|128|Indicates that the parameter accepts long binary data.|  
  
## ADO/WFC Equivalent  
 Package: **com.ms.wfc.data**  
  
|Constant|  
|--------------|  
|AdoEnums.ParameterAttributes.SIGNED|  
|AdoEnums.ParameterAttributes.NULLABLE|  
|AdoEnums.ParameterAttributes.LONG|  
  
## Applies To  
 [Attributes Property (ADO)](./attributes-property-ado.md)