---
external help file: Az.Aks-help.xml
Module Name: Az.Aks
online version: https://learn.microsoft.com/powershell/module/az.aks/start-azaksmanagedclustercommand
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Aks/Aks/help/Start-AzAksManagedClusterCommand.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Aks/Aks/help/Start-AzAksManagedClusterCommand.md
---

# Start-AzAksManagedClusterCommand

## SYNOPSIS
AKS will run a pod to run the command.
This is primarily useful for private clusters.
For more information see [AKS Run Command](https://docs.microsoft.com/azure/aks/private-clusters#aks-run-command-preview).

## SYNTAX

### RunExpanded (Default)
```
Start-AzAksManagedClusterCommand -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -Command <String> [-ClusterToken <String>] [-Context <String>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RunViaJsonString
```
Start-AzAksManagedClusterCommand -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -JsonString <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RunViaJsonFilePath
```
Start-AzAksManagedClusterCommand -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -JsonFilePath <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RunViaIdentityExpanded
```
Start-AzAksManagedClusterCommand -InputObject <IAksIdentity> -Command <String> [-ClusterToken <String>]
 [-Context <String>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
AKS will run a pod to run the command.
This is primarily useful for private clusters.
For more information see [AKS Run Command](https://docs.microsoft.com/azure/aks/private-clusters#aks-run-command-preview).

## EXAMPLES

### Example 1: Run AKS command
```powershell
Start-AzAksManagedClusterCommand -ResourceGroupName mygroup -ResourceName mycluster -Command "kubectl get nodes"
```

```output
ExitCode          : 0
FinishedAt        : 3/31/2023 8:52:17 AM
Id                : 0a3991475d9744fcbfdc2595b40e517f
Log               : NAME                              STATUS   ROLES   AGE   VERSION
                    aks-default-40136599-vmss000000   Ready    agent   46m   v1.24.9
                    aks-pool2-22198594-vmss000000     Ready    agent   43m   v1.24.9

ProvisioningState : Succeeded
Reason            :
StartedAt         : 3/31/2023 8:52:16 AM
```

AKS will create a pod to run the command.
This is primarily useful for private clusters.

### Example 2: Run AKS command via identity
```powershell
$cluster = Get-AzAksCluster -ResourceGroupName mygroup -Name mycluster
$cluster | Start-AzAksManagedClusterCommand -Command "kubectl get nodes"
```

```output
ExitCode          : 0
FinishedAt        : 3/31/2023 8:54:17 AM
Id                : 0a3991475d9744fcbfdc2595b40e517f
Log               : NAME                              STATUS   ROLES   AGE   VERSION
                    aks-default-40136599-vmss000000   Ready    agent   46m   v1.24.9
                    aks-pool2-22198594-vmss000000     Ready    agent   43m   v1.24.9

ProvisioningState : Succeeded
Reason            :
StartedAt         : 3/31/2023 8:54:16 AM
```

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

### -ClusterToken
AuthToken issued for AKS AAD Server App.

```yaml
Type: System.String
Parameter Sets: RunExpanded, RunViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command
The command to run.

```yaml
Type: System.String
Parameter Sets: RunExpanded, RunViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Context
A base64 encoded zip file containing the files required by the command.

```yaml
Type: System.String
Parameter Sets: RunExpanded, RunViaIdentityExpanded
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

### -InputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Aks.Models.IAksIdentity
Parameter Sets: RunViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JsonFilePath
Path of Json file supplied to the Run operation

```yaml
Type: System.String
Parameter Sets: RunViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Run operation

```yaml
Type: System.String
Parameter Sets: RunViaJsonString
Aliases:

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
Parameter Sets: RunExpanded, RunViaJsonString, RunViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceName
The name of the managed cluster resource.

```yaml
Type: System.String
Parameter Sets: RunExpanded, RunViaJsonString, RunViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.

```yaml
Type: System.String
Parameter Sets: RunExpanded, RunViaJsonString, RunViaJsonFilePath
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
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

### Microsoft.Azure.PowerShell.Cmdlets.Aks.Models.IAksIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Aks.Models.IRunCommandResult

## NOTES

## RELATED LINKS
