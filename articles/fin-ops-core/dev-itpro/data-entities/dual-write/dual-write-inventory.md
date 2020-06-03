---
# required metadata

title: Inventory availability in dual write
description: This topic provides information about checking inventory availability in dual-write.
author: yijialuan
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: riluan
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-05-26

---

# Inventory availability

[!include [banner](../../includes/banner.md)]

Using inventory availability, you can check your inventory before you add a product into the **Quotes**, **Orders**, or **Invoices** forms in model-driven apps in Dynamics 365. For example, checking inventory and determining a fulfullment date is a key task in the [prospect-to-cash](dual-write-prospect-to-cash.md) process. If you don't have enough inventory, you can estimate a delivery date based on projected inventory receipts and issues. You can also check the product's available-to-promise (ATP) information, where you can find the ATP quantity in the pre-defined time fence.

## On-hand Inventory 

In the header of the **Quotes**, **Orders**, or **Invoices** forms in Dynamics 365 Sales, a new button **On-hand Inventory** is added. When you click the button, a dialog box appears and you can specify the company and the product for which you want to check the on-hand inventory. It returns the inventory information from the Dynamics 365 Supply Chain Management, and shows the same information as [On-hand inventory](../../../../supply-chain/inventory/tasks/check-availability-stock.md). The information includes these quantities:

- **On-hand Quantity**
- **Reserved On-hand Quantity**
- **Available On-hand Quantity**
- **Orderd Quantity**
- **On-order Quantity**
- **Reserved Ordered Quantity**
- **Total Available Quantity**

## ATP information

On line items of the **Quotes**, **Orders**, or **Invoices** forms in Dynamics 365 Sales, a new button **ATP Information** is added. When you click the button, a dialog box appears and you can specify the company, product, Inventory Site, Inventory Warehouse and the Order Quantity. It returns the **ATP Information** from Supply Chain Management and shows the settings descrbed in [Order promising](../../../../supply-chain/sales-marketing/delivery-dates-available-promise-calculations.md#atp-calculations). The information includes **ATP quantity**, **Receipt quantity**, **Issue quantity**, and **On-hand quantity**.
