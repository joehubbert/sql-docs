---
description: "Connect Property (RDS)"
title: "Connect Property (RDS) | Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ""
ms.date: "01/19/2017"
ms.reviewer: ""
ms.topic: reference
apitype: "COM"
helpviewer_keywords: 
  - "Connect property [ADO]"
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: rothja
ms.author: jroth
---
# Connect Property (RDS)
Indicates the database name from which the query and update operations are run.  
  
 You can set the **Connect** property at design time in the [RDS.DataControl](./datacontrol-object-rds.md) object's OBJECT tags, or at run time in scripting code (for instance, VBScript).  
  
> [!IMPORTANT]
>  Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to [WCF Data Service](/dotnet/framework/wcf/).  
  
## Syntax  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### Parameters  
 *ConnectionString*  
 A valid connection string. For more general information about connection strings, see the [ConnectionString](../ado-api/connectionstring-property-ado.md) property or your provider documentation.  
  
> [!NOTE]
>  Specifying MS Remote as the provider for the **RDS.DataControl** would create a four-tier scenario. Scenarios greater than three tiers have not been tested and should not be needed.  
  
 *DataControl*  
 An object variable that represents an **RDS.DataControl** object.  
  
## Applies To  
 [DataControl Object (RDS)](./datacontrol-object-rds.md)  
  
## See Also  
 [Connect Property Example (VBScript)](./connect-property-example-vbscript.md)   
 [Query Method (RDS)](./query-method-rds.md)   
 [Refresh Method (RDS)](./refresh-method-rds.md)   
 [SubmitChanges Method (RDS)](./submitchanges-method-rds.md)