---
external help file: Az.DevCenter-help.xml
Module Name: Az.DevCenter
online version: https://learn.microsoft.com/powershell/module/az.devcenter/get-azdevcenteruserdevboxoperation
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DevCenter/DevCenter/help/Get-AzDevCenterUserDevBoxOperation.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DevCenter/DevCenter/help/Get-AzDevCenterUserDevBoxOperation.md
---

# Get-AzDevCenterUserDevBoxOperation

## SYNOPSIS
Gets an operation on a Dev Box.

## SYNTAX

### List (Default)
```
Get-AzDevCenterUserDevBoxOperation -Endpoint <String> -DevBoxName <String> -ProjectName <String>
 [-UserId <String>] [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### Get
```
Get-AzDevCenterUserDevBoxOperation -Endpoint <String> -DevBoxName <String> -ProjectName <String>
 [-UserId <String>] -OperationId <String> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### GetViaIdentity
```
Get-AzDevCenterUserDevBoxOperation -Endpoint <String> -InputObject <IDevCenterdataIdentity>
 [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### GetViaIdentityByDevCenter
```
Get-AzDevCenterUserDevBoxOperation -DevCenterName <String> -InputObject <IDevCenterdataIdentity>
 [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### ListByDevCenter
```
Get-AzDevCenterUserDevBoxOperation -DevCenterName <String> -DevBoxName <String> -ProjectName <String>
 [-UserId <String>] [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### GetByDevCenter
```
Get-AzDevCenterUserDevBoxOperation -DevCenterName <String> -DevBoxName <String> -ProjectName <String>
 [-UserId <String>] -OperationId <String> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
Gets an operation on a Dev Box.

## EXAMPLES

### Example 1: List operations on the dev box by endpoint
```powershell
Get-AzDevCenterUserDevBoxOperation -Endpoint "https://8a40af38-3b4c-4672-a6a4-5e964b1870ed-contosodevcenter.centralus.devcenter.azure.com/" -DevBoxName myDevBox -ProjectName DevProject
```

This command lists the operations on the dev box "myDevBox".

### Example 2: List operations on the dev box by dev center
```powershell
Get-AzDevCenterUserDevBoxOperation -DevCenterName Contoso -DevBoxName myDevBox -ProjectName DevProject
```

This command lists the operations on the dev box "myDevBox".

### Example 3: Get an operation on the dev box by endpoint
```powershell
Get-AzDevCenterUserDevBoxOperation -Endpoint "https://8a40af38-3b4c-4672-a6a4-5e964b1870ed-contosodevcenter.centralus.devcenter.azure.com/" -DevBoxName myDevBox -ProjectName DevProject -OperationId "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
```

This command gets the operation "00aa00aa-bb11-cc22-dd33-44ee44ee44ee" for the dev box "myDevBox".

### Example 4: Get an operation on the dev box by dev center
```powershell
Get-AzDevCenterUserDevBoxOperation -DevCenterName Contoso -DevBoxName myDevBox -ProjectName DevProject -OperationId "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
```

This command gets the operation "00aa00aa-bb11-cc22-dd33-44ee44ee44ee" for the dev box "myDevBox".

### Example 5: Get an operation on the dev box by endpoint and InputObject
```powershell
$devBoxInput = @{"DevBoxName" = "myDevBox"; "UserId" = "me"; "ProjectName" = "DevProject"; "OperationId" = "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"}
Get-AzDevCenterUserDevBoxOperation -Endpoint "https://8a40af38-3b4c-4672-a6a4-5e964b1870ed-contosodevcenter.centralus.devcenter.azure.com/" -InputObject $devBoxInput
```

This command gets the operation "00aa00aa-bb11-cc22-dd33-44ee44ee44ee" for the dev box "myDevBox".

### Example 6: Get an operation on the dev box by dev center and InputObject
```powershell
$devBoxInput = @{"DevBoxName" = "myDevBox"; "UserId" = "me"; "ProjectName" = "DevProject"; "OperationId" = "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"}
Get-AzDevCenterUserDevBoxOperation -DevCenterName Contoso -InputObject $devBoxInput
```

This command gets the operation "00aa00aa-bb11-cc22-dd33-44ee44ee44ee" for the dev box "myDevBox".

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

### -DevBoxName
The name of a Dev Box.

```yaml
Type: System.String
Parameter Sets: List, Get, ListByDevCenter, GetByDevCenter
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DevCenterName
The DevCenter upon which to execute operations.

```yaml
Type: System.String
Parameter Sets: GetViaIdentityByDevCenter, ListByDevCenter, GetByDevCenter
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Endpoint
The DevCenter-specific URI to operate on.

```yaml
Type: System.String
Parameter Sets: List, Get, GetViaIdentity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity Parameter
To construct, see NOTES section for INPUTOBJECT properties and create a hash table.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DevCenterdata.Models.IDevCenterdataIdentity
Parameter Sets: GetViaIdentity, GetViaIdentityByDevCenter
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OperationId
The id of the operation on a Dev Box.

```yaml
Type: System.String
Parameter Sets: Get, GetByDevCenter
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectName
The DevCenter Project upon which to execute operations.

```yaml
Type: System.String
Parameter Sets: List, Get, ListByDevCenter, GetByDevCenter
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserId
The AAD object id of the user.
If value is 'me', the identity is taken from the authentication context.

```yaml
Type: System.String
Parameter Sets: List, Get, ListByDevCenter, GetByDevCenter
Aliases:

Required: False
Position: Named
Default value: "me"
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DevCenterdata.Models.IDevCenterdataIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DevCenterdata.Models.Api20231001Preview.IDevBoxOperation

## NOTES

## RELATED LINKS
