---
title: Export customer electronic invoices
description: Learn how to get started with Electronic invoicing for Türkiye in Microsoft Dynamics 365 Finance, including prerequisites and an outline on configure parameters.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: how-to
ms.date: 08/12/2026
ms.reviewer: johnmichalak
ms.search.region: Türkiye
ms.search.validFrom: 2022-11-03
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.37
---

# Export customer electronic invoices

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and use electronic invoices in Microsoft Dynamics 365 Finance for Türkiye.

Microsoft Dynamics 365 Finance supports the generation of e-invoice documents in the required **UBL-TR** format.

Before you begin, ensure you meet the following prerequisites:

- Your legal entity's primary address is in Türkiye.
- To generate electronic invoice XML files in the UBL format, use Electronic Reporting (ER) configurations. These configurations define the necessary data models, mappings, and output formats required to structure and produce e-invoice documents in compliance with electronic invoicing standards.
- To enable the generation of electronic invoices in UBL-TR format version 1.2 and later, import the most recent versions of the Electronic reporting (ER) format configurations listed in the following table. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| Number | ER configuration name | Type | Description |
| --- | --- | --- | --- |
| 1 | Invoice model | Data model | It's a data model that standardizes the structure and components of an invoice. It serves as the foundational model for designing and generating various invoice-related electronic documents. |
| 2 | Invoice model mapping | Model mapping | It's the process of linking a data model (like the Invoice model) to the application data sources (such as tables, views, or calculated fields) in Dynamics 365 Finance. |
| 3 | UBL Sales invoice | Format | It's an **Electronic reporting (ER)** configuration in Dynamics 365 Finance that enables the generation of electronic invoices in a structured XML format. |
| 4 | Peppol Sales Invoice | Format | It's an electronic invoicing format designed to comply with the Pan-European Public Procurement Online (Peppol) framework. The format is based on XML and ensures standardized, structured invoicing in the EU. |
| 5 | E-Invoice (TR) | Format | It's a country/region-specific configuration designed to support electronic invoicing requirements in Türkiye. |

## Configure parameters

This section provides details about how to configure the required code lists in Microsoft Dynamics 365 Finance.

To enable the generation of electronic invoices in the UBL-TR format version 1.2 or later, import the most recent versions of the following Electronic reporting (ER) format configurations.
This process includes importing Electronic reporting (ER) configurations, configuring legal entity and module parameters and master data, and defining certain mandatory code values that the Turkish Revenue Administration (GİB) publishes, such as units of measure, tax type codes, and tax exemption reason codes.

