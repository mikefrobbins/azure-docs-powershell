---
external help file: Microsoft.Azure.PowerShell.Cmdlets.Dns.dll-Help.xml
Module Name: Az.Dns
ms.assetid: CD119EBE-E1A4-4E9D-B3BA-FDAF89BF0DDB
online version: https://learn.microsoft.com/powershell/module/az.dns/add-azdnsrecordconfig
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Dns/Dns/help/Add-AzDnsRecordConfig.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Dns/Dns/help/Add-AzDnsRecordConfig.md
---

# Add-AzDnsRecordConfig

## SYNOPSIS
Adds a DNS record to a local record set object.

## SYNTAX

### A
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Ipv4Address <String>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### AAAA
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Ipv6Address <String>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### NS
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Nsdname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### MX
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Exchange <String> -Preference <UInt16>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### PTR
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Ptrdname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### TXT
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Value <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### SRV
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Priority <UInt16> -Target <String> -Port <UInt16>
 -Weight <UInt16> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### CNAME
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Cname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Caa
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -CaaFlags <Byte> -CaaTag <String> -CaaValue <String>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### DS
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -KeyTag <Int32> -Algorithm <Int32> -DigestType <Int32>
 -Digest <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### TLSA
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Usage <Int32> -Selector <Int32> -MatchingType <Int32>
 -CertificateAssociationData <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### NAPTR
```
Add-AzDnsRecordConfig -RecordSet <DnsRecordSet> -Order <UInt16> -Preference <UInt16> -Flags <String> 
 -Services <String> -Regexp <String> -Replacement <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Add-AzDnsRecordConfig** cmdlet adds a Domain Name System (DNS) record to a **RecordSet** object.
The **RecordSet** object is an offline object, and changes to it do not change the DNS responses until after you run the Set-AzDnsRecordSet cmdlet to persist the change to the Microsoft Azure DNS service.
SOA records are created when a DNS zone is created, and are removed when the DNS zone is deleted.
You cannot add or remove SOA records, but you can edit them.
You can pass the **RecordSet** object to this cmdlet as a parameter or by using the pipeline operator.

## EXAMPLES

### Example 1: Add an A record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name www -RecordType A -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Ipv4Address 1.2.3.4
Set-AzDnsRecordSet -RecordSet $RecordSet

# You can also pipe the above sequence:

Get-AzDnsRecordSet -Name www -RecordType A -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Ipv4Address 1.2.3.4 | Set-AzDnsRecordSet
```

This example adds an A record to an existing record set.

### Example 2: Add an AAAA record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name www -RecordType AAAA -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Ipv6Address 2001:DB80:4009:1803::1005
Set-AzDnsRecordSet -RecordSet $RecordSet

# You can also pipe the above sequence:

Get-AzDnsRecordSet -Name www -RecordType AAAA -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Ipv6Address 2001:DB80:4009:1803::1005 | Set-AzDnsRecordSet
```

This example adds an AAAA record to an existing record set.

### Example 3: Add a CNAME record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name www -RecordType CNAME -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Cname contoso.com
Set-AzDnsRecordSet -RecordSet $RecordSet

# You can also pipe the above sequence:

Get-AzDnsRecordSet -Name www -RecordType CNAME -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Cname contoso.com | Set-AzDnsRecordSet
```

This example adds a CNAME record to an existing record set.
Because a CNAME record set can contain at most one record, it must initially be an empty record set, or existing records must be removed using Remove-AzDnsRecordConfig.

### Example 4: Add an MX record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name "@" -RecordType MX -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -Exchange mail.microsoft.com -Preference 5 -RecordSet $RecordSet
Set-AzDnsRecordSet -RecordSet $RecordSet

# You can also pipe the above sequence:

Get-AzDnsRecordSet -Name "@" -RecordType MX -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Exchange mail.microsoft.com -Preference 5 | Set-AzDnsRecordSet
```

This example adds an MX record to an existing record set.
The record name "@" indicates a record set at the zone apex.

### Example 5: Add an NS record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name abc -RecordType NS -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -Nsdname ns1.myzone.com -RecordSet $RecordSet
Set-AzDnsRecordSet -RecordSet $RecordSet

# You can also pipe the above sequence:

Get-AzDnsRecordSet -Name abc -RecordType NS -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Nsdname ns1.myzone.com | Set-AzDnsRecordSet
```

This example adds an NS record to an existing record set.

### Example 6: Add a PTR record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name 4 -RecordType PTR -ResourceGroupName MyResourceGroup -ZoneName 3.2.1.in-addr.arpa
Add-AzDnsRecordConfig -Ptrdname www.contoso.com -RecordSet $RecordSet
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name 4 -RecordType PTR -ResourceGroupName MyResourceGroup -ZoneName 3.2.1.in-addr.arpa | Add-AzDnsRecordConfig -Ptrdname www.contoso.com | Set-AzDnsRecordSet
```

This example adds a PTR record to an existing record set.

### Example 7: Add an SRV record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name _sip._tcp -RecordType SRV -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Priority 0 -Weight 5 -Port 8080 -Target target.example.com
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name _sip._tcp -RecordType SRV -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Priority 0 -Weight 5 -Port 8080 -Target target.example.com  | Set-AzDnsRecordSet
```

This example adds an SRV record to an existing record set.

### Example 8: Add a TXT record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name text -RecordType TXT -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Value "This is a TXT Record"
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name text -RecordType TXT -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Value "This is a TXT Record" | Set-AzDnsRecordSet
```

This example adds a TXT record to an existing record set.

### Example 9: Add a DS record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name www -RecordType DS -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -KeyTag 12345 -Algorithm 3 -DigestType 1 -Digest "49FD46E6C4B45C55D4AC"
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name www -RecordType DS -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -KeyTag 12345 -Algorithm 3 -DigestType 1 -Digest "49FD46E6C4B45C55D4AC" | Set-AzDnsRecordSet
```

