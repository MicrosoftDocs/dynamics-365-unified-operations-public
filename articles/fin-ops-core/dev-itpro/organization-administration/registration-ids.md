---
title: Registration IDs
description: The Registration IDs functionality provides a unified framework for managing registration IDs across all countries and regions.
author: 
ms.author: 
ms.topic: overview
ms.date: 08/03/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2026-02-28
ms.search.form: DirPartyTable, DirPartyTableRoles
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Registration IDs

[!include [banner](../../../finance/includes/banner.md)]

This article provides information about setting up and using registration IDs.

Many countries/regions have different regulations and requirements for recording registration numbers or IDs. 
This article provides an overview of the required settings and processing of supported registration types for parties in different European countries/regions. 
All countries/regions have their requirements for supporting various country/region-specific functionalities related to registration numbers provided by different state offices. 
Examples of registration IDs include VAT identification numbers, company registration numbers, tax identification numbers, national identification numbers for individuals, employer registration numbers, and customs or trade registration numbers.

This functionality provides a unified framework for managing registration IDs across all countries and regions, while still accommodating country‑ or region‑specific regulatory requirements, 
including those applicable in certain European countries/regions.

Within this unified framework, registration IDs are defined and processed through a consistent setup and data flow. 
**Registration types** are first created to represent different kinds of identification numbers mapped to specific **Country/region** and assigned to **Registration category** that define validation and reporting behavior. 
Only after this configuration is completed, registration IDs can be entered and maintained for legal entities, customers, vendors and other counterparties.
The following sections describe this overall flow for setting up and processing registration IDs.

## Registration type creation

Before you can enter a registration ID, you must set up **Registration types** for the different types of registration numbers that each party is subject to. 

Go to **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration types**  page to create and manage registration types for legal entities, vendors, customers, workers in different countries/regions.

|Field                 |Description      |
|------------------------------|----------------------------|                                                                           
| Name                | The name of the registration type. |                                                                           
| Description         | The description of the registration type. |
| Country/region      | The unique identifier of the country/region.|
| Tax authority       | The tax authority that is associated with the registration type.|
| Restricted to       | The kind of restriction that applies to the tax registration type: None, Person, Organization.|
| Format              | The validation format for the registration type.|
| Can be updated      | Defines if the registration number for the registration type can be updated after it's entered.|
| Unique              | Defines if the registration number for the registration type is unique. |
| Primary for country/region | If a party is associated with one or more addresses in a particular country/region, and the registration ID is valid for all these addresses, you must designate one address as primary for the country/region. You can only register one ID as primary. Defines if the registration number can be entered only for primary for country/region address. |

## Assign a registration category to a registration type

A **Registration category** is a country/region registration identifier that a country/region approves for use in tax, customs, and other purposes. 
This category defines validation rules for a particular registration ID, including check digits, and inclusion registration ID in different reports. 

Use the page **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration categories** to assign the registration type of a particular country/region to a supported registration category.

| Field            | Description|
|-----------------------|----------------|
| Registration type     | The registration type in a particular country/region.|
| Restricted to         | The kind of restriction that applies to the tax registration type: None, Person, Organization.|
| Registration category | The unique registration identifier approved for use in the country/region. The full list of supported categories is shown later in this article. |

## Set up invoice party applicability rules for registration category

Starting with Dynamics 365 Finance version 10.0.48, in registration categories, you can set up invoice party applicability rules to determine which registration IDs apply to each invoice party role based on country/region requirements, 
organizational level, and address purpose. These rules ensure consistent selection, validation, and storage of registration IDs across all invoice types, supporting regulatory compliance and accurate invoicing.

For more information, see [Invoice party applicability rules for registration category](invoice-party-applicability-rules.md).

## Enter registration IDs for Global address book records

The global address book (GAB) contains consolidated address information for customers, vendors, contacts, business relations, and legal entities. 
The party records that are stored in the global address book can contain one or more address records. 
These addresses are used for different purposes, such as invoice, billing or delivery. For more information, see [Global address book overview](../../../fin-ops-core/dev-itpro/organization-administration/overview-global-address-book.md). 

You can set up registration IDs for address information for legal entities, customers, vendors and workers.
Find the party (legal entity, vendor, customer, worker) record for which you want to enter the registration ID, and then select **Registration IDs** on forms related to party, legal entity, vendor, customer, worker 
to open the **Manage addresses** page. On the **Registration ID** tab, select **Add**, and enter the following information about the registration ID.

|Field                |Description                                                |
|---------------------|-----------------------------------------------------------|
| Registration type   | The registration type in the selected country/region.     |
| Registration number | The party registration ID.                                |
| Description         | The description of the registration number.               |
| Section             | The additional information about the registration number. |
| Issuing agency      | The authority that issued the registration number.        |
| Issued date         | The issued date for the registration number.              |
| Effective           | The effective date for the registration number.           |
| Expiration          | The expiration date for the registration number.          |

> [!NOTE]
> The tax exempt number of a legal entity, vendor, or customer can be selected from registration IDs related to the VAT ID and entered for the party.

## Search for records by registration ID

You can search for party records by registration ID on forms related to party, legal entity, vendor, customer, and worker. 

Select **Registration ID search** to open the **Registration ID search criteria** page. 
Enter your search criteria and select **Find**. The system displays the selected records from the global address book and the associated types of party record.

## Supported registration categories

The following table lists the supported registration categories and their descriptions.

| Finance registration category | Description |
|------------------------------|-------------|
| VAT ID | A value-added tax registration number issued by a tax authority and used for domestic VAT reporting and tax compliance. |
| EU VAT ID | A VAT registration number used for intra-EU transactions and reporting, including cross-border trade within the European Union. |
| Enterprise ID (COID) | An official registration number that uniquely identifies a legal entity in a national business or commercial register. |
| Branch ID | A registration number that identifies a specific branch or subdivision of a legal entity registered with a national authority. |
| Customs customer ID | A registration number used to identify a party in customs and import/export procedures with customs authorities. |
| Spisová značka  | A court or commercial register reference used to identify a legal entity, including its registration number, issuing authority, and register section (Czech Republic). |
| SIRET | An establishment-level registration number that uniquely identifies a specific physical location or establishment of a legal entity (France). |
| EAN | A standardized business or location identifier used for commercial, logistical, or electronic data exchange purposes (Denmark). |
| INN | A tax identification number assigned to individuals or organizations for tax reporting and compliance purposes (Russian Federation). |
| RRC | A registration reason code used together with a tax identification number to identify the tax registration context of an organization (Russian Federation). |
| OKDP | A classification code used to identify the type of economic activity of an organization for statistical and regulatory purposes (Russian Federation). |
| OKPO | A statistical registration number used to uniquely identify organizations and individual entrepreneurs in official registers (Russian Federation). |
| RCOAD | A registration or classification code used for administrative or statistical identification purposes (Russian Federation). |
| OGRN | A primary state registration number that uniquely identifies a legal entity in the state register (Russian Federation). |
| SNILS | A personal insurance number used to identify individuals for social security and pension purposes (Russian Federation). |
| CIFTS | A registration identifier used for tax or fiscal reporting in specific regulatory contexts (Russian Federation). |
| Passport | A government-issued identity document used to identify an individual. |
| Official identification document | An officially recognized identity document issued by a government authority to identify an individual. |
| Residence certificate | A document that confirms an individual’s legal residence status in a country or region. |
| Other identification document | Any additional government-issued document used to identify an individual when no specific category applies. |
| Not censused | Indicates that no official registration or identification number is available for the party. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
