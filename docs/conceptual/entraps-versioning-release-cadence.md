---
title: "Versioning, release cadence, and breaking changes"
description: "This article describes versioning, release cadence, and breaking change information for the Microsoft Entra PowerShell module."

ms.topic: concept-article
ms.date: 05/21/2024
ms.service: entra

author: omondiatieno
manager: CelesteDG
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As a Microsoft Entra PowerShell user, I want to understand the versioning, release cadence, and breaking changes policies so that I can plan and manage updates to my production environment effectively and minimize the risk of disruptions caused by breaking changes.
---

# Versioning, release cadence, and breaking changes

If you use Microsoft Entra PowerShell modules, it's important to understand the versioning, release cadence, and breaking changes policies to effectively manage updates to your production environment and minimize the risk of disruptions caused by breaking changes.

This article covers the versioning scheme used by Microsoft Entra PowerShell modules, the release cadence for planned updates, and the policies for breaking changes.

## Versioning

The Microsoft Entra PowerShell modules follow [Semantic Versioning](https://semver.org/) for version numbering.
Versions of Microsoft Entra PowerShell modules fall into one of the following three categories:

- **Generally available/v1.0**: Module version 1.0.0 and higher without _preview_ in the version. Adheres to breaking change policy.
- **Beta**: Module less than version 1.0.0. Don't adhere to breaking change policy.
- **Feature preview**: Module version 1.0.0 and higher with _preview_ in the version. The feature preview version doesn't adhere to the breaking change policy.

There are two Microsoft Entra PowerShell modules:

- **[Microsoft.Graph.Entra](https://www.powershellgallery.com/packages/Microsoft.Graph.Entra/)**: Installs the GA/v1.0 module to manage Microsoft Graph resources with `/v1.0` API version.
- **[Microsoft.Graph.Entra.Beta](https://www.powershellgallery.com/packages/Microsoft.Graph.Entra.Beta/)**: Installs the Beta module to manage Microsoft Graph resources with `/beta` API version.

## Release cadence

Planned updates to the Microsoft Entra PowerShell module are released on the first Wednesday of each month. These
12 planned updates per calendar year are in two categories:

- **Major versions**: At most, four per calendar year introduces breaking changes. The first number in the
  version number is updated. For example, version 1.6.0 to version 2.0.0.
- **Minor versions**: 10 per calendar year that doesn't introduce breaking changes. The second number in
  the version number is updated. For example, version 1.0.0 to version 1.1.0.
- **Experimental versions**: Every two weeks. Users can try out the latest versions without waiting for a full release by building the module from the GitHub repo.

Before upgrading to a major breaking change version of the Microsoft Entra PowerShell module, we recommend testing the breaking changes in a non-production environment.
> Before upgrading to a major breaking change version of the Microsoft Entra PowerShell module, you should test the breaking changes in a non-production environment.

Unplanned patch versions can be released at any time to fix bugs and don't introduce
breaking changes. The third number in the version number is updated. For example, version 1.2.0 to
version 1.2.1.

## Breaking changes

> [!IMPORTANT]
> Breaking changes can occur at any point for non-GA (Beta module) and feature preview modules. Non-GA
> modules aren't required to adhere to breaking change policies.

### When do breaking changes occur

We release breaking changes four times per year (March, June, September, and November). Communication will be done through our [Microsoft Entra community blog][entra-community-blog] and in our [What's new in Microsoft Entra ID][whats-new-in-entra] documentation.

## See Also

- [What's new in Microsoft Entra PowerShell][whats-new].

<!-- link references -->
[entra-community-blog]: https://techcommunity.microsoft.com/t5/microsoft-entra-blog/bg-p/Identity
[whats-new-in-entra]: /entra/fundamentals/whats-new
[whats-new]: whats-new-docs.md