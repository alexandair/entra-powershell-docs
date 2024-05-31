---
title: "Manage users with Microsoft Entra PowerShell"
description: "Learn how to use app-only authentication to enable non-interactive scenarios with the Microsoft Entra PowerShell SDK."

author: omondiatieno
manager: CelesteDG
ms.topic: how-to
ms.date: 05/22/2024
ms.author: jomondi
ms.reviewer: stevemutungi

#customer intent: As a developer, I want to authenticate with Microsoft Entra using app-only access, so that I can perform non-interactive operations, such as listing users and groups, using the Microsoft Entra PowerShell SDK.
---

# Manage users with Microsoft Entra PowerShell

Users are the representation of a Microsoft Entra work or school user account or a personal Microsoft account in Microsoft Entra PowerShell. The [user](link-to-cmdlet-for-user) resource in Microsoft Entra PowerShell is the representation of a user, and includes relationships and resources that are relevant to the user.

You can use Microsoft Entra PowerShell to access the relationships, documents, contacts, and preferences that are contextually relevant to a user. The user resource provides straightforward way for you to access and manipulate user resources without having to perform extra calls, look up specific authentication information, and directly issue queries against other Microsoft Entra PowerShell objects.

## Prerequisites

To manage users with Microsoft Entra PowerShell, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free][create-acount].
- One of the following roles: Global Administrator, User Administrator, or Group Administrator.
- Microsoft Entra PowerShell SDK installed. Follow the [Install the Microsoft Entra PowerShell SDK][installation] guide to install the SDK.

You can access a user's information and manage their data on their behalf or as an app with its own identity.

## Manage users in your organization

To manage users, you can perform the following common user management tasks:

### Create and delete users

1. Create a new user using the `UserPrincipalName` parameter.

    ```powershell
    $PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
    $PasswordProfile.Password = "<Password>"
    New-EntraUser -DisplayName "New User" -PasswordProfile $PasswordProfile -UserPrincipalName "NewUser@contoso.com" -AccountEnabled $true -MailNickName "NewUser"
    ```

    ```output
    ObjectId                             DisplayName UserPrincipalName               UserType
    --------                             ----------- -----------------               --------
    aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb New user    NewUser@contoso.com             Member
    ```

1. Delete a user.

    ```powershell
    Remove-EntraUser -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

### List a user's group memberships and determine whether a user is a member of a group

1. List a user’s group memberships.

    ```powershell
    Get-EntraUserMembership -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

    ```output
    Id                                   DeletedDateTime
    --                                   ---------------
    eeeeeeee-4444-5555-6666-ffffffffffff
    ffffffff-5555-6666-7777-gggggggggggg
    gggggggg-6666-7777-8888-hhhhhhhhhhhh
    hhhhhhhh-7777-8888-9999-iiiiiiiiiiii
    ```

### List the users who report to a user and assign managers to a user

1. Get a user's manager.

    ```powershell
    Get-EntraUserManager -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

    ```output
    ageGroup                        :
    onPremisesLastSyncDateTime      :
    creationType                    :
    imAddresses                     : {UserManager@contoso.com}
    preferredLanguage               :
    mail                            : UserManager@contoso.com
    securityIdentifier              : S-1-12-1-2222222222-3333333333-4444444444-5555555555
    identities                      : {@{signInType=userPrincipalName; issuer=contoso.com; issuerAssignedId=UserManager@contoso.com}}
    consentProvidedForMinor         :
    onPremisesUserPrincipalName     :
    ```

1. List the users who report to a specific user.

    ```powershell
    Get-EntraUserDirectReport -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

    ```output
    ageGroup                        :
    onPremisesLastSyncDateTime      :
    creationType                    :
    imAddresses                     : {User@contoso.com}
    preferredLanguage               :
    mail                            : User@contoso.com
    securityIdentifier              : S-1-12-1-2222222222-3333333333-4444444444-5555555555
                                      S-1-12-1-3333333333-4444444444-5555555555-6666666666
    identities                      : {@{signInType=userPrincipalName; issuer=contoso.com; issuerAssignedId=User@contoso.com}}
    consentProvidedForMinor         :
    onPremisesUserPrincipalName     :
    assignedLicenses                : {@{disabledPlans=System.Object[]; skuId=0a0a0a0a-1111-bbbb-2222-3c3c3c3c3c3c}, @{disabledPlans=System.Object[]; skuId=1b1b1b1b-2222-cccc-3333-4d4d4d4d4d4d},
                                    @{disabledPlans=System.Object[]; skuId=2c2c2c2c-3333-dddd-4444-5e5e5e5e5e5e}}
    ```

1. Assign a manager to a user.

    ```powershell
    Set-EntraUserManager -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb" -RefObjectId "bbbbbbbb-1111-2222-3333-cccccccccccc"
    ```

### Upload or retrieve a photo for the user

1. Upload a photo for a user.

    ```powershell
    Set-EntraUserThumbnailPhoto -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb" -FilePath D:\UserThumbnailPhoto.jpg
    ```

This example sets the thumbnail photo of the user specified with the ObjectId parameter to the image specified with the FilePath parameter.

1. Retrieve a user’s photo.

    ```powershell
    Get-EntraUserThumbnailPhoto -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

This example demonstrates how to retrieve the thumbnail photo of a user that is specified through the value of the ObjectId parameter.

### Grant users administrative roles in your organization

Grant a user an administrative role.

```powershell
Add-EntraDirectoryRoleMember -ObjectId "cccccccc-2222-3333-4444-dddddddddddd" -RefObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
```

This command adds a user to a Microsoft Entra role.

### Work with user licenses

1. Get details of a user's licenses.

    ```powershell
    Get-EntraUserLicenseDetail -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"
    ```

    ```output
    ObjectId                                    ServicePlans
    --------                                    ------------
    Ab-1cccccccccc-dddddddddddddddddddddddddddd {class ServicePlanInfo {...
    Bc-1dddddddddd-eeeeeeeeeeeeeeeeeeeeeeeeeeee {class ServicePlanInfo {...
    ```

1. Assign a license to a user based on a template user.

    ```powershell
    $LicensedUser = Get-EntraUser -ObjectId "dddddddd-3333-4444-5555-eeeeeeeeeeee"  
    $User = Get-EntraUser -ObjectId "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"  
    $License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
    $License.SkuId = $LicensedUser.AssignedLicenses.SkuId 
    $Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
    $Licenses.AddLicenses = $License 
    Set-EntraUserLicense -ObjectId $User.ObjectId -AssignedLicenses $Licenses
    ```

   For more information on the template user, see [Set-EntraUserLicense][set-entrauserlicense]

1. Remove a license from a user.

<TBD - Steve to advise on the cmdlets for removing a license from a user>

## Next steps

[Manage groups][tutorial-groups]

<!-- link references -->

[installation]: installation.md
[tutorial-groups]: tutorial-groups.md
[create-acount]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[set-entrauserlicense]: set-entrauserlicense.md