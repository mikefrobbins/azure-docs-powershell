---
external help file: Az.DynatraceObservability-help.xml
Module Name: Az.DynatraceObservability
online version: https://learn.microsoft.com/powershell/module/az.dynatraceobservability/get-azdynatracemonitorhost
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DynatraceObservability/DynatraceObservability/help/Get-AzDynatraceMonitorHost.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DynatraceObservability/DynatraceObservability/help/Get-AzDynatraceMonitorHost.md
---

# Get-AzDynatraceMonitorHost

## SYNOPSIS
List the VM/VMSS resources currently being monitored by the Dynatrace resource.

## SYNTAX

```
Get-AzDynatraceMonitorHost -MonitorName <String> -ResourceGroupName <String> [-SubscriptionId <String[]>]
 [-DefaultProfile <PSObject>] [<CommonParameters>]
```

## DESCRIPTION
List the VM/VMSS resources currently being monitored by the Dynatrace resource.

## EXAMPLES

### Example 1: List the compute resources currently being monitored by the Dynatrace resource
```powershell
Get-AzDynatraceMonitorHost -ResourceGroupName dyobrg -MonitorName dyob-pwsh01
```

This command lists the compute resources currently being monitored by the Dynatrace resource.

## PARAMETERS

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

### -MonitorName
Monitor resource name

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
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
Parameter Sets: (All)
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
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DynatraceObservability.Models.IVMInfo

## NOTES

## RELATED LINKS
