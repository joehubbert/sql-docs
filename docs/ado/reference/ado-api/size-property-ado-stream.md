---
description: "Size Property (ADO Stream)"
title: "Size Property (ADO Stream) | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "_Stream::Size"
helpviewer_keywords: 
  - "Size property [ADO Stream]"
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: rothja
ms.author: jroth
---
# Size Property (ADO Stream)
Indicates the size of the stream in number of bytes.  
  
## Return Values  
 Returns a **Long** value that specifies the size of the stream in number of bytes. The default value is the size of the stream, or -1 if the size of the stream is not known.  
  
## Remarks  
 **Size** can be used only with open [Stream](./stream-object-ado.md) objects.  
  
> [!NOTE]
>  Any number of bits can be stored in a **Stream** object, limited only by system resources. If the **Stream** contains more bits than can be represented by a **Long** value, **Size** is truncated and therefore does not accurately represent the length of the **Stream**.  
  
## Applies To  
 [Stream Object (ADO)](./stream-object-ado.md)  
  
## See Also  
 [Size Property (ADO Parameter)](./size-property-ado-parameter.md)