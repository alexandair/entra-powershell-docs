---
title: "Install Microsoft Entra PowerShell on Linux"
description: "Learn how to install the Microsoft Entra PowerShell module on Linux."

author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 05/13/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to learn how to install Microsoft Entra PowerShell module on Linux so that I can manage Microsoft Entra resources through PowerShell.
---

# Install Microsoft Entra PowerShell on Linux

This article explains how to install the Microsoft Entra PowerShell module on Linux.

## Prerequisites

- Install a supported version of [PowerShell version 7 or higher](/powershell/scripting/install/installing-powershell-on-linux)

## Installation

Open the Terminal or other shell host application and run `pwsh` to start PowerShell.

Use the [Install-Module](/powershell/module/powershellget/install-module) cmdlet to install the Entra PowerShell module:

```powershell
Install-Module -Name Microsoft.Graph.Entra -AllowPrerelease -Repository PSGallery -Force
```

## Update the Entra PowerShell module

Use [Update-Module](/powershell/module/powershellget/update-module) to update to the latest version
of the Microsoft Entra PowerShell module:

```powershell
Update-Module -Name Microsoft.Graph.Entra -AllowPrerelease -Force
```

Updating the Microsoft Entra PowerShell module using `Update-Module` doesn't remove old versions of the Entra
PowerShell module from your system.

## Uninstallation

To remove the Entra PowerShell module from your system, run

```powershell
Uninstall-Module -Name Microsoft.Graph.Entra -AllVersions
```

## Sign in

To start managing your Microsoft Entra resources with the Microsoft Entra PowerShell module, launch a PowerShell session
and run `Connect-Entra` to sign in to Microsoft Entra ID:

```powershell
Connect-Entra
```

Use your Microsoft Entra ID login credentials to log into the login window that opens.

You'll need to repeat this step for every new PowerShell session you start.

## Troubleshooting

For solutions to common installation issues with the Microsoft Entra PowerShell module, see
[Troubleshoot installation problems with the Microsoft Entra PowerShell module](troubleshooting.md#installation-issues).

## Install Dependencies

Microsoft Entra PowerShell module depends on some Microsoft Graph PowerShell SDK modules. The following snippet installs the required dependencies, if not installed already.

# [v1.0](#tab/v1)

- Install Microsoft Graph PowerShell SDK `v1.0` dependencies.

```powershell
$RequiredModules = (@'
Microsoft.Graph.DirectoryObjects
Microsoft.Graph.Users
Microsoft.Graph.Users.Actions
Microsoft.Graph.Users.Functions
Microsoft.Graph.Groups
Microsoft.Graph.Identity.DirectoryManagement
Microsoft.Graph.Identity.Governance
Microsoft.Graph.Identity.SignIns
Microsoft.Graph.Applications
'@).Split("`n")

# Check if the pre-requisite modules are installed and install them if needed
foreach ($module in $RequiredModules) {
    Write-Host -ForegroundColor Yellow -BackgroundColor DarkBlue "Checking for $module"
    if (!(Get-Module -Name $module -ListAvailable)) {
        Install-Module -Name $module -Scope CurrentUser
    }
}

<# Attribution: https://github.com/SamErde and https://github.com/alexandair #>
```

# [Beta](#tab/beta)

- Install Microsoft Graph PowerShell SDK `Beta` dependencies.

```powershell
$RequiredModules = (@'
Microsoft.Graph.Beta.Applications 
Microsoft.Graph.Beta.Users
Microsoft.Graph.Beta.Users.Actions
Microsoft.Graph.Beta.Users.Functions
Microsoft.Graph.Beta.Groups
Microsoft.Graph.Beta.Identity.DirectoryManagement
Microsoft.Graph.Beta.Identity.Governance
Microsoft.Graph.Beta.Identity.SignIns
Microsoft.Graph.Beta.Reports
'@).Split("`n")

# Check if the pre-requisite modules are installed and install them if needed
foreach ($module in $RequiredModules) {
    Write-Host -ForegroundColor Yellow -BackgroundColor DarkBlue "Checking for $module"
    if (!(Get-Module -Name $module -ListAvailable)) {
        Install-Module -Name $module -Scope CurrentUser
    }
}

<# Attribution: https://github.com/SamErde and https://github.com/alexandair #>
```

# [Both Beta and v1.0](#tab/both)

- Install `Beta` and `v1.0` dependencies.

```powershell
$RequiredModules = (@'
Microsoft.Graph.DirectoryObjects
Microsoft.Graph.Users
Microsoft.Graph.Users.Actions
Microsoft.Graph.Users.Functions
Microsoft.Graph.Groups
Microsoft.Graph.Identity.DirectoryManagement
Microsoft.Graph.Identity.Governance
Microsoft.Graph.Identity.SignIns
Microsoft.Graph.Applications
Microsoft.Graph.Beta.Applications 
Microsoft.Graph.Beta.Users
Microsoft.Graph.Beta.Users.Actions
Microsoft.Graph.Beta.Users.Functions
Microsoft.Graph.Beta.Groups
Microsoft.Graph.Beta.Identity.DirectoryManagement
Microsoft.Graph.Beta.Identity.Governance
Microsoft.Graph.Beta.Identity.SignIns
Microsoft.Graph.Beta.Reports
'@).Split("`n")

# Check if the pre-requisite modules are installed and install them if needed
foreach ($module in $RequiredModules) {
    Write-Host -ForegroundColor Yellow -BackgroundColor DarkBlue "Checking for $module"
    if (!(Get-Module -Name $module -ListAvailable)) {
        Install-Module -Name $module -Scope CurrentUser
    }
}

<# Attribution: https://github.com/SamErde and https://github.com/alexandair #>
```

---

## Provide feedback

To file an issue about Microsoft Entra PowerShell module, see: [File an issue on GitHub.][entra-posh-issues]

## Next steps

- To learn more about managing Microsoft Entra resources with the Microsoft Entra PowerShell module, see [Get started](quickstart-entra-powershell.md) article.
- To learn about common installation issues, see the [troubleshooting guide](troubleshooting.md).

[entra-posh-issues]: https://github.com/microsoftgraph/entra-powershell/issues