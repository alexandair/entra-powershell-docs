---
title: Assign app Roles
description: Learn how to assign application permissions to a service principal in Microsoft Entra PowerShell.
author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 07/18/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#Customer intent: As an IT admin managing server principal permissions in Microsoft Entra ID, I want to learn how to assign new permissions in Microsoft Entra PowerShell so that I can automate application consent.
---

# Assign app roles

Application permissions in Microsoft Graph assigned to service principals are also known as App Roles. App Roles allow the application to access data on its own, without a signed in user. This is useful for implementing automation when using Microsoft Entra PowerShell.

In this article, you learn how to connect to Microsoft Entra PowerShell in the delegated context and assign application permissions to a service principal to support an automation scenario.

## Prerequisites

To assign app roles to a service principal, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free][entra-id-account].
- A [Privileged Role Administrator][privileged-role-admin] role.
- Microsoft Entra PowerShell module installed. Follow the [Install the Microsoft Graph PowerShell module][install] guide to install the module.

## Connect to Microsoft Entra PowerShell

To connect to Microsoft Entra PowerShell with the necessary least privileged permissions, run the following command. Sign in with at least a **Privileged Role Administrator** role.

```powershell
Connect-Entra -Scopes 'AppRoleAssignment.ReadWrite.All', 'Application.Read.All'
```

When prompted to **Consent on behalf of your organization** select **Accept**.

## Assign permissions to a service principal

If you haven't created a service principal for your scenario, see [Create a custom application][custom-app].

Use the following example to assign the `User.Read.All` permission to your service principal:

```powershell
#Get service principal
$sp = Get-EntraServicePrincipal -Filter "DisplayName eq 'My Service Principal'"
#Get Graph App Id
$graphid = (Get-EntraServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'").id
#Get permission Id
$permission = (Get-EntraServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'").approles | ` Where {$_.Value -eq ‘User.Read.All’}
#Assign the permission
New-EntraServiceAppRoleAssignment -PrincipalId $sp.id -ResourceId $graphid -Id $permissions.id -ObjectId $sp.id
```

## Assign multiple permissions

```powershell
#Define your required permissions
$GetPermissions = "User.Read.All", "AuditLog.Read.All"
#Get service principal
$sp = Get-EntraServicePrincipal -Filter "DisplayName eq 'My Service Principal'"
#Get Graph App Id
$graphappid = (Get-EntraServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'").id
#Get permission Id
$permissions = (Get-MgServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'").approles | `
Where {$_.Value -in $GetPermissions}
#Assign the permission
Foreach ($perm in $permissions){
    New-EntraServiceAppRoleAssignment -PrincipalId $sp.id -ResourceId $graphid -Id $perm.id -ObjectId $sp.id
}
```

Use the [Microsoft Graph permissions reference](https://learn.microsoft.com/graph/permissions-reference) for guidance on selecting the correct permission for your application.

## Contributors

*This article is maintained by Microsoft. It was originally written by the following contributors.*

Principal author:

- [Daniel Bradley](https://www.linkedin.com/in/danielbradley2/) | Microsoft MVP

[privileged-role-admin]: /entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator
[install]: installation.md
[entra-id-account]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[custom-app]: create-custom-app.md
