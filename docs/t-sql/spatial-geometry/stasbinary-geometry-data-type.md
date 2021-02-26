---
description: "STAsBinary (geometry Data Type)"
title: "STAsBinary (geometry Data Type) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
f1_keywords: 
  - "STAsBinary_TSQL"
  - "STAsBinary (geometry Data Type)"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "STAsBinary (geometry Data Type)"
ms.assetid: 65353777-e3e6-461c-9504-ea4d83312692
author: MladjoA
ms.author: mlandzic 
---
# STAsBinary (geometry Data Type)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Returns the Open Geospatial Consortium (OGC) Well-Known Binary (WKB) representation of a geometry instance.  
 
## Syntax  
  
```  
  
.STAsBinary ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Return Types
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] return type: **varbinary(max)**  
  
 CLR return type: **SqlBytes**  
  
## Examples  
 The following example creates a `LineString` geometry instance from (0,0) to (2,3) from text. `STAsBinary()` returns the result in WKB.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STAsBinary();  
```  
  
## See Also  
 [OGC Methods on Geometry Instances](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
