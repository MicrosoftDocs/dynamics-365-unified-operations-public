---
# required metadata

title: Intercompany planning
description: This topic describes intercompany planning and explains how to configure intercompany planning with Planning Optimization in Supply Chain Management. 
author: ChristianRytt
manager: tfehr
ms.date: 12/02/2020
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
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: 10.0.14

---
# Intercompany planning

[!include [banner](../../includes/banner.md)]

For some organizations, logistic operations depend on other legal entities (companies) within the organization. Such operations are dealt with by using intercompany sales and purchases because each of these legal entities has a separate chart of accounts.

This topic describes intercompany planning and explains how to configure intercompany planning with Planning Optimization in Supply Chain Management.

Important intercompany terms used in this topic:

- *Upstream*  - Used as a relative reference in a firm or supply chain to indicate moving in the direction of the raw material supplier.
- *Downstream*  - Used as a relative reference in a firm or supply chain to indicate moving in the direction of the customer.
- *Planned intercompany demand*  - Planned demand for a product in a company based on planned demand for the product from a downstream company.

With master planning, a plan in one company can include planned intercompany demand related to planned orders from a plan in another company. This is useful to get full visibility of planned orders across companies and ensure that all required planned supply orders are created, without having to firm planned orders for the intercompany demand.

If you execute a master planning run from a master plan that includes planned downstream demand, then planned purchase orders from the related intercompany vendors will be included into the plan as demand.

## Required set up

To use intercompany planning, you must prepare your system as follows:

1. The relevant products must be released in all the relevant companies. For more information, see [Configure and use intercompany trade in Dynamics 365 Supply Chain Management ](https://docs.microsoft.com/learn/modules/configure-use-intercompany-trade-dyn365-supply-chain-mgmt/) on Microsoft Learn.
1. Downstream demand must be covered by purchases from a vendor with intercompany relation to the upstream company and relevant inventory dimension defaulting (site/warehouse) on the customer. For more information, see [Configure and use intercompany trade in Dynamics 365 Supply Chain Management ](https://docs.microsoft.com/learn/modules/configure-use-intercompany-trade-dyn365-supply-chain-mgmt/) on Microsoft Learn.
1. The master plan in the upstream company must include planned downstream demand and have the relevant company and master plan specified in the downstream plans.

## Include planned downstream demand

Follow these steps to configure your master plan to include planned downstream demand:

1. Go to  **Master planning \> Setup \> Plans \> Master plans**.
1. Select or create a plan.
1. On the  **Intercompany planning** FastTab, make the following settings:
    - **Include planned downstream demand** - Set this to  *Yes*  to enable intercompany planning for this master plan.
    - **Downstream plans** - When **Include planned downstream demand** is set to *Yes*, use the toolbar and grid here to add the desired master plan(s) from other companies.

## Peg across companies with multilevel pegging

With multilevel pegging, you can view pegging across companies to see the initial source of demand being covered by a supply. 

To view multilevel pegging information:

1. Go to **Master planning \> Master planning \> Planned orders**.
1. Select or open a planned order.
1. On the Action Pane, open the **View** tab and, from the **Requirements** group, select **Multilevel pegging**.

### Intercompany example with two companies

For this example, a planned production order is created in the USMF company to cover a sales order in the DEMF company. In USMF, the direct demand is a planned intercompany demand. For this to show up in USMF, master planning was first run in DEMF, then in USMF. 

The following screenshot shows how this example could appear on the **Multilevel pegging** page for the planned production order.

![Intercompany example with two companies](media/IntercompanyPlanning1.png)

### Intercompany example with three companies

For this example, a planned purchase order is created in the USMF company to cover a sales order in the FRRT company. In the DEMF and USMF companies, the direct demand is a planned intercompany demand. For this to show up in USMF, master planning was first run in FRRT, then DEMF, and finally USMF.

The following screenshot shows how this example could appear on the **Multilevel pegging** page for the planned production order.

![Intercompany example with three companies](media/IntercompanyPlanning2.png)
