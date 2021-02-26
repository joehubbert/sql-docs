---
title: Connect to Azure Arc
titleSuffix:
description: Connect an instance of SQL Server to Azure Arc
author: anosov1960
ms.author: sashan 
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
---
# Connect your SQL Server to Azure Arc

You can connect your SQL Server instance on premises to Azure Arc by following these steps.

## Prerequisites

* Your machine has at least one instance of SQL Server installed
* The **Microsoft.AzureArcData** resource provider has been registered using one of the methods below:  
    * Using Azure portal:
        - Select **Subscriptions** 
        - Choose your subscription
        - Under **Settings**, select **Resource providers**
        - Search for `Microsoft.AzureArcData` and select **Register**
    * Using PowerShell, run `Register-AzResourceProvider -ProviderNamespace Microsoft.AzureArcData`
    * Using CLI, run `az provider register --namespace 'Microsoft.AzureArcData`

## Generate a registration script for SQL Server

In this step you generate a script that discovers all SQL Server instances installed on the machine and registers them as __SQL Server - Azure Arc__ resources. If the hosting physical or virtual machine is not registered with Azure Arc, the script automatically does it.

1. Search for __SQL Server - Azure Arc__ resource type and add a new one through the creation blade.

![Start creation](media/join/start-creation-of-sql-server-azure-arc-resource.png)

2. Review the pre-requisites and go to the **Server details** tab.  

3. Select the the subscription, resource group, Azure region and the host operating system. If required, also specify the proxy that your network uses to connect to Internet.

> [!IMPORTANT]
> If the machine hosting the SQL Server instance is already [connected to Azure Arc](/azure/azure-arc/servers/onboard-portal), make sure to select the same resource group that contains the corresponding __Machine - Azure Arc__ resource.

![Server details](media/join/server-details-sql-server-azure-arc.png)

4. Go to the **Run script** tab and download the displayed registration script. The portal generates the script for the hosting OS you specified.

![Download script](media/join/download-script-sql-server-azure-arc.png)

## Connect the installed SQL Server instances to Azure Arc

In this step you will take the script you downloaded from Azure portal and execute it on the target physical or virtual machine. As a result, each installed SQL Server instance on the machine will be registered as a __SQL Server - Azure Arc__ resource. In addition, if the machines itself does not have the guest configuration agent installed, it will be installed automatically and registered as a __Machine - Azure Arc__ resource.

> [!NOTE]
> Make sure to execute the script using an account that meets the minimum permission requirements described in [prerequisites](overview.md#prerequisites).

### Windows

1. Launch an admin instance of __powershell.exe__ and sign in your PowerShell module with your Azure credentials. Follow the [sign in instructions](/powershell/azure/install-az-ps#sign-in).

2. Execute the downloaded script

   ```powershell
   & '.\RegisterSqlServerArc.ps1'
   ```

   > [!NOTE]
   > You may see issues the first time if you haven't previously installed the AZ module for powershell. In that case follow the instructions in the script to install and connect your account and run the script again.

### Linux

1. Use Azure CLI to sign in with your Azure credentials. Follow the [sign in instructions](/cli/azure/authenticate-azure-cli)

2. Grant the execution permission to the downloaded script and execute it.

   ```bash
   sudo chmod +x ./RegisterSqlServerArc.sh
   ./RegisterSqlServerArc.sh
   ```

## Register SQL Server instances on multiple machines

You can connect multiple SQL Server instances installed on multiple Windows or Linux machines to Azure Arc using the same script you generated for a single machine. Follow the instructions how [connect SQL Server instances to Azure Arc at scale](connect-at-scale.md).

## Validate the SQL Server - Azure Arc resources

Go [Azure portal](https://ms.portal.azure.com/#home) and open the newly registered __SQL Server - Azure Arc__ resource to validate.

![Validate connected SQL server ](media/join/validate-sql-server-azure-arc.png)

## Disconnect your SQL Server instance

To disconnect your SQL Server instance from Azure Arc, go to Azure portal, open the __SQL Server - Azure Arc__ resource for that instance, and click the **Unregister** button.

![Unregister SQL Server](media/join/unregister-sql-server-azure-arc.png)

## Next steps

* [Configure advanced data security for your SQL Server instance](configure-advanced-data-security.md)

* [Configure on-demand SQL assessment for your SQL Server instance](assess.md)