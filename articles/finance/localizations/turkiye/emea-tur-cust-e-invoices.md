---
title: Export of customer electronic invoices
description: Learn how to get started with Electronic invoicing for Türkiye in Microsoft Dynamics 365 Finance, including prerequisites and an outline on configure parameters.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 10/24/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Türkiye
ms.search.validFrom: 2022-11-03
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.37
---

# Export of customer electronic invoices

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and use electronic invoices in Microsoft Dynamics 365 Finance for Türkiye.

Microsoft Dynamics 365 Finance supports the generation of e-invoice documents in the required **UBL-TR** format.

Before you begin, ensure that the following prerequisites are met:

- Your legal entity's primary address must be in Türkiye.
- To generate electronic invoice XML files in the UBL format, you must use Electronic Reporting (ER) configurations. These configurations define the necessary data models, mappings, and output formats required to structure and produce e-invoice documents in compliance with electronic invoicing standards.
- To enable the generation of electronic invoices in UBL-TR format version 1.2 and later, import the most recent versions of the following Electronic reporting (ER) format configurations. For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| Number | ER configuration name | Type | Description |
|---|---|---|---|
| 1 | Invoice model | Data model | It's a data model that standardizes the structure and components of an invoice. It serves as the foundational model for designing and generating various invoice-related electronic documents.  |
| 2 | Invoice model mapping | Model mapping | It's the process of linking a data model (like the Invoice model) to the application data sources (such as tables, views, or calculated fields) in Dynamics 365 Finance.  |
| 3 | UBL Sales invoice | Format | It's an **Electronic reporting (ER)** configuration in Dynamics 365 Finance that enables the generation of electronic invoices in a structured XML format.  |
| 4 | Peppol Sales Invoice | Format | It's an electronic invoicing format designed to comply with the Pan-European Public Procurement Online (Peppol) framework. The format is based on XML and ensures standardized, structured invoicing in EU.|
| 5 | E-Invoice (TR) | Format | It's a country/region-specific configuration designed to support electronic invoicing requirements in Türkiye. |

## Configure parameters

This section provides details about how to configure the required code lists in Microsoft Dynamics 365 Finance.

To enable the generation of electronic invoices in the UBL-TR format version 1.2 or later, import the most recent versions of the following Electronic reporting (ER) format configurations.
This includes importing Electronic reporting (ER) configurations, configuring legal entity and module parameters and master data, and defining certain mandatory code values that are published by the Turkish Revenue Administration (GİB), such as units of measure, tax type codes, and tax exemption reason codes.

