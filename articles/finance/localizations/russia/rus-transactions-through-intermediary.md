---
title: Transactions through intermediary
description: Learn how to work with intermediary deals that are made by an agent in Russia with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/12/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Transactions through intermediary

[!include [banner](../../includes/banner.md)]

This article explains how to work with intermediary deals that are made by an agent in Russia with Microsoft Dynamics 365 Finance.

In economic activities that involve an intermediary, there are three participants:

- The person who sells or purchases goods (works or services)
- The third-party supplier or buyer
- The intermediary between the first two participants

Russian legislation defines three legal forms of intermediation:

- A commission agreement, where the committer (also known as the principal) engages a commissioner
- An agency agreement, where the principal engages an agent
- An assignment agreement, where the principal retains an attorney

The term *principal* refers to the party that engages the agent. The intermediary (the commissioner, agent, or attorney) performs legal actions and other actions (transactions) on behalf of the principal. Intermediaries can perform these actions in one of two ways:

- In their own name but at the principal's expense
- In the principal's name and at the principal's expense

The current implementation of this functionality has the following limitations:

- Credit notes can be registered only in the module where the original factures were registered.
- Sub-commission isn't supported.
- No commission bonus is calculated.
- No transactions are created in the general ledger, based on the report for the principal.

## Preliminary setup

### Set up an inventory profile for an agent's transactions

To set up an inventory profile for an agent's transactions, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Setup** \> **Dimensions** \> **Inventory profiles**.
1. Select **New** to create an inventory profile.
1. In the **Inventory profile** field, enter a name for the inventory profile.
1. In the **Name** field, enter a description.
1. In the **Kind of activity** field, select **Commission agent**.
1. Set the **Don't match** option to **No**.
1. In the **Kind of inventory** field, specify **Common**.
1. Select **Save**.

![Inventory profiles page.](../media/1_Inventory_profiles.jpg)

### Set up the Inventory profile and Owner tracking dimensions

To set up the Inventory profile and Owner tracking dimensions, follow these steps.

1. In Dynamics 365 Finance, go to **Product information management** \> **Setup** \> **Dimension and variant groups** \> **Tracking dimension groups**.
1. Select **New** to create a dimension group.
1. In the **Name** field, enter a name for the dimension group.
1. In the **Description** field, enter a description.
1. On the **Tracking dimensions** FastTab, set up the Inventory profile and Owner tracking dimensions:

    - On the **Inventory profile** line, select the **Active**, **Primary stocking**, **Physical inventory**, **Financial inventory**, **Coverage plan by dimensions**, and **Transfer** check boxes.
    - On the **Owner** line, select the **Active**, **Physical inventory**, and **Transfer** check boxes.

1. Select **Save**.

![Tracking dimension groups page.](../media/2_Tracking_dimension_groups.jpg)

### Set up a number sequence for the report for the principal

To set up a number sequence for the report for the principal, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence code for the **Report code** reference.

Learn more in [Purchases on commission](rus-purchases-on-commission.md) and [Sales on commission](rus-sales-on-commission.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
