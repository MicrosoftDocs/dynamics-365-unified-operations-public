---
title: Customer definitions entity
description: Definition of the Customer definitions data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Customer definitions entity

The **Customers definitions** entity supports creating and updating customers; and includes the most common fields for a typical customer.

## When to use this entity

Use the **Customer definitions** entity as the default entity for importing customers as long as it contains the necessary fields, or the missing fields can be added from the existing data sources, and when performance is a high priority.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | **Customer definitions** |
| **OData public entity** | CustomerBase |
| **OData public collection** | CustomersBase |
| **Related menu items** | Accounts receivable / Customers / All customers |
| **Related entities** | Customers V3, Customer details V2 |
| **Performance pattern** | Multiple threads supported – Recommendation is to set **Import threshold record count** to 1000 and set **Import task count** to 8. For more information, see [Parallel imports](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job#parallel-imports). |
| **Application Object Tree (AOT) name** | CustCustomerBaseEntity |

## Fields

| Field | Description |
|--|--|
| CUSTOMERACCOUNT | Specifies the primary key. The autogenerate mapping option can be used to use the next default value. This field is required. |
| ADDRESSCITY | Specifies a foreign key to the **Cities** entity. |
| ADDRESSCOUNTRYREGIONID | Specifies a foreign key to the **Country/regions** entity. This field is required when the ADDRESSDESCRIPTION is included. |
| ADDRESSCOUNTY | Specifies a foreign key to the **Counties** entity. |
| ADDRESSSTATE | Specifies a foreign key to the **States** entity. |
| ADDRESSZIPCODE | Specifies a foreign key to the **Postal codes V3** entity. |
| CUSTOMERGROUPID | Specifies a foreign key to the **Customer groups** entity. This field is required. |
| DEFAULTDIMENSIONDISPLAYVALUE | This field isn't supported. Use the **Customer details V2** entity instead. |
| INVOICEACCOUNT | This field isn't supported. Use the **Customer details V2** entity instead. |
| NAME | Specifies the customer's name if **PARTYTYPE** is **Organization.** It's ignored if **PARTYTYPE** is **Person**. This field is required, even when the **PARTYTYPE** is **Person**. |
| PARTYTYPE | Specifies the type of the customer. The allowed values are **Organization** and **Person**. If this field isn't specified, the default value is **Organization**. |
| PAYMENTMETHOD | Specifies a foreign key to the **Customer payment method** entity. |
| PAYMENTTERMS | Specifies a foreign key to the **Terms of payment** entity. |
| PERSONFIRSTNAME</br>PERSONMIDDLENAME</br>PERSONLASTNAME | These fields specify the customer's name if **PARTYTYPE** is **Person**. One of these fields is required if **PARTYTYPE** is **Person**. |
| SALECURRENCYCODE | Specifies the default currency. Specifies a foreign key to the **Currencies** entity. This field is required. |
| SALESTAXGROUP | Specifies a foreign key to the **Sales tax groups** entity. |

## Issues and considerations

The **Customers definitions** entity, when combined with the **Customer details V2** entity, supports most of the same functionality as the **Customers V3** entity. The highest performance can usually be achieved by using a combination of the **Customer definitions** and **Customer details V2** entities. In most cases, using one of those other entities, or even using both of them, one after the other, will outperform using the **Customers V3** entity.

The **Customers definitions** entity is compatible with the **Customers V3** entity for most fields, except that ORGANIZATIONNAME is renamed to NAME for the **Customers definitions** entity.

The **Customer definitions** entity shouldn't be customized to add more data sources.

## Example: Customer that is an organization

The following fields are required to create a customer that is an organization.

- *CUSTOMERACCOUNT*

- *PARTYTYPE*

- *NAME*

- *SALESCURRENCYCODE*

- *CUSTOMERGROUPID*

## Example: Customer that is a person

The following fields are required to create a customer that is a person.

- *CUSTOMERACCOUNT*

- *PARTYTYPE*

- *PERSONFIRSTNAME*

- *PERSONMIDDLENAME*

- *PERSONLASTNAME*

- *SALESCURRENCYCODE*

- *CUSTOMERGROUPID*

- *NAME*

> [!NOTE]
> Only one of the person name fields is required.

## Related resources

[Import customers in Dynamics 365 projects](/dynamics365/guidance/resources/import-customers)  
