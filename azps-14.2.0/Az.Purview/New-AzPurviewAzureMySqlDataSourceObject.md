---
external help file: Az.Purview-help.xml
Module Name: Az.Purview
online version: https://learn.microsoft.com/powershell/module/Az.Purview/new-azpurviewazuremysqldatasourceobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewAzureMySqlDataSourceObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewAzureMySqlDataSourceObject.md
---

# New-AzPurviewAzureMySqlDataSourceObject

## SYNOPSIS
Create an in-memory object for AzureMySqlDataSource.

## SYNTAX

```
New-AzPurviewAzureMySqlDataSourceObject [-CollectionReferenceName <String>] [-CollectionType <String>]
 [-Location <String>] [-Port <Int32>] [-ResourceGroup <String>] [-ResourceName <String>]
 [-ServerEndpoint <String>] [-SubscriptionId <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for AzureMySqlDataSource.

## EXAMPLES

### Example 1: Create Azure MySQL data source object
```powershell
New-AzPurviewAzureMySqlDataSourceObject -CollectionReferenceName 'parv-brs-2' -CollectionType 'CollectionReference' -Port 3306 -ServerEndpoint 'nause.mysql.database.azure.com'
```

```output
CollectionLastModifiedAt :
CollectionReferenceName  : parv-brs-2
CollectionType           : CollectionReference
CreatedAt                :
Id                       :
Kind                     : AzureMySql
LastModifiedAt           :
Location                 :
Name                     :
Port                     : 3306
ResourceGroup            :
ResourceName             :
Scan                     :
ServerEndpoint           : nause.mysql.database.azure.com
SubscriptionId           :
```

Create Azure MySQL data source object

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

### -Port

```yaml
Type: System.Int32
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

### Microsoft.Azure.PowerShell.Cmdlets.Purviewdata.Models.AzureMySqlDataSource

## NOTES

## RELATED LINKS
