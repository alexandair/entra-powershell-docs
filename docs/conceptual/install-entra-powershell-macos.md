---
title: "Install Microsoft Entra PowerShell on macOS"
description: "Learn how to install the Microsoft Entra PowerShell module on macOS."

author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 05/13/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to learn how to install Microsoft Entra PowerShell module on macOS so that I can manage Microsoft Entra resources through PowerShell.
---

# Install Microsoft Entra PowerShell on macOS

This article explains how to install the Entra PowerShell module from
[the PowerShell Gallery](/powershell/scripting/gallery/overview) on macOS.

## Prerequisites

- Install a supported version of
  [PowerShell version 7 or higher](/powershell/scripting/install/installing-powershell-on-macos)

- Install [Microsoft Graph PowerShell SDK module dependencies](#install-dependencies) if not installed.

## Installation

Open the Terminal or other shell host application and run `pwsh` to start PowerShell.

Use the [Install-Module](/powershell/module/powershellget/install-module) cmdlet to install the Entra
PowerShell module:

```powershell
Install-Module -Name Microsoft.Graph.Entra -AllowPrerelease -Repository PSGallery -Force
```

## Update the module

Use the [Update-Module](/powershell/module/powershellget/update-module) cmdlet to update to the
latest version of the Entra PowerShell module.

```powershell
Update-Module -Name Microsoft.Graph.Entra -AllowPrerelease -Force
```

Updating the Entra PowerShell module using `Update-Module` doesn't remove old versions of the Entra
PowerShell module from your system.

## Uninstallation

To remove the Entra PowerShell module from your system, run

```powershell
Uninstall-Module -Name Microsoft.Graph.Entra -AllVersions
```

## Sign in

To start managing your Microsoft Entra resources with the Entra PowerShell module, launch a PowerShell session
and run `Connect-Entra` to sign in to Microsoft Entra ID:

```powershell
Connect-Entra
```

Use the sign-in credentials in the sign in window that opens to sign into the Microsoft Entra ID.

You need to repeat this step for every new PowerShell session you start.

## Troubleshooting

For solutions to common installation issues with the Entra PowerShell module, see
[Troubleshoot installation problems with the Entra PowerShell module](troubleshooting.md#installation-issues).

## Install Dependencies

The Microsoft Entra PowerShell module requires certain Microsoft Graph PowerShell SDK modules. The following snippet installs these dependencies if they are not already installed.

[!INCLUDE [dependencies](../includes/install-entra-powershell-dependencies.md)]

## Provide feedback

To file an issue about Microsoft Entra PowerShell module, see: [File an issue on GitHub.][entra-posh-issues]

## Next steps

- To learn more about managing Entra resources with the Entra PowerShell module, see [Get started](quickstart-entra-powershell.md) article.
- To learn about common installation issues, see the [troubleshooting guide](troubleshooting.md).

[entra-posh-issues]: https://github.com/microsoftgraph/entra-powershell/issues