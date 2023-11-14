---
title: Set-EntraMSCustomSecurityAttributeDefinition.
description: This article provides details on Set-EntraMSCustomSecurityAttributeDefinition command.

ms.service: active-directory
ms.topic: reference
ms.date: 11/10/2023
ms.author: eunicewaweru
manager: CelesteDG
author: msewaweru
---

# Microsoft Entra PowerShell cmdlet reference example

# Set-EntraMSCustomSecurityAttributeDefinition

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Updates an existing custom security attribute definition.

## SYNTAX

```powershell
Set-EntraMSCustomSecurityAttributeDefinition
-Id <String>
[-Description <String>]
[-Status <String>]
[-UsePreDefinedValuesOnly <Boolean>]
[<CommonParameters>]
```

## DESCRIPTION 
  
Updates an Azure Active Directory (Azure AD) custom security attribute definition object identified by ID. 
## PERMISSIONS

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## EXAMPLES

### Example 1: Update custom security attribute definition


```powershell
Set-EntraMSCustomSecurityAttributeDefinition -Id "Engineering_ProjectDate" -Description "Target completion date (YYYY/MM/DD)" -UsePreDefinedValuesOnly $false
``` 

This example Update a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`

### Example 2: Deactivate a custom security attribute definition.

```powershell
Set-EntraMSCustomSecurityAttributeDefinition -Id Engineering_Project -Status "Deprecated"
```

This example Deactivate a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`


## PARAMETERS

### -Description
Description of the custom security attribute definition.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -Id
The unique identifier of a custom security attribute definition.

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
### -Status
Specifies whether the custom security attribute is active or deactivated. Acceptable values are 'Available' and 'Deprecated'.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsePreDefinedValuesOnly
Indicates whether only predefined values can be assigned to the custom security attribute.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## RELATED LINKS

- Get-EntraMSCustomSecurityAttributeDefinition
- New-EntraMSCustomSecurityAttributeDefinition