---
title: Migrate to Microsoft Entra PowerShell 
description: Learn about how to migrate from Azure AD PowerShell to Microsoft Entra PowerShell.

author: csmulligan
manager: CelesteDG
ms.topic: concept-article
ms.date: 04/05/2024
ms.author: cmulligan

#Customer intent: As an IT admin, I want to learn how to transition my existing scripts from Azure AD PowerShell to Microsoft Entra PowerShell for the best usability benefits.
---
# Migrate to Microsoft Entra PowerShell

Microsoft Entra PowerShell has over _98%_ compatibility with [Azure AD PowerShell][azuread-ps] module.
This article details the process of running your existing AzureAD PowerShell scripts with minimal modifications using Microsoft Entra PowerShell by using the `Enable-EntraAzureADAlias` command.

## Use compatibility mode with Enable-EntraAzureADAlias

The `Enable-EntraAzureADAlias` cmdlet enables compatibility mode through aliases. By default, Enable-EntraAzureADAlias only enables compatibility aliases for the current Microsoft Entra PowerShell session. For more information, see the [Enable-EntraAzureADAlias](/powershell/entra-preview/microsoft.graph.entra/enable-entraazureadalias) reference documentation.

To use Microsoft Entra PowerShell with your existing AzureAD PowerShell scripts, replace the `Connect-AzureAD` command with the three lines provided.

```powershell
Import-Module -Name Microsoft.Graph.Entra
Connect-Entra #Replaces Connect-AzureAD for auth
Enable-EntraAzureADAlias #enable aliasing 
```

### Example

In this example, you want to run a script that exports apps with expiring secrets using Microsoft Entra PowerShell. This example assumes that the Microsoft Entra PowerShell module is already [installed][installation].

<!--Check this example. I got the feedback: I don't understand this interaction. You are making a statement, not asking a question.

Use the -Prompt parameter of Read-Host. -->

```powershell
Connect-AzureAD
$Applications = Get-AzureADApplication -All $true
$Logs = @()
Write-Host "I would like to see the Applications with the Secrets and Certificates that expire in the next X amount of Days? <<Replace X with the number of days. The answer should be ONLY in Numbers>>" -ForegroundColor Green
$Days = Read-Host

Write-Host "Would you like to see Applications with already expired secrets or certificates as well? <<Answer with [Yes] [No]>>" -ForegroundColor Green
$AlreadyExpired = Read-Host

$now = Get-Date

foreach ($app in $Applications) {
    $AppName = $app.DisplayName
    $AppID = $app.objectid
    $ApplID = $app.AppId
    $AppCreds = Get-AzureADApplication -ObjectId $AppID | Select-Object -Property PasswordCredentials, KeyCredentials
    $secret = $AppCreds.PasswordCredentials
    $cert = $AppCreds.KeyCredentials

```

To use your script with the Microsoft Entra PowerShell module, replace the `Connect-AzureAD` cmdlet with the three lines provided in the snippet. You don’t need to rewrite the entire script. This code snippet is shortened for simplicity.

```powershell
Import-Module -Name Microsoft.Graph.Entra
Connect-MgGraph #Replaces Connect-AzureAD for auth
Enable-EntraAzureADAlias #Activate aliasing

$Applications = Get-AzureADApplication -All $true
$Logs = @()
Write-Host "I would like to see the Applications with the Secrets and Certificates that expire in the next X amount of Days? <<Replace X with the number of days. The answer should be ONLY in Numbers>>" -ForegroundColor Green
$Days = Read-Host
Write-Host "Would you like to see Applications with already expired secrets or certificates as well? <<Answer with [Yes] [No]>>" -ForegroundColor Green
$AlreadyExpired = Read-Host
$now = Get-Date
foreach ($app in $Applications) {
    $AppName = $app.DisplayName
    $AppID = $app.Objectid
    $ApplID = $app.AppId
    $AppCreds = Get-AzureADApplication -ObjectId $AppID | Select-Object -Property PasswordCredentials, KeyCredentials
    $secret = $AppCreds.PasswordCredentials
    $cert = $AppCreds.KeyCredentials
```

## Test compatibility with Test-EntraScript command

The `Test-EntraScript` cmdlet verifies if a script with AzureAD commands works with the Microsoft Entra PowerShell module. If there are compatibility issues, it lists them, including the line number, issue type, incompatible command, and the specific code snippet.

## Known issues

When migrating from the Azure AD PowerShell module to Microsoft Graph endpoints, you might encounter several known issues.

- Parameter `-Filter` might not work correctly.
- Parameter `-SearchString` might not work correctly.
- Output objects may differ slightly with AzureAD output objects.

## Related content

- [Introducing the Microsoft Entra PowerShell module](quickstart-entra-powershell.md)
- [Install the Microsoft Entra PowerShell module](installation.md)

<!-- link references -->
[azuread-ps]: /powershell/module/azuread
[enable-azuread-alias]: installation.md
[known-issues]: known-issues.md
[github-issues]: https://github.com/microsoftgraph/entra-powershell/issues
[installation]: installation.md