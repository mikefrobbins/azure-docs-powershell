---
external help file: Az.EventGrid-help.xml
Module Name: Az.EventGrid
online version: https://learn.microsoft.com/powershell/module/Az.EventGrid/new-azeventgridnumberlessthanorequalsadvancedfilterobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/EventGrid/EventGrid/help/New-AzEventGridNumberLessThanOrEqualsAdvancedFilterObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/EventGrid/EventGrid/help/New-AzEventGridNumberLessThanOrEqualsAdvancedFilterObject.md
---

# New-AzEventGridNumberLessThanOrEqualsAdvancedFilterObject

## SYNOPSIS
Create an in-memory object for NumberLessThanOrEqualsAdvancedFilter.

## SYNTAX

```
New-AzEventGridNumberLessThanOrEqualsAdvancedFilterObject [-Value <Double>] [-Key <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for NumberLessThanOrEqualsAdvancedFilter.

## EXAMPLES

### Example 1: Create an in-memory object for NumberLessThanOrEqualsAdvancedFilter.
```powershell
New-AzEventGridNumberLessThanOrEqualsAdvancedFilterObject -Key "testKey" -Value 11.22
```

```output
Key     OperatorType           Value
---     ------------           -----
testKey NumberLessThanOrEquals 11.22
```

Create an in-memory object for NumberLessThanOrEqualsAdvancedFilter.

## PARAMETERS

### -Key
The field/property in the event based on which you want to filter.

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
The filter value.

```yaml
Type: System.Double
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

### Microsoft.Azure.PowerShell.Cmdlets.EventGrid.Models.NumberLessThanOrEqualsAdvancedFilter

## NOTES

## RELATED LINKS
