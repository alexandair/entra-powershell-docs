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

# Get-EntraAuditSignInLogs

Reference

Module: **Microsoft.Graph.Entra.Beta**

## Synopsis

Get audit logs of sign ins.

## Syntax

```powershell
Get-EntraAuditSignInLogs 
 [-All <Boolean>]
 [-Top <Int32>] 
 [-Filter <String>] 
 [<CommonParameters>]
```

## Description  
  
The Get-EntraAuditSignInLogs cmdlet gets an Azure Active Directory sign in log.

## Permissions

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | AuditLog.Read.All and Directory.Read.All   |
|Delegated (personal Microsoft account) | Not supported   |
|Application | AuditLog.Read.All and Directory.Read.All |

## Examples

### Example 1: Get all logs
    
```powershell
 Get-EntraAuditSignInLogs -All $true 
``` 
```Output
Id                                   AppDisplayName                     AppId                                AppTokenProtectionStatus AuthenticationMethodsUsed AuthenticationProtocol Authe
                                                                                                                                                                                       ntica
                                                                                                                                                                                       tionR
                                                                                                                                                                                       equir
                                                                                                                                                                                       ement
--                                   --------------                     -----                                ------------------------ ------------------------- ---------------------- -----
1e332421-99c9-4ba7-bf52-bda3c9a3b400 Azure Active Directory PowerShell  1b730954-1685-4b74-9bfd-dac224a7b894                          {}                        ropc                   si...
9d78ea64-fa2e-48ca-a19d-d049693c5b00 Azure Portal                       c44b4083-3bb0-49c1-b47d-974e53cbdf3c                          {}                        none                   si...
b88f8107-f8b8-494a-bd7e-3ceddc3b8400 Azure Active Directory PowerShell  1b730954-1685-4b74-9bfd-dac224a7b894                          {}                        ropc                   si...
e05ec15b-8698-4633-81ff-983f233b8500 Azure Active Directory PowerShell  1b730954-1685-4b74-9bfd-dac224a7b894                          {}                        none
```
This command gets all sign in logs.

### Example 2: Get first n logs

```powershell
 Get-EntraAuditSignInLogs -Top 1
```
This example returns first n logs

### Example 3: Get audit logs containing a given ActivityDisplayName

```powershell
 Get-EntraAuditSignInLogs -Filter "ActivityDisplayName eq 'Add owner to application'"
 Get-EntraAuditSignInLogs -Filter "ActivityDisplayName eq 'Add owner to application'" -Top 1
```
These commands show how to get sign in logs by ActivityDisplayName

### Example 4: Get all sign in logs with a given result

```powershell
 Get-EntraAuditSignInLogs -Filter "result eq 'success'"
 Get-EntraAuditSignInLogs -Filter "result eq 'failure'" -Top 1cls
```
These commands show how to get sign in logs by result

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
