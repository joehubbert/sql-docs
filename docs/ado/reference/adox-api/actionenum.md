---
description: "ActionEnum"
title: "ActionEnum | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "ActionEnum"
helpviewer_keywords: 
  - "ActionEnum enumeration [ADOX]"
ms.assetid: f948febd-c885-4621-823b-421e116fec4e
author: rothja
ms.author: jroth
---
# ActionEnum
Specifies the type of action to be performed when [SetPermissions](./setpermissions-method-adox.md) is called.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adAccessDeny**|3|The group or user will be denied the specified permissions.|  
|**adAccessGrant**|1|The group or user will have at least the requested permissions.|  
|**adAccessRevoke**|4|Any explicit access rights of the group or user will be revoked.|  
|**adAccessSet**|2|The group or user will have exactly the requested permissions.|