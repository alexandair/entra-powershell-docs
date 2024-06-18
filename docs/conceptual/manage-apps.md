---
title: Manage apps
description: Learn how to register, configure and update apps in Microsoft Entra PowerShell.

author: csmulligan
manager: CelesteDG
ms.topic: how-to
ms.date: 05/24/2024
ms.author: cmulligan
ms.reviewer: stevemutungi

#Customer intent: As an IT admin managing apps in Microsoft Entra ID, I want to learn how to manage apps in Microsoft Entra PowerShell so that I can automate app management tasks.
---

# Manage apps

Your app needs to be registered in Microsoft Entra ID before the Microsoft identity platform can authorize it to access data stored in Microsoft Entra or Microsoft 365 tenants. This condition applies to apps that you develop yourself, that your tenant owns, or that you access through an active subscription.

Many settings for apps are recorded as objects that can be accessed, updated, or deleted using Microsoft Entra PowerShell. In this article, you learn how to use Microsoft Entra PowerShell to manage app and service principal objects.

## Prerequisites

To manage apps with Microsoft Entra PowerShell, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- Grant yourself the least privileged delegated permission indicated for the operation.
- Microsoft Entra PowerShell module installed. Follow the [Install Microsoft Entra PowerShell module](installation.md) guide to install the module.

<!-- All the below code snippets must be tested! -->

## Register an application

The following request creates an app by specifying only the required `displayName` property.

Least privileged delegated permission: `Application.ReadWrite.All`.

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
New-EntraApplication -DisplayName 'My new application'

The application is assigned an ID that's unique for apps in the tenant, and an appId that's globally unique in the Microsoft Entra ecosystem.

## Create a service principal for an application

Least privileged delegated permission: `Application.ReadWrite.All`.

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
$MyApp=(Get-EntraApplication -Filter "DisplayName eq 'My new application'")
New-EntraServicePrincipal  -AppId $MyApp.AppId 
```

## Configure basic properties for your app

Least privileged delegated permission: `Application.ReadWrite.All`.

You can configure multiple properties for your app. The below examples shows how to update the display name of an application.

```powershell
Set-EntraApplication -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb" -DisplayName "New Name"
```

The below example shows how to update the sign out url of an application:

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
Set-EntraApplication -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -LogoutUrl 'https://contoso.com/Security/ADFS.aspx/logout'

For more information, see [Set-EntraApplication](https://review.learn.microsoft.com/powershell/entra-preview/microsoft.graph.entra/set-entraapplication?branch=main&branchFallbackFrom=pr-en-us-86&view=entra-powershell-preview).

## Limit app sign-in to only assigned identities

Least privileged delegated permission: `Application.ReadWrite.All`.

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
 Set-EntraServicePrincipal -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb'  -AppRoleAssignmentRequired $True

## Assign permissions to an app

While you can assign permissions to an app through the Microsoft Entra admin center, you also assign permissions through Microsoft Graph by updating the `requiredResourceAccess` property of the app object. You must pass in both existing and new permissions. Passing in only new permissions overwrites and removes the existing permissions that haven't yet been consented to.

Assigning permissions doesn't automatically grant them to the app. You must still grant admin consent using the Microsoft Entra admin center. 

Least privileged delegated permission: `Application.ReadWrite.All`.

<!--Review / example needed! -->
```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
$RequiredResourceAccess = @(
  @{resourceAppId = '00000003-0000-0000-c000-000000000000'
      resourceAccess = @(
           @{
                 id = 'c79f8feb-a9db-4090-85f9-90d820caa0eb'
                 type = 'Scope'
             }
         @{
                id = '9a5d68dd-52b0-4cc2-bd40-abcf44ac3a30'
               type = 'Role'
           } )})
 Set-EntraApplication -ObjectId 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb' -RequiredResourceAccess $RequiredResourceAccess 

## Create app roles

To keep any existing app roles, include them in the request. Otherwise, they're replaced with the new object.

<!--Review / example needed! -->
```powershell
Set-EntraApplication -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb" -AppRoles $AppRoles
```

## Manage owners

### Retrieve the owner of a service principal

Least privileged delegated permission: `Application.ReadWrite.All`.

```powershell
 $ServicePrincipalId = (Get-EntraServicePrincipal -Top 1).ObjectId
 Get-EntraServicePrincipalOwner -ObjectId $ServicePrincipalId
```

### Assign an owner to a service principal

The first command gets the object ID of a service principal by using the `Get-EntraServicePrincipal` (./Get-EntraServicePrincipal.md) cmdlet, and then stores it in the $ServicePrincipalId variable.

The second command gets the object ID a user by using the `Get-EntraUser` (./Get-EntraUser.md) cmdlet, and then stores it in the $OwnerId variable.

The final command adds the user specified by $OwnerId an owner to a service principal specified by $ServicePrincipalId.

Least privileged delegated permission: `Application.ReadWrite.All`.

```powershell
 $ServicePrincipalId = (Get-EntraServicePrincipal -Top 1).ObjectId
 $OwnerId = (Get-EntraUser -Top 1).ObjectId
 Add-EntraServicePrincipalOwner -ObjectId $ServicePrincipalId -RefObjectId -$OwnerId
```

## Related content

- [Manage groups](manage-groups.md)
- [Manage users](manage-user.md)

<!-- link references -->

[installation]: installation.md
[tutorial-groups]: tutorial-groups.md
[create-acount]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[set-entrauserlicense]: set-entrauserlicense.md
