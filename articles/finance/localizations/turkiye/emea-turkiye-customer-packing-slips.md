---
title: Export of customer electronic packing slips
description: Learn how to configure and export customer electronic packing slips for Türkiye in Microsoft Dynamics 365 Finance by using UBL-TR format and Electronic reporting (ER) configurations.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 02/17/2026
ms.reviewer: johnmichalak
ms.search.region: Türkiye
ms.search.validFrom: 2026-01-19
ms.dyn365.ops.version: AX 10.0.45
---

# Export of customer electronic packing slips

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and use **electronic packing slips (e-packing slips)** in Microsoft Dynamics 365 Finance for Türkiye.  
Finance supports the generation of electronic packing slip XML file in the required **UBL-TR DespatchAdvice** format.

Before you begin, make sure you meet the following prerequisites:

- Your legal entity's primary address is in Türkiye.
- You import the Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services or Dataverse.
- You configure ER destinations if you want XML files to be automatically sent to file locations, email, SharePoint, or other channels.

The following ER configurations are required to generate UBL-TR packing slip documents.

| Number | ER configuration name | Type | Description |
|--------|------------------------|------|-------------|
| 1 | Invoice model | Data model | The shared data model that standardizes the structure of sales documents. It acts as the base model for generating packing slip XML output. |
| 2 | Packing slip model mapping | Model mapping | Links the Invoice data model to application data sources related to packing slips. |
| 3 | UBL Packing slip (TR) | Format | Generates Turkish electronic packing slip XML documents in the UBL-TR DespatchAdvice format. This is the final output format used for e-packing slips. |

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

## Configure parameters

This section describes how to configure the mandatory setup for generating UBL-TR electronic packing slips.

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the **UBL Packing slip (TR)** in **Packing slip parameter**.

### Configure legal entity data

To configure the legal entity for e-packing slip generation, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the legal entity.

   > [!NOTE]  
   > Unlike electronic invoices, electronic packing slips don't require bank information or IBAN to be configured.

### Configure customer account data

This section explains how to configure customer accounts for customer e-packing slips.

