---
external help file: Microsoft.WindowsAzure.Commands.Profile.dll-Help.xml
ms.assetid: 03EAFFB2-EA64-4227-A33B-D24EB4A75F71
online version: 
schema: 2.0.0
Module Name: Azure
---

# Add-AzureAccount

## SYNOPSIS
Adds the Azure account to Windows PowerShell.

[!INCLUDE [rdfe-banner](../../includes/rdfe-banner.md)]

## SYNTAX

### User (Default)
```
Add-AzureAccount [-Environment <String>] [-Credential <PSCredential>] [-Tenant <String>]
 [-Profile <AzureSMProfile>] [<CommonParameters>]
```

### ServicePrincipal
```
Add-AzureAccount [-Environment <String>] -Credential <PSCredential> [-ServicePrincipal] -Tenant <String>
 [-Profile <AzureSMProfile>] [<CommonParameters>]
```

## DESCRIPTION
The **Add-AzureAccount** cmdlet makes your Azure account and its subscriptions available in Windows PowerShell.
It's like logging into your Azure account in Windows PowerShell.
To log out of the account, use the **Remove-AzureAccount** cmdlet.

**Add-AzureAccount** downloads information about your Azure account and saves it in a subscription data file in your roaming user profile.
It also gets an access token that allows Windows PowerShell to access your Azure account on your behalf.
When the command completes, you can manage your Azure account in Windows PowerShell.

There are two different ways to make your Azure account available to Windows PowerShell.
You can use the **Add-AzureAccount** cmdlet, which uses Microsoft Entra authentication access tokens, or **Import-AzurePublishSettingsFile**, which uses a management certificate.

When you run **Add-AzureAccount**, it displays an interactive window that prompts you to sign into your Azure account.
This sign-in is valid until the access token expires.
When it expires, cmdlets that require access to your account prompt you to run **Add-AzureAccount** again.

This topic describes the cmdlet in the 0.8.10 version of the Microsoft Azure PowerShell module.
To get the version of the module you're using, in the Azure PowerShell console, type `(Get-Module -Name Azure).Version`.

## EXAMPLES

### Example 1: Add an account
```
PS C:\> Add-AzureAccount
```

This command adds an Azure account to Windows PowerShell.
When you run the command, a windows pops up to request the user name and password of the account.

### Example 2: Use an alternate subscription data file
```
PS C:\> Add-AzureAccount -SubscriptionDataFile C:\Testing\SDF.xml
```

This command uses the **SubscriptionDataFile** parameter to direct **Add-AzureAccount** to store the account data in the C:\Testing\SDF.xml file, instead of the default file.

## PARAMETERS

### -Credential
```yaml
Type: PSCredential
Parameter Sets: User
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: PSCredential
Parameter Sets: ServicePrincipal
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Environment
Specifies an Azure environment.

An Azure environment an independent deployment of Microsoft Azure, such as AzureCloud for global Azure and AzureChinaCloud for Azure operated by 21Vianet in China.
You can also create on-premises Azure environments by using Azure Pack and the WAPack cmdlets.
For more information, see [Azure Pack](/previous-versions/azure/windows-server-azure-pack/).

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Profile
Specifies the Azure profile from which this cmdlet reads.
If you do not specify a profile, this cmdlet reads from the local default profile.

```yaml
Type: AzureSMProfile
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServicePrincipal
```yaml
Type: SwitchParameter
Parameter Sets: ServicePrincipal
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tenant
```yaml
Type: String
Parameter Sets: User
Aliases: TenantId

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: String
Parameter Sets: ServicePrincipal
Aliases: TenantId

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None
You cannot pipe input to this cmdlet

## OUTPUTS

### None
This cmdlet does not return any output.

## NOTES
* **Add-AzureAccount** (and the Microsoft Entra authentication method) takes precedence over **Import-AzurePublishSettings** (and the management certificate method). If you use **Add-AzureAccount** even once on your account, the Microsoft Entra authentication method is used and the management certificate is ignored. To remove the Microsoft Entra token and restore the management certificate method, use the **Remove-AzureAccount** cmdlet. For more information, type: **Get-Help Remove-AzureAccount**.
* The error, "Your credentials have expired. Please use Add-AzureAccount to log in again." indicates that your access token is expired and Windows PowerShell cannot access your Azure account. To restore access to your account, run **Add-AzureAccount** again.
* The Azure PowerShell account and subscription cmdlets get their data from the  subscription data file, not from the live Azure account. If you change your account or subscriptions outside of Windows PowerShell, such as by using the Azure Management Portal, run **Add-AzureAccount** again to refresh the subscription data file.

## RELATED LINKS

[Add-AzureEnvironment](./Add-AzureEnvironment.md)

[Get-AzureEnvironment](./Get-AzureEnvironment.md)

[Import-AzurePublishSettingsFile](./Import-AzurePublishSettingsFile.md)

[Get-AzureAccount](./Get-AzureAccount.md)

[Remove-AzureAccount](./Remove-AzureAccount.md)
