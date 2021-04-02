---
title: Party and global address book
description: This topic describes the Party and global address book functionality of dual-write.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 02/22/2021
ms.topic: article
ms.service: dynamics-ax-applications
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2021-02-22
---

# Party and global address book

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

*Party* and *global address book* are concepts in Finance and Operations applications. A party can be an organization or a person. It's convenient to globally store and manage properties of a party, such as the name, language, contacts, and addresses. Then, when a property value is changed in one place, the change is reflected in all places where the party is involved.

## Party

A party is a person or an organization that is involved in a business. When the party concept is used, a person or an organization can play more than one role in a business (for example, worker, customer, vendor, or contact). The role is based on the context and purpose. Here are some examples of roles from two fictitious companies, Contoso and Fabrikam:

+ **Worker** – An employee. An example is an employee of Contoso.
+ **Vendor** – A supplier organization, or a sole proprietor who supplies goods or services to a business. For example, if Fabrikam sells supplies to Contoso, Fabrikam is a vendor of Contoso.
+ **Contact** – A person to contact. For example, if Contoso buys supplies from Fabrikam, employees at Contoso will reach out to the contact at Fabrikam.
+ **Customer** – A person or company that buys things from a company. For example, if Contoso buys supplies from Fabrikam, Contoso is a customer of Fabrikam.

The party model is often used to represent medium to complex relationships between organizations and people, especially when a party plays more than one role. Here are some common examples:

+ A party can be both a customer and a vendor. For example, in North America, Fabrikam sells electric wires to Contoso and buys assembled speakers from Contoso. In Europe, Fabrikam sells parts to Contoso, but it doesn't buy anything from Contoso.
+ A party can be both an employee and a customer. For example, an employee of Contoso buys electronics from Contoso for personal use.
+ There can be a many-to-many (N:N) relationship between a person and an organization. For example, Fabrikam provides service specialists and employs a placement coordinator. The placement coordinator matches service specialists to work requests from several of Fabrikam's customers. Contoso is one of Fabrikam's customers. When Contoso requires a service specialist, it contacts the placement coordinator, who then facilitates the request. Because the placement coordinator handles requests for all customers, an N:N relationship is involved.

The following illustration shows the data model for party.

![Data model for party](media/party-gab-image1.png)

> [!TIP]
> When you're trying to create a new account record, use the **Party** field to search for the record by name. In this way, if you find the record, you just have to select it. The system then automatically fills in all the data from the party. You don't have to manually set all the required fields. This behavior can be found on the out-of-box **Account**, **Contact**, and **Vendor** pages.

Dual-write doesn't support all party roles of Finance and Operations apps. For a complete list of party roles, see [Global address book overview](../../../fin-ops/organization-administration/overview-global-address-book.md).

### Global address book

The global address book is a directory of postal and electronic addresses of the organizations and individuals that participate in a business.

The global address book stores and handles as many postal addresses and electronic addresses as required. For example, Fabrikam has gas stations in 50 locations. Each location has a different postal address, email address, and phone number. All business purchases are billed to the main gas station but shipped directly to the specific gas station that requested the purchase. The global address book stores the main gas station as the billing address for Fabrikam and stores each gas station as a shipping address. The addresses can be stored one time and then retrieved as they are required for quotations and orders.

Depending on the business context, a person or an organization might play more than one role, and the same postal address and electronic address might be used for all the roles. In this case, a change of address in one role should appear in all the other roles. The global address book stores and handles addresses globally.

The following illustration shows the data model for the global address book.

![Data model for the global address book](media/party-gab-image2.png)

## Contact

In customer engagement apps, a contact is a person. However, the **Contact** table has been overloaded to represent a person, a portal user, a business-to-consumer (B2C) customer, or a vendor. The representation is implicit, and you can't tell the difference unless you examine related transactions. The **Contact** table has been limited to a one-to-one (1:1) relationship with the **Account** table. As part of the party and global address book model, dual-write introduces explicit properties for classification and allows for N:N relationships between a contact that is a person and an organization (**Account** or **Vendor** entity).

There are two types of **Contact** rows:

+ **Striped contact** – A **Contact** row where the **Company** field has a mandatory value.
+ **Unstriped contact** – A **Contact** row where the **Company** field is blank.

The **Contact** table can store the following types of rows.

