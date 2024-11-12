---
title: Intercompany master scheduling
description: Learn about intercompany master scheduling, which is the means by which you calculate requirements and generate planned intercompany orders.
author: kamaybac
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Intercompany master scheduling

[!include [banner](../../includes/banner.md)]

Intercompany master scheduling is the means by which you calculate requirements and generate planned intercompany orders across several internal companies. Intercompany master scheduling is carried out over the number of iterations that you specify. To enable Microsoft Dynamics 365 Supply Chain Management to carry out intercompany master scheduling, you must set up master scheduling in each of your intercompany companies. This entails several iterations in which Microsoft Dynamics 365 Supply Chain Management automatically creates an intercompany purchase order; this, in turn, leads to the automatic creation of an intercompany sales order, which again leads to new demands.

You set up the intercompany master plan and the intercompany scheduling order in the **Master planning** parameters in each of the intercompany companies.

In order to propagate the demand throughout the intercompany chain, you must set parameters to ensure that planned purchase orders are automatically firmed; that is, orders cannot be changed in terms of time or quantity. Set up the **Firming time fence** on the Coverage group, or the **Firming time fence** in the Master plan. If no **Firming time fence** is set up, no intercompany purchase orders are created automatically. Only the first execution of the master scheduling results in planned orders. However, because no intercompany purchase order is created, no intercompany sales order is created, and, therefore, no more intercompany purchase orders are created, and so on.

When you start the intercompany master scheduling, Microsoft Dynamics 365 Supply Chain Management performs one master scheduling in each intercompany company; then, it performs a second master scheduling in each intercompany company, and so on, until the specified number of iterations is reached. A maximum of 30 iterations is possible; however, the more iterations that you choose, the longer the scheduling takes.

Because the master scheduling in the companies is controlled by the intercompany scheduling sequence, that is, the order in which the program prioritizes the master schedules between each intercompany company, you can start the intercompany master scheduling from any of the intercompany companies. Because the intercompany scheduling sequence determines the order in which the master scheduling is performed in the companies, it is not important where the intercompany master scheduling is started. In each iteration, the current company executes last.

> [!NOTE]
> The best practice is to allow intercompany master scheduling to be initiated from one Microsoft Dynamics 365 Supply Chain Management company.

On the **Intercompany master scheduling** page, you can start a sequence of master scheduling, which executes a master scheduling the first time with the principle for updating the requirement calculation that you have selected for the first iteration for all the intercompany companies. Subsequent iterations use the secondary principle that you select for the next iteration, and this principle is applied until the number of iterations that you have specified is reached.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
