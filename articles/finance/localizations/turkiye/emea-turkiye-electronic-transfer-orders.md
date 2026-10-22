---
title: Export of electronic waybills for transfer order shipments
description: Learn how to generate electronic waybills (e-Waybills) in the UBL-TR DespatchAdvice format for transfer order shipments for the Republic of Türkiye in Microsoft Dynamics 365 Finance.
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: how-to
ms.date: 10/21/2026 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2026-10-12 
ms.search.form: InventTransferOrders, InventTransferParmTable, InventTransferJour 
ms.custom: 
  - bap-template
---

# Export of electronic waybills for transfer order shipments

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to generate electronic waybills (e-Waybills) for transfer order shipments for the Republic of Türkiye in Microsoft Dynamics 365 Finance.

When you move goods between warehouses, Finance supports generating e-Waybill XML files in the required **UBL-TR DespatchAdvice** format. This process is similar to the process for customer electronic packing slips. To learn more, see [Export of customer electronic packing slips](emea-turkiye-customer-packing-slips.md).

> [!NOTE]
> The procedures in this article apply regardless of whether the warehouses on the transfer order use warehouse management processes (WMS).

## Prerequisites

Before you begin, ensure that you meet the following prerequisites:

- The primary address of your legal entity is in Türkiye.
- You import the Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services or Microsoft Dataverse. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You configure ER destinations if you want XML files to be automatically sent to file locations, email, SharePoint, or other channels.
- You set up a serial prefix for transfer order shipments. Learn more in [Use continuous serial numbering of packing slips and invoices](emea-tur-serial-numbering.md#shipment-for-a-transfer-order).
- You set up unit of measure mappings. Learn more in [Set up unit of measure mappings for e-packing slips](emea-turkiye-customer-packing-slips.md#set-up-unit-of-measure-mappings-for-e-packing-slips).

To generate UBL-TR e-Waybill documents, you need the following ER configurations.

| Number | ER configuration name | Type | Description |
| --- | --- | --- | --- |
| 1 | Invoice model | Data model | The shared data model that standardizes the structure of sales and inventory documents. It acts as the base model for generating e-Waybill XML output. |
| 2 | Packing slip model mapping | Model mapping | Links the Invoice data model to application data sources related to packing slips and transfer order shipments. |
| 3 | UBL Packing slip (TR) | Format | The base format that generates Turkish electronic documents in the UBL-TR DespatchAdvice format. |
| 4 | UBL Transfer orders (TR) | Format | A format that is derived from the **UBL Packing slip (TR)** format. It generates Turkish e-Waybill XML documents for transfer order shipments in the UBL-TR DespatchAdvice format. |

> [!NOTE]
> The **UBL Transfer orders (TR)** format is derived from the **UBL Packing slip (TR)** format. When you import the **UBL Transfer orders (TR)** format, the parent configurations are imported automatically.

## Configure parameters

This section describes how to configure the mandatory setup for generating UBL-TR e-Waybills.

### Reference the imported ER format configuration

To reference the imported ER format configuration, follow these steps:

1. In Finance, go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, in the **Waybill** field, select **UBL Transfer orders (TR)**.
1. Select **Save**.

> [!NOTE]
> Use the **Waybill** parameter to generate e-Waybills for transfer order shipments. To generate electronic packing slips for sales orders, also select the **UBL Packing slip (TR)** format in the **Packing slip** field on the **Accounts receivable parameters** page. Learn more in [Export of customer electronic packing slips](emea-turkiye-customer-packing-slips.md#reference-the-imported-er-format-configurations).

## Configure transportation details

For e-Waybills in Türkiye, specify transportation-related information on the transfer order. This information populates the vehicle, driver, and carrier sections of the UBL-TR DespatchAdvice XML. Complete the transportation details before you post the shipment.

To define transportation details for a transfer order, follow these steps:

1. In Finance, go to **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Select a transfer order.
1. On the Action Pane, on the **Ship** tab, in the **Transportation** group, select **Transportation details**.
1. Enter the carrier, vehicle, and driver information.

For a description of the fields on the **Transportation details** page, see [Configure transportation details for electronic packing slips](emea-turkiye-customer-packing-slips.md#configure-transportation-details-for-electronic-packing-slips).

> [!NOTE]
> If required transportation information is missing or incomplete, the generated UBL-TR DespatchAdvice document might fail validation during submission.

## Post the transfer order shipment

You can generate e-Waybills after you post the shipment of a transfer order.

> [!IMPORTANT]
> Before you post the shipment, ensure that you select the correct scenario in the **Invoice profile** field on the **Shipment** page. The invoice profile determines the `<ProfileID>` value in the generated UBL-TR DespatchAdvice XML.

To post a transfer order shipment, follow these steps:

1. In Finance, go to **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Select the transfer order to ship.
1. On the Action Pane, on the **Ship** tab, in the **Operations** group, select **Ship transfer order**.
1. On the **Shipment** page, on the **Overview** tab, in the **Update** field, select **All**.
1. In the **Serial prefix** field, select the serial prefix.
1. In the **Invoice profile** field, select the scenario for the e-Waybill.
1. Select **OK** to post.

After the posting process, the **Transfer status** field of the transfer order is set to *Shipped*.

The following table describes the available invoice profile options and their corresponding `<ProfileID>` values that are written to the UBL-TR DespatchAdvice XML.

| Invoice profile | ProfileID value | Description |
| --- | --- | --- |
| None | *(not set)* | No invoice profile is applied. The shipment is posted without a specific document classification in the UBL-TR DespatchAdvice XML. |
| Standard packing slip | `TEMELIRSALIYE` | Specifies the standard e-Waybill process profile for regular shipments. This option is the default for most e-Waybill scenarios. |
| Special handling packing slip | `HKSIRSALIYE` | Specifies the Wholesale Market Registration System e-Waybill profile. Use this option for shipments that are subject to produce market tracking requirements. |
| Regulated packing slip | `IDISIRSALIYE` | Specifies the Construction Steel Tracking System e-Waybill profile. Use this option for shipments of construction steel products that are subject to regulatory tracking requirements. |

> [!NOTE]
> The selected scenario is written to the `<ProfileID>` element in the generated UBL-TR DespatchAdvice XML. Ensure that you select the correct scenario before you post the shipment, because you can't change the scenario after the document is generated. For the current list of valid ProfileID values, see [UBL-TR Kod Listeleri](https://ebelge.gib.gov.tr/eirsaliyemevzuat.html).

## Generate the e-Waybill XML file

To generate an e-Waybill XML file, follow these steps:

1. In Finance, go to **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Select a transfer order that has a posted shipment.
1. On the Action Pane, on the **Transfer order** tab, in the **View** group, select **Transfer order history**.
1. On the **Transfer order history** page, select the line where the **Update type** field is set to *Shipment*. The **Voucher** field shows the preprinted serial number that's assigned to the shipment.
1. On the Action Pane, on the **Transfer order** tab, in the **Print** group, select one of the following options:
    - **Send e-Waybill original** – Generate the original e-Waybill XML file.
    - **Send e-Waybill copy** – Generate a copy of the e-Waybill XML file.

If you configure ER destinations, the system automatically sends the XML to the defined destination. If you don't configure a destination, the system stores the XML output on the **Electronic reporting jobs** page.

## View e-Waybills

If you define ER destinations for the e-Waybill format, the system sends the generated output files to the file destination that you configure for the ER destination. Learn more in [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

If you don't define ER destinations for the e-Waybill format, the system generates output files on the **Electronic reporting jobs** page.

To view the e-Waybill files, follow these steps:

1. In Finance, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.
1. Select **Open** to download the file that contains the e-Waybill.

If the system fails to generate the e-Waybill because of errors, you can view more details about the error by selecting **Show log** \> **Message details**.

## Related information

- [Use continuous serial numbering of packing slips and invoices](emea-tur-serial-numbering.md)
- [Export of customer electronic packing slips](emea-turkiye-customer-packing-slips.md)
- [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