The code lists can be found in [e-invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

### Reference the imported ER format configurations

1. Go to **Accounts receivable > Setup > Accounts receivable parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents in the parameter below:

    - **Sales and Free text invoice**: E-Invoice (TR)

### Configure legal entity data

This section provides information about how to configure legal entity for customer e-invoices.

To configure legal entity, follow these steps;

1. Go to **Organization administration > Organizations > Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the legal entity.
1. In the **Bank account** field, enter the reference to the legal entity bank account.

> [!NOTE]
> Make sure that a valid International Bank Account Number (IBAN) is defined for the selected bank account.

### Configure customer data

This section provides information about how to configure customer accounts for customer e-invoices.

To configure customer account, follow these steps;  

1. Go to **Accounts receivable > Customers > All customers**, and select a customer.
1. On the **Addresses** FastTab, add a valid address for the customer.
1. Specify the VAT ID of the customer. For more information, see [Set up VAT IDs of customers and vendors](../../localizations/turkiye/emea-turkiye-set-up-legal-entity.md#set-up-vat-ids-of-customers-and-vendors).
1. In the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
1. Set the **eInvoice attachment** option to **Yes** to attach an XML file to the electronic invoice, if an attachment is necessary.
1. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered as the customer's contact. All available contact persons must already be defined for the selected customer.
1. On the **Sales demographics** FastTab, in the **Employee responsible** field, select the person who is considered as the vendor's contact.

> [!NOTE]  
> After **Registration IDs** are defined for customer and vendor accounts, the **Tax exempt number** field is automatically populated.  
> If needed, you can also select the value manually.

### Set up unit of measure mappings for e-invoices

This section explains how to set up unit of measure mappings in Finance so that internal unit codes (such as *EA*, *KG*, or *M*), are correctly converted to UN/ECE unit codes (such as *C62*, *KGM*, or *MTR*).  

To configure the mappings, follow these steps:

1. Go to **Organization administration > Setup > Units > Units**.
1. Select a unit, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, in the **Code** column, enter the **internal unit ID** (for example, *EA* for "each") that represents the unit used in Dynamics 365 Finance.
1. In the **Standard code** column, select the checkbox.
1. In the **Value** section, in the **Value** field, enter the **UN/ECE unit code** (for example, *C62* for "each").  
   This value is used as the **unitCode** attribute in the `<InvoicedQuantity>` element of the generated e-invoice XML.

:::image type="content" source="../media/emea-tur-unit-code-mapping.png" alt-text="Screenshot of unit code mapping configuration page showing internal unit codes mapped to UN/ECE unit codes.":::

> [!NOTE]
> The configured unit mapping determines the `unitCode` value that appears in the `<cbc:InvoicedQuantity>` element of the generated UBL-TR e-invoice XML.  
> For example:
>
> ```xml
> <cbc:InvoicedQuantity unitCode="C62">1.00</cbc:InvoicedQuantity>
> ```
>
> In this example, the internal unit **EA** (each) defined in Dynamics 365 Finance is mapped to the international unit code **C62**, which is then written into the XML as the `unitCode` attribute.

> [!TIP]
> If no specific units of measure are defined, the default unit **EA** (each) is used in the UBL-TR e-invoice XML.

### Set up tax exempt code mappings for e-invoices

This section explains how to define and assign **Sales tax exempt codes** in Dynamics 365 Finance so that e-invoices generated in the **UBL-TR** format include the correct **TaxExemptionReasonCode** values.

#### Define sales tax exempt codes

The **Sales tax exempt codes** page provides a centralized location to create standardized exemption identifiers that represent legal reasons for tax exemption in Türkiye.

To define sales tax exempt codes:

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax exempt codes**.  
1. Select **New** to create a new record.  
1. In the **Exempt code** field, enter a unique identifier (for example, *301* or *351*).  
1. In the **Description** field, enter a meaningful description (for example, *11/1-a Mal İhracatı* or *KDV – İstisna Olmayan Diğer*).  
1. Select **Save**.  

For the official UBL-TR exemption code list, see [e-Invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

> [!NOTE]  
> These exemption codes are later used in the UBL-TR e-invoice XML file to populate the **TaxExemptionReasonCode** element.  

#### Assign tax exempt codes to sales tax codes

After defining the exemption codes, you must assign them to the relevant **sales tax codes** within **sales tax groups**.  
This assignment ensures that the correct **TaxExemptionReasonCode** values are included in the generated UBL-TR e-invoice XML.

To assign exemption codes to sales tax codes:

1. Go to **Tax > Setup > Sales tax > Sales tax groups**.  
1. Select an existing **Sales tax group** that includes one or more sales tax codes for exemption scenarios.  
1. On the **Setup** FastTab, for **each sales tax code line**, set the **Exempt** check box to **Yes**.  
   This setting ensures that transactions using this tax code don't calculate tax amounts.  
1. In the **Exempt code** field on the same line, select the relevant exemption code from the dictionary.  
   This mapping determines which **TaxExemptionReasonCode** value appears in the generated e-invoice XML.

> [!TIP]  
> The **Exempt** check box must be set per tax code line in the Sales tax group, not at the group level.  
> Only legally exempt transactions, such as export sales or diplomatic missions, should have the **Exempt** option enabled.

### Set up TaxTypeCode mappings for e-invoices

This section describes how to set up the **TaxTypeCode** lookup in the **Application specific parameters** page for the **E-Invoice (TR)** ER format to ensure compliance with the requirements in UBL-TR **XML** file.

To set up a **TaxTypeCode**, follow these steps.

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the list of ER formats, select **E-Invoice (TR)** format.
1. In the **Versions** FastTab, select the most recent **Completed** version and select **Setup** in **Application specific parameters** on the ActionPane.
1. In the **Lookups** section, select **TaxCodeLookUp**.
1. Add a new mapping line and set the **Lookup result** to the required **TaxTypeCode** from the official code list from GIB such as *0015 – Gerçek Usulde Katma Değer Vergisi*.
1. In the **Code** field, select the appropriate sales tax code to map it to the corresponding **TaxTypeCode**.
1. Repeat for all required tax types.
1. Save your changes and set the **State** to **Completed**.

:::image type="content" source="../media/emea-tur-cust-e-invoices-tax-type-code.png" alt-text="Screenshot of TaxTypeCode mapping configuration showing sales tax codes mapped to TaxTypeCode values.":::

> [!NOTE]
> The configured **TaxTypeCode** value is written into the `<TaxTypeCode>` element in the generated UBL-TR XML.  
> For example:
>
> ```xml
> <cbc:TaxTypeCode>0015</cbc:TaxTypeCode>
> ```

You can review the list of **TaxTypeCode** values currently available in the system.

To review the list, follow these steps.

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the list of ER formats, select **E-Invoice (TR)** format.
1. In the **Versions** FastTab, select **Completed** version and select **Application specific parameters** on the ActionPane.
1. Select **Designer** in ActionPane.
1. Select **Format enumerations**.

:::image type="content" source="../media/emea-tur-tax-type-code-list.png" alt-text="Screenshot of TaxTypeCode list showing available tax type code values in the system.":::

This can help ensure that the values you configure in the **Application specific parameters** are aligned with the enumeration definitions in the ER format.

## Export of electronic invoices for customers

This section describes how to generate, view, and access electronic invoices for customers in Finance.  
It provides guidance on how to create UBL-TR compliant XML files from posted invoices, access and verify the generated documents to automatically distribute them through Electronic Reporting (ER) destinations.

### Generate e-invoices

When an invoice is posted, you can generate an electronic invoice from any invoice journal. Select the invoice, and then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Send** \> **Original**.

:::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of sending an e-invoice showing the Invoice tab with Document group and Send Original option.":::

### View e-invoices

If ER destinations are defined for electronic invoice formats, the output files that are generated are sent to a related file destination that's configured for the ER destination.
For more information about how to configure destinations for generated electronic documents, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

If no Electronic reporting (ER) destinations are defined for electronic invoice formats, output files for electronic invoices are generated on the Electronic reporting jobs page.

To view these files;

1. Go to **Organization administration > Electronic reporting > Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

    :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of Show files button in Electronic reporting jobs page.":::

1. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** \> **Message details** to view more details about the error message.

:::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of Message details showing error information for electronic invoice generation.":::

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices are automatically sent to the defined destinations immediately after the invoices are posted.

When you post the invoices, you must turn on the Print invoice parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
