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

# Get-EntraMSPrivilegedResource

Reference

Module: **Microsoft.Graph.Entra.Beta**

## Synopsis

Get azure AD MS privileged resource.

## Syntax

```powershell
Get-EntraMSPrivilegedResource
   -ProviderId <String>
   [-Top <Int32>]
   [-Filter <String>]
   [<CommonParameters>]
```

```powershell
Get-EntraMSPrivilegedResource
   -ProviderId <String>
   -Id <String>
   [<CommonParameters>]
```

## Description  
  
Get azure AD MS privileged resource.

## Permissions

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | PrivilegedAccess.Read.AzureResources, PrivilegedAccess.ReadWrite.AzureResources    |
|Delegated (personal Microsoft account) |     |
|Application | PrivilegedAccess.Read.AzureResources, PrivilegedAccess.ReadWrite.AzureResources |

## Examples

### Example 1: Get all users
    
This example demonstrates how to retrieve all resource from Microsoft Entra ID.

    
```powershell
 Get-EntraMSPrivilegedResource -ProviderId aadRoles
``` 
     

    
```Output
Id                                   DisplayName                          ExternalId
--                                   -----------                          ----------
0d626126-a0f3-444c-a025-84c2715389b4 ToGraph_443DEMos1                    /0d626126-a0f3-444c-a025-84c2715389b4
951691f3-d9e5-4f43-8e48-9b1624f61fe3 MOD Demo Platform UnifiedApiConsumer /951691f3-d9e5-4f43-8e48-9b1624f61fe3
9c8f84d0-3bd6-4ec4-a753-a6990777f438 "Ahiresh"                            /administrativeUnits/9c8f84d0-3bd6-4ec4-a753-a6990777...
c4fd2cd1-7902-4be2-a25b-d5cc5ff93517 Pradeep Gupta                        /administrativeUnits/c4fd2cd1-7902-4be2-a25b-d5cc5ff9...
d40bbf91-9b28-42bb-a42c-f2ada9332fb6 AdminUnitName1                       /administrativeUnits/d40bbf91-9b28-42bb-a42c-f2ada933...
d5aec55f-2d12-4442-8d2f-ccca95d4390e Contoso                              /
eb2a1f04-5fb2-44fb-b159-b8989da9a6a8 56544new2$£3                         /eb2a1f04-5fb2-44fb-b159-b8989da9a6a8
```
Get all resources for AzureResource provider

### Example 2: Get a specific privileged resource
In this example, we'll provide the resource ID to retrieve a specific resource.

```powershell
 Get-EntraMSPrivilegedResource -ProviderId aadRoles -Id 9c8f84d0-3bd6-4ec4-a753-a6990777f438
```

```Output

Id                                   DisplayName ExternalId
--                                   ----------- ----------
9c8f84d0-3bd6-4ec4-a753-a6990777f438 "Ahiresh"   /administrativeUnits/9c8f84d0-3bd6-4ec4-a75...
```

Get a resource for AzureResource provider with Id `9c8f84d0-3bd6-4ec4-a753-a6990777f438`.

### Example 3: Get a specific privileged resources by filter.

```powershell
 Get-EntraMSPrivilegedResource -ProviderId aadRoles -Filter "DisplayName eq 'AdminUnitName1'"
```

```Output
Id                                   DisplayName    ExternalId
--                                   -----------    ----------
d40bbf91-9b28-42bb-a42c-f2ada9332fb6 AdminUnitName1 /administrativeUnits/d40bbf91-9b28-42bb-a42c-f2ada9...
```
Get a resource for AzureResource provider by Filter

### Example 3: Get top privileged resources.
```powershell
Get-EntraMSPrivilegedResource -ProviderId aadRoles -Top 1
```

```output
Id                                   DisplayName       ExternalId
--                                   -----------       ----------
0d626126-a0f3-444c-a025-84c2715389b4 ToGraph_443DEMos1 /0d626126-a0f3-444c-a025-84c271...
```
Get top resources for AzureResource provider

## Parameters

### -Filter 
The filter for Odata query.

```yaml
Type: String
Parameter Sets: 
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -Id
The unique identifier of the specific resource.

```yaml
Type: String
Parameter Sets: 
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProviderId 
The unique identifier of the specific provider
```yaml
Type:	String
Parameter Sets: 
Aliases:

Position:	Named
Default value:	None
Required:	True
Accept pipeline input:	True
Accept wildcard characters:	False
```

### -Top
The top result count
```yaml
Type:	String
Parameter Sets: 
Aliases:

Position:	Named
Default value:	None
Required:	False
Accept pipeline input:	True
Accept wildcard characters:	False
```

## Inputs
String

## Outputs
Object


## Related links
