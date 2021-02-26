---
title: azdata arc dc debug reference
titleSuffix: SQL Server big data clusters
description: Reference article for azdata arc dc debug commands.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
---

# azdata arc dc debug

Applies to [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

The following article provides reference for the **sql** commands in the **azdata** tool. For more information about other **azdata** commands, see [azdata reference](reference-azdata.md)

## Commands

|Command|Description|
| --- | --- |
[azdata arc dc debug copy-logs](#azdata-arc-dc-debug-copy-logs) | Copy logs.
[azdata arc dc debug dump](#azdata-arc-dc-debug-dump) | Trigger memory dump.
## azdata arc dc debug copy-logs
Copy the debug logs from the data controller - Kubernetes configuration is required on your system.
```bash
azdata arc dc debug copy-logs --namespace -ns 
                              [--container -c]  
                              
[--target-folder -d]  
                              
[--pod]  
                              
[--resource-kind -rk]  
                              
[--resource-name -rn]  
                              
[--timeout -t]  
                              
[--skip-compress -sc]  
                              
[--exclude-dumps -ed]
```
### Required Parameters
#### `--namespace -ns`
Kubernetes namespace of the data controller.
### Optional Parameters
#### `--container -c`
Copy the logs for the containers with similar name, Optional, by default copies logs for all containers. Cannot be specified multiple times. If specified multiple times, last one will be used
#### `--target-folder -d`
Target folder path to copy logs to. Optional, by default creates the result in the local folder.  Cannot be specified multiple times. If specified multiple times, last one will be used
#### `--pod`
Copy the logs for the pods with similar name. Optional, by default copies logs for all pods. Cannot be specified multiple times. If specified multiple times, last one will be used
#### `--resource-kind -rk`
Copy the logs for the resource of a particular kind. Cannot specified multiple times. If specified multiple times, last one will be used. If specified, --resource-name should also be specified to identify the resource.
#### `--resource-name -rn`
Copy the logs for the resource of the specified name. Cannot be specified multiple times. If specified multiple times, last one will be used. If specified, --resource-kind should also be specified to identify the resource.
#### `--timeout -t`
The number of seconds to wait for the command to complete. The default value is 0 which is unlimited
#### `--skip-compress -sc`
Whether or not to skip compressing the result folder. The default value is False which compresses the result folder.
#### `--exclude-dumps -ed`
Whether or not to exclude dumps from result folder. The default value is False which includes dumps.
### Global Arguments
#### `--debug`
Increase logging verbosity to show all debug logs.
#### `--help -h`
Show this help message and exit.
#### `--output -o`
Output format.  Allowed values: json, jsonc, table, tsv.  Default: json.
#### `--query -q`
JMESPath query string. See [http://jmespath.org/](http://jmespath.org) for more information and examples.
#### `--verbose`
Increase logging verbosity. Use --debug for full debug logs.
## azdata arc dc debug dump
Trigger memory dump and copy it out from container - Kubernetes configuration is required on your system.
```bash
azdata arc dc debug dump --namespace -ns 
                         [--container -c]  
                         
[--target-folder -d]
```
### Required Parameters
#### `--namespace -ns`
Kubernetes namespace of the data controller.
### Optional Parameters
#### `--container -c`
The target container to be triggered for dumping the running processes.
`controller`
#### `--target-folder -d`
Target folder to copy the dump out.
`./output/dump`
### Global Arguments
#### `--debug`
Increase logging verbosity to show all debug logs.
#### `--help -h`
Show this help message and exit.
#### `--output -o`
Output format.  Allowed values: json, jsonc, table, tsv.  Default: json.
#### `--query -q`
JMESPath query string. See [http://jmespath.org/](http://jmespath.org) for more information and examples.
#### `--verbose`
Increase logging verbosity. Use --debug for full debug logs.

## Next steps

For more information about other **azdata** commands, see [azdata reference](reference-azdata.md). 

For more information about how to install the **azdata** tool, see [Install azdata](..\install\deploy-install-azdata.md).

