---
# required metadata

title: Hazardous materials inquiries and reports
description: This topic describes how to work with the various reports related to hazardous materials. Many of these reports are required to remain compliant with various hazardous material regulations during shipping and storage.
author: dasani-madipalli
manager: tfehr
ms.date: 06/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  HMIMStockListLimits, HMIMShipperDeclaration, HMIMCarrOfMerchByRoad, HMIMMultimodalDGItem, HMIMCarrOfMerchByRoadItem
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Release 10.0.11
---

# Hazardous materials inquiries and reports

[!include [banner](../includes/banner.md)]

Supply Chain Management provides a variety of reports related to hazardous materials. Many of these are required to remain compliant with various hazardous material regulations during shipping and storage.

These reports, with the exception of the multi-model dangerous goods report, use the delivery method defined on the shipment to locate the regulation to use for printing the item shipping text. The mode of delivery is associated with the shipping carrier and the carrier service. You must set up a shipping carrier and service and link that to a mode of delivery. The mode of delivery is related to the hazardous materials regulation.

The following diagram shows the sequence of activities that occur when the system generates hazardous material reports.

![Hazardous material reports sequence](media/hazmat-report-sequence.png "Hazardous material reports sequence")

## Set up hazardous materials reporting

If you are shipping items with hazardous material, then you will usually need to generate specific reports to preserve safety and comply with hazardous materials regulations. To set up your reports:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
2. Open the **Reports** tab.
3. Expand the **Hazardous materials report parameter** FastTab
4. Make the settings described in the following table.

| Group | Setting | Description |
| --- | --- | --- |
| **Multimodal&nbsp;Dangerous Goods** | **Regulation&nbsp;code** | Choose the regulation to be used when generating a multimodal dangerous goods report. |
| **Hazardous Material stock limits** | **Regulation code** | Choose the regulation to be used when evaluating stock limits. |
| **Carriage of merchandise by road** | **CMR group product** | CMR stands for carcinogenic, mutagenic, and reprotoxic substances. Set this to **Yes** to configure the system to print specific warnings and messages related to the handling of these substances. |
| **Carriage of merchandise by road** | **Hazardous material group description** | Enter text with specific warnings related to CMR and carriage of merchandise by road. This text will be included in the report. |
| **Shippers declaration** | **Warning** | Enter text with a warning message to be printed on the shipper's declaration form (for example, "Warning: Dangerous Goods, Flammable"). |
| **Shippers declaration** | **Footer declaration** | Enter text to provide a specific message at the bottom of the shipment declaration document. |
| **Hazardous goods report language** | **Hazardous goods domestic report language** | Select the default language to be used for hazardous material reports associated with domestic shipments. |
| **Hazardous goods report language** | **Hazardous goods export report language** | Select the default language to be used for hazardous material reports associated with international shipments. |

## Hazardous materials report

The **Hazardous materials** report shows a list of all items that have been set up and defined with dangerous goods information. Use it to monitor and review the information you need to maintain. It shows a limited selection of fields from the hazardous material setup. You can personalize the page to add additional fields as required.

To view this information, go to **Product information management \> Inquiries and reports \> Hazardous material shipping documentation \> Hazardous materials**.

<a name="stock-limit-report"></a>

## Hazardous material stock limit report

The **Hazardous material stock limit report** page lets you monitor the stock levels of the hazardous materials in your warehouse locations to make sure they remain under established, safe limits. The limits shown here come from those defined for each released product.

To view the report, go to **Product information management \> Inquiries and reports \> Hazardous shipping documentation \> Hazardous material stock limits**.

For more information about how to set stock limits on each released product, see [Set stock limits for hazardous products](hazmat-items.md#stock-limits).

The regulation used for stock limits is defined on the **Warehouse management \> Setup \> Warehouse management parameters** page. Open the **Reports** tab and set a **Regulation code** for the **Hazardous materials stock limit** parameter. See also Set up hazardous materials reporting.

## Verified gross mass report

This report lets you print information about the weight of a shipment.

To generate and print this report, go to **Warehouse management \> shipments \> All shipments** and open the relevant shipment. Then open the **Shipments** tab in the Action Pane and, in the **Hazardous materials document** group, select **Verified gross mass**.

## Multimodal dangerous goods report

This report is provided for shipments to be moved using a combination of transport methods. It is typically used when a shipment is first moved by road and then later by sea.

To generate and print this report, go to **Warehouse management \> shipments \> All shipments** and open the relevant shipment. Then open the **Shipments** tab in the Action Pane and, in the **Hazardous materials document** group, select **Multi model dangerous goods**.

When you generate this report, the information is saved so you can edit and/or reprint it if needed. To edit a generated report, go to **Warehouse management \> Inquiries and reports \> Hazardous materials shipping documentation \> Multimodal dangerous goods** and then locate the relevant report in the list. After editing the content as needed, select **Print** from the Action Pane to print the report.

## Shippers declaration report

This report lets print information related to a declaration of what materials are included in the shipment.

To generate and print this report, go to **Warehouse management \> shipments \> All shipments** and open the relevant shipment. Then open the **Shipments** tab in the Action Pane and, in the **Hazardous materials document** group, select **Shippers declaration**.

## Carriage of merchandise by road report

This is similar to a bill of lading but is commonly used for road transportation in Europe under the ADR regulations. This report will pick up the shipping print text for an item unless you use the group description parameter found in warehouse management parameters.

To generate and print this report, go to **Warehouse management \> shipments \> All shipments** and open the relevant shipment. Then open the **Shipments** tab in the Action Pane and, in the **Hazardous materials document** group, select **Carriage of merchandise by road**.

When you generate this report, the information is saved so you can edit and/or reprint it if needed. To edit a generated report, go to **Warehouse management \> Inquiries and reports \> Hazardous materials shipping documentation \> Carriage of merchandise by road** and then locate the relevant report in the list. After editing the content as needed, select **Print** from the Action Pane to print the report.

## Shipment summary report

This report provides a summary of the points on a shipment summarized by the transport category related to the released items.

To generate and print this report, go to **Warehouse management \> shipments \> All shipments** and open the relevant shipment. Then open the **Shipments** tab in the Action Pane and, in the **Hazardous materials document** group, select **Shipment summary**.

## Bill of landing report

When the hazardous materials feature is enabled on your system, bill of landing reports include a **Hazardous materials** column, which indicates whether a load includes hazardous materials. This report is available from the **All loads** page, as usual.

## Packing list report

When the hazardous materials feature is enabled on your system, packing lists will include additional information related to the shipping print text for an item. This report is available from the **All loads** page, as usual.
