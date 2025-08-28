---
title: Export of customer electronic invoices
description: Learn how to get started with Electronic invoicing for Türkiye in Microsoft Dynamics 365 Finance, including prerequisites and an outline on configure parameters.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 08/18/2023
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

## Prerequisites

Before you begin, ensure that the following prerequisites are met:

- Your legal entity’s primary address must be in Türkiye.
- To generate electronic invoice XML files in the UBL format, you must use Electronic Reporting (ER) configurations. These configurations define the necessary data models, mappings, and output formats required to structure and produce e-invoice documents in compliance with electronic invoicing standards.
- To enable the generation of electronic invoices in **UBL-TR** format version 1.2 and later, import the specified or later versions of the following Electronic reporting (ER) format configurations. For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| Number | ER configuration name | Type | Description |
|---|---|---|---|
| 1 | Invoice model | Data model | It is a data model that standardizes the structure and components of an invoice. It serves as the foundational model for designing and generating various invoice-related electronic documents.  |
| 2 | Invoice model mapping | Model mapping | It is the process of linking a data model (like the Invoice model) to the application data sources (such as tables, views, or calculated fields) in Dynamics 365 Finance.  |
| 3 | UBL Sales invoice | Format | It is an **Electronic reporting (ER)** configuration in Dynamics 365 Finance that enables the generation of electronic invoices in a structured XML format.  |
| 4 | Peppol Sales Invoice | Format | It is an electronic invoicing format designed to comply with the Pan-European Public Procurement Online (Peppol) framework. The format is based on XML and ensures standardized, structured invoicing in EU.|
| 5 | E-Invoice (TR) | Format | It is a country/region-specific configuration designed to support electronic invoicing requirements in Türkiye. |

## Configure parameters

This sections provides details about how to configure the required code lists in Microsoft Dynamics 365 Finance.

To enable the generation of electronic invoices in the UBL-TR format version 1.2 or later, import the most recent versions of the following Electronic reporting (ER) format configurations.
This includes importing Electronic reporting (ER) configurations, configuring legal entity and module parameters and master data, and defining certain mandatory code values that are published by the Turkish Revenue Administration (GİB), such as units of measure, tax type codes, and tax exemption reason codes. 

The code lists can be found in [e-invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html). 

### Reference the imported ER format configurations

1. Go to **Accounts receivable > Setup > Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents in the parameter below:

    - **Sales and Free text invoice**: E-Invoice (TR)

### Configure legal entity data

This section provides information about how to configure legal entity for customer e-invoices. 

to configure legal entity, follow these steps;

1. Go to **Organization administration > Organizations > Legal entities**, and select a legal entity.
2. On the **Addresses** FastTab, add a valid primary address for the legal entity.
3. In the **Bank account** field, enter the reference to the legal entity bank account.

> [!NOTE]
> Make sure that a valid International Bank Account Number (IBAN) is defined for the selected bank account.

### Configure customer data

This section provides information about how to configure customer accounts for customer e-invoices. 

To configure customer account, follow these steps;  

