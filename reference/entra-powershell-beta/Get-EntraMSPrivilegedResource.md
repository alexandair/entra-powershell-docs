---
title: Get-EntraMSPrivilegedResource.
description: This article provides details on Get-EntraMSPrivilegedResource command.

ms.service: active-directory
ms.topic: reference
ms.date: 11/22/2023
ms.author: eunicewaweru
ms.reviewer: stevemutungi
manager: CelesteDG
author: msewaweru
---

# Get-EntraMSPrivilegedResource

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Get Microsoft Entra ID privileged resource.

## SYNTAX

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

## DESCRIPTION  
  
Get Microsoft Entra ID privileged resource.

## PERMISSIONS

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | PrivilegedAccess.Read.AzureResources, PrivilegedAccess.ReadWrite.AzureResources    |
|Delegated (personal Microsoft account) |     |
|Application | PrivilegedAccess.Read.AzureResources, PrivilegedAccess.ReadWrite.AzureResources |

## EXAMPLES

### Example 1: Get all resources

This example demonstrates how to retrieve all resources from Microsoft Entra ID.

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

Get all resources for AzureResource provider.

### Example 2: Get a specific privileged resource

In this example, we provide the resource ID to retrieve a specific resource.

```powershell
 Get-EntraMSPrivilegedResource -ProviderId aadRoles -Id 9c8f84d0-3bd6-4ec4-a753-a6990777f438
```

```Output

Id                                   DisplayName ExternalId
--                                   ----------- ----------
9c8f84d0-3bd6-4ec4-a753-a6990777f438 "Ahiresh"   /administrativeUnits/9c8f84d0-3bd6-4ec4-a75...
```

Get a resource for AzureResource provider with Id `9c8f84d0-3bd6-4ec4-a753-a6990777f438`.

### Example 3: Get a specific privileged resource by filter

```powershell
 Get-EntraMSPrivilegedResource -ProviderId aadRoles -Filter "DisplayName eq 'AdminUnitName1'"
```

```Output
Id                                   DisplayName    ExternalId
--                                   -----------    ----------
d40bbf91-9b28-42bb-a42c-f2ada9332fb6 AdminUnitName1 /administrativeUnits/d40bbf91-9b28-42bb-a42c-f2ada9...
```

Get a resource for AzureResource provider by Filter

### Example 3: Get top privileged resources

```powershell
Get-EntraMSPrivilegedResource -ProviderId aadRoles -Top 1
```

```output
Id                                   DisplayName       ExternalId
--                                   -----------       ----------
0d626126-a0f3-444c-a025-84c2715389b4 ToGraph_443DEMos1 /0d626126-a0f3-444c-a025-84c271...
```

Get top resources for AzureResource provider.

## PARAMETERS

### -Filter

The filter for OData query.

```yaml
Type: String
Parameter Sets: GetQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Id

The unique identifier of the specific resource

```yaml
Type: String
Parameter Sets: GetById
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ProviderId

The unique identifier of the specific provider

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Top

The top result count

```yaml
Type: Int32
Parameter Sets: GetQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

## INPUTS

String

## OUTPUTS

Object

## RELATED LINKS
