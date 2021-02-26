---
description: "Name Property (ADO MD)"
title: "Name Property (ADO MD) | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
f1_keywords: 
  - "Level::Name"
  - "CubeDef::Name"
  - "Member::Name"
  - "Catalog::Name"
  - "Dimension::Name"
  - "Name"
  - "Axis::Name"
  - "Hierarchy::Name"
helpviewer_keywords: 
  - "Name property [ADO MD]"
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: rothja
ms.author: jroth
---
# Name Property (ADO MD)
Indicates the name of an object.  
  
## Return Values  
 Returns a **String** and is read-only.  
  
## Remarks  
 You can retrieve the **Name** property of an object by an ordinal reference, after which you can refer to the object directly by name. For example, if `cdf.CubeDefs(0).Name` yields "Bobs Video Store", you can refer to this [CubeDef](./cubedef-object-ado-md.md) as `cdf.CubeDefs("Bobs Video Store")`.  
  
## Applies To  

:::row:::
    :::column:::
        [Axis Object (ADO MD)](./axis-object-ado-md.md)  
        [Catalog Object (ADO MD)](./catalog-object-ado-md.md)  
        [CubeDef Object (ADO MD)](./cubedef-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Dimension Object (ADO MD)](./dimension-object-ado-md.md)  
        [Hierarchy Object (ADO MD)](./hierarchy-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Level Object (ADO MD)](./level-object-ado-md.md)  
        [Member Object (ADO MD)](./member-object-ado-md.md)  
    :::column-end:::
:::row-end:::

## See Also  
 [Catalog Example (VB)](./catalog-example-vb.md)   
 [Caption Property (ADO MD)](./caption-property-ado-md.md)   
 [Description Property (ADO MD)](./description-property-ado-md.md)   
 [UniqueName Property (ADO MD)](./uniquename-property-ado-md.md)