---
external help file: Az.Resources-help.xml
Module Name: Az.Resources
online version: https://learn.microsoft.com/powershell/module/az.resources/new-azadserviceprincipalapproleassignment
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Resources/Resources/help/New-AzADServicePrincipalAppRoleAssignment.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Resources/Resources/help/New-AzADServicePrincipalAppRoleAssignment.md
---

# New-AzADServicePrincipalAppRoleAssignment

## SYNOPSIS
Create new navigation property to appRoleAssignments for servicePrincipals

## SYNTAX

### ObjectIdWithResourceIdParameterSet (Default)
```
New-AzADServicePrincipalAppRoleAssignment -ServicePrincipalId <String> -ResourceId <String>
 [-AdditionalProperties <Hashtable>] [-AppRoleId <String>] [-DefaultProfile <PSObject>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ObjectIdWithResourceDisplayNameParameterSet
```
New-AzADServicePrincipalAppRoleAssignment -ServicePrincipalId <String> [-AdditionalProperties <Hashtable>]
 [-AppRoleId <String>] -ResourceDisplayName <String> [-DefaultProfile <PSObject>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SPNWithResourceIdParameterSet
```
New-AzADServicePrincipalAppRoleAssignment -ResourceId <String> [-AdditionalProperties <Hashtable>]
 [-AppRoleId <String>] -ServicePrincipalDisplayName <String> [-DefaultProfile <PSObject>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SPNWithResourceDisplayNameParameterSet
```
New-AzADServicePrincipalAppRoleAssignment [-AdditionalProperties <Hashtable>] [-AppRoleId <String>]
 -ResourceDisplayName <String> -ServicePrincipalDisplayName <String> [-DefaultProfile <PSObject>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Create new navigation property to appRoleAssignments for servicePrincipals

## EXAMPLES

### Example 1: ObjectIdWithResourceIdParameterSet
```powershell
New-AzADServicePrincipalAppRoleAssignment -ServicePrincipalId 00001111-aaaa-2222-bbbb-3333cccc4444 -ResourceId a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1 -AppRoleId b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2
```

```output
Id                                          AppRoleId                            PrincipalDisplayName PrincipalId                          CreatedDateTime
--                                          ---------                            -------------------- -----------                          ---------------
Zbm-cUeDXUmlicIc3eenIkgIm8kv9kJPj4MFhepACNE b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2 funapp1214           00001111-aaaa-2222-bbbb-3333cccc4444 12/14/2023 7:04:28 AM
```

Create an appRoleAssignment using ServicePrincipalId and ResourceId.

### Example 2: SPNWithResourceDisplayNameParameterSet
```powershell
New-AzADServicePrincipalAppRoleAssignment -ServicePrincipalDisplayName funapp1214 -ResourceDisplayName nori-sp -AppRoleId b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2
```

```output
Id                                          AppRoleId                            PrincipalDisplayName PrincipalId                          CreatedDateTime
--                                          ---------                            -------------------- -----------                          ---------------
Zbm-cUeDXUmlicIc3eenIlqgWRlWp2hFrXIJiqP2j78 b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2 funapp1214           00001111-aaaa-2222-bbbb-3333cccc4444 12/14/2023 7:07:16 AM
```

Create an appRoleAssignment for service principal using ServicePrincipal DisplayName and Resource DisplayName.

## PARAMETERS

### -AdditionalProperties
ParameterSetName='CreateExpanded')]
Additional Parameters

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

### -AppRoleId
The identifier (id) for the app role which is assigned to the principal.
This app role must be exposed in the appRoles property on the resource application's service principal (resourceId).
If the resource application has not declared any app roles, a default app role ID of 00000000-0000-0000-0000-000000000000 can be specified to signal that the principal is assigned to the resource app without any specific app roles.
Required on create.

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

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with Azure.

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

### -ResourceDisplayName
The display name of the resource app's service principal to which the assignment is made.

```yaml
Type: System.String
Parameter Sets: ObjectIdWithResourceDisplayNameParameterSet, SPNWithResourceDisplayNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceId
The unique identifier (id) for the resource service principal for which the assignment is made.
Required on create.
Supports $filter (eq only).

```yaml
Type: System.String
Parameter Sets: ObjectIdWithResourceIdParameterSet, SPNWithResourceIdParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServicePrincipalDisplayName
The name displayed in directory

```yaml
Type: System.String
Parameter Sets: SPNWithResourceIdParameterSet, SPNWithResourceDisplayNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServicePrincipalId
The unique identifier (id) for the user, group or service principal being granted the app role.
Required on create.

```yaml
Type: System.String
Parameter Sets: ObjectIdWithResourceIdParameterSet, ObjectIdWithResourceDisplayNameParameterSet
Aliases:

Required: True
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

### Microsoft.Azure.PowerShell.Cmdlets.Resources.MSGraph.Models.ApiV10.IMicrosoftGraphAppRoleAssignment

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Resources.MSGraph.Models.ApiV10.IMicrosoftGraphAppRoleAssignment

## NOTES

## RELATED LINKS
