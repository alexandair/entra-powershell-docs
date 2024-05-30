---
title: "Create a custom application to connect to Microsoft Entra PowerShell"
description: "Learn how to create a custom application to be used authenticate to Microsoft Entra PowerShell."

ms.topic: how-to
ms.date: 05/23/2024
author: omondiatieno
manager: CelesteDG
ms.author: jomondi
ms.reviewer: stevemutungi254

#customer intent: As a Microsoft Entra PowerShell user, I want to understand how to create a custom application to improve my security posture.
---

# Create a custom application to connect to Microsoft Entra PowerShell

## Prerequisites

To create a custom application and grant it permissions, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- One of the following roles: Cloud Application Administrator, or Application Administrator.

## Use Microsoft Entra admin center

To create custom applications for connecting to Microsoft Entra ID using Microsoft Entra PowerShell, follow the steps in the following section. Use the custom application to isolate and limit the permissions granted for a Microsoft Entra resource.

1. Sign in to the [Microsoft Entra admin center][entra-admin-portal] as at least a [Cloud Application Administrator][cloud-app-admin].
1. Browse to **Identity** > **Applications** > **App registrations** and then select > **New Registration**.
1. Enter a name for your application, for example *Microsoft Entra PowerShell App*.
1. For **Supported account types**, select **Accounts in this organization directory**.
1. For **Redirect URI** select:
        - **Public client/native** from the drop-down
        - **URI value**: `http://localhost`
1. Select **Register**.
To manage the resources that your application gets access to in your tenant, locate the application's service principal in the **Enterprise applications** pane.

1. Browse to **Identity** > **Applications** > **Enterprise applications** > **All applications** and select the application you created.
    1. Under **Manage**, select **Properties** and set **Assignment required?** to **Yes**.
    1. Select **Save**.
    1. Under **Manage**, select **Users and groups**.
    1. Select **Add user/group** and add the users and groups permitted to use this application.
    1. Once you add all the users and groups, select **Assign**.

>[!NOTE]
> In the app's **Overview** section, copy the Application (client ID) and Directory (tenant) ID. You use the values when connecting to Microsoft Entra ID.

### Assign API permissions to the custom application

You need to set up Microsoft Graph permissions for the new application to connect to Microsoft Entra ID and manage Microsoft Entra resources.

1. Browse to **Identity** > **Applications** > **Enterprise applications** > **All applications** and select the application you created.
1. Under **API permissions**, select **Add a permission** > Select Microsoft APIs > Microsoft Graph.
1. Choose the type of permissions you require, either delegated or application permissions. 
    - If you need to sign in to the app to manage your resources in Microsoft Entra ID, select **Delegated permissions**.
    - If you want the app to access Microsoft Entra resources on its own without user interaction, select **Application permissions**
1. Search for the required permission for example, `User.Read.All`.
1. Select **Grand admin consent for TenantName**. Select **Yes**. Ensure the status shows a green checkmark.

You can now use the newly created app by connecting with:

```powershell
Connect-Entra -ClientId <YOUR_NEW_APP_ID> -TenantId <YOUR_TENANT_ID>
```

For more connection options, see the [Connect-Entra][connect-entra-command] command details.

<!-- link references -->
[entra-admin-portal]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[cloud-app-admin]: /entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator
[connect-entra-command]: installation.md