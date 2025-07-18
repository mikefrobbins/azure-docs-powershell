---
external help file: Microsoft.Azure.PowerShell.Cmdlets.RecoveryServices.SiteRecovery.dll-Help.xml
Module Name: Az.RecoveryServices
online version: https://learn.microsoft.com/powershell/module/az.recoveryservices/start-azrecoveryservicesasrclustertestfailoverjob
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/RecoveryServices/RecoveryServices/help/Start-AzRecoveryServicesAsrClusterTestFailoverJob.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/RecoveryServices/RecoveryServices/help/Start-AzRecoveryServicesAsrClusterTestFailoverJob.md
---

# Start-AzRecoveryServicesAsrClusterTestFailoverJob

## SYNOPSIS
Starts a test failover operation for a cluster.

## SYNTAX

```
Start-AzRecoveryServicesAsrClusterTestFailoverJob
 -ReplicationProtectionCluster <ASRReplicationProtectionCluster> -Direction <String>
 [-ClusterRecoveryPoint <ASRClusterRecoveryPoint>]
 [-ListNodeRecoveryPoint <System.Collections.Generic.List`1[System.String]>] [-LatestProcessedRecoveryPoint]
 -AzureVMNetworkId <String> [-DefaultProfile <IAzureContextContainer>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Start-AzRecoveryServicesAsrClusterTestFailoverJob** cmdlet starts test failover of an Azure Site Recovery replication protection cluster.
You can check whether the job succeeded by using the Get-AzRecoveryServicesAsrJob cmdlet.

## EXAMPLES

### Example 1
```powershell
$currentJob = Start-AzRecoveryServicesAsrClusterTestFailoverJob -ReplicationProtectionCluster $protectionCluster -Direction PrimaryToRecovery -AzureVMNetworkId $TestRecoveryNetwork -LatestProcessedRecoveryPoint
```

Starts a test failover operation for the specified cluster. If LatestProcessedRecoveryPoint is passed and no specific recovery point is provided, it will pick the latest processed recovery points and the ASR job used to track the operation.

### Example 2
```powershell
$currentJob = Start-AzRecoveryServicesAsrClusterTestFailoverJob -ReplicationProtectionCluster $protectionCluster -Direction PrimaryToRecovery -AzureVMNetworkId $TestRecoveryNetwork -ClusterRecoveryPoint $clusterRecoveryPoint -ListNodeRecoveryPoint $nodeRecoveryPoints
```

Starts a test failover operation for the specified cluster and by passing ClusterRecoveryPoint and NodeRecoveryPoints, it will pick the specified recovery points and returns the ASR job used to track the operation.

## PARAMETERS

### -AzureVMNetworkId
Specifies the Azure vm network id for recovery VM after failover.

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

### -ClusterRecoveryPoint
Specifies the recovery point for the cluster.

```yaml
Type: Microsoft.Azure.Commands.RecoveryServices.SiteRecovery.ASRClusterRecoveryPoint
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with Azure.

```yaml
Type: Microsoft.Azure.Commands.Common.Authentication.Abstractions.Core.IAzureContextContainer
Parameter Sets: (All)
Aliases: AzContext, AzureRmContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Direction
Specifies the failover direction.
The acceptable values for this parameter are:

- PrimaryToRecovery
- RecoveryToPrimary

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: PrimaryToRecovery, RecoveryToPrimary

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LatestProcessedRecoveryPoint
Fetch the latest processed recovery points if not passed for cluster or any individual node.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: LatestProcessedRecoveryPoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListNodeRecoveryPoint
Specifies the recovery points for the nodes which are not part of cluster recovery point.

```yaml
Type: System.Collections.Generic.List`1[System.String]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReplicationProtectionCluster
Specifies the replication protection cluster.

```yaml
Type: Microsoft.Azure.Commands.RecoveryServices.SiteRecovery.ASRReplicationProtectionCluster
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
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

### Microsoft.Azure.Commands.RecoveryServices.SiteRecovery.ASRReplicationProtectionCluster

## OUTPUTS

### Microsoft.Azure.Commands.RecoveryServices.SiteRecovery.ASRJob

## NOTES

## RELATED LINKS
