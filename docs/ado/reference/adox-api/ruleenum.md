---
description: "RuleEnum"
title: "RuleEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "RuleEnum"
helpviewer_keywords: 
  - "RuleEnum enumeration [ADOX]"
ms.assetid: 738fd3ff-3daf-483d-a0b9-88bef1be54c1
author: rothja
ms.author: jroth
---
# RuleEnum
Specifies the rule to follow when a [Key](./key-object-adox.md) is deleted.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adRICascade**|1|Cascade changes.|  
|**adRINone**|0|Default. No action is taken.|  
|**adRISetDefault**|3|Foreign key value is set to the default.|  
|**adRISetNull**|2|Foreign key value is set to null.|  
  
## Applies To  
 [DeleteRule Property (ADOX)](./deleterule-property-adox.md)