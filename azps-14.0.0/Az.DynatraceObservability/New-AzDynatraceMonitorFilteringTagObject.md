---
external help file: Az.DynatraceObservability-help.xml
Module Name: Az.DynatraceObservability
online version: https://learn.microsoft.com/powershell/module/Az.DynatraceObservability/new-azdynatracemonitorfilteringtagobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DynatraceObservability/DynatraceObservability/help/New-AzDynatraceMonitorFilteringTagObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DynatraceObservability/DynatraceObservability/help/New-AzDynatraceMonitorFilteringTagObject.md
---

# New-AzDynatraceMonitorFilteringTagObject

## SYNOPSIS
Create an in-memory object for FilteringTag.

## SYNTAX

```
New-AzDynatraceMonitorFilteringTagObject [-Action <String>] [-Name <String>] [-Value <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for FilteringTag.

## EXAMPLES

### Example 1: Create an in-memory object for FilteringTag
```powershell
New-AzDynatraceMonitorFilteringTagObject -Action 'Include' -Name 'Environment' -Value 'Prod'
```

```output
Action  Name        Value
------  ----        -----
Include Environment Prod
```

This command creates an in-memory object for FilteringTag.

## PARAMETERS

### -Action
Valid actions for a filtering tag.
Exclusion takes priority over inclusion.

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

### -Name
The name (also known as the key) of the tag.

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

### -Value
The value of the tag.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DynatraceObservability.Models.FilteringTag

## NOTES

## RELATED LINKS
