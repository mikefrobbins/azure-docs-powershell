---
external help file: Microsoft.Azure.PowerShell.Cmdlets.Dns.dll-Help.xml
Module Name: Az.Dns
ms.assetid: AD97BCAF-69BA-4C16-8B57-AB243D796B71
online version: https://learn.microsoft.com/powershell/module/az.dns/new-azdnsrecordconfig
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Dns/Dns/help/New-AzDnsRecordConfig.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Dns/Dns/help/New-AzDnsRecordConfig.md
---

# New-AzDnsRecordConfig

## SYNOPSIS
Creates a new DNS record local object.

## SYNTAX

### A
```
New-AzDnsRecordConfig -Ipv4Address <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Aaaa
```
New-AzDnsRecordConfig -Ipv6Address <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Ns
```
New-AzDnsRecordConfig -Nsdname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Mx
```
New-AzDnsRecordConfig -Exchange <String> -Preference <UInt16> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Ptr
```
New-AzDnsRecordConfig -Ptrdname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Txt
```
New-AzDnsRecordConfig -Value <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Srv
```
New-AzDnsRecordConfig -Priority <UInt16> -Target <String> -Port <UInt16> -Weight <UInt16>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### CName
```
New-AzDnsRecordConfig -Cname <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Caa
```
New-AzDnsRecordConfig -CaaFlags <Byte> -CaaTag <String> -CaaValue <String>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### Ds
```
New-AzDnsRecordConfig -KeyTag <Int32> -Algorithm <Int32> -DigestType <Int32> -Digest <String>
 [-DefaultProfile <IAzureContextContainer>] [<CommonParameters>]
```

### Tlsa
```
New-AzDnsRecordConfig -Usage <Int32> -Selector <Int32> -MatchingType <Int32>
 -CertificateAssociationData <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

### Naptr
```
New-AzDnsRecordConfig -Flags <UInt16> -Order <UInt16> -Preference <UInt16> -Services <String>
 -Regexp <String> -Replacement <String> [-DefaultProfile <IAzureContextContainer>]
 [<CommonParameters>]
```

## DESCRIPTION
The **New-AzDnsRecordConfig** cmdlet creates a local **DnsRecord** object.
An array of these objects is passed to the New-AzDnsRecordSet cmdlet using the *DnsRecords* parameter to specify the records to create in the record set.

## EXAMPLES

### Example 1: Create a RecordSet of type A
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -IPv4Address 1.2.3.4
$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType A -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records

# When creating a RecordSet containing a single record, the above sequence can also be condensed into a single line:

$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType A -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords (New-AzDnsRecordConfig -IPv4Address 1.2.3.4)

# To create a record set containing multiple records, use New-AzDnsRecordConfig to add each record to the $Records array,
# then call New-AzDnsRecordSet, as follows:

$Records = @()
$Records += New-AzDnsRecordConfig -IPv4Address 1.2.3.4
$Records += New-AzDnsRecordConfig -IPv4Address 5.6.7.8
$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType A -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This example creates a **RecordSet** named www in the zone myzone.com.
The record set is of type A and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.

