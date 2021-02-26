---
description: "InheritTypeEnum"
title: "InheritTypeEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "InheritTypeEnum"
helpviewer_keywords: 
  - "InheritTypeEnum enumeration [ADOX]"
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: rothja
ms.author: jroth
---
# InheritTypeEnum
Specifies how objects will inherit permissions set with [SetPermissions](./setpermissions-method-adox.md).  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Both objects and other containers contained by the primary object inherit the entry.|  
|**adInheritContainers**|2|Other containers that are contained by the primary object inherit the entry.|  
|**adInheritNone**|0|Default. No inheritance occurs.|  
|**adInheritNoPropagate**|4|The **adInheritObjects** and **adInheritContainers** flags are not propagated to an inherited entry.|  
|**adInheritObjects**|1|Non-container objects in the container inherit the permissions.|  
  
## Applies To  
 [SetPermissions Method (ADOX)](./setpermissions-method-adox.md)