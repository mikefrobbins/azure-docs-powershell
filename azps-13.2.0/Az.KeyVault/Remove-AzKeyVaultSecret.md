---
external help file: Microsoft.Azure.PowerShell.Cmdlets.KeyVault.dll-Help.xml
Module Name: Az.KeyVault
online version: https://learn.microsoft.com/powershell/module/az.keyvault/remove-azkeyvaultsecret
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/KeyVault/KeyVault/help/Remove-AzKeyVaultSecret.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/KeyVault/KeyVault/help/Remove-AzKeyVaultSecret.md
---

# Remove-AzKeyVaultSecret

## SYNOPSIS
Deletes a secret in a key vault.

## SYNTAX

### ByVaultName (Default)
```
Remove-AzKeyVaultSecret [-VaultName] <String> [-Name] <String> [-Force] [-PassThru] [-InRemovedState]
 [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### BySecretUri
```
Remove-AzKeyVaultSecret [-Id] <String> [-Force] [-PassThru] [-InRemovedState]
 [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByInputObject
```
Remove-AzKeyVaultSecret [-InputObject] <PSKeyVaultSecretIdentityItem> [-Force] [-PassThru] [-InRemovedState]
 [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The Remove-AzKeyVaultSecret cmdlet deletes a secret in a key vault.
If the secret was accidentally deleted the secret can be recovered using Undo-AzKeyVaultSecretRemoval by a user with special 'recover' permissions.
This cmdlet has a value of high for the **ConfirmImpact** property.

## EXAMPLES

### Example 1: Remove a secret from a key vault
```powershell
Remove-AzKeyVaultSecret -VaultName 'Contoso' -Name 'FinanceSecret' -PassThru
```

```output
Vault Name           : Contoso
Name                 : FinanceSecret
Version              : f622abc7b1394092812f1eb0f85dc91c
Id                   : https://contoso.vault.azure.net:443/secrets/financesecret/f622abc7b1394092812f1eb0f85dc91c
Deleted Date         : 5/25/2018 4:45:34 PM
Scheduled Purge Date : 8/23/2018 4:45:34 PM
Enabled              : True
Expires              :
Not Before           :
Created              : 4/19/2018 5:56:02 PM
Updated              : 4/26/2018 7:48:40 PM
Content Type         :
Tags                 :
```

This command removes the secret named FinanceSecret from the key vault named Contoso.'

### Example 2: Remove a secret from a key vault without user confirmation
```powershell
Remove-AzKeyVaultSecret -VaultName 'Contoso' -Name 'FinanceSecret' -PassThru -Force
```

```output
Vault Name           : Contoso
Name                 : FinanceSecret
Version              : f622abc7b1394092812f1eb0f85dc91c
Id                   : https://contoso.vault.azure.net:443/secrets/financesecret/f622abc7b1394092812f1eb0f85dc91c
Deleted Date         : 5/25/2018 4:45:34 PM
Scheduled Purge Date : 8/23/2018 4:45:34 PM
Enabled              : True
Expires              :
Not Before           :
Created              : 4/19/2018 5:56:02 PM
Updated              : 4/26/2018 7:48:40 PM
Content Type         :
Tags                 :
```

This command removes the secret named FinanceSecret from the key vault named Contoso.
The command specifies the *Force* and *Confirm* parameters, and, therefore, the cmdlet does not prompt you for confirmation.

### Example 3: Remove a secret from a key vault (using uri)
```powershell
Remove-AzKeyVaultSecret -Id 'https://contoso.vault.azure.net:443/secrets/financesecret' -PassThru
```

```output
Vault Name           : Contoso
Name                 : FinanceSecret
Version              : f622abc7b1394092812f1eb0f85dc91c
Id                   : https://contoso.vault.azure.net:443/secrets/financesecret/f622abc7b1394092812f1eb0f85dc91c
Deleted Date         : 5/25/2018 4:45:34 PM
Scheduled Purge Date : 8/23/2018 4:45:34 PM
Enabled              : True
Expires              :
Not Before           :
Created              : 4/19/2018 5:56:02 PM
Updated              : 4/26/2018 7:48:40 PM
Content Type         :
Tags                 :
```

This command removes the secret named 'FinanceSecret' from the key vault named 'Contoso'.

### Example 4: Remove a secret in Azure Key Vault by command Remove-Secret in module Microsoft.PowerShell.SecretManagement
```powershell
# Install module Microsoft.PowerShell.SecretManagement
Install-Module Microsoft.PowerShell.SecretManagement -Repository PSGallery -AllowPrerelease
# Register vault for Secret Management
Register-SecretVault -Name AzKeyVault -ModuleName Az.KeyVault -VaultParameters @{ AZKVaultName = 'test-kv'; SubscriptionId = 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' }
# Set secret for vault AzKeyVault
$secure = ConvertTo-SecureString -String "****" -AsPlainText -Force
Set-Secret -Vault AzKeyVault -Name secureSecret -SecureStringSecret $secure 
Remove-Secret -Vault AzKeyVault -Name secureSecret
```

```output
None
```

This example removes a secret named `secureSecret` in Azure Key Vault `test-kv` by command `Remove-Secret` in module `Microsoft.PowerShell.SecretManagement`.

### Example 4: Purge deleted secret from the key vault permanently
```powershell
Remove-AzKeyVaultSecret -VaultName 'Contoso' -Name 'FinanceSecret' -InRemovedState
```

This command removes the secret named FinanceSecret from the key vault named Contoso permanently.
Executing this cmdlet requires the 'purge' permission, which must have been previously and explicitly granted to the user for this key vault.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with azure

```yaml
Type: IAzureContextContainer
Parameter Sets: (All)
Aliases: AzContext, AzureRmContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The URI of the KeyVault Secret.
Please ensure it follows the format: `https://<vault-name>.vault.azure.net/secrets/<secret-name>/<version>`

```yaml
Type: String
Parameter Sets: BySecretUri
Aliases: SecretId

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InRemovedState
If present, removes the previously deleted secret permanently.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Key Vault Secret Object

```yaml
Type: PSKeyVaultSecretIdentityItem
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the name of a secret.
This cmdlet constructs the fully qualified domain name (FQDN) of a secret based on the name that this parameter specifies, the name of the key vault, and your current environment.

```yaml
Type: String
Parameter Sets: ByVaultName
Aliases: SecretName

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Indicates that this cmdlet returns a **Microsoft.Azure.Commands.KeyVault.Models.Secret** object.
By default, this cmdlet does not generate any output.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VaultName
Specifies the name of the key vault to which the secret belongs.
This cmdlet constructs the FQDN of a key vault based on the name that this parameter specifies and your current environment.

```yaml
Type: String
Parameter Sets: ByVaultName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.Commands.KeyVault.Models.PSKeyVaultSecretIdentityItem

## OUTPUTS

### Microsoft.Azure.Commands.KeyVault.Models.PSDeletedKeyVaultSecret

## NOTES

## RELATED LINKS

[Get-AzKeyVaultSecret](./Get-AzKeyVaultSecret.md)

[Set-AzKeyVaultSecret](./Set-AzKeyVaultSecret.md)

[Undo-AzKeyVaultSecretRemoval](./Undo-AzKeyVaultSecretRemoval.md)
