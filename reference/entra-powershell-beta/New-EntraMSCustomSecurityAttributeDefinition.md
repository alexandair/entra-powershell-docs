---
title: New-EntraMSCustomSecurityAttributeDefinition

description: This article provides details of the New-EntraMSCustomSecurityAttributeDefinition command.

ms.service: active-directory
ms.topic: reference
ms.date: 11/10/2023
ms.author: eunicewaweru
manager: CelesteDG
author: msewaweru
---

# New-EntraMSCustomSecurityAttributeDefinition

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Adds a new custom security attribute definition.

## SYNTAX

```powershell
New-EntraMSCustomSecurityAttributeDefinition
-AttributeSet <String>
[-Description <String>]
-IsCollection <Boolean>
-IsSearchable <Boolean>
-Name <String>
-Status <String>
-Type <String>
 -UsePreDefinedValuesOnly <Boolean>
```

## DESCRIPTION 
  
Adds a new Microsoft Entra ID custom security attribute definition object.

## PERMISSIONS

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## EXAMPLES

### Example 1: Add a custom security attribute definition.
  
```powershell
New-EntraMSCustomSecurityAttributeDefinition-AttributeSet "Engineering" -Name "ProjectDate" -Description "Target completion date" -Type "String" -Status "Available" -IsCollection $false -IsSearchable $true -UsePreDefinedValuesOnly $true
``` 
    
This example adds a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String

## PARAMETERS

### -AttributeSet
Name of the attribute set in Azure AD.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -Description
Description for the custom security attribute definition.

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
### -IsCollection
Indicates whether multiple values can be assigned to the custom security attribute.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -IsSearchable
Indicates whether custom security attribute values will be indexed for searching on objects that are assigned attribute values.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -Name
Name of the custom security attribute. It must be unique within an attribute set.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -Status
Specifies whether the custom security attribute is active or deactivated. Acceptable values are 'Available' and 'Deprecated'.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -Type
Specifies the data type of the attribute.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
### -UsePreDefinedValuesOnly
Indicates whether only predefined values can be assigned to the custom security attribute. If set to false, free-form values are allowed.

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUT

## RELATED LINKS

- Get-EntraMSCustomSecurityAttributeDefinition
- [Set-EntraMSCustomSecurityAttributeDefinition](./Set-EntraMSCustomSecurityAttributeDefinition.md)
