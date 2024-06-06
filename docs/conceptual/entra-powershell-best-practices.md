---
title: "Microsoft Entra PowerShell best practices"
description: "Learn how to optimize performance, enhance security, and ensure scalability when working with Microsoft Entra PowerShell."

ms.topic: concept-article
ms.date: 05/23/2024
ms.service: entra
author: omondiatieno
manager: CelesteDG
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to understand the best practices when interacting with Microsoft Entra PowerShell module for improved performance and security posture.
---

# Microsoft Entra PowerShell best practices

This article shares best practices for using the Microsoft Entra PowerShell module to boost performance, enhance security, and scale reliably.

## Register an app instead of using a Microsoft Enterprise app

You can register your own applications tailored to different use cases with specific permissions, such as for marketing or help desk teams. This approach allows for more granular permission management and minimizes the security impact if an app is compromised. To create a registered app, see [Create a custom application][create-a-custom-app].

Sign in using the application you register by running:

```powershell
Connect-Entra -ClientId <your-custom-app-id> -TenantId <your-tenant-id> -CertificateName <certificate-subject>
```

You can also use the aliases `AppId` or `ApplicationId` instead of `ClientId`.

## Security

Apply the following consent and authorization best practices in your app to enhance security:

- **Apply least privilege**: Grant users and apps only the lowest privileged permission they require to call the Microsoft Entra resource. Choose the least privileged permissions. For example, if the app reads only the profile of the currently signed-in user, grant `User.Read` instead of `User.ReadBasic.All`. For a full list of permissions, see [permissions reference][permissions-ref].

- **Use the correct permission type based on scenarios**: Avoid using both application and delegated permissions in the same app. If you're building an interactive application where a signed-in user is present, your application should use *delegated permissions*. If, however, your application runs without a signed-in user, such as a background service or daemon, your application should use *application permissions*.

- **Be thoughtful with application permissions**: Avoid using application permissions for interactive scenarios to prevent security and compliance risks, as this can unintentionally elevate a user's privileges and bypass administrator policies.

- **Be thoughtful when configuring your app**: This affects end user and admin experiences, along with application adoption and security. For example:

  - Your application's name, logo, domain, publisher verification status, privacy statement, and terms of use show up in consent and other experiences. Configure these settings carefully so that your end users understand them.
  - Consider who consents to your application - either end users or administrators - and configure your application to [request permissions appropriately](/azure/active-directory/develop/active-directory-v2-scopes).
  - Ensure that you understand the difference between [static, dynamic, and incremental consent](/azure/active-directory/develop/v2-permissions-and-consent#consent-types).

- **Consider multi-tenant applications**. Expect customers to have various application and consent controls in different states. For example:

  - Tenant administrators can disable the ability for end users to consent to applications. In this case, an administrator would need to consent on behalf of their users.
  - Tenant administrators can set custom authorization policies such as blocking users from reading other user's profiles, or limiting self-service group creation to a limited set of users. In this case, your application should expect to handle `403 Forbidden` error response when acting on behalf of a user.

- **Watch out for permission creep** - Keep an eye on the permissions that accrue for the registered app over time.

- **Leverage Microsoft Entra recommendations** - [Microsoft Entra recommendations][entra-recommendations] feature diligently monitor your tenant’s status, ensuring it remains secure and healthy. You have visibility into used apps, expiring credentials, over-privileged applications among others.

## Performance optimizations

The following practices can help you optimize performance when working with Microsoft Entra PowerShell:

### Use a filter

Filtering is done on the server side by limiting your selection to retrieve a subset of a collection, which helps reduce unnecessary network traffic and data processing.

```powershell
Get-EntraUser -Filter "startswith(DisplayName,'Ada')"
```

### Select only required properties

Selecting the required properties by using the `-Property` parameter to only get required properties.

## Maintenance

Apply the following maintenance best practices to ensure your Microsoft Entra PowerShell module and scripts are up to date and functioning optimally:

### Keep Microsoft Entra PowerShell module up to date

Keeping your module up to date is crucial for several reasons. Firstly, it allows you to benefit from the latest features and enhancements, ensuring you have access to the most current cmdlets and functionalities. More importantly, regular updates improve your security posture. Our team consistently implements security fixes and patches, helping to protect your systems from vulnerabilities.

> [!TIP]
> If you use the Microsoft Entra PowerShell with Azure Automation, update the PowerShell modules in your Azure Automation accounts as well.

```powershell
Update-Module -Name Microsoft.Graph.Entra
```

After upgrading your module, remove the older versions.

### Use Get-Help

`Get-Help` provides immediate access to comprehensive documentation right in the command line. This command offers detailed information about Microsoft Entra PowerShell cmdlets, functions, scripts, and concepts, including examples of how to use them, parameters they accept, and the output they generate. Get-Help promotes more efficient scripting, and helps avoid common mistakes.

```powershell
Get-Help Get-EntraUser -Detailed
```

### Use the debug option

`-Debug` helps you in troubleshooting by providing detailed diagnostic information as you interact with Microsoft Entra PowerShell. It can help you understand exactly how your scripts are functioning and where any problems might arise during development and testing phase.

```powershell
Get-EntraUser -Top 1 -Debug
```

<!-- link references -->
[permissions-ref]: entraps-permissions-guide.md
[entra-recommendations]: /entra/identity/monitoring-health/overview-recommendations
[create-a-custom-app]: create-custom-application.md
