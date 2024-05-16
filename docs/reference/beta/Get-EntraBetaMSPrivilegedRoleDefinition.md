---
title: Get-EntraBetaMSPrivilegedRoleDefinition.
description: This article provides details on the Get-EntraBetaMSPrivilegedRoleDefinition command.

ms.service: active-directory
ms.topic: reference
ms.date: 10/25/2023
ms.author: eunicewaweru
ms.reviewer: stevemutungi
manager: CelesteDG
author: msewaweru
---

# Get-EntraBetaMSPrivilegedRoleDefinition

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Get role definitions.

## SYNTAX

### GetQuery (Default)

```powershell
Get-EntraBetaMSPrivilegedRoleDefinition -ProviderId <String> -ResourceId <String> [-Top <Int32>]
 [-Filter <String>] [<CommonParameters>]
```

### GetById

```powershell
Get-EntraBetaDMSPrivilegedRoleDefinition -ProviderId <String> -ResourceId <String> -Id <String>
 [<CommonParameters>]
```

## DESCRIPTION

Get role definitions.

## Permissions

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | PrivilegedAccess.Read.AzureAD, PrivilegedAccess.ReadWrite.AzureAD    |
|Delegated (personal Microsoft account) |     |
|Application | PrivilegedAccess.Read.AzureAD, PrivilegedAccess.ReadWrite.AzureAD |

## Examples

### Example 1: Get all role definitions

This example demonstrates how to retrieve all the Role definitions.

```powershell
Get-EntraBetaMSPrivilegedRoleDefinition -ProviderId aadRoles -ResourceId d5aec55f-2d12-4442-8d2f-ccca95d4390e -Top 2
```

```output
Id                                   DisplayName                                   ExternalId
--                                   -----------                                   ----------
0526716b-113d-4c15-b2c8-68e3c22b9f80 Authentication Policy Administrator           0526716b-113d-4c15-b2c8-68e3c22b9f80
0964bb5e-9bdb-4d7b-ac29-58e794862a40 Search Administrator                          0964bb5e-9bdb-4d7b-ac29-58e794862a40
```

Get role definitions for a specific provider and resource.

### Example 2: Get a specific role definition

This example demonstrates how to  role definitions for a specific provider, resource, and Id.

```powershell
 Get-EntraBetaMSPrivilegedRoleDefinition -ProviderId aadRoles -ResourceId d5aec55f-2d12-4442-8d2f-ccca95d4390e -Id ffd52fa5-98dc-465c-991d-fc073eb59f8f
```

```output
Id                                   DisplayName                 ExternalId
--                                   -----------                 ----------
ffd52fa5-98dc-465c-991d-fc073eb59f8f Attribute Assignment Reader ffd52fa5-98dc-465c-991d-fc073e...
```

Get a role definition for a specific provider, resource, and Id

### Example 2: Get a specific role definition based on a filter

This example demonstrates how to  role definitions for a specific provider, resource, and filter

```powershell
 Get-EntraBetaMSPrivilegedRoleDefinition -ProviderId aadRoles -ResourceId d5aec55f-2d12-4442-8d2f-ccca95d4390e -Filter "DisplayName eq 'Device Users'"
 ```

 ```output
Id                                   DisplayName  ExternalId                           ResourceId
--                                   -----------  ----------                           ----------
d405c6df-0af8-4e3b-95e4-4d06e542189e Device Users d405c6df-0af8-4e3b-95e4-4d06e542189e d5aec55f...
```

Get a role definition for a specific provider, resource, and filter

## PARAMETERS

### -Id

The id of a role definition

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

### -ResourceId

The unique identifier of the specific resource

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

### -Top

Fetch top role definition

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

### System.String

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
