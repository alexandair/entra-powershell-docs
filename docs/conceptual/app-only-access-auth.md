---
title: "Use app-only authentication"
description: "Learn how to use app-only authentication to enable non-interactive scenarios with the Microsoft Entra PowerShell module."

author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 05/25/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As an IT admin, I want to authenticate with Microsoft Entra ID using app-only access, so that I can perform non-interactive operations, using the Microsoft Entra PowerShell module to manage Microsoft Entra resources.
---

# Use app-only authentication

In this article, you learn how to use app-only access for automation scenarios using the Microsoft Entra PowerShell to manage Microsoft Entra resources.

> [!IMPORTANT]
> App-only access grants permissions directly to an application,
> and requires an administrator to consent to the required permission scopes.
> For more information on app-only access, see
> [Microsoft identity platform and the OAuth 2.0 client credentials flow][client-cred-flow].

## Prerequisites

To use app-only access with the Microsoft Entra PowerShell module, you need:

- A Microsoft Entra ID account. If you don't already have one, you can
  [Create an account for free][entra-id-account].
- One of the following roles: Privileged Role Administrator, Cloud Application Administrator, or Application Administrator.
- Microsoft Entra PowerShell module installed. Follow the [Install the Microsoft Entra PowerShell module][installation] guide to install the module.
- A certificate to use as a credential for the application. The certificate can be a self-signed certificate or a certificate from an authority. For more information on how to create a self-signed certificate, see [Create a self-signed public certificate][self-signed-cert]. Self-signed certificates aren't recommended for production scenarios. Obtain a certificate from a certificate authority for production scenarios.

## Use certificate-based authentication

You should have this information to authenticate using a certificate.

- Certificate subject or thumbprint of the certificate uploaded to your Microsoft Entra app registration.
- Application ID for your app registration. To get the Application ID, see: [Create a custom application][create-custom-application].
- Your tenant ID.

In this section, you learn how to use a certificate to authenticate with the Microsoft Entra PowerShell module. You can use the certificate thumbprint, certificate name, or the certificate itself to authenticate. To authenticate using the given examples, you need to sign in with at least a [Privileged Role Administrator](/entra/role-based-access-control/permissions-reference.md#privileged-role-administrator) role.

### Use Certificate Thumbprint

```powershell
Connect-Entra -ClientId "YOUR_APP_ID" -TenantId "YOUR_TENANT_ID" -CertificateThumbprint "YOUR_CERT_THUMBPRINT"
```

To find the certificate thumbprint in the [Microsoft Entra admin center][entra-admin-center], navigate to **Identity** > **App registrations** > **Certificates & secrets** > **Certificates**. Select the certificate and copy its thumbprint.

Alternatively, you can use the following PowerShell command to get your self-signed certificate:

```powershell
Get-ChildItem Cert:\CurrentUser\My
```

### Use Certificate name

```powershell
Connect-Entra -ClientId "YOUR_APP_ID" -TenantId "YOUR_TENANT_ID" -CertificateName "YOUR_CERT_SUBJECT"
```

You can find the certificate subject by running the command:

```powershell
Get-ChildItem Cert:\CurrentUser\My\$CertThumbprint | Select Subject
```

### Use a certificate

```powershell
$Cert = Get-ChildItem Cert:\CurrentUser\My\$CertThumbprint
Connect-Entra -ClientId "YOUR_APP_ID" -TenantId "YOUR_TENANT_ID" -Certificate $Cert
```

To use a certificate stored in your machine's certificate store or another
location when connecting to Microsoft Entra PowerShell, specify the
certificate's location.

If the authentication succeeds, you see the message
`Welcome To Microsoft Graph!`. Run `Get-EntraContext` to verify that you've
authenticated with app-only method. The output should look like the following.

```powershell
ClientId              : YOUR_APP_ID
TenantId              : YOUR_TENANT_ID
CertificateThumbprint :
Scopes                : {Group.Read.All, User.Read.All}
AuthType              : AppOnly
CertificateName       : YOUR_CERT_SUBJECT
Account               :
AppName               : {Your Awesome Application Name Here}
ContextScope          : Process
Environment           : Global
```

## Use client secret credentials

Client credentials grant is used to authenticate and authorize the app to access resources on its own behalf. Support for client secret credentials is added by adding **-ClientSecretCredential** parameter to **Connect-Entra**. See [Get-Credential][get-credential] on how to get or create credentials.

```powershell
$ClientSecretCredential = Get-Credential -Credential "Client_Id"
# Enter client_secret in the password prompt.
Connect-Entra -TenantId "Tenant_Id" -ClientSecretCredential $ClientSecretCredential
```

To create or add a client secret, see: [Add a client secret][add-client-secret].

>[!NOTE]
>It's recommended to use PowerShell 7 or higher when using client secret credentials authentication method.

## Use managed identity

A common challenge when writing automation scripts is the management of secrets, credentials, certificates, and keys used to secure communication between services. Eliminate the need to manage credentials by allowing the module to obtain access tokens for Azure resources that are protected by Microsoft Entra ID. The identity is managed by the Azure platform and doesn't require you to provision or rotate any secrets.

- **System-assigned managed identity** - Uses an automatically managed identity on a service instance. The identity is tied to the lifecycle of a service instance.

  ```powershell
  Connect-Entra -Identity
  ```

- **User-assigned managed identity** - Uses a user created managed identity as a standalone Azure resource.

  ```powershell
  Connect-Entra -Identity -ClientId "User_Assigned_Managed_identity_Client_Id"
  ```

## Next steps

- [Manage groups with Microsoft Entra PowerShell][manage-groups]

<!-- link references -->
[client-cred-flow]: /entra/identity-platform/v2-oauth2-client-creds-grant-flow
[entra-id-account]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[installation]: installation.md
[self-signed-cert]: /entra/identity-platform/howto-create-self-signed-certificate
[create-custom-application]: create-custom-application.md
[get-credential]: /powershell/module/microsoft.powershell.security/get-credential
[entra-admin-center]: https://entra.microsoft.com
[add-client-secret]: /entra/identity-platform/quickstart-register-app#add-a-client-secret
[manage-groups]: tutorial-groups.md
