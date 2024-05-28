---
title: Use Find-EntraCommand cmdlet 
description: Learn how to use the Find-EntraCommand to find cmdlets.

author: csmulligan
manager: CelesteDG
ms.topic: how-to
ms.date: 05/01/2024
ms.author: cmulligan

#customer intent: As a PowerShell user, I want to use the Find-EntraCommand cmdlet to easily discover the API path that a command calls, so that I can efficiently work with Microsoft Entra PowerShell commands and understand the permissions required for each command.
---

# Use Find-EntraCommand cmdlet 

Find-EntraCommand aims to make it easier for you to discover which API path a command calls, by providing a URI or a command name.

The Find-EntraCommand allows to:

- Pass a Microsoft Graph URL (relative and absolute) and get an equivalent Microsoft Entra PowerShell command.
- Pass a command and get the URL it calls.
- Pass a command or URI wildcard (.*) to find all commands that match it.

The output of this cmdlet also includes the permissions required to authenticate the specified cmdlet. For more information on cmdlet permissions, see  [Use  Find-EntraPermission](find-entra-permission.md). Not all cmdlets have the permissions available on running this command. This is an ongoing feature, and permissions will continue to be added.

The permissions displayed don't show the privilege levels. To learn more, including how to choose permissions, permission type and what is the most privileged/least privileged permission, use the corresponding API page doc.

## Find Microsoft Entra PowerShell commands by URI

### Syntax

```powershell
Find-EntraCommand -Uri <String[]> [-Method <String>] [-ApiVersion <String>] [<CommonParameters>]
```

### Examples

#### Example 1: Use a URI to get all related cmdlets

```powershell
Find-EntraCommand -Uri '/users/{id}'
```

```Output
 APIVersion: v1.0
Command       Module Method URI              OutputType           Permissions                                                                                                                                                    Variants
-------       ------ ------ ---              ----------           -----------                                                                                                                                                    --------
Get-EntraUser    Users  GET    /users/{user-id} IMicrosoftGraphUser1 {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...}  {Get1, GetViaIdentity1}
Remove-EntraUser Users  DELETE /users/{user-id}                      {DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All, Directory.AccessAsUser.All}    {Delete, DeleteViaIdentity}
Update-EntraUser Users  PATCH  /users/{user-id}                      {DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All, Directory.AccessAsUser.All...} {Update, UpdateExpanded, UpdateViaIdentity, UpdateViaIdentityExpanded}
   APIVersion: beta
Command       Module Method URI              OutputType          Permissions                                                                                                                                                    Variants
-------       ------ ------ ---              ----------          -----------                                                                                                                                                    --------
Get-EntraUser    Users  GET    /users/{user-id} IMicrosoftGraphUser {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...}  {Get, GetViaIdentity}
Remove-EntraUser Users  DELETE /users/{user-id}                     {DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All, Directory.AccessAsUser.All}    {Delete1, DeleteViaIdentity1}
Update-EntraUser Users  PATCH  /users/{user-id}                     {DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All, DeviceManagementServiceConfig.ReadWrite.All, Directory.AccessAsUser.All...} {Update1, UpdateExpanded1, UpdateViaIdentity1, UpdateViaIdentityExpanded1}
```

>[!Note]
>1. For **-ApiVersion** parameter, there are two possible values: `v1.0` and `Beta`.
>1. The **-Method** parameter is only available when using URI to find commands and allows the HTTPs methods such as GET, POST, PUT, PATCH and DELETE.
>1. The output shown in this article has been shortened for readability.
## Find Microsoft Entra PowerShell commands by command name

### Syntax

```powershell
Find-EntraCommand -Command <String[]> [-ApiVersion <String>] [<CommonParameters>]
```

### Examples

#### Example 1: Pass a command and get the URI it calls

```powershell
Find-EntraCommand -Command 'Get-EntraUser'
```

