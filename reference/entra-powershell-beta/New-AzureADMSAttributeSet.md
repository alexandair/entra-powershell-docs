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

# New-EntraMSAttributeSet

Reference

Module: **Microsoft.Graph.Entra.Beta**

## Synopsis

Create a new attributeSet object.

## Syntax

```powershell
New-EntraMSAttributeSet 
[-Id <String>]
[-Description <String>]
[-MaxAttributesPerSet <Int32>]
[<CommonParameters>]
```

## Description  
  
The New-EntraMSAttributeSet cmdlet Create a new attributeSet object

## Permissions

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## Examples

### Example : Create a new attributeSet object
  
```powershell
 New-EntraMSAttributeSet -Id "Engineering" -Description "Attributes for engineering team" -MaxAttributesPerSet 10
``` 
     
    
```Output
   Id          OdataType   Description                       MaxAttributesPerSet
   --          ---------   -----------                       -------------------
   Engineering             Attributes for engineering team   10
```

Add a single attribute set.

- Attribute set: `Engineering`

## Parameters

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

## Inputs

### None

## Outputs

### System.Object

## Related links

- Get-EntraMSAttributeSet
- Set-EntraMSAttributeSet
