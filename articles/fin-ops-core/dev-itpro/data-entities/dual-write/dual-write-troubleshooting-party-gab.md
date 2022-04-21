---
title: Party and global address book troubleshooting
description: This topic provides troubleshooting information that can help you fix issues that are related to dual-write party and global address book functions.
author: RamaKrishnamoorthy
ms.date: 07/30/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: AX 7.0.0
---

# Party and global address book troubleshooting

[!include [banner](../../includes/banner.md)]



This topic provides troubleshooting information that can help you fix issues that are related to dual-write party and global address book functions.

## Verify these prerequisites

Before you use the party and global address book functionality, make sure these are configured correctly.

+ Integration keys.

    | Map | Keys |
    |-----|------|
    | Account |  accountnumber [Account Number]<br>msdyn_company.cdm_companycode [Company (Company Code)] |
    | Contact | msdyn_contactpersonid [Account Number/Contact Person ID]<br>msdyn_company.cdm_companycode [Company (Company Code)] |
    | Contact For Customer/Vendor | msdyn_contactforpartynumber [Contact For Party Number]<br>msdyn_associatedcompanyid.cdm_companycode [Associated Company (Company Code)] |
    | Vendor | msdyn_vendoraccountnumber [Vendor Account Number]<br>msdyn_company.cdm_companycode [Company (Company Code)]|

+ Map versions. For more information, see [Party and global address book](party-gab.md#setup).

## Error about Location ID key when you try to add an address

You might receive the following error message when you try to add an address to an account or contact in a Finance and Operations app or Microsoft Dataverse:

*Unable to write data to entity msdyn_partypostaladdresses. Writes to DirPartyPostalAddressLocationCDSEntity failed with error message Request failed with status code BadRequest and CDS error code: 0x80040265 response message: An error occurred in plugin. A record that has the attribute values Location ID already exists. The entity key Location ID Key requires that this set of attributes contains unique values. Select unique values and try again.*

To fix this issue, make sure that the key on the **Address** table is set as shown in the following table.

Property | Value
---|---
Display Name | Location Key
Name | msdyn_locationkey
Fields | msdn_locationid, parentid
Status | Active
System Job | (blank)

If Dual-write Party and Global Address Book Solutions is not installed, then the key on this table is set to the **msdyn_locationid** field. Install the dual-write orchestration solution version (version 2.2.2.60 or later). This replaces the previous key created on **Address** table.

## Error when you try to run Customers, Vendors, or Contacts V2 maps

You might receive the following error message when you try to run **Customers**, **Vendors**, or **Contacts V2** maps:

*Customers V3 (accounts): Project validation failed. Missing destination field msdyn_billingaccount.accountnumber in the schema. Missing destination field msdyn_primarycontact.msdyn_contactforpartynumber in the schema.*

There are multiple keys defined on the **msdyn_company** table in Dataverse. Dual-write cannot determine which key to use as integration key, and it randomly assigns one of the keys as integration key. To fix this issue, update the integration keys manually as described in step 8 of [Party and global address book](party-gab.md#setup). Then refresh the table mappings. The missing destination field error should disappear.

## Error that the Party ID is different between Finance and Operations apps and Dataverse

You might receive an error message that the Party ID is different between a Finance and Operations app and Dataverse for the **Customers**, **Vendors**, or **Contacts V2** maps.

To fix this issue, use the latest version of maps as described in step 7 of [Party and global address book](party-gab.md#setup).

## Errors when upgrading Dual-write Party and Global Address Book Solutions

You might receive error messages when you upgrade Dual-write Party and Global Address Book Solutions from 2.4.0155 to later versions.

The party and global address book functionality was part of the dual-write orchestration solution when it was released for preview in January and February 2021. Based on customer feedback, the functionality was released for General Availability as a separate solution. As a separate solution, the functionality is optional. If you are using the preview version of the dual-write orchestration solution that contains party and global address book functionality, then you need to uninstall the dual-write orchestration solutions or reset the Dataverse environment and get the latest solutions.

Dual-write Party and Global Address Book Solutions contains the following solutions.

+ **Party** - Includes the schemas for party, postal address, and electronic address.
+ **Dynamics365GABExtended** - Includes all code and schema changes to support **Accounts**, **Vendors**, **Contacts**, and **Contact** for party functionality. This support was separated from the **Dynamics365FinanceExtended** and **Dynamics365SupplyChainExtended** solutions.
+ **Dynamics365GABDualWriteEntityMaps** - Includes all the dual-write mapping changes required for global address book functionality.
+ **Dynamics365GABParty_Anchor**

## Error when you try to create a new contact from the View Contact form

You might receive the following error message when you try to create a new contract from the **View Contact** form in a Finance and Operations app:

*Unable to write data to entity msdyn_contactforparties. Unable to lookup msdyn_parties with values {000006057}. Unable to lookup cdm_workers with values {000020}.*

To fix this issue, create the **Contact** record using the **Add Contact** form.

## Error when you try to update a contact

You might receive the following error message when you try to update a contact that originated in Dataverse in a Finance and Operations app.

*Unable to write data to entity msdyn_contactforparties.Writes to smmContactPersonV2Entity failed with error message Request failed with status code BadRequest and CDS error code: 0x0 response message: An error occurred while validating input parameters: Microsoft.OData.ODataException: Cannot convert the literal '' to the expected type 'Edm.Int32'.*

To fix this issue, install the latest Dual-write Party and Global Address Book Solutions. This issue is fixed in version 3.0.0.26.

## Error when you create a new customer, vendor, or contact in Dataverse

You might receive the following error message when you try to create a new customer, vendor, or contact in Dataverse:

*Cannot update a party's type from 'DirOrganization' to 'DirPerson', a delete of the existing party followed by an insert with the new type should be performed instead.*

This issue occurs in non-production environments if users try connecting one Finance and Operations app to different Dataverse organizations, or if they try to reset the existing Dataverse organizations. The issue is due to the number sequence for Party ID in the **msdyn_party** table in Dataverse. The follow sequence of events generates the error:

1. An account is created in Dataverse. Dataverse creates a new party with Party ID **Party-001** and Party type **Organization**. 
2. The new account is then sent to the Finance and Operations app.
3. The Dataverse environment is reset later or the same Finance and Operations apps environment is again connected to a different Dataverse organization.
4. You create a new contact this time in Dataverse. The number sequence for **msdyn_party** starts with **Party-001**. This time, the party record is created with **Party-001** and Party type as **Person**.
5. The data is synced to the Finance and Operations app. Because the Finance and Operations app already has **Party-001** as **Organization**, the error is generated.

To fix this issue, change the auto number sequence for the **msdyn_partynumber** field in the **msdyn_party** table to a different auto number sequence.

## Error when you run the initial sync of party postal addresses and party electronic addresses

You might receive an error such as "the **Party** number could not be found" when you try to run the initial sync of party postal addresses and party electronic addresses.

There is a range added to the **DirPartyCDSEntity** entity in Finance and Operations apps to filter only parties of type **Person** and **Organization**. As a result, the initial sync of the **CDS Parties – msdyn_parties** mapping will not sync parties of other types, including **Legal Entity** and **Operating Unit**. When the initial sync runs for **CDS Party postal addresses (msdyn_partypostaladdresses)** or **Party Contacts V3 (msdyn_partyelectronicaddresses)** you might see errors, for example, that the **Party** number could not be found in Dataverse.

We are working to remove the party type range on the Finance and Operations apps entity so that parties of all types synchronize to Dataverse successfully. Check back to this topic for updates. 

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
