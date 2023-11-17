---
title: New-EntraMSAttributeSet
description: This article provides details of New-EntraMSAttributeSet command.

ms.service: active-directory
ms.topic: reference
ms.date: 11/10/2023
ms.author: eunicewaweru
manager: CelesteDG
author: msewaweru
---

# Microsoft Entra PowerShell cmdlet reference example

# New-EntraMSAttributeSet

Reference

Module: **Microsoft.Graph.Entra.Beta**

## SYNOPSIS

Adds a new attribute set.

## SYNTAX

```powershell
New-EntraMSAttributeSet 
[-Id <String>]
[-Description <String>]
[-MaxAttributesPerSet <Int32>]
[<CommonParameters>]
```

## DESCRIPTION 
  
The New-EntraMSAttributeSet cmdlet Adds a new Azure Active Directory (Azure AD) attribute set object.

## PERMISSIONS

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## EXAMPLES

### Example : Create a new attributeSet object.
  
```powershell
 New-EntraMSAttributeSet -Id "Engineering" -Description "Attributes for engineering team" -MaxAttributesPerSet 10
``` 
     
    
```Output
   Id          OdataType   Description                       MaxAttributesPerSet
   --          ---------   -----------                       -------------------
   Engineering             Attributes for engineering team   10
```

this example Add a single attribute set.

- Attribute set: `Engineering`

## PARAMETERS

### -Description
Description for the attribute set.

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
Name of the attribute set. Must be unique within a tenant.

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
### -MaxAttributesPerSet
Maximum number of custom security attributes that can be defined in the attribute set.

```yaml
Type: Int32
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

## OUTPUT

## RELATED LINKS

- Get-EntraMSAttributeSet
- Set-EntraMSAttributeSet
