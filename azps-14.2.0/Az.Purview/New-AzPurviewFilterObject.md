---
external help file: Az.Purview-help.xml
Module Name: Az.Purview
online version: https://learn.microsoft.com/powershell/module/Az.Purview/new-azpurviewfilterobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewFilterObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewFilterObject.md
---

# New-AzPurviewFilterObject

## SYNOPSIS
Create an in-memory object for Filter.

## SYNTAX

```
New-AzPurviewFilterObject [-ExcludeUriPrefix <String[]>] [-IncludeUriPrefix <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for Filter.

## EXAMPLES

### Example 1: Create filter object
```powershell
New-AzPurviewFilterObject -ExcludeUriPrefix @('https://foo.file.core.windows.net/share1/user/temp') -IncludeUriPrefix @('https://foo.file.core.windows.net/share1/user','https://foo.file.core.windows.net/share1/aggregated')
```

```output
ExcludeUriPrefix  : {https://foo.file.core.windows.net/share1/user/temp}
Id                :
IncludeUriPrefix  : {https://foo.file.core.windows.net/share1/user,
                    https://foo.file.core.windows.net/share1/aggregated}
Name              :
```

Create filter object

## PARAMETERS

### -ExcludeUriPrefix

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeUriPrefix

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

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

### Microsoft.Azure.PowerShell.Cmdlets.Purviewdata.Models.Filter

## NOTES

## RELATED LINKS
