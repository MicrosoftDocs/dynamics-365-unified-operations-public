---
# required metadata

title: Address books FAQ
description: This article provides answers to frequently asked questions related to address books. 
author: msftbrking 
ms.date: 07/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirPartyCheckDuplicate, DirPartyTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: b177fa0f-ac9a-415e-9498-15438e132f60
ms.search.region: Global
# ms.search.industry: 
ms.author: brking
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Address books FAQ

[!include [banner](../includes/banner.md)]

## How do I check for duplicate records?

You can check for duplicate records directly from the **Global address book** list page. On the Action Pane, on the **Party** tab, in the **Maintain** group, select **Check for duplicates**. Then select the values to include in the check for duplicates.

## Can I bulk add or delete party records from an address book?

Yes, you can add multiple party records to an address book and also remove multiple party records.

- To add multiple party records to an address book, on the **Global address book** list page, select the parties in the list. Then, on the Action Pane, on the **Party** tab, in the **Maintain** group, select **Assign parties**. Select the address books to add the selected party records to, and then select **OK**. All the selected party records are added to the address books that you selected.
- To remove multiple party records from an address book, on the **Global address book** list page, select the parties in the list. Then, on the Action Pane, on the **Party** tab, in the **Maintain** group, select **Remove parties**. Select the address books to remove the parties from, and then select **OK**. All the selected party records are removed from the address books that you selected.

## Can I delete historical addresses?

As of Microsoft Dynamics 365 Finance version 10.0.32, an administrator can use the following procedure to enable the advanced address maintenance feature so that historical addresses can be deleted.

1. Go to **Feature Management \> Check for updates**.
2. Search for **Advanced address maintenance**. Advanced address maintenance is disabled by default.
3. Select **Enable**.

After the **Advanced address maintenance** feature is enabled by an administrator, follow these steps to delete historical addresses.

1. Open the **Global address book** list page.
2. Select the party record to remove historical addresses for.
3. On the **Addresses** tab, select **More options \> Advanced**.
4. On the **History** tab, select one or more addresses.
5. Select **Delete** to delete the selected addresses.

If an address that you're trying to delete is linked to another record, you receive an error message.

Alternatively, you can set up a SysOperation framework batch job to delete multiple historical addresses.

1. Go to **Organization administration \> Periodic \> Delete inactivated addresses**.
2. Select **OK**.

You're notified whether the batch job succeeded or failed.

You can also delete inactive postal addresses through the Microsoft Office add-in.

1. Open the **Global address book** list page.
2. Select the party record to remove historical addresses for.
3. On the **Addresses** tab, select **More options \> Advanced**.
4. Select the Microsoft Office logo in the upper-right corner.
5. Select **Inactive Logistics Postal Address**.
6. Sign in to the add-in by using your credentials. You can use the add-in to delete only inactive addresses.

> [!NOTE]
> You can't use this procedure to update records or insert new records. For example, if you try to update the **ValidFrom** date, the record will be deleted instead.

## Can I change the party type of a record, or do I have to delete the old record and create a new one?

Occasionally, you might have to change the party type of a record from person to organization or from organization to person. For example, Nancy is a member of the sales team for Fabrikam U.K. At a trade show in London, Nancy meets six new prospects, and creates a prospect party record for each prospect. When Nancy saves the records, each record is also created in the global address book. Fabrikam has set the default party type to organization, but two of the new prospects should have a record type of person. Therefore, on returning from the trade show, Nancy must change the party type of the two prospect records. To change a party record from one party type to another, you must first create a new party record of the correct type in the global address book. You then associate the old party record with this new record. After you have made the new party association, delete the original party record that has the incorrect record type.

## How do I change the name or address of a party record?

You can update the name of a party record, and the addresses that are associated with that record, at any time.

- To update the name of a party record, open the party record, and then, on the Action Pane, select **Edit**. On the **General** FastTab, enter the new name for the party, and then save the record.
- To update an address for a party record, open the party record, and then, on the **Addresses** FastTab, select the address to update. Select **Edit**, and then, on the **Edit address** page, make the required changes to the address or address parameters.

## Can I merge two or more party records into one record?

Occasionally, you might want to merge two or more party records into a single record. This can occur if you create one or more duplicate party records, either on purpose or unintentionally. When you merge party records, you select one record to keep. The information from the other records is then merged into this record. For example, you discover that information about Fabrikam is stored in three party records: A, B, and C. You decide to keep party record A. Therefore, the information that is stored in party records B and C will be merged into party record A. There are some situations where you can't merge party records:

- You can't merge party records that are associated with the same party role, such as customer or vendor, in the same legal entity. For example, party A is associated with a customer in legal entity 123, and party B is associated with a different customer in legal entity 123. These party records can't be merged, because if they were merged, the merged party record would be associated with multiple customers in the same legal entity, and this isn't allowed. However, the records can be merged if party B is associated with a vendor in legal entity 123 or with a customer in a different legal entity.
- You can't merge internal party organization records in the same legal entity, team, or operating unit.

## Should I create a party record in the global address book or in another place, such as the Customer or Vendor page?

You can enter party records either in the global address book or on the appropriate entity page. When you add a record in one location, the same record is always added in the other location. For example, if you add a party record for a customer in the global address book, the record is also added on the **Customer** page. Likewise, if you add a party record for a customer on the **Customer** page, the record is also added in the global address book. Use the following guidelines to decide where you should enter new party records:

- **Creating a party record when you don't know the entity type** – If you must create a party record but don't know the entity type (for example, you don't know whether the entity is a customer or an opportunity), create the record in the global address book. You can select the entity type later.
- **Creating a party record when you know the entity type** – If you know the entity type for the party, you can create a record on the applicable page for that type. For example, create a record for a customer on the **Customer** page. When you create and save a record by using the appropriate entity page, the record is automatically created in the global address book.

## Can I translate address information for party records?

You can set up translations of address information, so that the information appears in your user language (system language) in your program, but in another language on documents such as sales orders. You can enter translations for country/region names, address purposes, and name sequences. For example, your system language is Danish, and you create a sales order for a customer in France. In this case, you can view the customer record in Danish in the program but display the address information in French on the printed sales order. When you set up translations, you should enter a translation for every item in the list. Any item that you don't enter a translation for will appear in the system language. For example, your system language is Danish, and you send a document to a customer in Spain. If you haven't entered Spanish (ESP) translations for the address information, that information will appear in Danish both in the program and on the printed document.

## After I import addresses, why can't I edit the records?

When you import addresses, there is a field that is named **IsLocationOwner**. This field indicates whether the party that is associated with the location (address) is the owner of the address. If the party is the owner of the address, the address can be edited when the party is used in the global address book or from the master record page (such as the customer, vendor, or worker). If the party isn't the owner of the address, the record can't be edited. 

When you import addresses, the **IsLocationOwner** field should be set to **Yes** if you want the address to be editable by using the associated party. If this field is incorrectly imported, the location owner can be updated in the global address book.

For more information about how to change the location owner of an imported address, see [Managing location owners](./global-address-book-location-owner.md).

## If the party type is Legal entity, Organization or Team, will the global address book synchronize the customer record in Customer experience?
No, the gloable address book will not synchronize the two fields in Customer experience. V3 mapping only supports Organization, so the record doesn't reach Dataverse and no errors are displayed. A separate party record of type **Organization** needs to be created.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
