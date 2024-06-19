---
title: Manage groups
description: Learn how to create, edit, update, and delete a group in Microsoft Entra PowerShell.
ms.topic: how-to
ms.date: 04/17/2024
author: csmulligan
manager: CelesteDG
ms.author: cmulligan
ms.reviewer: stevemutungi

#Customer intent: As an IT admin managing groups and users in Microsoft Entra ID, I want to learn hot to create, edit and update a group in Microsoft Entra PowerShell so that I can automate group management tasks.
---

# Manage groups

In this tutorial, you'll learn how to create, edit, update, and delete a group in Microsoft Entra PowerShell. You'll also learn how to add and remove users from a group.

## Prerequisites

- A Microsoft Entra user account. If you don't already have one, you can [create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- Install the latest Microsoft Entra PowerShell module. For more information, see [Install the Microsoft Entra PowerShell module](installation.md).
- Have at least the [Groups Administrator role](/entra/identity/role-based-access-control/permissions-reference#groups-administrator).

## Create groups

To create a group, make sure you have the required permissions to create a group.

```powershell
Connect-Entra -Scopes 'Group.ReadWrite.All' 
```

To create a new group, run the following command.

```powershell
New-EntraGroup -DisplayName 'My new group' -MailEnabled $false -SecurityEnabled $true -MailNickName 'NotSet'
```

```Output
DisplayName  Id                                   MailNickname Description GroupTypes
-----------  --                                   ------------ ----------- ----------
My new group aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb NotSet                   {}
```

This command creates a new group with the name `My new group`.

Search for the created group by using the following command.

```powershell
Get-EntraGroup -Filter "DisplayName eq 'My new group'"
```

```Output
DisplayName        Id                                   MailNickname     Description        GroupTypes
-----------        --                                   ------------     -----------        ----------
My new group       aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb mynewgroup       My new group        {Unified}
```

This command returns the details of the newly created group. You can also use the `ObjectId` (GUID) to search, update, or delete the group.

## Update groups

Update the group description by running the following command. The `ObjectId` is the Group ID.

```powershell
Set-EntraGroup -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -Description 'This is my new updated group details' 
```

To confirm the updated description, run the `Get-EntraGroup` again.

```powershell
Get-EntraGroup -Filter "DisplayName eq 'My new group'"  
```

## Add a user to a group

Add a user to the group by running the following command. The `ObjectId` is the Group ID and the `RefObjectId` is the User ID. You can get the User ID from the [Microsoft Entra admin center](https://entra.microsoft.com/) or by running the `Get-EntraUser` command.

```powershell
Add-EntraGroupMember -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -RefObjectId 'bbbbbbbb-1111-2222-3333-cccccccccccc' 
```

## Add a user as a group owner

Add a group owner to a group by running the following command. The `ObjectId` is the Group ID and the `RefObjectId` is the User ID. 

```powershell
Add-EntraGroupOwner -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -RefObjectId 'bbbbbbbb-1111-2222-3333-cccccccccccc'
```

To confirm the updated group owner, run the `Get-EntraGroupOwner` command. This command returns the User ID of one or more group owners.

```powershell
Get-EntraGroupOwner -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb'
```

```Output
ageGroup                        :
onPremisesLastSyncDateTime      :
creationType                    :
imAddresses                     : {Hayden@contoso.com}
preferredLanguage               : en
mail                            : Hayden@contoso.com
securityIdentifier              : B-2-33-4-5555555555-6666666666-7777777-8888888888
identities                      : {@{signInType=userPrincipalName; issuer=contoso.com; issuerAssignedId=Hayden@contoso.com}}
consentProvidedForMinor         :
onPremisesUserPrincipalName     :
```

## Clean up resources

To remove the group, run the following command.

```powershell
Remove-EntraGroup -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb'
```

## Related content

- [Manage users](manage-user.md)

<!-- link references -->

[installation]: installation.md
[tutorial-groups]: tutorial-groups.md
[create-acount]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[set-entrauserlicense]: set-entrauserlicense.md