| Row type | Description |
|----------|-------------|
| A person who is a customer (for example, a sellable contact or a B2C customer) | A striped contact record where the **Company** field isn't blank and the **Is Customer** field is set to **Yes**. |
| A person who is a vendor (for example, a sole proprietor such as a vendor) | A striped contact record where the **Company** field isn't blank and the **Is Vendor** field is set to **Yes**. |
| A person who is both a customer and a vendor | A striped contact record where the **Company** field isn't blank, the **Is Customer** field is set to **Yes**, and the **Is Vendor** field is set to **Yes**. A person can be both a producer for one product and a consumer for another product. Both Finance and Operations apps and dual-write support this relationship. |
| A person who is a contact person for an organization, but isn't a customer or a vendor | An unstriped contact record where the **Company** field is blank, the **Is Customer** field is set to **No**, and the **Is Vendor** field is set to **No**. |

## Contact for Party

**Contact for Party** stores and handles N:N relationships between **Account** rows and **Contact** rows. It can filter out the striped **Contact** rows from unstriped rows and associate only the unstriped **Contact** rows with **Account** or **Vendor** rows.

For example, Natasha Jones and Miguel Reyes are veterinarians who provide care for farms in their areas. Natasha serves the Seattle area, and Miguel serves the Kent area. In the customer engagement app, the farms are represented as customers, and the veterinarians are represented as contact persons. A single **Contact** record for Natasha is associated with all the farms that Natasha works with. Likewise, a single **Contact** record for Miguel is associated with all the farms that Miguel works with.

These relationships are stored in the **Contact for Party** table. You can find the information on the out-of-box **Account**, **Contact**, and **Vendor** pages:

+ On the **Account** page, you can use the **Associated Contacts** tab to associate one or more contacts with the **Account** row. In this way, you assign contact persons for an organization. You can then select one contact as the primary contact for the account. If you use the **Quick create** page, you can only select a contact person. The behavior is the same when you're using the **Vendor** page and the record type is **Organization**.
+ On the **Contact** page, when the row is a customer, a vendor, or both (a striped contact), you can use the **Associated Contacts** tab to associate one or more contacts. In this way, you assign contact persons for a B2C customer or vendor. You can then select one contact as the primary contact. If you use the **Quick create** page, you can only select a contact person.
+ On the **Contact** page, when the row is a contact person (an unstriped contact), you can use the **Associated Organizations** tab to associate one or more customers or vendors. In this way, you assign customers or vendors to the underlying contact person. The customer or vendor can be an organization, a person, or both. You can select a value in only one of the four fields at a time:

    + If you select a value in the **Party ID** field, the underlying contact is assigned to all the roles of the selected party.
    + If you select a value in the **Associated Contact** field, you're selecting the striped contact of the **Person** type.
    + If you select a value in the **Associated Account** or **Associated Vendor** field, you're selecting an organization.

    ![Associated Organizations tab on the Contact page](media/party-gab-image3.png)

    Regardless of your selection, the association is created at the party level, it applies to all the roles of the party, and it's stored in the **Contact for Party** entity.

> [!NOTE]
> The display name for the **Contact for Party** table in customer engagement apps is **Contact for Customer/Vendor**.

When you open a **Contact** row where both the **Is Customer** field and the **Is Vendor** are set to **No**, the **Associated Organizations** tab is shown. Use this tab to associate one or more customer or vendor organizations with the contact.

When you open a **Contact** row where either the **Is Customer** field or the **Is Vendor** field is set to **Yes**, the **Associated Contacts** tab is shown. Use this tab to associate one or more contacts.

## Postal addresses

A new **Addresses** tab has been introduced on the **Account**, **Contact**, and **Vendor** pages. This tab supports multiple postal addresses by using a grid, as shown in the following illustration.

![Grid for postal addresses](media/party-gab-image4.png)

The grid includes the following columns:

+ **Postal Address Roles** – The purpose of the postal address.
+ **Is Primary** – A value that indicates whether the address is the primary address.
+ **Address Number** – The address order.

You can use the **New Address** button above the grid to create as many postal addresses as you want.

The **Address 1** and **Address 2** fields on the **Summary** tab of the **Account** page correspond to the **Delivery** and **Invoice** addresses, respectively.

![Summary tab for postal addresses](media/party-gab-image5.png)

The **Address 1**, **Address 2**, and **Address 3** fields on the **Summary** tab of the **Contact** page correspond to the **Business**, **Delivery**, and **Invoice** addresses, respectively.

## Electronic addresses

A new **Electronic Addresses** tab has been introduced on the **Account**, **Contact**, and **Vendor** pages. This tab supports multiple electronic addresses by using a grid, as shown in the following illustration.