To configure customer account data, follow these steps:  

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
1. On the **Addresses** FastTab, add a valid address for the customer.
1. Specify the VAT ID of the customer. For more information, see [Set up VAT IDs of customers and vendors](../../localizations/turkiye/emea-turkiye-set-up-legal-entity.md#set-up-vat-ids-of-customers-and-vendors).
1. In the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
1. Set the **eInvoice attachment** option to **Yes** to attach an XML file to the electronic packing slip, if an attachment is necessary.

   > [!NOTE]  
   > - After you define **Registration IDs** for customer and vendor accounts, the **Tax exempt number** field is automatically populated.  
   > If needed, you can also select the value manually.
   > - The delivery address and delivery terms are essential because these values are mapped into the UBL-TR DespatchAdvice XML structure. 

### Set up unit of measure mappings for e-packing slips

This section explains how to set up unit of measure mappings in Finance so that internal unit codes (such as *EA*, *KG*, or *M*) are correctly converted to UN/ECE unit codes (such as *C62*, *KGM*, or *MTR*).  

To configure the mappings, follow these steps:

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit, and then select **External codes**.
1. On **External codes**, in the **Overview** section, in the **Code** column, enter the internal unit ID (for example, *EA* for "each") that represents the unit used in Finance.
1. Select the checkbox in the **Standard code** column.
1. In the **Value** section, enter the UN/ECE unit code (for example, *C62* for "each") in the **Value** field. This value is used as the **unitCode** attribute in the `<InvoicedQuantity>` element of the generated e-invoice XML.

   > [!NOTE]
   > The configured unit mapping determines the `unitCode` value that appears in the `<cbc:DeliveredQuantity>` element of the generated UBL-TR e-packing slip XML.  
   > For example:
   >
   > ```xml
   > <cbc:DeliveredQuantity unitCode="C62">1.00</cbc:DeliveredQuantity>
   > ```
   >
   > In this example, the internal unit **EA** (each) defined in Finance is mapped to the international unit code **C62**, which is then written into the XML as the `unitCode` attribute.
   
   > [!TIP]
   > If you don't define specific units of measure, the default unit **EA** (each) is used in the UBL-TR e-packing slip XML.

   :::image type="content" source="../media/emea-turkiye-unit-code-mapping.png" alt-text="Screenshot of the Units of measure configuration page showing external code mappings.":::

## Configure transportation details for electronic packing slips

For electronic packing slips in Türkiye, you must specify transportation-related information on the sales order.  
This information populates the vehicle, driver, and carrier sections of the UBL-TR DespatchAdvice XML.

Maintain transportation details at the sales order level and complete them before posting the packing slip.

### Define transportation details on a sales order

To define transportation information for a sales order, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select a sales order.
1. On the Action Pane, select **Pick and pack**.
1. Select **Transportation details**.

Use the **Transportation details** page to enter carrier, vehicle, and driver information that's required for electronic packing slip generation.

   :::image type="content" source="../media/emea-turkiye-transportation-details.png" alt-text="Screenshot of the Transportation details page showing carrier, vehicle, and driver fields.":::

### Carrier information

Carrier information identifies the party that transports the goods.

The following table describes the carrier-related fields on the **Transportation details** page.

| Field | Description |
|------|-------------|
| Carrier type | Specifies the type of carrier that performs the transportation. |
| Carrier | Identifies the transport company. |

   > [!NOTE]  
   > Carrier information is mandatory for e-Packing slip documents in Türkiye and maps to the **CarrierParty** section of the UBL-TR DespatchAdvice XML.

### Vehicle and trailer information

Vehicle information identifies the transport vehicle used for delivery.

The following table describes vehicle-related fields.

| Field | Description |
|------|-------------|
| Registration number | Specifies vehicle plate number. |
| Trailer registration number | Specifies trailer plate number. |

This information maps to the **TransportMeans** elements in the UBL-TR DespatchAdvice XML.

   > [!NOTE]  
   > If no trailer is used, only the vehicle registration number is required.

### Driver information

Driver information identifies the person responsible for transporting the goods.

The following table describes driver-related fields.

| Field | Description |
|------|-------------|
| Driver | Reference to a predefined driver record. |
| Driver name | Full name of the driver. |

Turkish regulations require including the driver name in the electronic packing slip XML.

### Effect on electronic packing slip generation

Transportation details come from the sales order when you post the packing slip. You pass the values to the Electronic Reporting (ER) format during XML generation. 

If required transportation information is missing or incomplete, the generated UBL-TR DespatchAdvice document might fail validation during submission.

## Generate electronic packing slips

You can generate electronic packing slips after posting a packing slip for a sales order.

To generate an electronic packing slip XML file, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select a sales order that has a posted packing slip.
1. Select the **Pick and pack** tab.
1. On the Action Pane, select **Packing slip journal**.
1. Select a packing slip journal.
1. Select **Preview/Print**.
1. Select **Original preview**.

If you configure ER destinations, the XML automatically goes to the defined destination. If you don't configure a destination, the **Electronic reporting jobs** page stores the XML output.

   :::image type="content" source="../media/emea-turkiye-generate-packing-slip.png" alt-text="Screenshot of the Packing slip journal page showing the Preview/Print menu options.":::

## View electronic packing slips

If you define ER destinations for electronic packing slip formats, the system sends the generated output files to a related file destination that you configure for the ER destination.
Learn more about configuring destinations for generated electronic documents in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

If you don't define Electronic reporting (ER) destinations for electronic packing slip formats, the system generates output files for electronic packing slips on the Electronic reporting jobs page.

To view these e-packing slip files, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.
1. Select **Open** to download the file that contains the electronic packing slip.

   :::image type="content" source="../media/emea-turkiye-view-packing-slip.png" alt-text="Screenshot of the Electronic reporting jobs page showing the Show files option.":::

If generation of the electronic packing slip fails because of errors, you can view more details about the error message by selecting **Show log** \> **Message details**.

   :::image type="content" source="../media/emea-turkiye-message-details.png" alt-text="Screenshot of the Message details dialog showing error information.":::

## Send electronic packing slips to ER destinations

You can set up ER destinations for electronic packing slip formats. When you set up these destinations, the system automatically sends output XML files that contain electronic packing slips to the defined destinations immediately after the packing slips are posted.

When you post the packing slips, turn on the **Print packing slip** parameter.

Learn more in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
