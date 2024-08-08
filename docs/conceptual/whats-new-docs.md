---
title: What is new in Microsoft Entra PowerShell
description: "Learn about the latest features of Microsoft Entra PowerShell."
ms.topic: overview
ms.date: 08/08/2024
author: omondiatieno
manager: CelesteDG
ms.author: jomondi
ms.reviewer: stevemutungi254
keywords: Microsoft Entra powershell, entra-powershell, manage entra resources using powershell, entra powershell new features, what's new in entra powershell

#customer intent: As a PowerShell user, I want an overview of the latest features of Microsoft Entra PowerShell module.
---

# What's new in the Entra PowerShell module

This article lists all new articles that were added or had significant updates in the last month. It also lists the new features in the Microsoft Entra PowerShell module, currently in public preview, to manage Microsoft Entra resources.

## What's new in docs

### July 2024

#### New articles

- [Azure AD  PowerShell cmdlet map][cmdlet-map] -  Find the cmdlets equivalents for Azure AD, Azure AD Preview, and MSOnline PowerShell modules in Microsoft Entra PowerShell.
- [Assign app roles to a service principal][assign-app-roles] - Assign app roles in Microsoft Entra PowerShell to automate application consent.

#### Updated articles

- The reference TOC has been updated to group cmdlets for easier navigation.

## Module version history

- [Version 0.12.0-preview][posh-0.12.0]

  - Added 3 new cmdlets for Global Secure Access - Private Access App segment management (preview)
  - Added missing types that were throwing warnings on missing types for Get-EntraApplication and Get-EntraBetaApplication commands.
  - Documentation improvements - Added Beta documentation for over 50 cmdlets
  - Added required permissions for 34 additional commands.
  - Resolve broken link in New-EntraRoleDefinition.

- [Version 0.11.0-preview][posh-0.11.0]

  - We have added the required scopes in the examples for top cmdlets.
  - We have resolved local build issue for PowerShell 7.x.
  - Additional bug fixes from GitHub issues.


- [Version 0.10.0-preview][posh-0.10.0]

  - Added the ability to auto-install module dependencies.
  - Official public preview release version.
  - Added Connect-Entra examples.

[assign-app-roles]: create-assign-app-roles.md
[cmdlet-map]: azuread-powershell-to-entra-powershell-mapping.md
[posh-0.12.0]: https://www.powershellgallery.com/packages/Microsoft.Graph.Entra/0.12.0-preview
[posh-0.11.0]: https://www.powershellgallery.com/packages/Microsoft.Graph.Entra/0.11.0-preview
[posh-0.10.0]: https://www.powershellgallery.com/packages/Microsoft.Graph.Entra/0.10.0-preview