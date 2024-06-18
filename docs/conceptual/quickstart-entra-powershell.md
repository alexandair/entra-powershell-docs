---
title: Get started with the module
description: Get started with the Microsoft Entra PowerShell module by using it perform some basic tasks.

author: csmulligan
manager: CelesteDG
ms.topic: quickstart
ms.date: 04/17/2024
ms.author: cmulligan

#customer intent: As an IT admin, I want to learn how to use the Microsoft Entra PowerShell module, so that I can manage Entra resources.
---

# Get started with the module

Microsoft Entra PowerShell provides a command-line interface for managing Microsoft Entra resources. [Explore more about Entra PowerShell](overview.md).

This article helps you get started with Microsoft Entra PowerShell and teaches the core concepts behind it.

## Prerequisites

- [Install the Microsoft Entra PowerShell Module](installation.md).

## Sign in

Microsoft Entra PowerShell supports two types of authentication: _delegated access_, and _app-only access_. To use Microsoft Entra PowerShell, you need to authenticate to access Microsoft Entra resources. Sign in with an admin account of your tenant, if prompted.

```powershell
Connect-Entra -Scopes 'User.Read.All' 
```

To see all the possible options, refer to the [authentication](authentication-methods.md) article.

## Find all available commands

You can get all available commands in Microsoft Entra PowerShell module by using the following command.

```powershell
Get-Command -Module Microsoft.Graph.Entra
```

## Get Help

To be effective with the Microsoft Entra PowerShell, you need to use `Get-Help` command for detailed help about specific commands, including their syntax, parameters, and usage examples.

For example, to learn more about the `Get-EntraUser` command, run:

```powershell
Get-Help Get-EntraUser -Detailed
```

### Get user information

To retrieve the list of users in Microsoft Entra ID, run the following command.

```powershell
Get-EntraUser
```

This command outputs a list of users in your tenant. 

```Output
DisplayName           ID                                     Mail                    UserPrincipalName
------------           --                                     ----                    -----------------
Contoso Demo UserOne   00000000-0000-0000-0000-000000000000   demoone@contoso.com    demoone@contoso.com
Contoso Demo UserTwo   11111111-1111-1111-1111-111111111111   demotwo@contoso.com    demotwo@contoso.com
Contoso Demo UserFour  55555555-5555-5555-5555-555555555555   demofour@contoso.com   demofour@contoso.com
```

You can run the following command to get the details of one single user.

```powershell
Get-EntraUser -ObjectId '00000000-0000-0000-0000-000000000000'
```

## Data collection

Microsoft Entra PowerShell collects telemetry data by default. We collect information about the Microsoft Entra PowerShell version and the cmdlet executed. Microsoft aggregates collected data to identify patterns of usage to identify common issues and to improve the experience of Microsoft Entra PowerShell. Microsoft Entra PowerShell doesn't collect any private or personal data. For example, the usage data helps identify issues such as cmdlets with low success and helps prioritize our work.

## Learn the basics with quickstarts and tutorials

To get started with Microsoft Entra PowerShell, try an in-depth tutorial for the:

- [Manage users](manage-user.md)


