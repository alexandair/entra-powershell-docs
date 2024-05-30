---
title: Microsoft Entra PowerShell overview

description: "Learn about the features of Microsoft Entra PowerShell that can help you derive insights and analytics, and build unique, intelligent apps in Microsoft Entra ID."
ms.topic: overview
ms.date: 05/14/2024
author: omondiatieno
manager: CelesteDG
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to learn about Microsoft Entra PowerShell, so that I can get started with using the module.
---
# Microsoft Entra PowerShell overview

The Microsoft Entra PowerShell module is a scenario-focused command-line tool that allows administrators to manage and automate Microsoft Entra product family resources programmatically. This includes efficiently managing users, groups, applications, service principals, policies, and more. The module builds upon and is part of the Microsoft Graph PowerShell SDK and is fully interoperable with all cmdlets in the Microsoft Graph PowerShell SDK, enabling you to perform complex operations with simple, well documented commands. The module also offers a backward compatibility option with the [deprecated AzureAD Module](https://techcommunity.microsoft.com/t5/microsoft-entra-blog/important-update-deprecation-of-azure-ad-powershell-and-msonline/ba-p/4094536) to accelerate migration. We recommend using PowerShell version 7 or higher with the Entra PowerShell module on all platforms, including Windows, Linux, and macOS.

## Microsoft Graph PowerShell vs. Microsoft Entra PowerShell

Microsoft Entra PowerShell is a part of our increased investment in Microsoft Graph PowerShell SDK. It brings high-quality and scenario-optimized Entra resource management to the Microsoft Graph PowerShell SDK. Still, it keeps all the benefits of Microsoft Graph PowerShell SDK for authorization, connection management, error handling, and (low-level) API coverage. As Entra PowerShell builds on the Microsoft Graph PowerShell SDK, it is completely interoperable.

## Microsoft Entra PowerShell features & benefits

The Microsoft Entra PowerShell provides the following benefits:

- **Focus on usability and quality**: Microsoft Entra PowerShell offers human-readable parameters, deliberate parameter set specification, inline documentation, and core PowerShell fundamentals like pipelining.
- **Flexible and granular authorization**: Consistent with Microsoft Graph PowerShell SDK, Entra PowerShell enables administrative consent for the permissions you want to grant to the application and supports specifying your own application identity for maximum granularity in app permission assignment. You can also use certificate, Service Principal, or Managed Identity auth patterns.
- **Open Source**: The Microsoft Entra PowerShell module is open source, allowing contributions from the community to create great PowerShell experiences and share them with everyone. Open source promotes collaboration and facilitates the development of innovative business solutions. You can view Microsoft's customizations and adapt them to meet your needs.
- **Cross-Platform Support**: Microsoft Entra PowerShell module works on all platforms, including Windows, macOS, and Linux, providing flexibility in managing Entra resources across different operating systems. Note: Cross platform works if you're using PowerShell 7 or higher.
- **Backward compatibility with AzureAD module**: Accelerates migration from the recently announced AzureAD module deprecation.
- **Regular Updates**: Microsoft Entra PowerShell commands are updated regularly to support the latest Graph API and product feature updates, ensuring that users have access to the latest features and capabilities.

## Migrate from AzureAD PowerShell module

Microsoft Entra PowerShell is over 98% compatible with the AzureAD module and selected MSOnline cmdlets. By using the `Enable-EntraAzureADAlias` command, you only need to update one or two lines in your existing scripts, making migration to Microsoft Graph PowerShell quick and effortless. To learn how to migrate from [Azure AD PowerShell][azure-ad-powershell] or [MSOnline][msonline-powershell] to Microsoft Entra PowerShell, follow this [migration guide][migration-guide].

## Installation and Get started

Microsoft Entra PowerShell module is published on the [PowerShell Gallery][powershell-gallery]. Follow the [installation][installation] instructions to install the Microsoft Entra PowerShell module.

To start managing Microsoft Entra resources such as creating users, groups, and other tasks, see [Get-started][get-started] guide.

## The right start - Microsoft Entra PowerShell best practices

You can apply the [best practices guide][best-practices-guide] to optimize use of Microsoft Entra PowerShell, ensure efficient scripting, secure access, and effective resource management. This guide helps you follow recommended methods, avoiding common pitfalls and enhancing overall productivity.

## Known Issues

Here are the known issues with the Microsoft Entra PowerShell module, along with recommended workarounds.

|          Feature          |                                                                Issue                                                                 |                                   Workaround/Comments                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
| `-All` parameter          | We don't support `-All` Boolean parameter as was the case with AzureAD PowerShell module. `-All` is supported as a switch parameter. | Replace `-All:$true` with `-All` parameter in your scripts.                             |
| `-SearchString` parameter | The parameter `-SearchString` may not work as expected.                                                                              | No workaround. `-SearchString` is offered for backward compatibility with AzureAD only. |

## Next steps

- Create a free [Microsoft Entra ID account][free-entra-id].
- Got questions? Check out our [Frequently Asked Questions][faqs]

[free-entra-id]: https://azure.microsoft.com/free/entra-id
[azure-ad-powershell]: /powershell/module/azuread
[msonline-powershell]: /powershell/module/msonline
[migration-guide]: migration-guide.md
[get-started]: quickstart-entra-powershell.md
[installation]: installation.md
[powershell-gallery]: installation.md
[faqs]: entraps-faq.yml
[best-practices-guide]: installation.md