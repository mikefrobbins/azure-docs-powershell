---
description: Learn how to create and use service principals with Azure PowerShell.
ms.custom: devx-track-azurepowershell
ms.devlang: powershell
ms.service: azure-powershell
title: Use Azure service principals with Azure PowerShell
---

# Create an Azure service principal with Azure PowerShell

Automated tools that use Azure services should always have restricted permissions. Instead of having
applications sign in as a fully privileged user, Azure offers service principals.

An Azure service principal is an identity created for use with applications, hosted services, and
automated tools to access Azure resources. This access is restricted by the roles assigned to the
service principal, giving you control over which resources can be accessed and at which level. For
security reasons, it's always recommended to use service principals with automated tools rather than
allowing them to log in with a user identity.

This article shows you the steps for creating, getting information about, and resetting a service
principal with Azure PowerShell.

> [!CAUTION]
> When you create a service principal using the
> [New-AzADServicePrincipal](/powershell/module/Az.Resources/New-AzADServicePrincipal) command, the
> output includes credentials that you must protect. As an alternative, consider using
> [managed identities](/azure/active-directory/managed-identities-azure-resources/overview) to avoid
> the need to use credentials.

[!INCLUDE [azps-prerequisites-h2.md](../../includes/azps-prerequisites-h2.md)]

## Create a service principal

Create a service principal with the
[New-AzADServicePrincipal](/powershell/module/Az.Resources/New-AzADServicePrincipal) cmdlet. When
creating a service principal, you choose the type of sign-in authentication it uses.

