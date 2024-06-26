---
external help file: Az.HdInsightOnAks-help.xml
Module Name: Az.HdInsightOnAks
online version: https://learn.microsoft.com/powershell/module/az.hdinsightonaks/New-AzHdInsightOnAksClusterServiceConfigsProfileObject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/HdInsightOnAks/HdInsightOnAks/help/New-AzHdInsightOnAksClusterServiceConfigsProfileObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/HdInsightOnAks/HdInsightOnAks/help/New-AzHdInsightOnAksClusterServiceConfigsProfileObject.md
---

# New-AzHdInsightOnAksClusterServiceConfigsProfileObject

## SYNOPSIS
Create a service config profile.

## SYNTAX

```
New-AzHdInsightOnAksClusterServiceConfigsProfileObject -ServiceName <String> -Config <IClusterServiceConfig[]>
 [<CommonParameters>]
```

## DESCRIPTION
Create a service config profile.

## EXAMPLES

### Example 1: Create a service config profile
```powershell
$coreSiteConfigFile=New-AzHdInsightOnAksClusterConfigFileObject -FileName "core-site.xml" -Value @{"fs.defaultFS"="abfs://testcontainer@$teststorage.dfs.core.windows.net"}
$yarnComponentConfig= New-AzHdInsightOnAksClusterServiceConfigObject -ComponentName "yarn-config" -File $coreSiteConfigFile
$yarnServiceConfigProfile=New-AzHdInsightOnAksClusterServiceConfigsProfileObject -ServiceName "yarn-service" -Config $yarnComponentConfig
```

This cmdlet creates the service config profile of "yarn-service" with the component service config.

## PARAMETERS

### -Config
List of service configs.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.HdInsightOnAks.Models.IClusterServiceConfig[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServiceName
Name of the service the configurations should apply to.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.PowerShell.Cmdlets.HdInsightOnAks.Models.IClusterServiceConfig[]

### System.String

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.HdInsightOnAks.Models.IClusterServiceConfigsProfile

## NOTES

## RELATED LINKS