### Example 10: Add a TLSA record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name _443._tcp.www -RecordType TLSA -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Usage 3 -Selector 1 -MatchingType 1 -CertificateAssociationData "49FD46E6C4B45C55D4AC"
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name _443._tcp.www -RecordType TLSA -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Usage 3 -Selector 1 -MatchingType 1 -CertificateAssociationData "49FD46E6C4B45C55D4AC" | Set-AzDnsRecordSet
```

### Example 11: Add a NAPTR record to a record set
```powershell
$RecordSet = Get-AzDnsRecordSet -Name www -RecordType NAPTR -ResourceGroupName MyResourceGroup -ZoneName myzone.com
Add-AzDnsRecordConfig -RecordSet $RecordSet -Order 100 -Preference 100 -Flags "s" -Services "http" -Regexp "" -Replacement "www.contoso.com"
Set-AzDnsRecordSet -RecordSet $RecordSet

# The above sequence can also be piped:

Get-AzDnsRecordSet -Name www -RecordType NAPTR -ResourceGroupName MyResourceGroup -ZoneName myzone.com | Add-AzDnsRecordConfig -Order 100 -Preference 100 -Flags "s" -Services "http" -Regexp "" -Replacement "www.contoso.com" | Set-AzDnsRecordSet
```

## PARAMETERS

### -Algorithm
The algorithm field of the DS record to add.

```yaml
Type: System.Int32
Parameter Sets: DS
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CaaFlags
The flags for the CAA record to add. Must be a number between 0 and 255.

```yaml
Type: System.Byte
Parameter Sets: Caa
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CaaTag
The tag field of the CAA record to add.

```yaml
Type: System.String
Parameter Sets: Caa
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CaaValue
The value field for the CAA record to add.

```yaml
Type: System.String
Parameter Sets: Caa
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateAssociationData
The certificate association data field of the TLSA record to add.

```yaml
Type: System.String
Parameter Sets: TLSA
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Cname
Specifies the domain name for a canonical name (CNAME) record.

```yaml
Type: System.String
Parameter Sets: CNAME
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with azure

```yaml
Type: Microsoft.Azure.Commands.Common.Authentication.Abstractions.Core.IAzureContextContainer
Parameter Sets: (All)
Aliases: AzContext, AzureRmContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Digest
The digest field of the DS record to add.

```yaml
Type: System.String
Parameter Sets: DS
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DigestType
The digest type field of the DS record to add.

```yaml
Type: System.Int32
Parameter Sets: DS
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exchange
Specifies the mail exchange server name for a mail exchange (MX) record.

```yaml
Type: System.String
Parameter Sets: MX
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Flags
Specifies the flags for a Named Authority Pointer (NAPTR) record.

```yaml
Type: System.String
Parameter Sets: NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```


### -Ipv4Address
Specifies an IPv4 address for an A record.

```yaml
Type: System.String
Parameter Sets: A
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Ipv6Address
Specifies an IPv6 address for an AAAA record.

```yaml
Type: System.String
Parameter Sets: AAAA
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -KeyTag
The key tag field of the DS record to add.

```yaml
Type: System.Int32
Parameter Sets: DS
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MatchingType
The matching type field of the TLSA record to add.

```yaml
Type: System.Int32
Parameter Sets: TLSA
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nsdname
Specifies the name server name for a name server (NS) record.

```yaml
Type: System.String
Parameter Sets: NS
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Order
Specifies the order for a naming authority pointer (NAPTR) record.

```yaml
Type: System.UInt16
Parameter Sets: NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port
Specifies the port for a service (SRV) record.

```yaml
Type: System.UInt16
Parameter Sets: SRV
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Preference
Specifies the preference for an MX/NAPTR record.

```yaml
Type: System.UInt16
Parameter Sets: MX, NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Priority
Specifies the priority for an SRV record.

```yaml
Type: System.UInt16
Parameter Sets: SRV
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Ptrdname
Specifies the target domain name of a pointer resource (PTR) record.

```yaml
Type: System.String
Parameter Sets: PTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RecordSet
Specifies the **RecordSet** object to edit.

```yaml
Type: Microsoft.Azure.Commands.Dns.DnsRecordSet
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Regexp
Specifies the regexp field for a Named Authority Pointer (NAPTR) record.

```yaml
Type: System.String
Parameter Sets: NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Replacement
Specifies the replacement field for a Named Authority Pointer (NAPTR) record.

```yaml
Type: System.String
Parameter Sets: NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Services
Specifies the services field for a Named Authority Pointer (NAPTR) record.

```yaml
Type: System.String
Parameter Sets: NAPTR
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Selector
The selector field of the TLSA record to add.

```yaml
Type: System.Int32
Parameter Sets: TLSA
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Target
Specifies the target for an SRV record.

```yaml
Type: System.String
Parameter Sets: SRV
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Usage
The usage field of the TLSA record to add.

```yaml
Type: System.Int32
Parameter Sets: TLSA
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value
Specifies the value for a TXT record.

```yaml
Type: System.String
Parameter Sets: TXT
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Weight
Specifies the weight for an SRV record.

```yaml
Type: System.UInt16
Parameter Sets: SRV
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.Commands.Dns.DnsRecordSet

### System.String

### System.UInt16

### System.Byte

## OUTPUTS

### Microsoft.Azure.Commands.Dns.DnsRecordSet

## NOTES

## RELATED LINKS

[Get-AzDnsRecordSet](./Get-AzDnsRecordSet.md)

[Remove-AzDnsRecordConfig](./Remove-AzDnsRecordConfig.md)

[Set-AzDnsRecordSet](./Set-AzDnsRecordSet.md)
