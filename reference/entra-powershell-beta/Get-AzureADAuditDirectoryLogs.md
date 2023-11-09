---
title: Example of the Microsoft Entra PowerShell cmdlet reference content.
description: This article provides an example of how to write cmdlet reference content for Microsoft Entra PowerShell docs.

ms.service: active-directory
ms.topic: reference
ms.date: 10/25/2023
ms.author: eunicewaweru
manager: CelesteDG
author: msewaweru
---

# Microsoft Entra PowerShell cmdlet reference example

# Get-EntraAuditDirectoryLogs

Reference

Module: **Microsoft.Entra.Users**

## Synopsis

Get directory audit logs

## Syntax

```powershell
Get-EntraAuditDirectoryLogs 
[-All <Boolean>] 
[-Top <Int32>] 
[-Filter <String>] 
[<CommonParameters>]
```

## Description  
  
The Get-AzureADAuditDirectoryLogs cmdlet gets an Azure Active Directory audit log.

## Permissions

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | AuditLog.Read.All and Directory.Read.All |
|Delegated (personal Microsoft account) | Not supported    |
|Application | AuditLog.Read.All and Directory.Read.All |

## Examples

### Example 1: Get all logs
    
```powershell
 Get-EntraAuditDirectoryLogs -All $true 
``` 
This command gets all audit logs


### Example 2: Get first n logs

```powershell
 Get-AzureADAuditDirectoryLogs -Top 1
```
```Output
Id                                                            ActivityDateTime     ActivityDisplayName Category              CorrelationId                        LoggedByService OperationT
                                                                                                                                                                                  ype
--                                                            ----------------     ------------------- --------              -------------                        --------------- ----------
Directory_aa14d505-735f-4c2d-a3e5-9f2774b15cbf_AE4VI_41199522 11/9/2023 8:28:00 AM Update application  ApplicationManagement aa14d505-735f-4c2d-a3e5-9f2774b15cbf Core Directory  Update
```

This example returns first n logs

### Example 3: Get audit logs containing a given ActivityDisplayName

```powershell
 Get-AzureADAuditDirectoryLogs -Filter "ActivityDisplayName eq 'Update rollout policy of feature'" 
 Get-AzureADAuditDirectoryLogs -Filter "ActivityDisplayName eq 'Update rollout policy of feature'" -Top 1
```
These commands show how to get audit logs by ActivityDisplayName

### Example 4: Get all audit logs with a given result

```powershell
 Get-AzureADAuditDirectoryLogs -Filter "result eq 'success'"
 Get-AzureADAuditDirectoryLogs -Filter "result eq 'failure'" -All $true
```
These commands show how to get audit logs by result

## Parameters

### -All
Boolean to express that return all results from the server for the specific query

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Top
The maximum number of records to return.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Filter
The oData v3.0 filter statement. 
Controls which objects are returned.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## Inputs


## Outputs


## Related links
