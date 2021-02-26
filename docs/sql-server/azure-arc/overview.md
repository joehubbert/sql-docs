---
title: Azure Arc enabled SQL Server
titleSuffix:
description: Manage instances of SQL Server with Azure Arc enabled SQL Server
author: anosov1960
ms.author: sashan 
ms.reviewer: mikeray
ms.date: 12/08/2020
ms.topic: conceptual
ms.prod: sql
ms.custom: references_regions
---

# Azure Arc enabled SQL Server (preview)

Azure Arc enabled SQL Server is part of the Azure Arc for servers. It extends Azure services to SQL Server instances hosted outside of Azure in the customer’s datacenter, on the edge or in a multi-cloud environment.

To enable Azure services, a running SQL Server instance must be registered with Azure Arc using the Azure portal and a registration script. After registration the instance will be represented on Azure as a __SQL Server – Azure Arc__ resource   . The properties of this resource reflect a subset of the SQL Server configuration settings.

The SQL Server can be installed in a virtual or physical machine running Windows or Linux that is connected to Azure Arc via the Connected Machine agent. The agent is installed and machine is and registered automatically as part of the SQL Server instance registration. The Connected Machine agent communicates outbound securely to Azure Arc over TCP port 443. If the machine connects through a firewall or a HTTP proxy server to communicate over the Internet, review the [network configuration requirements for the Connected Machine agent](/azure/azure-arc/servers/agent-overview#prerequisites).

The public preview of Azure Arc enabled SQL Server supports a set of solutions that require the Microsoft Monitoring Agent (MMA) server extension to be installed and connected to a Azure Log analytics workspace for data collection and reporting. These solutions include Advanced data security using Azure Security Center and Azure Sentinel, and SQL Environment health checks using On-demand SQL Assessment feature.

The following diagram illustrates the architecture of Azure Arc enable SQL Server.

![Public preview architecture](media/overview/pubic-preview-architecture.png)

## Prerequisites

### Supported SQL versions and operating systems

Azure Arc enabled SQL Server supports SQL Server 2012 or higher running on one of the following versions of the Windows or Linux operating system:

- Windows Server 2012 R2 and higher
- Ubuntu 16.04 and 18.04 (x64)
- Red Hat Enterprise Linux (RHEL) 7 (x64) 
- SUSE Linux Enterprise Server (SLES) 15 (x64)

### Required permissions

To connect the SQL Server instances and the hosting machine to Azure Arc, you must have an account with privileges to perform the following actions:
   * Microsoft.AzureArcData/sqlServerInstances/read
   * Microsoft.AzureArcData/sqlServerInstances/write
   * Microsoft.HybridCompute/machines/read
   * Microsoft.HybridCompute/machines/write
   * Microsoft.GuestConfiguration/guestConfigurationAssignments/read

For optimal security, we recommend creating a custom role in Azure that has the minimal permissions listed. For information on how to create a custom role in Azure with these permissions, see [Custom roles overview](/azure/active-directory/users-groups-roles/roles-custom-overview). To add role assignment, see [Add or remove role assignments using Azure portal](/azure/role-based-access-control/role-assignments-portal) or [Add or remove role assignments using Azure RBAC and Azure CLI](/azure/role-based-access-control/role-assignments-cli).

### Azure subscription and service limits

Before configuring your SQL server instances and machines with Azure Arc, review the Azure Resource Manager [subscription limits](/azure/azure-resource-manager/management/azure-subscription-service-limits#subscription-limits) and [resource group limits](/azure/azure-resource-manager/management/azure-subscription-service-limits#resource-group-limits) to plan for the number of machines to be connected.

### Networking configuration and resource providers

Review [networking configuration, transport layer security and resource providers](/azure/azure-arc/servers/agent-overview#prerequisites) required for Connected machine agent.

The resource provider `Microsoft.AzureArcData` is required to connect the SQL Server instances to Azure Arc. See the resource provider registration instructions in the [Prerequisites](connect.md#prerequisites) section.

If you already have SQL Server instances connected to Azure Arc, follow these steps to migrate the existing **SQL Server - Azure Arc** resources to the new namespace.

### Supported Azure regions

The public preview is available in the following regions:
- East US
- East US 2
- West US 2
- Australia East
- Southeast Asia
- North Europe
- West Europe
- UK South

## Next steps

- [Connect your SQL Server to Azure Arc](connect.md)
- [Configure your SQL Server instance for periodic environment health check using on-demand SQL assessment](assess.md)
- [Configure advanced data security for your SQL Server instance](configure-advanced-data-security.md)