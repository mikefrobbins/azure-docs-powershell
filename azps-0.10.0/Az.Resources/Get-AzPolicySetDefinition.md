---
external help file: Microsoft.Azure.PowerShell.Cmdlets.ResourceManager.dll-Help.xml
Module Name: Az.Resources
online version: https://learn.microsoft.com/en-us/powershell/module/az.resources/get-Azpolicysetdefinition
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/Azs-tzl/src/Resources/Resources/help/Get-AzPolicySetDefinition.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/Azs-tzl/src/Resources/Resources/help/Get-AzPolicySetDefinition.md
---

# Get-AzPolicySetDefinition

## SYNOPSIS
Gets policy set definitions.

## SYNTAX

### NameParameterSet (Default)
```
Get-AzPolicySetDefinition [-Name <String>] [-ApiVersion <String>] [-Pre]
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### ManagementGroupNameParameterSet
```
Get-AzPolicySetDefinition [-Name <String>] -ManagementGroupName <String> [-ApiVersion <String>] [-Pre]
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### SubscriptionIdParameterSet
```
Get-AzPolicySetDefinition [-Name <String>] -SubscriptionId <Guid> [-ApiVersion <String>] [-Pre]
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### IdParameterSet
```
Get-AzPolicySetDefinition -Id <String> [-ApiVersion <String>] [-Pre]
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### BuiltinFilterParameterSet
```
Get-AzPolicySetDefinition [-ManagementGroupName <String>] [-SubscriptionId <Guid>] [-Builtin]
 [-ApiVersion <String>] [-Pre] [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### CustomFilterParameterSet
```
Get-AzPolicySetDefinition [-ManagementGroupName <String>] [-SubscriptionId <Guid>] [-Custom]
 [-ApiVersion <String>] [-Pre] [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-AzPolicySetDefinition** cmdlet gets a collection of policy set definitions or a specific policy set definition identified by name or ID.

## EXAMPLES

### Example 1: Get all policy set definitions
```
PS C:\> Get-AzPolicySetDefinition
```

This command gets all the policy set definitions.

### Example 2: Get policy set definition from current subscription by name
```
PS C:\> Get-AzPolicySetDefinition -Name 'VMPolicySetDefinition'
```

This command gets the policy set definition named VMPolicySetDefinition from the current default subscription.

### Example 3: Get policy set definition from subscription by name
```
PS C:\> Get-AzPolicySetDefinition -Name 'VMPolicySetDefinition' -subscriptionId 'aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e'
```

This command gets the policy definition named VMPolicySetDefinition from the subscription with ID aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e.

### Example 4: Get all custom policy set definitions from management group
```
PS C:\> Get-AzPolicySetDefinition -ManagementGroupName 'Dept42' -Custom
```

This command gets all custom policy set definitions from the management group named Dept42.

## PARAMETERS

### -ApiVersion
When set, indicates the version of the resource provider API to use.
If not specified, the API version is automatically determined as the latest available.

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

### -Builtin
Limits list of results to only built-in policy set definitions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: BuiltinFilterParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Custom
Limits list of results to only custom policy set definitions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CustomFilterParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with azure

```yaml
Type: Microsoft.Azure.Commands.Common.Authentication.Abstractions.IAzureContextContainer
Parameter Sets: (All)
Aliases: AzContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The fully qualified policy set definition Id, including the subscription.
e.g.
/subscriptions/{subscriptionId}/resourcegroups/{resourceGroupName}

```yaml
Type: System.String
Parameter Sets: IdParameterSet
Aliases: ResourceId

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ManagementGroupName
The name of the management group of the policy set definition(s) to get.

```yaml
Type: System.String
Parameter Sets: ManagementGroupNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

```yaml
Type: System.String
Parameter Sets: BuiltinFilterParameterSet, CustomFilterParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
The policy set definition name.

```yaml
Type: System.String
Parameter Sets: NameParameterSet, ManagementGroupNameParameterSet, SubscriptionIdParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Pre
When set, indicates that the cmdlet should use pre-release API versions when automatically determining which version to use.

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

### -SubscriptionId
The subscription ID of the policy set definition(s) to get.

```yaml
Type: System.Nullable`1[System.Guid]
Parameter Sets: SubscriptionIdParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

```yaml
Type: System.Nullable`1[System.Guid]
Parameter Sets: BuiltinFilterParameterSet, CustomFilterParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String

### System.Nullable`1[[System.Guid, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]]

## OUTPUTS

### System.Management.Automation.PSObject

## NOTES

## RELATED LINKS
