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

# Set-EntraMSAttributeSet

Reference

Module: **Microsoft.Graph.Entra.Beta**

## Synopsis

Updates an existing attribute set.

## Syntax

```powershell
Set-EntraMSAttributeSet 
-Id <String>
[-Description <String>]
[-MaxAttributesPerSet <Int32>]
[<CommonParameters>]
```

## Description  
  
The Set-EntraMSAttributeSet cmdlet Updates an attribute set object identified by ID.
## Permissions

|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|CustomSecAttributeDefinition.ReadWrite.All|Not available.|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|CustomSecAttributeDefinition.ReadWrite.All|Not available.|

## Examples

### Example 1 
  
```powershell
 Set-AzureADMSAttributeSet -Id "Engineering" -Description "Attributes for cloud engineering team"
``` 

Update an attribute set.

- Attribute set: `Engineering`

### Example 2
```powershell
Set-AzureADMSAttributeSet -Id "Engineering" -MaxAttributesPerSet 20
```

Update an attribute set.

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
Name of the attribute set.

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

### System.String

## Outputs

### System.Object

## Related links

- Get-EntraMSAttributeSet
- New-EntraMSAttributeSet