You can find the code lists in [e-invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents in the **Sales and Free text invoice: E-Invoice (TR)** parameter.

### Configure legal entity data

This section explains how to configure a legal entity for customer e-invoices.

To configure a legal entity, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the legal entity.
1. In the **Bank account** field, enter the reference for the legal entity bank account.

   > [!NOTE]
   > Ensure that you define a valid International Bank Account Number (IBAN) for the selected bank account.

### Configure customer account data

This section explains how to configure customer accounts for customer e-invoices.

To configure customer account data, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
1. On the **Addresses** FastTab, add a valid address for the customer.
1. Specify the VAT ID of the customer. Learn more in [Set up VAT IDs of customers and vendors](../../localizations/turkiye/emea-turkiye-set-up-legal-entity.md#set-up-vat-ids-of-customers-and-vendors).
1. In the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices.
1. Set the **eInvoice attachment** option to **Yes** to attach an XML file to the electronic invoice, if an attachment is necessary.
1. In the **Invoice type** field, select the type of electronic invoice to generate for this customer:

   - **e-Invoice** – The `ProfileID` element in the generated XML is determined by the **Invoice scenario** field or the **Requires commercial approval** option.
   - **e-Archive** – The `ProfileID` element in the generated XML is automatically set to `EARSIVFATURA`, regardless of the **Invoice scenario** field setting.

   > [!NOTE]
   > The **Invoice type** field is required when you set the **eInvoice** option to **Yes**. Select **e-Archive** for customers who aren't registered in the GİB e-Invoice system.

1. In the **Invoice scenario** field, select the invoice scenario that determines the `ProfileID` value in the generated UBL-TR XML file. The following scenarios are available:

   | Invoice scenario | ProfileID value in XML | Description |
   | --- | --- | --- |
   | Basic invoice | `TEMELFATURA` | Standard transactions to recipients who aren't subject to the commercial invoice process. |
   | Commercial invoice | `TICARIFATURA` | Used when the recipient is registered as a GİB e-Invoice user and the commercial invoice process applies. |
   | Export invoice | `IHRACAT` | Used for export transactions where customs procedures are involved. |
   | Passenger sales | `YOLCUBERABERFATURA` | Used for passenger accompanied goods transactions. |
   | Pharmaceutical / Medical Device Invoice | `ILAC_TIBBICIHAZ` | Used for pharmaceutical and medical device sales. |
   | Produce market invoice profile | `HKS` | Used for produce market (hal) transactions registered in the Produce Market Registration System. |
   | Steel tracking invoice profile | `IDIS` | Used for transactions within the Steel Tracking System (İnşaat Demiri İzleme Sistemi). |
   | Public sector invoice | `KAMU` | Used for invoices issued to public sector entities. |
   | Special invoice | `OZELFATURA` | Used for special invoice scenarios as defined by GİB. |
   | Investment incentive invoice | `YATIRIMTESVIK` | Used for transactions covered by an investment incentive certificate. |
   | Energy / EV invoice | `ENERJI` | Used for energy and electric vehicle charging service transactions. |
   | Standard code invoice | `STDKODFATURA` | Used for standard code invoice transactions. |

1. Set the **Requires commercial approval** option to **Yes** if the customer is required to issue commercial (TİCARİFATURA) invoices.
When you set this option to **Yes**, Finance always assigns the `TICARIFATURA` ProfileID in the generated XML, regardless of the **Invoice scenario** field setting.

   > [!IMPORTANT]
   > The **Requires commercial approval** option overrides the **Invoice scenario** setting. Use this option for customers who aren't registered as e-Invoice users and are subject to the commercial invoice approval process.

1. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered as the customer's contact. You must already define all available contact persons for the selected customer.
1. On the **Sales demographics** FastTab, in the **Employee responsible** field, select the person who is considered as the vendor's contact.

### Set up unit of measure mappings for e-invoices

This section explains how to set up unit of measure mappings in Finance so that internal unit codes (such as *EA*, *KG*, or *M*) correctly convert to UN/ECE unit codes (such as *C62*, *KGM*, or *MTR*).  

To configure the mappings, follow these steps:

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, enter the **internal unit ID** (for example, *EA* for "each") in the **Code** column. This ID represents the unit used in Finance.
1. Select the checkbox in the **Standard code** column.
1. In the **Value** section, enter the **UN/ECE unit code** (for example, *C62* for "each") in the **Value** field.  
   This value is used as the **unitCode** attribute in the `<InvoicedQuantity>` element of the generated e-invoice XML.

:::image type="content" source="../media/emea-turkiye-unit-code-mapping.png" alt-text="Screenshot of the units of measure mapping configuration.":::

The configured unit mapping determines the `unitCode` value that appears in the `<cbc:InvoicedQuantity>` element of the generated UBL-TR e-invoice XML. For example:

```xml
<cbc:InvoicedQuantity unitCode="C62">1.00</cbc:InvoicedQuantity>
```

In this example, the internal unit **EA** (each) defined in Finance is mapped to the international unit code **C62**, which is then written into the XML as the `unitCode` attribute.

   > [!TIP]
   > If you don't define specific units of measure, the default unit **EA** (each) is used in the UBL-TR e-invoice XML.

### Set up tax-exempt code mappings for e-invoices

This section explains how to define and assign **Sales tax exempt codes** in Finance so e-invoices generated in the **UBL-TR** format include the correct **TaxExemptionReasonCode** values.

#### Define sales tax exempt codes

The **Sales tax exempt codes** page provides a centralized location to create standardized exemption identifiers that represent legal reasons for tax exemption in Türkiye.

To define sales tax exempt codes, follow these steps:

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax exempt codes**.  
1. Select **New** to create a new record.  
1. In the **Exempt code** field, enter a unique identifier (for example, *301* or *351*).  
1. In the **Description** field, enter a meaningful description (for example, *11/1-a Mal İhracatı* or *KDV – İstisna Olmayan Diğer*).  
1. Select **Save**.  

For the official UBL-TR exemption code list, see [e-Invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

   > [!NOTE]  
   > Use these exemption codes in the UBL-TR e-invoice XML file to populate the **TaxExemptionReasonCode** element.  

#### Assign tax-exempt codes to sales tax codes

After defining the exemption codes, assign them to the relevant **sales tax codes** within **sales tax groups**.  
This assignment ensures that the correct **TaxExemptionReasonCode** values are included in the generated UBL-TR e-invoice XML.

To assign exemption codes to sales tax codes, follow these steps:

1. Go to **Tax** > **Setup** > **Sales tax** > **Sales tax groups**.  
1. Select an existing **Sales tax group** that includes one or more sales tax codes for exemption scenarios.  
1. On the **Setup** FastTab, for **each sales tax code line**, set the **Exempt** check box to **Yes**. This setting ensures that transactions using this tax code don't calculate tax amounts.  
1. In the **Exempt code** field on the same line, select the relevant exemption code from the dictionary. This mapping determines which **TaxExemptionReasonCode** value appears in the generated e-invoice XML.

   > [!TIP]  
   > Set the **Exempt** check box per tax code line in the Sales tax group, not at the group level.  
   > Only legally exempt transactions, such as export sales or diplomatic missions, should have the **Exempt** option enabled.

### Set up TaxTypeCode mappings for e-invoices

This section describes how to set up the **TaxTypeCode** lookup in the **Application specific parameters** page for the **E-Invoice (TR)** ER format to ensure compliance with the requirements in UBL-TR **XML** file.

To set up a **TaxTypeCode**, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the list of ER formats, select **E-Invoice (TR)** format.
1. In the **Versions** FastTab, select the most recent **Completed** version and select **Setup** in **Application specific parameters** on the ActionPane.
1. In the **Lookups** section, select **TaxCodeLookUp**.
1. Add a new mapping line and set the **Lookup result** to the required **TaxTypeCode** from the official code list from GIB such as *0015 – Gerçek Usulde Katma Değer Vergisi*.
1. In the **Code** field, select the appropriate sales tax code to map it to the corresponding **TaxTypeCode**.
1. Repeat for all required tax types.
1. Save your changes and set the **State** to **Completed**.

:::image type="content" source="../media/emea-turkiye-customer-electronic-invoices-tax-type-code.png" alt-text="Screenshot of the tax type code configuration page.":::

The configured **TaxTypeCode** value is written into the `<TaxTypeCode>` element in the generated UBL-TR XML. For example:

```xml
<cbc:TaxTypeCode>0015</cbc:TaxTypeCode>
```

You can review the list of **TaxTypeCode** values currently available in the system.

To review the list, follow these steps:

1. Go to **Organization administration ** > **Electronic reporting** > **Configurations**.
1. In the list of ER formats, select **E-Invoice (TR)** format.
1. In the **Versions** FastTab, select **Completed** version and select **Application specific parameters** on the ActionPane.
1. Select **Designer** in ActionPane.
1. Select **Format enumerations**.

:::image type="content" source="../media/emea-turkiye-tax-type-code-list.png" alt-text="Screenshot of the tax type code list in the application specific parameters.":::

This information can help ensure that the values you configure in the **Application specific parameters** align with the enumeration definitions in the ER format.

## Export of electronic invoices for customers

This section describes how to generate, view, and access electronic invoices for customers in Finance. It also provides guidance on how to create UBL-TR compliant XML files from posted invoices, and how to access and verify the generated documents to automatically distribute them through Electronic Reporting (ER) destinations.

### Generate e-invoices for sales order

When you post a sales order invoice, select an **Invoice profile** on the **Posting invoice** page. The selected profile gives you transaction-level control over the `ProfileID` value that appears in the UBL-TR XML. If you select an **Invoice profile**, it overrides the customer's default electronic invoice configuration for that transaction. Otherwise, Finance determines the `ProfileID` by using the customer's electronic invoice settings.

To post a sales order invoice and select the invoice profile, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select a sales order. On the Action Pane, select **Invoice** > **Generate** > **Invoice**.
1. On the **Overview** FastTab, select the appropriate value in the **Invoice profile** field.
1. Select **OK**.

For example, if you select **Commercial invoice**, the generated XML contains the following `ProfileID` element:

```xml
<cbc:ProfileID>TICARIFATURA</cbc:ProfileID>
```

### Generate e-invoices for free text invoices

You can generate electronic invoices for free text invoices. When you create a free text invoice, select an **Invoice profile** on the **Free text invoice header**. The selected profile provides transaction-level control over the `ProfileID` value that is generated in the UBL-TR XML.

   > [!NOTE]
   > The **Invoice profile** field is optional. If you don't select a value, Finance determines the `ProfileID` by using the customer's electronic invoice configuration. For customers whose **Invoice type** is **e-Archive**, the generated XML always uses `EARSIVFATURA`.

To create and post a free text invoice, follow these steps:

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Create or select a free text invoice.
1. In the **Free text invoice header**, select the appropriate value in the **Invoice profile** field.

   :::image type="content" source="../media/emea-turkiye-free-text-invoice-profile.png" alt-text="Screenshot of the invoice profile field on a free text invoice header.":::

1. Complete the invoice, and then select **Post**.

The available **Invoice profile** values are the same as the values described in the **Configure customer account data** section.

   > [!IMPORTANT]
   > If you select an **Invoice profile** on the free text invoice, it overrides the customer's default electronic invoice configuration for that transaction. If you don't select a profile, Finance determines the `ProfileID` by using the customer's electronic invoice settings. For the official ProfileID code list, see [e-Invoice Legislation and Technical Architecture](https://ebelge.gib.gov.tr/efaturamevzuat.html).

### Generate e-invoices from invoice journal

After you post a sales order invoice, you can generate an electronic invoice from the invoice journal.

To generate an electronic invoice from the invoice journal, follow these steps:

1. Select the invoice.
1. On the Action Pane, select the **Invoice** tab.
1. In the **Document** group, select **Send** > **Original**.

   :::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of the Send Original option in the invoice journal.":::

### View e-invoices

If you define Electronic Reporting (ER) destinations for electronic invoice formats, the system sends the generated output files to a related file destination configured for the ER destination.  
Learn how to configure destinations for generated electronic documents in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).  

If you don't define ER destinations for electronic invoice formats, the system generates output files for electronic invoices on the **Electronic reporting jobs** page.  

To view these e-invoice files, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

   :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of the Show files button on the Electronic reporting jobs page.":::

1. Select **Open** to download the file that contains the electronic invoice.

If the system fails to generate the electronic invoices because of errors, select **Show log** > **Message details** to view more details about the error message.  

   :::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of the Message details pane showing error log information.":::

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, the system automatically sends output XML files that contain electronic invoices to the defined destinations immediately after the invoices are posted.  

When you post the invoices, turn on the **Print invoice** parameter.  

Learn more about ER destinations in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
