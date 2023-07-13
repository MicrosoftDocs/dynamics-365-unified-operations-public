---
title: Registration IDs
description: This article provides information about setting up and using registration IDs.
author: kfend
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: kfend
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 264824
ms.search.form: DirPartTaxRegistrationSearch, LogisticsPostalAddress, TaxRegistrationLegislationTypes, TaxRegistrationType
---

# Registration IDs

[!include [banner](../includes/banner.md)]

This article provides information about setting up and using registration IDs.

Many countries and regions have different regulations and requirements for recording registration numbers or IDs. This article provides an overview of the required settings and processing of supported registration types for parties in different European countries/regions. All countries/regions have their requirements for supporting various country/region-specific functionalities related to registration numbers provided by different state offices. Examples of registration numbers include, social security number (SSN), tax identification number (TIN), and European VAT identification (EU VAT ID). This feature provides unified framework for all countries in all regions taking into account country/region-specific requirements of some European countries. The following sections describe the overall flow of information that is used for setting up and processing registration IDs.

## Registration type creation
Before you can enter registration ID, you must set up registration types for the different types of registration numbers that each party is subject to. Go to **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration types**  page to create and manage registration types for vendors, customers, workers, and legal entities in different countries/regions.

|Field                 |Description      |
|------------------------------|----------------------------|                                                                           
| Name                | The name of the registration type. |                                                                           
| Description         | The description of the registration type. |
| Country/region      | The unique identifier of the country/region.|
| Tax authority       | The tax authority that is associated with the registration type.|
| Restricted to       | The kind of restriction that applies to the tax registration type: None, Person, Organization.|
| Format              | The validation format for the registration type.|
| Can be updated      | Defines if the registration number for the registration type can be updated after it is entered.|
| Unique              | Defines if the registration number for the registration type is unique. |
| Primary for country | If a party is associated with one or more addresses in particular country and the registration ID is valid for all these addresses, you must designate one address as primary for the country/region. You can only register one ID as primary. Defines if the registration number can be entered only for primary for country/region address. |

## Assign a registration type to a registration category
Registration category is country/region registration identifier approved for using in particular country/region for tax, customs and other purposes. This category defines validation rules of particular registration ID (including check digits etc.) and inclusion registration ID in different reports. Use the page **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration categories** to assign registration type of particular country to supported registration category.

| Field            | Description|
|-----------------------|----------------|
| Registration type     | The registration type in particular country/region.|
| Restricted to         | The kind of restriction applies to the tax registration type: None, Person, Organization.|
| Registration category | The unique registration identifier approved for using in the country/region. The full list of supported categories is shown later in this article. |

## Enter registration IDs for Global address book records

The global address book (GAB) contains consolidated address information for customers, vendors, contacts, business relations, and legal entities. For more information see, [Global address book overview](../../fin-ops-core/fin-ops/organization-administration/overview-global-address-book.md). The party records that are stored in the global address book can contain one or more address records. These addresses are used for different purposes, such as billing or delivery. You can set up registration IDs for address information for customers, vendors, workers, and legal entities. Find the party (legal entity, vendor, customer, worker) record for which you want to enter the register ID, and then click **Registration IDs** on forms related to party, legal entity, vendor, customer, worker to open the **Manage addresses** page. On the **Tax registration** tab, click **Add**, and enter following information about the registration ID.


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
> The tax exempt number of legal entity, vendor, customer can be selected from registration IDs related to the VAT ID and entered for the party.

## Search for records by registration ID
Search for party records based on a registration ID is available on forms related to party, legal entity, vendor, customer, and worker. Click **Registration ID search** to open the **Registration ID search criteria** page. Specify search criteria and click **Find**. The system will display the selected records from the global address book and the associated types of party record.

## Supported registration categories
The following table lists the supported registration types. If you're familiar with the Microsoft Dynamics AX 2012 fields for registration IDs, this table also maps those fields to the Dynamics 365 Finance registration categories.

| Finance Registration category         |Country/Region  | Dynamics AX 2012 term/field|
|---------------------------------------------------------------|---------------------|---------------------------------|
| VAT ID                                                        | All countries/regions of the European Union (EU)|  Tax exempt number (Legislative type TAX ID in AX 2012 R3)|
| Enterprise ID (COID)                                          | Belgium Czech Republic Estonia Hungary Latvia Lithuania Poland Switzerland | Enterprise number (EnterpriseNumber) Registration number (RegNum\_W) Registration number (RegNum\_W) Registration number (RegNum\_W) Registration number (RegNum\_W) Enterprise code (EnterpriseCode) Registration number (RegNum\_W) UID (Legislative type UID in AX 2012 R3) |
| Branch ID                                                     | Belgium            | Branch number (BranchNumber)|
| Spisová značka (Registration number, Issuing agency, Section) | Czech Republic     | Inset number (CommercialRegisterInsetNumber) Kept at commercial register (CommercialRegister) Section of commercial register (CommercialRegisterSection)|
| Customs customer ID                                           | Finland | Customs customer number (CustomsCustomerNumber\_FI)|
| INN                                                           | Russian Federation| INN (Legislative type INN in AX 2012 R3)|
| RRC                                                           | Russian Federation| RRC (Legislative type RRC in AX 2012 R3)|
| OKDP                                                          | Russian Federation| OKDP (Legislative type OKDP in AX 2012 R3)|
| OKPO                                                          | Russian Federation| OKPO (Legislative type OKPO in AX 2012 R3)|
| RCOAD                                                         | Russian Federation| RCOAD (Legislative type RCOAD in AX 2012 R3)|
| OGRN                                                          | Russian Federation| OGRN (Legislative type OGRN in AX 2012 R3) |
| SNILS                                                         | Russian Federation| SNILS (Legislative type SNILS in AX 2012 R3)|
| CIFTS                                                         | Russian Federation| CIFTS (Legislative type CIFTS in AX 2012 R3)|
| Passport                                                      | Spain             | Passport|
| Official identification document                              | Spain             | Official identification document|
| Residence certificate                                         | Spain             | Residence certificate|
| Other identification document                                 | Spain             | Other identification document|
| Not censused                                                  | Spain             | Not available in AX 2012 R3|
| SIRET                                                         | France            | Not available in AX 2012 R3|


For more information about registration IDs processing, including required prerequisites, see the following task recordings for VAT ID in Lifecycle Services (LCS):

-   Set up VAT ID
-   VAT ID registration of vendor
-   Party search using VAT ID






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
