---
title: "Install Microsoft Entra PowerShell on Windows"
description: "Learn how to install the Microsoft Entra PowerShell module on Windows."

author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 05/07/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to learn how to install Microsoft Entra PowerShell module on Windows so that I can manage Microsoft Entra resources through PowerShell.
---

# Install the Microsoft Entra PowerShell module on Windows

The recommended installation method and PowerShell version for the Entra PowerShell module:

- Install from the [PowerShell Gallery][posh-gallery]
- Use with PowerShell version 5.1+ or version 7+.

## Prerequisites

- Run the following command from PowerShell to determine your PowerShell version:

  ```powershell
  $PSVersionTable.PSVersion
  ```

- Install [Microsoft Graph PowerShell SDK module dependencies](#install-dependencies) if not installed.

- Determine if you have the Entra PowerShell module installed:

  ```powershell
  Get-Module -Name Microsoft.Graph.Entra -ListAvailable
  ```

# [PowerShell 7](#tab/powershell)

- Install a supported version of
  [PowerShell version 7 or higher][install-windows]

# [Windows PowerShell](#tab/windowspowershell)

- Update to
   [Windows PowerShell 5.1][posh-5.1]
- Install [.NET Framework 4.7.2 or later](/dotnet/framework/install)
- Update PowerShellGet

   To update PowerShellGet, launch Windows PowerShell 5.1 elevated as an administrator and run the following command:

   ```powershell
   Install-Module -Name PowerShellGet -Force -AllowClobber
   ```

---

- Set the PowerShell execution policy to remote signed or less restrictive

  - Check the PowerShell execution policy:

    ```powershell
    Get-ExecutionPolicy -List
    ```

  - Set the PowerShell execution policy to remote signed:

    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

  For more information about execution policies, see
  [about_Execution_Policies][execution-policies].

## Installation

Use the [Install-Module][install-module] cmdlet to install the Entra PowerShell module:

```powershell
Install-Module -Name Microsoft.Graph.Entra -Scope CurrentUser -AllowPrerelease
```

Optionally, you can change the scope of the installation using the **Scope** parameter. This operation requires admin permissions.

```powershell
Install-Module -Name Microsoft.Graph.Entra -Scope AllUsers -AllowPrerelease
```

To install the `Beta` module, run the following command.

```powershell
Install-Module -Name Microsoft.Graph.Entra.Beta -AllowPrerelease
```

> [!IMPORTANT]
> We recommend using Microsoft Entra PowerShell v1.0 (GA) module for script writing. If you need to test or adopt features not yet available in v1.0, you might use the Beta module. However, the cmdlets in the Beta version can change unexpectedly, which makes it unsuitable for production as it could break existing scripts.

### Verify installation

After the installation is completed, you can verify the installed version with the following command.

```powershell
Get-InstalledModule -Name Microsoft.Graph.Entra
```

To verify the installed submodules and their versions, run:

```powershell
Get-InstalledModule
```

The version in the output should match the latest version published on the PowerShell Gallery. Now you're ready to use the module.

## Updating the module

Use [Update-Module][update-module] to update to the latest version
of the Microsoft Entra PowerShell.

```powershell
Update-Module -Name Microsoft.Graph.Entra -AllowPrerelease
```

Updating the Entra PowerShell module using `Update-Module` doesn't remove old versions of the Entra PowerShell module from your system.

## Uninstalling the module

To remove the Entra PowerShell module, run the command:

```powershell
Uninstall-Module -Name Microsoft.Graph.Entra -AllVersions
```

## Sign in

To start managing your Entra resources with the Entra PowerShell module, launch a PowerShell session and run `Connect-Entra` to sign in to Microsoft Entra ID:

```powershell
Connect-Entra
```

See [more authentication][auth-methods] options.

## Troubleshooting

For solutions to common installation issues with the Entra PowerShell module, see [Troubleshoot installation problems with the Entra PowerShell module][troubleshooting].

## Install Dependencies

The Microsoft Entra PowerShell module requires certain Microsoft Graph PowerShell SDK modules. The following snippet installs these dependencies if they are not already installed.

[!INCLUDE [dependencies](../includes/install-entra-powershell-dependencies.md)]

## Provide feedback

To file an issue about Microsoft Entra PowerShell module, see: [File an issue on GitHub.][entra-posh-issues]

## Next steps

- To learn more about managing Entra resources with the Entra PowerShell module, see [Get started][get-started] article.
- To learn about common installation issues, see the [troubleshooting guide][troubleshooting].

[entra-posh-issues]: https://github.com/microsoftgraph/entra-powershell/issues
[get-started]: quickstart-entra-powershell.md
[auth-methods]: authentication-methods.md
[troubleshooting]: troubleshooting.md
[update-module]: /powershell/module/powershellget/update-module
[execution-policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[install-module]: /powershell/module/powershellget/install-module
[posh-5.1]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[install-windows]: /powershell/scripting/install/installing-powershell-on-windows
[posh-gallery]: https://www.powershellgallery.com/packages/Microsoft.Graph.Entra