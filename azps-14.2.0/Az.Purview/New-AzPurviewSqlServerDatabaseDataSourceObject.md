---
external help file: Az.Purview-help.xml
Module Name: Az.Purview
online version: https://learn.microsoft.com/powershell/module/Az.Purview/new-azpurviewsqlserverdatabasedatasourceobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewSqlServerDatabaseDataSourceObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewSqlServerDatabaseDataSourceObject.md
---

# New-AzPurviewSqlServerDatabaseDataSourceObject

## SYNOPSIS
Create an in-memory object for SqlServerDatabaseDataSource.

## SYNTAX

```
New-AzPurviewSqlServerDatabaseDataSourceObject [-CollectionReferenceName <String>] [-CollectionType <String>]
 [-Location <String>] [-ResourceGroup <String>] [-ResourceName <String>] [-ServerEndpoint <String>]
 [-SubscriptionId <String>] [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for SqlServerDatabaseDataSource.

## EXAMPLES

### Example 1: Create SQL Server Database data source object
```powershell
New-AzPurviewSqlServerDatabaseDataSourceObject -CollectionReferenceName 'parv-brs-2' -CollectionType 'CollectionReference' -ServerEndpoint '12.13.14.12'
```

```output
CollectionLastModifiedAt :
CollectionReferenceName  : parv-brs-2
CollectionType           : CollectionReference
CreatedAt                :
Id                       :
Kind                     : SqlServerDatabase
LastModifiedAt           :
Location                 :
Name                     :
ResourceGroup            :
ResourceName             :
Scan                     :
ServerEndpoint           : 12.13.14.12
SubscriptionId           :
```

Create SQL Server Database data source object

## PARAMETERS

### -CollectionReferenceName

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

### -CollectionType

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

### -Location

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

### -ResourceGroup

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

### -ResourceName

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

### -ServerEndpoint

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

### -SubscriptionId

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

### Microsoft.Azure.PowerShell.Cmdlets.Purviewdata.Models.SqlServerDatabaseDataSource

## NOTES

## RELATED LINKS