```Output
APIVersion: v1.0
Command    Module Method URI              OutputType           Permissions                                                                                                                                                   Variants
-------    ------ ------ ---              ----------           -----------                                                                                                                                                   --------
Get-EntraUser Users  GET    /users           IMicrosoftGraphUser1 {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...} {List1}
Get-EntraUser Users  GET    /users/{user-id} IMicrosoftGraphUser1 {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...} {Get1, GetViaIdentity1}
   APIVersion: beta
Command    Module Method URI              OutputType          Permissions                                                                                                                                                   Variants
-------    ------ ------ ---              ----------          -----------                                                                                                                                                   --------
Get-EntraUser Users  GET    /users/{user-id} IMicrosoftGraphUser {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...} {Get, GetViaIdentity}
Get-EntraUser Users  GET    /users           IMicrosoftGraphUser {DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All, DeviceManagementManagedDevices.Read.All, DeviceManagementManagedDevices.ReadWrite.All...} {List}
```

#### Example 2: Pass a command and get the permissions required

```powershell
Find-EntraCommand -command Get-EntraUser | Select -First 1 -ExpandProperty Permissions 
```

```Output
Name                                         IsAdmin Description                                   FullDescription
----                                         ------- -----------                                   ---------------
Directory.AccessAsUser.All                   True    Access the directory as you                   Allows the app to have the same access to information in your work or school directory as you do.
Directory.Read.All                           True    Read directory data                           Allows the app to read data in your organization's directory.
Directory.ReadWrite.All                      True    Read and write directory data                 Allows the app to read and write data in your organization's directory, such as other users, groups.  It does not allow the app to delete users or groups, or reset user...
User.Read.All                                True    Read all users' full profiles                 Allows the app to read the full set of profile properties, reports, and managers of other users in your organization, on your behalf.
User.ReadBasic.All                           False   Read all users' basic profiles                Allows the app to read a basic set of profile properties of other users in your organization on your behalf. Includes display name, first and last name, email address a...
User.ReadWrite.All                           True    Read and write all users' full profiles       Allows the app to read and write the full set of profile properties, reports, and managers of other users in your organization, on your behalf.
```

## Find Microsoft Entra PowerShell commands using a command wildcard

### Syntax

```powershell
Find-EntraCommand -Command .*searchstring.* [-ApiVersion <String>] [<CommonParameters>]
```

### Examples

#### Example 1: Search for commands using a command wildcard

```powershell
Find-EntraCommand -Command .*UserToDo.* -APIVersion 'v1.0'
```

```Output
   APIVersion: v1.0
Command                                        Module          Method URI
-------                                        ------          ------ ---
Get-EntraUserTodoList                             Users           GET    /users/{user-id}/todo/lists
Get-EntraUserTodoList                             Users           GET    /users/{user-id}/todo/lists/{todoTaskList-id}
Get-EntraUserTodoListDelta                        Users.Functions GET    /users/{user-id}/todo/lists/delta
Get-EntraUserTodoListExtension                    Users           GET    /users/{user-id}/todo/lists/{todoTaskList-id}/extensions
Get-EntraUserTodoListExtension                    Users           GET    /users/{user-id}/todo/lists/{todoTaskList-id}/extensions/{extension-id}
Get-EntraUserTodoListTask                         Users           GET    /users/{user-id}/todo/lists/{todoTaskList-id}/tasks
Get-EntraUserTodoListTask                         Users           GET    /users/{user-id}/todo/lists/{todoTaskList-id}/tasks/{todoTask-id}
```

## Find Microsoft Entra PowerShell commands using a URI wildcard

### Syntax

```powershell
Find-EntraCommand -Uri .*searchstring.* [-ApiVersion <String>] [<CommonParameters>] [-Method <String>]
```

### Examples

#### Example 1: Search for commands using URI wildcard

```powershell
Find-EntraCommand -Uri ".*users.*" -Method 'Get' -ApiVersion 'v1.0'
```

```Output
Command                               Module                       Method URI
-------                               ------                       ------ ---
Get-EntraUser                            Users                        GET    /users/{user-id}
Get-EntraUser                            Users                        GET    /users
Get-EntraUserActivity                    CrossDeviceExperiences       GET    /users/{user-id}/activities/{userActivity-id}
Get-EntraUserActivity                    CrossDeviceExperiences       GET    /users/{user-id}/activities
Get-EntraUserActivityHistoryItem         CrossDeviceExperiences       GET    /users/{user-id}/activities/{userActivity-id}/historyItems/{activityHistoryItem-id}
```