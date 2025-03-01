---
external help file: Az.Fabric-help.xml
Module Name: Az.Fabric
online version: https://learn.microsoft.com/powershell/module/az.fabric/get-azfabriccapacity
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Fabric/Fabric/help/Get-AzFabricCapacity.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Fabric/Fabric/help/Get-AzFabricCapacity.md
---

# Get-AzFabricCapacity

## SYNOPSIS
Get a FabricCapacity

## SYNTAX

### List (Default)
```
Get-AzFabricCapacity [-SubscriptionId <String[]>] [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### Get
```
Get-AzFabricCapacity -CapacityName <String> -ResourceGroupName <String> [-SubscriptionId <String[]>]
 [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### List1
```
Get-AzFabricCapacity -ResourceGroupName <String> [-SubscriptionId <String[]>] [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### GetViaIdentity
```
Get-AzFabricCapacity -InputObject <IFabricIdentity> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
Get a FabricCapacity

## EXAMPLES

### Example 1: List Capacities by Resource Group
```powershell
Get-AzFabricCapacity -ResourceGroupName "testrg" -SubscriptionId "aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e"
```

```output
Location Name               SystemDataCreatedAt SystemDataCreatedBy SystemDataCreatedByType SystemDataLastModifiedAt SystemDataLastModifiedBy SystemDataLastModifiedByType ResourceGroupName
-------- ----               ------------------- ------------------- ----------------------- ------------------------ ------------------------ ---------------------------- -----------------
West Central US  azsdktest                                                                                                                                                       testrg
West Central US  azsdktest2                                                                                                                                                      testrg
```

The above command lists all Fabric capacities within the resource group 'testrg' in the subscription 'aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e'

### Example 2: List Capacities by Subscription
```powershell
Get-AzFabricCapacity -SubscriptionId "aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e"
```

```output
Location Name               SystemDataCreatedAt SystemDataCreatedBy SystemDataCreatedByType SystemDataLastModifiedAt SystemDataLastModifiedBy SystemDataLastModifiedByType ResourceGroupName
-------- ----               ------------------- ------------------- ----------------------- ------------------------ ------------------------ ---------------------------- -----------------
West Central US  azsdktest                                                                                                                                                       testrg
West Central US  azsdktest2                                                                                                                                                      testrg
West Europe      azsdktest3                                                                                                                                                      testrg3
```

The above command lists all Fabric capacities in the subscription 'aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e'.

### Example 3: Get Capacity
```powershell
Get-AzFabricCapacity -ResourceGroupName "testrg" -SubscriptionId "aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e" -CapacityName "azsdktest"
```

```output
AdministrationMember         : {azsdktest@microsoft.com}
Id                           : /subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/resourceGroups/testrg/providers/Microsoft.Fabric/capacities/azsdktest
Location                     : West Central US
Name                         : azsdktest
ProvisioningState            : Succeeded
ResourceGroupName            : testrg
SkuName                      : F2
SkuTier                      : Fabric
State                        : Active
SystemDataCreatedAt          :
SystemDataCreatedBy          :
SystemDataCreatedByType      :
SystemDataLastModifiedAt     :
SystemDataLastModifiedBy     :
SystemDataLastModifiedByType :
Tag                          : {
                               }
Type                         : Microsoft.Fabric/capacities
```

The above command retrieves the Fabric capacity named 'azsdktest' within the resource group 'testrg' in the subscription 'aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e'.

## PARAMETERS

### -CapacityName
The name of the Microsoft Fabric capacity.
It must be a minimum of 3 characters, and a maximum of 63.

```yaml
Type: System.String
Parameter Sets: Get
Aliases:

Required: True
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
Type: Microsoft.Azure.PowerShell.Cmdlets.Fabric.Models.IFabricIdentity
Parameter Sets: GetViaIdentity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ResourceGroupName
The name of the resource group.
The name is case insensitive.

```yaml
Type: System.String
Parameter Sets: Get, List1
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
Type: System.String[]
Parameter Sets: List, Get, List1
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

### Microsoft.Azure.PowerShell.Cmdlets.Fabric.Models.IFabricIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Fabric.Models.IFabricCapacity

## NOTES

## RELATED LINKS
