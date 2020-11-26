---
# required metadata

title: Intercompany planning
description: This topic describes intercompany planning and explains how to configure intercompany planning with Planning Optimization in Supply Chain Management. 
author: ChristianRytt
manager: tfehr
ms.date: 11/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-11-26
ms.dyn365.ops.version: 10.0.14

---
# Intercompany planning

[!include [banner](../../includes/banner.md)]

Logistic operations of some companies depend on other legal entities within the organization. Such operations are dealt with by using intercompany sales and purchases because these legal entities have a separate chart of accounts.

This topic describes intercompany planning and explains how to configure intercompany planning with Planning Optimization in Supply Chain Management.

Important intercompany terms used in this topic:

- **Upstream**  - Used as a relative reference in a firm or supply chain to indicate moving in the direction of the raw material supplier.
- **Downstream**  - Used as a relative reference in a firm or supply chain to indicate moving in the direction of the customer.
- **Planned intercompany demand**  - Planned demand for a product in a company based on planned demand for the product from a downstream company.

With master planning you can get a plan in one company to include planned intercompany demand related to planned orders from a plan in another company. This is useful to get full visibility of planned orders cross companies and ensure that required planned supply orders are created, without having to firm planned orders for the intercompany demand.

If you run a master planning from a master plan that includes planned downstream demand, then planned purchase orders from the related intercompany vendors will be included into the plan as demand.

To achieve this the following setup is required:

1. Products must be released in relevant companies.
 For more information see [Configure and use intercompany trade in Dynamics 365 Supply Chain Management ](https://docs.microsoft.com/en-us/learn/modules/configure-use-intercompany-trade-dyn365-supply-chain-mgmt/).
2. Downstream demand must be covered by purchase from a vendor with intercompany relation to the upstream company and relevant inventory dimension defaulting (site/warehouse) on the customer.
 For more information see [Configure and use intercompany trade in Dynamics 365 Supply Chain Management ](https://docs.microsoft.com/en-us/learn/modules/configure-use-intercompany-trade-dyn365-supply-chain-mgmt/).
3. The master plan in the upstream company must Include planned downstream demand and have the relevant Company and Master plan specified in the Downstream plans.

Follow these steps to configure your master plan to include planned downstream demand.

1. Go to  **Master planning \&gt; Setup \&gt; Plans \&gt; Master plans**.
2. On the  **Intercompany planning** tab, set the following value:

- **Include planned downstream demand**  – Set this option to  **Yes**  to enable intercompany for this Master plan.
- **Downstream plans** – Add the desired Master plan(s) from other companies with **New** or remove downstream Master plans with **Delete**.

## Pegging cross companies with Multilevel pegging

### Intercompany example with two companies: USMF, DEMF

Here a planned production order is created in USMF to cover a sales order in DEMF. In USMF the direct demand is a Planned intercompany demand.

For this to show up in USMF master planning was first run in DEMF, then USMF

![](RackMultipart20201126-4-ujgd4r_html_48f1cea32d00f81a.png)

### Intercompany example with three companies: USMF, DEMF, FRRT

Here a planned purchase order is created in USMF to cover a sales order in FRRT. In DEMF and USMF the direct demand is a Planned intercompany demand.

For this to show up in USMF master planning was first run in FRRT, then DEMF, and finally USMF

![](RackMultipart20201126-4-ujgd4r_html_bf1c4e48618fd97b.png)
