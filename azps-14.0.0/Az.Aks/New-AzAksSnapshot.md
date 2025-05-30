---
external help file: Az.Aks-help.xml
Module Name: Az.Aks
online version: https://learn.microsoft.com/powershell/module/az.aks/new-azakssnapshot
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Aks/Aks/help/New-AzAksSnapshot.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Aks/Aks/help/New-AzAksSnapshot.md
---

# New-AzAksSnapshot

## SYNOPSIS
create a snapshot.

## SYNTAX

### CreateExpanded (Default)
```
New-AzAksSnapshot -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -Location <String> [-CreationDataSourceResourceId <String>] [-SnapshotType <String>] [-Tag <Hashtable>]
 [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CreateViaJsonFilePath
```
New-AzAksSnapshot -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -JsonFilePath <String> [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CreateViaJsonString
```
New-AzAksSnapshot -ResourceGroupName <String> -ResourceName <String> [-SubscriptionId <String>]
 -JsonString <String> [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
create a snapshot.

## EXAMPLES

### Example 1: Creates or updates a snapshot
```powershell
$pool = Get-AzAksNodePool -ResourceGroupName mygroup -ClusterName mycluster -Name default
New-AzAksSnapshot -ResourceGroupName mygroup -ResourceName 'snapshot1' -Location eastus -SnapshotType 'NodePool' -CreationDataSourceResourceId $pool.Id
```

```output
Location Name      SystemDataCreatedAt   SystemDataCreatedBy  SystemDataCreatedByType SystemDataLastModifiedAt SystemDataLastModifiedBy SystemDataLastModifiedByType
-------- ----      -------------------   -------------------  ----------------------- ------------------------ ------------------------ ----------------------------
eastus   snapshot1 3/30/2023 10:24:43 AM user1@microsoft.com User                    3/30/2023 10:24:43 AM    user1@microsoft.com     User
```

Creates or updates a snapshot for a nodepool "default" of a managed cluster "mycluster".

## PARAMETERS

### -CreationDataSourceResourceId
This is the ARM ID of the source object to be used to create the target object.

```yaml
Type: System.String
Parameter Sets: CreateExpanded
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

### -JsonFilePath
Path of Json file supplied to the Create operation

```yaml
Type: System.String
Parameter Sets: CreateViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Create operation

```yaml
Type: System.String
Parameter Sets: CreateViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Location
The geo-location where the resource lives

```yaml
Type: System.String
Parameter Sets: CreateExpanded
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

### -ResourceName
The name of the managed cluster resource.

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

### -SnapshotType
The type of a snapshot.
The default is NodePool.

```yaml
Type: System.String
Parameter Sets: CreateExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag
Resource tags.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: CreateExpanded
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

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Aks.Models.ISnapshot

## NOTES

## RELATED LINKS