### Example 2: Create a RecordSet of type AAAA
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Ipv6Address 2001:db8::1
$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType AAAA -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This example creates a **RecordSet** named www in the zone myzone.com.
The record set is of type AAAA and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 3: Create a RecordSet of type CNAME
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Cname www.contoso.com
$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType CNAME -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This example creates a **RecordSet** named www in the zone myzone.com.
The record set is of type CNAME and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 4: Create a RecordSet of type MX
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Exchange "mail.microsoft.com" -Preference 5
$RecordSet = New-AzDnsRecordSet -Name "www" -RecordType AAAA -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named www in the zone myzone.com.
The record set is of type MX and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 5: Create a RecordSet of type NS
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Nsdname ns1-01.azure-dns.com
$RecordSet = New-AzDnsRecordSet -Name "ns1" -RecordType NS -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named ns1 in the zone myzone.com.
The record set is of type NS and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 6: Create a RecordSet of type PTR
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Ptrdname www.contoso.com
$RecordSet = New-AzDnsRecordSet -Name "4" -RecordType PTR -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "3.2.1.in-addr.arpa" -DnsRecords $Records
```

This command creates a **RecordSet** named 4 in the zone 3.2.1.in-addr.arpa.
The record set is of type PTR and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 7: Create a RecordSet of type SRV
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Priority 0 -Weight 5 -Port 8080 -Target sipservice.contoso.com
$RecordSet = New-AzDnsRecordSet -Name "_sip._tcp" -RecordType SRV -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named _sip._tcp in the zone myzone.com.
The record set is of type SRV and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record, pointing to the IP address 2001.2.3.4.
The service (sip) and the protocol (tcp) are specified as part of the record set name, not as part of the record data.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 8: Create a RecordSet of type TXT
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Value "This is a TXT Record"
$RecordSet = New-AzDnsRecordSet -Name "text" -RecordType TXT -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named text in the zone myzone.com.
The record set is of type TXT and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 9: Create a RecordSet of type DS
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -KeyTag 12345 -Algorithm 3 -DigestType 1 -Digest "49FD46E6C4B45C55D4AC"
$RecordSet = New-AzDnsRecordSet -Name "childds" -RecordType DS -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named childds in the zone myzone.com.
The record set is of type DS and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
The record data contains the key tag, algorithm, digest type, and digest of the child zone's DNSKEY record.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 10: Create a RecordSet of type TLSA
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Usage 3 -Selector 1 -MatchingType 1 -CertificateAssociationData "49FD46E6C4B45C55D4AC"
$RecordSet = New-AzDnsRecordSet -Name "_443._tcp.www" -RecordType TLSA -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named _443._tcp.www in the zone myzone.com.
The record set is of type TLSA and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
The record data contains the usage, selector, and matching type of the certificate association data.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

### Example 11: Create a RecordSet of type NAPTR
```powershell
$Records = @()
$Records += New-AzDnsRecordConfig -Flags 0 -Order 100 -Preference 100 -Services "SIP+D2U" -Regexp "" -Replacement "example.com"
$RecordSet = New-AzDnsRecordSet -Name "naptr123" -RecordType NAPTR -ResourceGroupName "MyResourceGroup" -TTL 3600 -ZoneName "myzone.com" -DnsRecords $Records
```

This command creates a **RecordSet** named naptr123 in the zone myzone.com.
The record set is of type NAPTR and has a TTL of 1 hour (3600 seconds).
It contains a single DNS record.
The record data contains the order, preference, flags, services, regexp, and replacement fields.
To create a **RecordSet** using only one line of pn_PowerShell_short, or to create a record set with multiple records, see Example 1.

## PARAMETERS

### -Algorithm
The algorithm field of the DS record to add.

```yaml
Type: System.Int32
Parameter Sets: Ds
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
Parameter Sets: Tlsa
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
Parameter Sets: CName
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
Parameter Sets: Ds
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
Parameter Sets: Ds
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
Parameter Sets: Mx
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Flags
Specifies the flags for a NAPTR record.

```yaml
Type: System.UInt16
Parameter Sets: Naptr
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
Parameter Sets: Aaaa
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
Parameter Sets: Ds
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
Parameter Sets: Tlsa
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
Parameter Sets: Ns
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Order
Specifies the order for a NAPTR record.

```yaml
Type: System.UInt16
Parameter Sets: Naptr
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
Parameter Sets: Srv
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
Parameter Sets: Mx, NAPTR
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
Parameter Sets: Srv
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
Parameter Sets: Ptr
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Regexp
Specifies the regexp for a NAPTR record.

```yaml
Type: System.String
Parameter Sets: Naptr
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Replacement
Specifies the replacement for a NAPTR record.

```yaml
Type: System.String
Parameter Sets: Naptr
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Services
Specifies the services for a NAPTR record.

```yaml
Type: System.String
Parameter Sets: Naptr
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
Parameter Sets: Tlsa
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
Parameter Sets: Srv
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
Parameter Sets: Tlsa
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
Parameter Sets: Txt
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
Parameter Sets: Srv
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

### System.String

### System.UInt16

### System.Byte

## OUTPUTS

### Microsoft.Azure.Commands.Dns.DnsRecordBase

## NOTES

## RELATED LINKS

[Add-AzDnsRecordConfig](./Add-AzDnsRecordConfig.md)

[New-AzDnsRecordSet](./New-AzDnsRecordSet.md)

[Remove-AzDnsRecordConfig](./Remove-AzDnsRecordConfig.md)
