---
external help file: Az.DnsResolver-help.xml
Module Name: Az.DnsResolver
online version: https://learn.microsoft.com/powershell/module/az.dnsresolver/update-azdnsresolverpolicyvirtualnetworklink
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DnsResolver/DnsResolver/help/Update-AzDnsResolverPolicyVirtualNetworkLink.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DnsResolver/DnsResolver/help/Update-AzDnsResolverPolicyVirtualNetworkLink.md
---

# Update-AzDnsResolverPolicyVirtualNetworkLink

## SYNOPSIS
Updates a DNS resolver policy virtual network link.

## SYNTAX

### UpdateExpanded (Default)
```
Update-AzDnsResolverPolicyVirtualNetworkLink -DnsResolverPolicyName <String> -Name <String>
 -ResourceGroupName <String> [-SubscriptionId <String>] [-IfMatch <String>] [-Tag <Hashtable>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UpdateViaIdentityExpanded
```
Update-AzDnsResolverPolicyVirtualNetworkLink -InputObject <IDnsResolverIdentity> [-IfMatch <String>]
 [-Tag <Hashtable>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Updates a DNS resolver policy virtual network link.

## EXAMPLES

### Example 1: Update an existing DNS Resolver Policy Link by name
```powershell
Update-AzDnsResolverPolicyVirtualNetworkLink  -ResourceGroupName powershell-test-rg -DnsResolverPolicyName exampleDnsResolverPolicyName -Name psdnsresolverpolicylinkname33nmy1fz -Tag @{"key0" = "value0"}
```

```output
Location Name                                Type                                     Etag
-------- ----                                ----                                     ----
westus2  psdnsresolverpolicylinkname33nmy1fz Microsoft.Network/dnsResolverPolicyLinks "0000efd6-0000-0800-0000-60401c7c0000"
```

This command updates an existing DNS Resolver Policy Links by name ( adding tag ).

### Example 2: Updates an existing DNS Resolver by identity
```powershell
$dnsResolverPolicyLinkObject = Get-AzDnsResolverPolicyVirtualNetworkLink  -ResourceGroupName powershell-test-rg -DnsResolverPolicyName exampleDnsResolverPolicyName -Name psdnsresolverpolicylinkname33nmy1fz
Update-AzDnsResolverPolicyVirtualNetworkLink  -InputObject $dnsResolverPolicyLinkObject  -Tag @{}
```

```output
Location Name                                Type                                     Etag
-------- ----                                ----                                     ----
westus2  psdnsresolverpolicylinkname33nmy1fz Microsoft.Network/dnsResolverPolicyLinks "0000efd6-0000-0800-0000-60401c7c0000"
```

This command updates an existing DNS Resolver Policy Links by identity ( removing tag ).

## PARAMETERS

### -AsJob
Run the command as a job

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The DefaultProfile parameter is not functional.
Use the SubscriptionId parameter when available if executing the cmdlet against a different subscription.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases: AzureRMContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DnsResolverPolicyName
The name of the DNS resolver policy.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IfMatch
ETag of the resource.
Omit this value to always overwrite the current resource.
Specify the last-seen ETag value to prevent accidentally overwriting any concurrent changes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity Parameter
To construct, see NOTES section for INPUTOBJECT properties and create a hash table.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DnsResolver.Models.IDnsResolverIdentity
Parameter Sets: UpdateViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
The name of the DNS resolver policy virtual network link for the DNS resolver policy.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded
Aliases: DnsResolverPolicyVirtualNetworkLinkName

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoWait
Run the command asynchronously

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
The name of the resource group.
The name is case insensitive.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.
The value must be an UUID.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag
Tags for the DNS resolver policy virtual network link.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DnsResolver.Models.IDnsResolverIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DnsResolver.Models.Api20230701Preview.IDnsResolverPolicyVirtualNetworkLink

## NOTES

## RELATED LINKS
