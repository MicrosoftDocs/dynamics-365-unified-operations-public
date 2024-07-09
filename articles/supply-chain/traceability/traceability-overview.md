---
title: Supply Chain Traceability overview (preview)
description: Supply Chain Traceability enables you to trace raw materials and subassemblies in a product and track the usage and disposal over the full value chain. As a result, it helps you meet a wider range of business objectives, including efficiency, resilience, responsiveness, and sustainability.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Supply Chain Traceability overview (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Companies are under increasing pressure to comply with legislation (such as the EU and German Supply Chain Act), especially when it comes to recalling defective and potentially unsafe products, or for the sake of linking products with certain documents. The Supply Chain Traceability add-in for Dynamics 365 Supply Chain Management lets you collect business and industry-specific data across the product value chain, which can be used for regulation audits and compliance process. Beyond compliance, Supply Chain Traceability also enables companies to meet a wide range of business objectives, including efficiency, resilience, responsiveness, and sustainability.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Supply Chain Traceability enables you to trace raw materials and subassemblies in a product and track the usage and disposal over the full value chain. As a result, it helps you meet a wider range of business objectives, including efficiency, resilience, responsiveness, and sustainability.

Supply Chain Traceability follows products and goods as they move through the supply chain and collects information about the provenance of inputs, supplier sourcing practices, and conversion processes. It provides the following features and benefits:

- **Accurate tracking** – Track and document the chain of custody based on individual identifiers (such as serial numbers or batch numbers) across the entire value chain, and throughout the full lifecycle of an item.
- **As-built BOM registration** – Document composition genealogy information (as-built BOM) and activity events (such as procurement, production, and distribution) against each serial and batch number. You can trace all the way back to find the origin of each single part. <!--KFM: This is from release plan. Do we have this in the current preview? -->
- **Forward and backward search** – Use the where-used functionality to track the consumption of materials throughout your entire value chain and find finished or semi-finished goods that could be impacted by a defective component.
- **Public API** – Integrate with external systems using the robust Supply Chain Traceability API. While this requires some initial setup and configuration, it offers a high degree of flexibility and customization to cater to specific business needs.
- **Integration with the [production floor execution interface](../production-control/production-floor-execution-use.md)** – Production floor workers can register the serial numbers and batch numbers of each component and each finished good.
