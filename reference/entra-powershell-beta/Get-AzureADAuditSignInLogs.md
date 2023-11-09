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

# Get-EntraUser

Reference

Module: **Microsoft.Entra.Users**

## Synopsis

Gets users from Microsoft Entra ID.

## Syntax

```powershell
Get-EntraUser 
 [-ReturnDeletedUsers] 
 [-City <String>] 
 [-Country <String>] 
 [-Department <String>]
 [-DomainName <String>]
 [-EnabledFilter <UserEnabledFilter>]
 [-State <String>]
 [-Synchronized]
 [-Title <String>]
 [-HasErrorsOnly]
 [-LicenseReconciliationNeededOnly]
 [-UnlicensedUsersOnly]
 [-UsageLocation <String>]
 [-SearchString <String>]
 [-MaxResults <Int32>]
 [-TenantId <Guid>]
 [<CommonParameters>]
```

```powershell
Get-EntraUser
 -UserId <Guid>
 [-ReturnDeletedUsers]
 [-TenantId <Guid>]
 [<CommonParameters>]
```

## Description  
  
The Get-EntraUser cmdlet gets an individual user or list of users. Specify the `UserId` parameter to get a specific user.

## Permissions

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | User.Read, User.ReadWrite, User.ReadBasic.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All    |
|Delegated (personal Microsoft account) | User.Read, User.ReadWrite    |
|Application | User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## Examples

### Example 1: Get all users
    
This example demonstrates how to retrieve all users from Microsoft Entra ID.

    
```powershell
 Get-EntraUser
``` 
     

    
```Output
   DisplayName               Id                                   Mail                                    UserPrincipalName
-----------               --                                   ----                                    -----------------
Conf Room Adams           1d7e70f5-72ce-4f1d-98e3-e2dd66627fd1 Adams@M365x05119916.OnMicrosoft.com     Adams@M365x05119916.OnMicrosoft.com
Adele Vance               17f6ebc5-24af-42b1-8cbb-2efd9369faf8 AdeleV@M365x05119916.OnMicrosoft.com    AdeleV@M365x05119916.OnMicrosoft.com
MOD Administrator         97c67ffc-ddf9-4df5-b623-a920b2693c6c admin@M365x05119916.OnMicrosoft.com     admin@M365x05119916.onmicrosoft.com
Alex Wilber               ed862efd-3f2b-422e-94f3-f139d4c1e65c AlexW@M365x05119916.OnMicrosoft.com     AlexW@M365x05119916.OnMicrosoft.com
Allan Deyoung             9b18b5c4-99ea-487b-a140-795c1173a924 AllanD@M365x05119916.OnMicrosoft.com    AllanD@M365x05119916.OnMicrosoft.com
Automate Bot              5b7bbaab-154e-46ec-b257-508da1878b51                                         AutomateB@M365x05119916.OnMicrosoft.com
Conf Room Baker           7bdbd1dd-c77a-4528-b441-4a1455fa132c Baker@M365x05119916.OnMicrosoft.com     Baker@M365x05119916.OnMicrosoft.com
Bianca Pisani             12622127-890c-429d-946b-d351c3d7285a                                         BiancaP@M365x05119916.OnMicrosoft.com
Brian Johnson (TAILSPIN)  ad8a1e70-aefe-4ee7-9bdf-3e2fcdcfdb81 BrianJ@M365x05119916.OnMicrosoft.com    BrianJ@M365x05119916.OnMicrosoft.com
```

This command retrieves all users in the company. It displays up to the default value of 500 results.

### Example 2: Get a specific user
In this example, we'll provide the user's ID to retrieve a specific user.

```powershell
 Get-EntraUser -UserId 1d7e70f5-72ce-4f1d-98e3-e2dd66627fd1
```

```Output
DisplayName     Id                                   Mail                                UserPrincipalName
-----------     --                                   ----                                -----------------
Conf Room Adams 1d7e70f5-72ce-4f1d-98e3-e2dd66627fd1 Adams@M365x05119916.OnMicrosoft.com Adams@M365x05119916.OnMicrosoft.com
```

This example returns the details of the user with the ID `1d7e70f5-72ce-4f1d-98e3-e2dd66627fd1`.

## Parameters

### -All
Indicates that this cmdlet returns all results.
Do not specify together with the _MaxResults_ parameter.

```yaml
Type: SwitchParameter
Parameter Sets: All__0
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserId
Specifies the unique object ID of the user to get.

```yaml
Type: Guid
Parameter Sets: GetUser__0
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

## Inputs


## Outputs


## Related links

- New-EntraUser
- Remove-EntraUser
- Update-EntraUser