![Grid for electronic addresses](media/party-gab-image6.png)

The grid includes the following columns:

+ **Type** – The type of electronic address.
+ **Is Primary** A value that indicates whether the address is the primary address.
+ **Purpose** – The purpose of the electronic address.

You can use the **New Electronic Address** button above the grid to create as many addresses as you want.

Electronic addresses are available only in this grid. In future releases, all postal address and electronic address fields will be removed from other tabs (for example, the **Summary** and **Details** tabs).

## Setup

If you're an existing dual-write customer, the following setup instructions are required. Otherwise, you can skip this section.

1. Stop the following maps, because they are no longer required. Instead, run the Contacts V2 (msdyn\_contactforparties) map.

    + CDS Contacts V2 and Contacts (refers to customer contacts)
    + CDS Contacts V2 and Contacts (refers to vendor contacts)

2. The following entity mappings are updated for party functionality. Therefore, the latest version must be applied to these mappings.

    | Map | Update to this version | Changes |
    |-----|------------------------|---------|
    | Customers V3 (accounts) | 1.0.0.5 | The **PartyNumber** field and other party-related fields were removed. The other fields include fields for the name, personal details, postal address, and electronic contact address. |
    | Customer V3 (contacts) | 1.0.0.5 | The **PartyNumber** field and other party-related fields were removed. The other fields include fields for the name, personal details, postal address, and electronic contact address. |
    | Vendors V2 (msdyn\_vendors) | 1.0.0.6 | The **PartyNumber** field and other party-related fields were removed. The other fields include fields for the name, personal details, postal address, and electronic contact address. |
    | CDS Sales quotation headers (quotes) | 1.0.0.6 | The contact person was replaced by a **ContactforParty** reference. |
    | Sales invoice headers V2 (invoices) | 1.0.0.4 | The contact person was replaced by a **ContactforParty** reference. |
    | CDS Sales order headers (salesorders) | 1.0.0.5 | The contact person was replaced by a **ContactforParty** reference. |
    | Contacts V2 (msdyn\_contactforparties) | 1.0.0.2 | This map is new. If you have a previous version of the party solution, be sure to update this map to the latest version. |
    | CDS Party postal address locations (msdyn\_partypostaladdresses) | 1.0.0.1 | This new map was added as part of the previous party preview release. |
    | CDS postal address history V2 (msdyn\_postaladdresses) | | This new map was added as part of the previous party preview release. |
    | CDS postal address locations (msdyn\_postaladdresscollections) | | This new map was added as part of the previous party preview release. |
    | Party Contacts V3 (msdyn\_partyelectronicaddresses) | | This new map was added as part of this release. |

## Templates

A collection of table maps work together for party and global address book interaction, as shown in the following table.

| Finance and Operations app | Customer engagement app | Description |
|----------------------------|-------------------------|-------------|
| [Contact person titles](mapping-reference.md#223) | msdyn\_salescontactpersontitles |
| [Customers V3](mapping-reference.md#101) | accounts |
| [Customers V3](mapping-reference.md#116) | contacts |
| [CDS Parties](mapping-reference.md#220) | msdyn\_parties |
| [CDS Party postal address locations](mapping-reference.md#233) | msdyn\_partypostaladdresses |
| [CDS postal address history V2](mapping-reference.md#235) | msdyn\_postaladdresses |
| [CDS postal address locations](mapping-reference.md#234) | msdyn\_postaladdresscollections |
| [CDS sales quotation header](mapping-reference.md#215) | quotes |
| [CDS sales order headers](mapping-reference.md#217) | salesorders |
| [Complimentary closings](mapping-reference.md#222) | msdyn\_complimentaryclosings |
| [Contacts V2](mapping-reference.md#221) | msdyn\_contactforparties |
| [Decision making roles](mapping-reference.md#224) | msdyn\_decisionmakingroles |
| [Employment job functions](mapping-reference.md#225) | msdyn\_employmentjobfunctions |
| [Loyalty levels](mapping-reference.md#226) | msdyn\_loyaltylevels |
| [Party contacts V3](mapping-reference.md#236) | msdyn\_partyelectronicaddresses |
| [Personal character types](mapping-reference.md#227) | msdyn\_personalcharactertypes |
| [Sales invoice headers V2](mapping-reference.md#118) | invoices |
| [Salutations](mapping-reference.md#228) | msdyn\_salutations |
| [Vendors V2](mapping-reference.md#202) | msdyn\_vendors |

For more information, see [Dual-write mapping reference](mapping-reference.md).
