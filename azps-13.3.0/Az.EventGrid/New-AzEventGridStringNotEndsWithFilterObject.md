---
external help file: Az.EventGrid-help.xml
Module Name: Az.EventGrid
online version: https://learn.microsoft.com/powershell/module/Az.EventGrid/new-azeventgridstringnotendswithfilterobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/EventGrid/EventGrid/help/New-AzEventGridStringNotEndsWithFilterObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/EventGrid/EventGrid/help/New-AzEventGridStringNotEndsWithFilterObject.md
---

# New-AzEventGridStringNotEndsWithFilterObject

## SYNOPSIS
Create an in-memory object for StringNotEndsWithFilter.

## SYNTAX

```
New-AzEventGridStringNotEndsWithFilterObject [-Value <String[]>] [-Key <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for StringNotEndsWithFilter.

## EXAMPLES

### Example 1: Create an in-memory object for StringNotEndsWithFilter.
```powershell
New-AzEventGridStringNotEndsWithFilterObject -Key "testKey" -Value "value1","value2"
```

```output
Key     OperatorType
---     ------------
testKey StringNotEndsWith
```

Create an in-memory object for StringNotEndsWithFilter.

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
The set of filter values.

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

### Microsoft.Azure.PowerShell.Cmdlets.EventGrid.Models.StringNotEndsWithFilter

## NOTES

## RELATED LINKS
