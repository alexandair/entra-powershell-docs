---
title: "Use Find-EntraPermission cmdlet"
description: "Learn how to use the Find-EntraPermission to discover permissions related to a domain."

ms.topic: how-to
ms.date: 01/31/2024
author: omondiatieno
manager: CelesteDG
ms.author: jomondi
reviewer: stevemutungi

#customer intent: As a Microsoft Entra PowerShell user, I want to find the identifier for a specific permission, so that I can accurately supply the permission-related parameters of commands like New-MgApplication and other application and consent related commands.
---

# Using Find-EntraPermission cmdlet

The Microsoft Entra PowerShell module requires users to have domain knowledge of both the semantics and syntax of Microsoft Graph API permissions used to authorize access to the API. This cmdlet helps to answer the following questions:

- How do I find the values to supply to the permission-related parameters of commands like New-MgApplication and other application and consent related commands?
- What permissions are applicable to a certain domain, for example, application, directory? To use Microsoft Entra PowerShell module to access Microsoft Graph, users must sign in to a Microsoft Entra application using the `Connect-Entra` command.

Currently, PowerShell commands and scripts have no way of validating user input that refers to permissions or providing an ‘auto-complete’ user experience to help users accurately supply input to commands. This also affects commands or scripts implemented with the module itself.

## Find permissions related to a given domain

```powershell
Find-EntraPermission application
```

```Output
PermissionType: Delegated

Id                                   Consent Name                                      Description
--                                   ------- ----                                      -----------
c79f8feb-a9db-4090-85f9-90d820caa0eb Admin   Application.Read.All                      Allows the app to read applications and service principals on behalf of the signed-in user.
bdfbf15f-ee85-4955-8675-146e8e5296b5 Admin   Application.ReadWrite.All                 Allows the app to create, read, update and delete applications and service principals on behalf of the signed-in user. Does not allow management of consent grants.
b27add92-efb2-4f16-84f5-8108ba77985c Admin   Policy.ReadWrite.ApplicationConfiguration Allows the app to read and write your organization's application configuration policies on behalf of the signed-in user.  This includes policies such as activityBasedTimeoutPolicy, claimsMappingPolicy, homeRealmDiscoveryPolicy,  tokenIssuancePolicy and tokenLifetimePolicy.


   PermissionType: Application

Id                                   Consent Name                                      Description
--                                   ------- ----                                      -----------
9a5d68dd-52b0-4cc2-bd40-abcf44ac3a30 Admin   Application.Read.All                      Allows the app to read all applications and service principals without a signed-in user.
1bfefb4e-e0b5-418b-a88f-73c46d2cc8e9 Admin   Application.ReadWrite.All                 Allows the app to create, read, update and delete applications and service principals without a signed-in user.  Does not allow management of consent grants.
18a4783c-866b-4cc7-a460-3d5e5662c884 Admin   Application.ReadWrite.OwnedBy             Allows the app to create other applications, and fully manage those applications (read, update, update application secrets and delete), without a signed-in user. Â It cannot update any apps that it is not an owner of.
be74164b-cff1-491c-8741-e671cb536e13 Admin   Policy.ReadWrite.ApplicationConfiguration Allows the app to read and write your organization's application configuration policies, without a signed-in user.  This includes policies such as activityBasedTimeoutPolicy, claimsMappingPolicy, homeRealmDiscoveryPolicy, tokenIssuancePolicy  and tokenLifetimePolicy.
```

## Find the identifier for a specific permission

```powershell
Find-EntraPermission application.Read | Format-List
```

```Output
Id             : c79f8feb-a9db-4090-85f9-90d820caa0eb
PermissionType : Delegated
Consent        : Admin
Name           : Application.Read.All
Description    : Allows the app to read applications and service principals on behalf of the signed-in user.

Id             : bdfbf15f-ee85-4955-8675-146e8e5296b5
PermissionType : Delegated
Consent        : Admin
Name           : Application.ReadWrite.All
Description    : Allows the app to create, read, update and delete applications and service principals on behalf of the signed-in user. Does not allow management of consent grants.

Id             : 9a5d68dd-52b0-4cc2-bd40-abcf44ac3a30
PermissionType : Application
Consent        : Admin
Name           : Application.Read.All
Description    : Allows the app to read all applications and service principals without a signed-in user.
```
