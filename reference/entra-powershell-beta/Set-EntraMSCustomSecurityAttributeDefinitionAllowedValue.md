---
title: Set-EntraMSCustomSecurityAttributeDefinitionAllowedValue.
description: This article provides details on the Set-EntraMSCustomSecurityAttributeDefinitionAllowedValue command.

ms.service: active-directory
ms.topic: reference
ms.date: 11/10/2023
ms.author: eunicewaweru
ms.reviewer: stevemutungi
manager: CelesteDG
author: msewaweru
---

# Set-EntraMSCustomSecurityAttributeDefinitionAllowedValue

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Updates an existing custom security attribute definition predefined value.

## SYNTAX

```powershell
Set-EntraMSCustomSecurityAttributeDefinitionAllowedValue
-CustomSecurityAttributeDefinitionId <String>
-Id <String>
[-Description <String>]
[-IsActive <Boolean>] 
[<CommonParameters>]
```

## DESCRIPTION
  
Updates a Microsoft Entra ID custom security attribute definition predefined value object identified by ID.

## PERMISSIONS

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## EXAMPLES

### Example 1: Deactivate a predefined value

```powershell
Set-EntraMSCustomSecurityAttributeDefinitionAllowedValue -CustomSecurityAttributeDefinitionId "Engineering_Project" -Id "Alpine" -IsActive $false
```

This example deactivates a predefined value.

- Attribute set: `Engineering`
- Attribute: `Project`
- Predefined value: `Alpine`

## PARAMETERS

### -CustomSecurityAttributeDefinitionId

The unique identifier of a custom security attribute definition in the Microsoft Entra ID.

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

### -Id

Predefined value for the custom security attribute.

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

### -IsActive

Specifies whether the predefined value is active or deactivated. If set to false, this predefined value can't be assigned to any other supported directory objects.

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

- Get-EntraMSCustomSecurityAttributeDefinitionAllowedValue
- Add-EntraMSCustomSecurityAttributeDefinitionAllowedValue
