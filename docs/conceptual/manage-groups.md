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

 - Install the latest Microsoft Entra PowerShell module. For more information, see [Install the Microsoft Entra PowerShell module](installation.md).
 - Have at least the [Groups Administrator role](/entra/identity/role-based-access-control/permissions-reference#groups-administrator).

## Create and edit a group

1. To create a group, make sure you have the required permissions to create a group.

```powershell
Connect-MgGraph -Scopes 'Group.ReadWrite.All' 
```

1. To create a new group, run the following command.

```powershell
New-EntraGroup -DisplayName 'My new group' -MailEnabled $false -SecurityEnabled $true -MailNickName 'NotSet'
```

This command creates a new group with the name `My new group`.

1. Search for the created group by using the command below.

```powershell
Get-EntraGroup -Filter "DisplayName eq 'My new group'" | Format-List
```

This command returns the details of the newly created group. You can also use the `ObjectId` (GUID) to search, update, or delete the group.

1. Update the group description by running the command below. The `ObjectId` is the Group ID.

```powershell
Set-EntraGroup -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -Description 'This is my new updated group details' 
```

To confirm the updated description, run the `Get-EntraGroup` again.

```powershell
Get-EntraGroup -Filter "DisplayName eq 'My new group'" | Format-List 
```

## Add a user to a group

Add a user to the group by running the command below. The `ObjectId` is the Group ID and the `RefObjectId` is the User ID. You can get the User ID from the [Microsoft Entra admin center](https://entra.microsoft.com/) or by running the `Get-EntraUser` command.

```powershell
Add-EntraGroupMember -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -RefObjectId 'bbbbbbbb-1111-2222-3333-cccccccccccc' 
```

## Add a user as a group owner

Add a group owner to a group by running the command below. The `ObjectId` is the Group ID and the `RefObjectId` is the User ID. 

```powershell
Add-EntraGroupOwner -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -RefObjectId 'bbbbbbbb-1111-2222-3333-cccccccccccc'
```

To confirm the updated group owner, run the `Get-EntraGroupOwner` command. This command returns the User ID of one or more group owners.

```powershell
Get-EntraGroupOwner -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb'
```

## Clean up resources

To remove the user from the group, run the following command.

```powershell
Remove-EntraGroupMember -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -MemberId 'cccccccc-2222-3333-4444-dddddddddddd'
```

To remove the group, run the following command.

```powershell
Remove-EntraGroup -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb'
```

## Related content

- [Manage apps](manage-apps.md)
- [Manage users](manage-user.md)

<!-- link references -->

[installation]: installation.md
[tutorial-groups]: tutorial-groups.md
[create-acount]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[set-entrauserlicense]: set-entrauserlicense.md