---
title: Commercial invoices
description: This article describes how to create and print a commercial invoice when using warehouse management processes (WMS).  
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: WHSShipPlanningListPage, WHSShipmentDetails
ms.topic: how-to
ms.date: 10/17/2022
ms.custom: bap-template
---

# Commercial invoices

[!include [banner](../includes/banner.md)]

This article describes how to create and print a commercial invoice when using warehouse management processes (WMS).  <!-- Is WMS required for this? If so, we should move this topic to the Warehouse management area. -->

A commercial invoice is required for the export and import clearance process. It is used to calculate tariffs, international commercial terms <!-- I'm missing something here. Do we mean that the invoice is used to calculate these terms, or that it is required for these terms, or something else? -->, and for customs purposes. Commercial invoices are generally not needed for shipments between EU countries, just between EU countries and non-EU countries. A few countries require the commercial invoice to be on a specific form, but for most countries the seller or exporter version is acceptable as long as all the pertinent information is included.

You can print the commercial invoice for a single shipment from the **All shipments** list page or from the **Shipment details** page.

## Document content

The commercial invoice includes the following information, which is prefilled with data from the shipment invoice applies to:

- Invoice number and date
- Seller
- Sold-to address
- Ship-to address
- International commercial terms (Incoterms) <!-- I found this via Google (original was "IncoTerm"), is this right? I don't see this on the sample image--what does this mean? -->
- Terms of sale <!-- I added this, since it wasn't listed. Or is this the "IncoTerm"? -->
- Payment terms
- Currency of settlement
- Mode of shipment
- Product details (including quantity, description, unit of measure, unit price, and total price)
- Total commercial value
- Miscellaneous charges
- Total invoice value

If you need change or add data to the commercial invoice, then export the generated document to an editable format, such as Microsoft Word. After export, you can apply any required changes before a declaration is made.

The following illustration shows an example of a commercial invoice.

![Example commercial invoice.](media/commercial-invoice-example.png "Example commercial invoice")

## Print a commercial invoice

To print a commercial invoice for a shipment, do the following:

1. Do one of the following:
    - Go to **Transportation management \> Planning \> Shipments \> All shipments** and select the shipment you want to print the commercial invoice for.
    - Open the **Shipment details** page for the shipment you want to print the commercial invoice for. There are several ways to get here (including from the **All shipments** page).
1. On the Action Pane, open the **Shipments** tab and, from the **Print** group, select **Commercial invoice**.
1. A preview of the document opens. Use the commands provided on the Action Pane to print or export the document as needed.

> [!NOTE]
> You must deploy the TMSCommercialInvoice report prior to using this function. <!-- More info is needed about this step. How do we do this? Maybe we need a section about this? Or maybe we have a link for this? -->
