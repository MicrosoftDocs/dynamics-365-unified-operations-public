---
title: Party and global address book troubleshooting
description: Learn about how you can fix issues that are related to dual-write party and global address book functions, including a table of prerequisites to verify.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: troubleshooting-general
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: AX 7.0.0
---

# Party and global address book troubleshooting

[!include [banner](../../includes/banner.md)]

This article provides troubleshooting information that can help you fix problems related to dual-write party and global address book functions.

## Verify these prerequisites

Before you use the party and global address book functionality, make sure these prerequisites are configured correctly.

+ Integration keys.

    | Map | Keys |
    |-----|------|
    | Account |  accountnumber [Account Number]<br>msdyn_company.cdm_companycode [Company (Company Code)] |
    | Contact | msdyn_contactpersonid [Account Number/Contact Person ID]<br>msdyn_company.cdm_companycode [Company (Company Code)] |
    | Contact For Customer/Vendor | msdyn_contactforpartynumber [Contact For Party Number]<br>msdyn_associatedcompanyid.cdm_companycode [Associated Company (Company Code)] |
    | Vendor | msdyn_vendoraccountnumber [Vendor Account Number]<br>msdyn_company.cdm_companycode [Company (Company Code)]|

+ Map versions. For more information, see [Party and global address book](party-gab.md#setup).

## Error about Location ID key when you try to add an address

You might receive the following error message when you try to add an address to an account or contact in a finance and operations app or Microsoft Dataverse:

*Unable to write data to entity msdyn_partypostaladdresses. Writes to DirPartyPostalAddressLocationCDSEntity failed with error message Request failed with status code BadRequest and CDS error code: 0x80040265 response message: An error occurred in plugin. A record that has the attribute values Location ID already exists. The entity key Location ID Key requires that this set of attributes contains unique values. Select unique values and try again.*

To fix this issue, make sure that the key on the **Address** table is set as shown in the following table.

Property | Value
---|---
Display Name | Location Key
Name | msdyn_locationkey
Fields | msdn_locationid, parentid
Status | Active
System Job | (blank)

If you didn't install Dual-write Party and Global Address Book Solutions, the key on this table is set to the **msdyn_locationid** field. Install the dual-write orchestration solution version (version 2.2.2.60 or later). This version replaces the previous key created on the **Address** table.

## Error when you try to run Customers, Vendors, or Contacts V2 maps

You might receive the following error message when you try to run **Customers**, **Vendors**, or **Contacts V2** maps:

*Customers V3 (accounts): Project validation failed. Missing destination field msdyn_billingaccount.accountnumber in the schema. Missing destination field msdyn_primarycontact.msdyn_contactforpartynumber in the schema.*

You defined multiple keys on the **msdyn_company** table in Dataverse. Dual-write can't determine which key to use as the integration key, so it randomly assigns one of the keys as the integration key. To fix this issue, update the integration keys manually as described in step 8 of [Party and global address book](party-gab.md#setup). Then refresh the table mappings. The missing destination field error disappears.

## Error that the Party ID is different between finance and operations apps and Dataverse

You might receive an error message that the Party ID is different between a finance and operations app and Dataverse for the **Customers**, **Vendors**, or **Contacts V2** maps.

To fix this problem, use the latest version of maps as described in step 7 of [Party and global address book](party-gab.md#setup).

## Errors when upgrading Dual-write Party and Global Address Book Solutions

You might receive error messages when you upgrade Dual-write Party and Global Address Book Solutions from 2.4.0155 to later versions.

The party and global address book functionality was part of the dual-write orchestration solution when it was released for preview in January and February 2021. Based on customer feedback, Microsoft released the functionality as a separate solution for General Availability. As a separate solution, the functionality is optional. If you're using the preview version of the dual-write orchestration solution that contains party and global address book functionality, uninstall the dual-write orchestration solutions or reset the Dataverse environment and get the latest solutions.

Dual-write Party and Global Address Book Solutions contains the following solutions.

+ **Party** - Includes the schemas for party, postal address, and electronic address.
+ **Dynamics365GABExtended** - Includes all code and schema changes to support **Accounts**, **Vendors**, **Contacts**, and **Contact** for party functionality. This support was separated from the **Dynamics365FinanceExtended** and **Dynamics365SupplyChainExtended** solutions.
+ **Dynamics365GABDualWriteEntityMaps** - Includes all the dual-write mapping changes required for global address book functionality.
+ **Dynamics365GABParty_Anchor**

## Error when you try to create a new contact from the View Contact form

You might receive the following error message when you try to create a new contract from the **View Contact** form in a finance and operations app:

*Unable to write data to entity msdyn_contactforparties. Unable to look up msdyn_parties with values {000006057}. Unable to look up cdm_workers with values {000020}.*

To fix this problem, create the **Contact** record by using the **Add Contact** form.

## Error when you try to update a contact

You might receive the following error message when you try to update a contact that originated in Dataverse in a finance and operations app.

*Unable to write data to entity msdyn_contactforparties.Writes to smmContactPersonV2Entity failed with error message Request failed with status code BadRequest and CDS error code: 0x0 response message: An error occurred while validating input parameters: Microsoft.OData.ODataException: Can't convert the literal '' to the expected type 'Edm.Int32'.*

To fix this issue, install the latest Dual-write Party and Global Address Book Solutions. This issue is fixed in version 3.0.0.26.

## Error when you create a new customer, vendor, or contact in Dataverse

You might receive the following error message when you try to create a new customer, vendor, or contact in Dataverse:

*Can't update a party's type from 'DirOrganization' to 'DirPerson', a delete of the existing party followed by an insert with the new type should be performed instead.*

This issue occurs in non-production environments if users try connecting one finance and operations app to different Dataverse organizations, or if they try to reset the existing Dataverse organizations. The issue is due to the number sequence for Party ID in the **msdyn_party** table in Dataverse. The following sequence of events generates the error:

1. An account is created in Dataverse. Dataverse creates a new party with Party ID **Party-001** and Party type **Organization**.
1. The new account is then sent to the finance and operations app.
1. The Dataverse environment is reset later or the same finance and operations apps environment is again connected to a different Dataverse organization.
1. You create a new contact this time in Dataverse. The number sequence for **msdyn_party** starts with **Party-001**. This time, the party record is created with **Party-001** and Party type as **Person**.
1. The data is synced to the finance and operations app. Because the finance and operations app already has **Party-001** as **Organization**, the error is generated.

To fix this issue, change the auto number sequence for the **msdyn_partynumber** field in the **msdyn_party** table to a different auto number sequence.

## Error when you run the initial sync of party postal addresses and party electronic addresses

You might receive an error such as "the **Party** number couldn't be found" when you try to run the initial sync of party postal addresses and party electronic addresses.

The **DirPartyCDSEntity** entity in finance and operations apps includes a filter that only syncs parties of type **Person** and **Organization**. As a result, the initial sync of the **CDS Parties – msdyn_parties** mapping doesn't sync parties of other types, including **Legal Entity** and **Operating Unit**. When you run the initial sync for **CDS Party postal addresses (msdyn_partypostaladdresses)** or **Party Contacts V3 (msdyn_partyelectronicaddresses)**, you might see errors that the **Party** number couldn't be found in Dataverse.

The product team is working to remove the party type range on the finance and operations apps entity so that parties of all types synchronize to Dataverse successfully. Check back to this article for updates.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