> [!IMPORTANT]
> Beginning with Az PowerShell module version 7.x,
> [New-AzADServicePrincipal](/powershell/module/Az.Resources/New-AzADServicePrincipal) no longer
> assigns the [Contributor](/azure/role-based-access-control/built-in-roles#contributor) role to the
> service principal by default. To assign a specific role to a service principal, see
> [Steps to add a role assignment](/azure/role-based-access-control/role-assignments-steps).

> [!NOTE]
> If your account doesn't have permission to create a service principal, `New-AzADServicePrincipal`
> returns an error message containing "Insufficient privileges to complete the operation". Contact
> your Microsoft Entra admin to create a service principal.
>
> In a Microsoft Entra ID directory where user setting **Users can register applications** has been
> set to **No**, you must be a member of one of the following Microsoft Entra ID built-in roles
> (which have the action: `microsoft.directory/applications/createAsOwner` or `microsoft.directory/applications/create`):
> - [Application Developer](/entra/identity/role-based-access-control/permissions-reference#application-developer)	
> - [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator)
> - [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
> - [Global Administrator](/entra/identity/role-based-access-control/permissions-reference#global-administrator)
> - [Hybrid Identity Administrator](/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator)
>
> For more information about user settings in Microsoft Entra ID, see [Restrict who can create applications](/entra/identity/role-based-access-control/delegate-app-roles#restrict-who-can-create-applications).

There are two types of authentication available for service principals: Password-based
authentication, and certificate-based authentication.

### Password-based authentication

> [!IMPORTANT]
> The default role for a password-based authentication service principal is **Contributor**. This
> role has full permissions to read and write to an Azure account. For information on managing role
> assignments, see
> [Manage service principal roles](#manage-service-principal-roles).

Without any other authentication parameters, password-based authentication is used and a random
password created for you. If you want password-based authentication, this method is recommended.

```azurepowershell-interactive
$sp = New-AzADServicePrincipal -DisplayName ServicePrincipalName
```

The returned object contains the `PasswordCredentials.SecretText` property containing the generated
password. Make sure that you store this value somewhere secure to authenticate with the service
principal. Its value _won't_ be displayed in the console output. If you lose the password,
[reset the service principal credentials](#reset-credentials).

The following code allows you to export the secret:

```azurepowershell-interactive
$sp.PasswordCredentials.SecretText
```

The object returned from `New-AzADServicePrincipal` contains the `Id` and `DisplayName` members,
either of which can be used for sign in with the service principal.

> [!IMPORTANT]
> Signing in with a service principal requires the tenant ID which the service principal was created
> under. To get the active tenant when the service principal was created, run the following command
> _immediately after_ service principal creation:

```azurepowershell-interactive
(Get-AzContext).Tenant.Id
```

### Certificate-based authentication

> [!IMPORTANT]
> There is no default role assigned when creating a certificate-based authentication service
> principal. For information on managing role assignments, see
> [Manage service principal roles](#manage-service-principal-roles).

Service principals using certificate-based authentication are created with the `CertValue`
parameter. This parameter takes a base64-encoded ASCII string of the public certificate. This is
represented by a PEM file, or a text-encoded CRT or CER. Binary encodings of the public certificate
aren't supported. These instructions assume that you already have a certificate available.

```azurepowershell-interactive
$cert = <public certificate as base64-encoded string>
$sp = New-AzADServicePrincipal -DisplayName ServicePrincipalName -CertValue $cert
```

The object returned from `New-AzADServicePrincipal` contains the `Id` and `DisplayName` properties,
either of which can be used for sign in with the service principal. Clients which sign in with the
service principal also need access to the certificate's private key.

> [!IMPORTANT]
> Signing in with a service principal requires the tenant ID which the service principal was created
> under. To get the active tenant when the service principal was created, run the following command
> _immediately after_ service principal creation:

```azurepowershell-interactive
(Get-AzContext).Tenant.Id
```

## Get an existing service principal

A list of service principals for the active tenant can be retrieved with
[Get-AzADServicePrincipal](/powershell/module/az.resources/get-azadserviceprincipal). By default
this command returns _all_ service principals in a tenant. For large organizations, it may take
a long time to return results. Instead, using one of the optional server-side filtering arguments is
recommended:

- `DisplayNameBeginsWith` requests service principals that have a _prefix_ that match the provided
  value. The display name of a service principal is the value set with `DisplayName` during
  creation.
- `DisplayName` requests an _exact match_ of a service principal name.

## Manage service principal roles

Azure PowerShell has the following cmdlets to manage role assignments:

- [Get-AzRoleAssignment](/powershell/module/az.resources/get-azroleassignment)
- [New-AzRoleAssignment](/powershell/module/az.resources/new-azroleassignment)
- [Remove-AzRoleAssignment](/powershell/module/az.resources/remove-azroleassignment)

For more information on Role-Based Access Control (RBAC) and roles, see
[RBAC: Built-in roles](/azure/active-directory/role-based-access-built-in-roles).

The following example adds the **Reader** role and removes the **Contributor** role:

```azurepowershell-interactive
New-AzRoleAssignment -ApplicationId <service principal application ID> -RoleDefinitionName 'Reader'
Remove-AzRoleAssignment -ObjectId <service principal object ID> -RoleDefinitionName 'Contributor'
```

> [!IMPORTANT]
> Role assignment cmdlets don't take the service principal object ID. They take the associated
> application ID, which is generated at creation time. To get the application ID for a service
> principal, use `Get-AzADServicePrincipal`.

> [!NOTE]
> If your account doesn't have permission to assign a role, you see an error message that your
> account "doesn't have authorization to perform action
> 'Microsoft.Authorization/roleAssignments/write'". Contact your Microsoft Entra admin to
> manage roles.

Adding a role _doesn't_ restrict previously assigned permissions. When restricting a service
principal's permissions, the **Contributor** role should be removed.

The changes can be verified by listing the assigned roles:

```azurepowershell-interactive
Get-AzRoleAssignment -ServicePrincipalName ServicePrincipalName
```

## Sign in using a service principal

Test the new service principal's credentials and permissions by signing in. To sign in with a
service principal, you need the `applicationId` value associated with it, and the tenant it's
created under.

To sign in with a service principal using a password:

```azurepowershell
# Use the application ID as the username, and the secret as password
$credentials = Get-Credential
Connect-AzAccount -ServicePrincipal -Credential $credentials -Tenant <tenant ID>
```

Certificate-based authentication requires that Azure PowerShell can retrieve information from a
local certificate store based on a certificate thumbprint.

```azurepowershell
Connect-AzAccount -ServicePrincipal -Tenant <TenantId> -CertificateThumbprint <Thumbprint> -ApplicationId <ApplicationId>
```

For instructions on importing a certificate into a credential store accessible by PowerShell, see
[Certificate-based authentication](authenticate-noninteractive.md#certificate-based-authentication)

## Reset credentials

If you forget the credentials for a service principal, use
[New-AzADSpCredential](/powershell/module/az.resources/new-azadspcredential) to add a new credential
with a random password. This cmdlet doesn't support user-defined credentials when resetting the
password.

> [!IMPORTANT]
> Before assigning any new credentials, you may want to remove existing credentials to prevent sign
> in with them. To do so, use the
> [Remove-AzADSpCredential](/powershell/module/az.resources/remove-azadspcredential) cmdlet:

```azurepowershell-interactive
Remove-AzADSpCredential -DisplayName ServicePrincipalName
```

```azurepowershell-interactive
$newCredential = New-AzADSpCredential -ServicePrincipalName ServicePrincipalName
```

## Troubleshooting

If you receive the error: _"New-AzADServicePrincipal: Another object with the same value for
property identifierUris already exists."_, verify that a service principal with the same name
doesn't already exist.

```azurepowershell-interactive
Get-AzAdServicePrincipal -DisplayName ServicePrincipalName
```

If the existing service principal is no longer needed, you can remove it using the following
example.

```azurepowershell-interactive
Remove-AzAdServicePrincipal -DisplayName ServicePrincipalName
```

This error can also occur when you've previously created a service principal for an Azure Active
Directory application. If you remove the service principal, the application is still available. This
application prevents you from creating another service principal with the same name.

You can use the following example to verify that a Microsoft Entra application with the same
name doesn't exist:

```azurepowershell-interactive
Get-AzADApplication -DisplayName ServicePrincipalName
```

If an application with the same name does exist and is no longer needed, it can be removed using the
following example.

```azurepowershell-interactive
Remove-AzADApplication -DisplayName ServicePrincipalName
```

Otherwise, choose an alternate name for the new service principal that you're attempting to create.
