---
title: Customers V3 entity
description: Definition of the Customers V3 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Customers V3 entity

The **Customers V3** entity supports creating and updating customers; and includes all the fields for a typical customer. It also includes about 80 fields that the other customer entities support.

## When to use this entity

Use the **Customers V3** entity when the scenario includes approximately 80 fields that aren't supported by the **Customer definitions** and **Customer details V2** entities. Do not use the **Customers V3** entity in scenarios where high performance is required, including where the volume or frequency is high.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Customers V3 |
| **OData public entity** | CustomerV3 |
| **OData public collection** | CustomersV3 |
| **Related menu items** | Accounts receivable / Customers / All customers |
| **Related entities** | Customer definitions, Customer details V2 |
| **Performance pattern** | Single thread only |
| **Application Object Tree (AOT) name** | CustCustomerV3Entity |

## Fields

| Field | Description |
|--|--|
| CUSTOMERACCOUNT | Specifies the primary key. |
| ADDRESSCITY | Specifies a foreign key to the **Cities** entity. |
| ADDRESSCOUNTRYREGIONID | Specifies a foreign key to the **Country/regions** entity. This field is required when the ADDRESSDESCRIPTION is included. |
| ADDRESSCOUNTY | Specifies a foreign key to the **Counties** entity. |
| ADDRESSSTATE | Specifies a foreign key to the **States** entity. |
| ADDRESSZIPCODE | Specifies a foreign key to the **Postal codes V3** entity. |
| CUSTOMERGROUPID | Specifies a foreign key to the **Customer groups** entity. This field is required. |
| DEFAULTDIMENSIONDISPLAYVALUE | Updating this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item**.** |
| INVOICEACCOUNT | Specifies a foreign key that is a self-relation to another customer. The customer referenced by **INVOICEACCOUNT** has to exist before this field can be updated. |
| NAME | Specifies the customer's name if **PARTYTYPE** is **Organization.** It's ignored if **PARTYTYPE** is **Person**. This field is required. |
| PARTYTYPE | Specifies the type of the customer. The allowed values are **Organization** and **Person**. If this field isn't specified, the default value is **Organization**. |
| PAYMENTMETHOD | Specifies a foreign key to the **Customer payment method** entity. |
| PAYMENTTERMS | Specifies a foreign key to the **Terms of payment** entity. |
| PERSONFIRSTNAME</br>PERSONMIDDLENAME</br>PERSONLASTNAME | These fields specify the customer's name if **PARTYTYPE** is **Person**. One of these fields is required if **PARTYTYPE** is **Person**. |
| SALECURRENCYCODE | Specifies the default currency. Specifies a foreign key to the **Currencies** entity. This field is required. |
| SALESTAXGROUP | Specifies a foreign key to the **Sales tax groups** entity. |

## Issues and considerations

The **Customers V3** entity's ability to support all scenarios related to creating and updating customers reduces its performance.

## Example: Customer that is an organization

The following fields are required to create a customer that is an organization.

- CUSTOMERACCOUNT

- PARTYTYPE

- CUSTOMERGROUPID

- SALESCURRENCYCODE

- ORGANIZATIONNAME

## Example: Customer that is a person

The following fields are required to create a customer that is a person.

- CUSTOMERACCOUNT

- PARTYTYPE

- PERSONFIRSTNAME

- PERSONMIDDLENAME

- PERSONLASTNAME

- CUSTOMERGROUPID

- SALESCURRENCYCODE

> [!NOTE]
> Only one of the person name fields is required.

## Related resources

[Import customers in Dynamics 365 projects](/dynamics365/guidance/resources/import-customers)  