1. Go to **Accounts receivable > Customers > All customers**, and select a customer.
2. On the **Addresses** FastTab, add a valid address for the customer.
3. Specify the VAT ID of the customer. For more information, see [Set up a legal entity for Türkiye](../../localizations/turkiye/emea-turkiye-set-up-legal-entity.md#set-up-vat-ids-of-customers-and-vendors).
4. In the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
5. Set the **eInvoice attachment** option to **Yes** to attach a XML file to the electronic invoice, if an attachment is necessary.
6. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered the customer's contact. All available contact persons must already be defined for the selected customer.
7. On the **Sales demographics** FastTab, in the **Employee responsible** field, select the person who is considered the vendor's contact.

> [!NOTE]  
> After **Registration IDs** are defined for customer and vendor accounts, the **Tax exempt number** field is automatically populated.  
> If needed, you can also select the value manually.

### Configure _InvoicedQuantity_ mapping for units

This section provides information about how to configure **InvoicedQuantity** mapping for units in Finance.

To configure **InvoicedQuantity** mapping for units, follow these steps; 

1. Go to **Organization administration > Setup > Units > Units**.
2. Select a unit, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** column, enter a code that corresponds to the selected unit ID.
4. In the **Standard code** column, select the checkbox.
5. In the **Value** section, in the **Value** field, enter the external code to use as the [Units](https://unece.org/sites/default/files/2021-06/rec20_Rev17e-2021.xlsx) of measure code for international trade.

![InvoiceTypeCode mapping](../media/emea-tur-invoice-quantity-mapping.png)

> [!NOTE]
> For scenarios where no specific units of measure are assumed, the default value **EA** (each) is used.

### Configure _TaxExemptionReasonCode_ mapping for sales tax codes

This section describes how to configure a **Sales tax group** in Dynamics 365 Finance for exemption scenarios in Türkiye to ensure that e-invoices generated in UBL-TR format contain the correct **TaxExemptionReasonCode** value. 

**TaxExemptionReasonCode** explains why a transaction is exempt from tax (for example, exports or special exemptions). 
Before you can assign a **TaxExemptionReasonCode** to sales tax groups, you must first define **Sales tax exempt codes**.  
The **Sales tax exempt codes** page in Finance provides a central place to define standardized exemption identifiers that represent the legal reasons for tax exemption. 

In the context of Türkiye’s e-invoice processes, these codes are critical because they are directly mapped to the **TaxExemptionReasonCode** element in the UBL-TR XML file. 
This ensures that e-invoices contain the correct legal basis for the exemption, as required by regulations.  

To define sales tax exempt codes:

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax exempt codes**.  
2. Select **New** to create a new record.  
3. In the **Exempt code** field, enter a unique identifier (for example, *301* or *351*).  
4. In the **Description** field, enter a meaningful description (for example, *11/1-a Mal İhracatı* or *KDV - İstisna Olmayan Diğer*).  
5. Select **Save**. 

The **TaxExemptionReasonCode** is used in the UBL-TR format of e-invoice to provide standardized tax information. 

To assign a **TaxExemptionReasonCode** to a sales tax code through the Sales tax group, follow these steps:

1. Go to **Tax > Setup > Sales tax > Sales tax groups**.
2. Select an existing sales tax group which includes sales tax code for the exemption scenario.
3. On the **Setup** FastTab, set the **Exempt** option to **Yes**. This setting ensures that all transactions linked to this sales tax group will not calculate tax amounts.
4. In the **Exempt code** field, select an exemption code for the exemption. To access the exemption code list in UBL-TR, see [e-invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

> [!NOTE]
> In Türkiye, the **Exempt** option should only be enabled for transactions that are legally tax exempt, such as export sales, sales to diplomatic missions, or sales under special VAT exemption clauses.

### Configure _TaxTypeCode_ mapping in Application specific parameters

This section describes how to set up the **TaxTypeCode** lookup in the **Application specific parameters** page for the **E-Invoice (TR)** ER format to ensure compliance with the Turkish Revenue Administration (GİB) requirements in UBL-TR **XML** file.

To create a **TaxTypeCode**, follow these steps; 

1. Go to **Organization administration > Electronic reporting > Configurations**.
2. In the list of ER formats, select **E-Invoice (TR)** format.
3. In the **Versions** FastTab, select **Completed** version and select **Application specific parameters** on the ActionPane.
4. In the **Lookups** section, select **TaxCodeLookUp**.
5. Add a new mapping line and set the **Lookup result** to the required **TaxTypeCode** from the official code list from GIB such as _0015 – Gerçek Usulde Katma Değer Vergisi_.
6. In the **Code** field, select the appropriate sales tax code to map it to the corresponding **TaxTypeCode**, ensuring compliance with XML requirements.
7. Repeat for all required tax types.
8. Save your changes and set the **State** to **Completed**.

![Mapping TaxTypeCode](../media/emea-tur-cust-e-invoices-tax-type-code.png)

You can review the list of **TaxTypeCode** values currently available in the system. 

To review the list; 

1. Go to **Organization administration > Electronic reporting > Configurations**.
2. In the list of ER formats, select **E-Invoice (TR)** format.
3. In the **Versions** FastTab, select **Completed** version and select **Application specific parameters** on the ActionPane.
4. Select **Designer** in ActionPane.
5. Select **Format enumerations**.

![TaxTypeCode list](../media/emea-tur-tax-type-code-list.png)

This can help ensure that the values you configure in the **Application specific parameters** are aligned with the enumeration definitions in the ER format.

## Export of electronic invoices for customers

### Generate e-invoices

When an invoice is posted, you can generate an electronic invoice from any invoice journal. Select the invoice, and then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Send** \> **Original**.

![Sending an e-invoice.](../media/emea-nor-ger-einvoice.jpg)

### View e-invoices

If ER destinations are defined for electronic invoice formats, the output files that are generated are sent to a related file destination that is configured for the ER destination. 
For more information about how to configure destinations for generated electronic documents, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

If no Electronic reporting (ER) destinations are defined for electronic invoice formats, output files for electronic invoices are generated on the Electronic reporting jobs page. 

To view these files;

1. Go to **Organization administration > Electronic reporting > Electronic reporting jobs**.
2. Select a job, and then select **Show files**.

    ![Show files button.](../media/emea-nor-ger-einvoice-open.jpg)

3. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** \> **Message details** to view more details about the error message.

![Message details.](../media/emea-nor-ger-einvoice-log.jpg)

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices are automatically sent to the defined destinations immediately after the invoices are posted. 
When you post the invoices, you must turn on the Print invoice parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
