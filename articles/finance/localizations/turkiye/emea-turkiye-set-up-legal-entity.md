---
title: Set up a legal entity for Türkiye
description: Learn how to set up a legal entity and configure VAT ID registration prerequisites in Microsoft Dynamics 365 Finance, including creating registration types, assigning them to registration categories, and selecting tax offices for legal entities, customers, and vendors.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/23/2025
ms.reviewer: johnmichalak
ms.search.region: Türkiye
ms.search.validFrom: 2016-06-30
ms.search.form: TaxRegistrationType, TaxRegistrationTypeCreate, TaxRegistrationLegislationTypes, RegNumIssuerTable
---

# Set up a legal entity for Türkiye

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity for a company that's located in Türkiye and is using the features for Türkiye that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company, and it contains the tax and legal attributes that are required for the rest of the configuration for Türkiye.

Before you begin, open the **Feature management** workspace, and verify that the **Globalization expansion - Türkiye** feature is enabled. 
If it is not enabled, enable it. After you're sure that the feature is enabled, complete the following procedures.

## Create a legal entity

To create a legal entity, follow this step.

- Go to **Organization administration > Organizations > Legal entities**, create a legal entity, and set the country of the primary address to Türkiye. Some functionality is enabled only for Türkiye. Examples include specific reports or electronic invoices.

## Configure VAT IDs of the legal entity, customers, and vendors

In Türkiye, the Value-added tax (VAT) ID is a 10-digit numeric code assigned by the Revenue Administration (GIB) to individuals and legal entities for use in tax-related transactions. While Turkish citizens may use their Turkish Citizenship Number which is 11-digit for personal tax matters, obtaining a VAT number is mandatory for legal entities (such as companies, associations, and foundations) as well as for individuals engaged in commercial activities.

You can set up the VAT ID of the legal entity and its vendors and customers using the [Registration IDs](../../localizations/europe/emea-registration-ids.md) functionality.

### Configure a registration type for VAT ID

Before you set up the VAT ID of the legal entity and its vendors and customers, you need to configure the registration type for VAT ID by following the steps described in [Set up VAT ID](../../localizations/europe/eur-00015-vat-id.md).

> [!NOTE] 
> When creating a new Registration type, the **Country/Region** value must be set to **TUR** for Türkiye.

You need to configure two distinct registration types for the following party types:

- Organizations
- Persons

To do that, you need to assign distinct names to the registration types, for example:

- "TURVAT_Organization" for organizations.
- "TURVAT_Person" for persons.

In the **Restricted to** field:

- You must select **Organization** for the "TURVAT_Organization" registration type.
- You must select **Person** for the "TURVAT_Person" registration type.

In the **Format** field;

- For TURVAT_Organization, enter 10-digit "##########".
- For TURVAT_Person, enter 11-digit "###########".

Complete setting up the registration type and registration category for VAT ID by following the steps described in [Set up VAT ID](../../localizations/europe/eur-00015-vat-id.md).

### Configure tax offices (Issuing agencies)

In Türkiye, every legal entity, customer, and vendor must be linked to a **tax office** for identification and regulatory reporting.  
In Finance, this information is managed through the **Issuing agencies** setup. By defining tax office names and codes, you ensure that **Registration IDs** are correctly associated with the appropriate tax authority. This setup is essential for generating compliant e-invoice (UBL-TR) documents and other statutory reports.

To define tax offices, follow these steps:  

1. Go to **Organization administration > Global address book > Issuing agencies**.  
1. On the **Issuing agencies** page, select **New**.  
1. In the **Issuing agency** field, enter the numeric tax office code (for example, *34272*).  
1. In the **Description** field, enter the name of the tax office (for example, *Kadıköy vergi dairesi*).  
1. Repeat these steps for all relevant tax offices.
1. Select **Save**.

> [!NOTE]  
> The tax office information entered here is used in e-invoice (UBL-TR) XML files and other legal reports. Incorrect configuration may result in validation errors from GİB (Turkish Revenue Administration).

### Set up VAT ID of legal entity

This section provides information about how to set up a VAT ID of a legal entity in Türkiye.

To create a VAT ID for the legal entity, follow these steps: 

1. Go to **Organization administration > Organizations > Legal entities**.
1. In the list find and select the legal entity you want to work with.
1. Select **Registration IDs** in ActionPane.

	1. Select **New** and enter values in the **Name or description** fields.
	1. In the **Country/region** field, enter or select a value.
	1. In the **Primary for country/region** field, select **Yes** and then select **Save**.	
	1. Select **Add** on the **Overview** Tab in **Registration ID** FastTab.
	1. In the **Registration type** field, enter or select a value that is created for Türkiye.
	1. In the **Registration number** field, enter a value. For example, specify a VAT ID. The ID must have the same format as the registration type.
	1. In the **Issuing agency** field, select the appropriate tax office.
    1. Select a tax office in the **Issuing agency** field in **Registration ID** FastTab. 
	1. On the **General** tab, in the **Effective** field, enter a date and then select **Save** if it is needed.
	1. Select **Save** and close the page.

### Set up VAT IDs of customers and vendors

This section explains how to add VAT registration IDs to a customer or vendor account. 

To create a VAT ID for a customer or a vendor, follow these steps:

1. Go to **Accounts payable > Vendors > All vendors** or **Accounts receivable > Customers > All customers**.
1. In the list find and select the vendor or the customer record you want to work with.
1. Select **Registration IDs** in **Registration** section.

	1. Select **New** and enter values in the **Name or description** fields.
	1. In the **Country/region** field, enter or select a value.
	1. In the **Primary for country/region** field, select **Yes** and then select **Save**.	
	1. Select **Add** on the **Overview** Tab in **Registration ID** FastTab.
	1. In the **Registration type** field, enter or select a value that is created for Türkiye.
	1. In the **Registration number** field, enter a value. For example, specify a VAT ID. The ID must have the same format as the registration type.
    1. Select a tax office in the **Issuing agency** field in **Registration ID** FastTab. 
	1. On the **General** tab, in the **Effective** field, enter a date and then select **Save** if it is needed.
	1. Select **Save** and close the page.

> [!NOTE] 
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you use.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
