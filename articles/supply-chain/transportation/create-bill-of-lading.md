---
title: Create a bill of lading
description: Learn how to create a bill of lading when using warehouse management processes (WMS), including an outline on a master bill of lading.  
author: lisascholz
ms.author: lisascholz
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSBillOfLading, WHSLoadPlanningWorkbench, WHSBillOfLadingCarrier, WHSBillOfLadingOrder, WHSOutboundLoadPlanningWorkbench, WHSInboundLoadPlanningWorkbench
---

# Create a bill of lading

[!include [banner](../includes/banner.md)]

This article describes how to create a bill of lading when using warehouse management processes (WMS).  

A bill of lading is a legal document between the company that ships the items and the carrier. The document accompanies the shipped items, and it serves as a receipt of shipment when the items are delivered at the destination. If you're using warehouse management, there are two ways to generate a bill of lading:

- Create the report manually, using the **Bill of lading** page.
- Generate the report from the **Outbound load planning workbench** or **Inbound load planning workbench**, depending on whether the load is inbound or outbound.

If you generate the bill of lading from the **Outbound load planning workbench** or **Inbound load planning workbench**, the load status must be *Shipped*. If there's more than one shipment in the load, a bill of lading is created for each shipment. After a bill of lading has been created, you can make changes to it on the **Bill of lading** page.

## Master bill of lading

If there's more than one shipment in the load, you can generate a master bill of lading. This has the same layout and information as a bill of lading, but contains the summarized content for all the shipments. If the **Create a master bill of lading when there's more than one shipment on a load** option is set to **Yes** on the **Transportation management parameters** page, a master bill of lading is automatically generated if you create a bill of lading from the **Outbound load planning workbench** or **Inbound load planning workbench**, and there's more than one shipment. You can also get a list of the bills of lading by clicking **Related information** &gt; **Bill of lading**. If you're creating bills of lading manually, you can create a master bill of lading on the **Bill of lading** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
