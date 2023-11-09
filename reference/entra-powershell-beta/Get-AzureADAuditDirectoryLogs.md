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

Module: **Microsoft.Graph.Entra.Beta**

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
  
The Get-EntraAuditDirectoryLogs cmdlet gets an Azure Active Directory audit log.

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
```Output
Id                                                                      ActivityDateTime       ActivityDisplayName                                             Category              Correla
                                                                                                                                                                                     tionId
--                                                                      ----------------       -------------------                                             --------              -------
Directory_ef68dfed-9958-4f95-bd74-3aa75c01a67c_OVEBB_40241821           11/9/2023 11:24:21 AM  Add owner to application                                        ApplicationManagement ef68...
Directory_ef68dfed-9958-4f95-bd74-3aa75c01a67c_OVEBB_40241781           11/9/2023 11:24:21 AM  Add application                                                 ApplicationManagement ef68...
Directory_a8217b8c-0ea9-4f05-aaab-8db30605f091_JAA85_43195159           11/9/2023 10:52:20 AM  Add owner to application                                        ApplicationManagement a821...
Directory_a8217b8c-0ea9-4f05-aaab-8db30605f091_JAA85_43195118           11/9/2023 10:52:20 AM  Add application                                                 ApplicationManagement a821...
Directory_aa14d505-735f-4c2d-a3e5-9f2774b15cbf_AE4VI_41199522           11/9/2023 8:28:00 AM   Update application                                              ApplicationManagement aa14...
```
This command gets all audit logs


### Example 2: Get first n logs

```powershell
 Get-EntraAuditDirectoryLogs -Top 1
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
 Get-EntraAuditDirectoryLogs -Filter "ActivityDisplayName eq 'Update rollout policy of feature'" 
 Get-EntraAuditDirectoryLogs -Filter "ActivityDisplayName eq 'Update rollout policy of feature'" -Top 1
```
```Output
Id                                                                   ActivityDateTime     ActivityDisplayName              Category       CorrelationId                        LoggedByServi
                                                                                                                                                                               ce
--                                                                   ----------------     -------------------              --------       -------------                        -------------
Application Proxy_2c0e148e-1408-4692-be62-35ca34ec01a1_BB5Y7_4531378 11/2/2023 7:00:29 AM Update rollout policy of feature Authentication 2c0e148e-1408-4692-be62-35ca34ec01a1 Applicatio...
```
These commands show how to get audit logs by ActivityDisplayName

### Example 4: Get all audit logs with a given result

```powershell
 Get-EntraAuditDirectoryLogs -Filter "result eq 'success'"
 Get-EntraAuditDirectoryLogs -Filter "result eq 'failure'" -All $true
```
```Output
Id                                                                   ActivityDateTime       ActivityDisplayName                                             Category              Correlatio
                                                                                                                                                                                  nId
--                                                                   ----------------       -------------------                                             --------              ----------
Directory_a8dc89f7-2ceb-4fb8-bfa8-cb9b09fad089_EODNR_146579472       11/9/2023 5:59:49 AM   Add policy                                                      Policy                a8dc89f...
Directory_6c386ffd-d932-499a-95ae-61a432717230_LN77B_179264024       11/9/2023 5:50:25 AM   Update policy                                                   Policy                6c386ff...
Directory_98bcc458-cd1d-4780-9a49-4d99e376a070_FQTVD_147687339       11/9/2023 5:50:14 AM   Update policy                                                   Policy                98bcc45...
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
