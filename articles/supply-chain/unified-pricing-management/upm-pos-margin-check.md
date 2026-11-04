---
title: Margin checks at point of sale (preview)
description: Learn how to set up margin check in Unified pricing management so that Store Commerce evaluates the margin of price overrides and manual discounts.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPParameters
ms.topic: how-to
ms.date: 11/03/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Margin checks at point of sale (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

When store staff override a price or enter a manual discount at the point of sale (POS), they might sell an item at a margin that's lower than your pricing policy allows. *Margin check* in the **Unified pricing management** module helps prevent this outcome. It evaluates the margin that results from each price override or manual discount that you enter in the [Store Commerce app](../../commerce/dev-itpro/store-commerce.md). Depending on the result, POS lets the change go ahead, requires a store manager to approve it, or blocks it.

This article explains how margin check works, how to set it up in Commerce headquarters, and what sales associates and store managers experience in POS.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## How margin check works

When a sales associate enters a price override or a manual discount, POS uses two independent controls to decide whether the change requires manager approval:

- **Margin status** – POS calculates the margin that the change would produce and compares it with the margin thresholds that you set up in headquarters.
- **Operator discount limit** – POS compares the change with the discount limits that apply to the operator. These limits come from the operator's POS permission group and any worker-specific overrides.

The margin thresholds divide margins into the following three ranges:

- **Acceptable** – The margin is at or above the acceptable margin percentage. The change goes ahead without margin approval.
- **Questionable** – The margin is below the acceptable margin percentage but at or above the questionable margin percentage. A manager must approve the change.
- **Unacceptable** – The margin is below the questionable margin percentage. POS blocks the change, and a manager can't approve it.

Because the two controls are independent, the following situations can occur:

- A change can require manager approval even when the resulting margin is acceptable, if it exceeds the sales associate's discount limit.
- A change that results in an unacceptable margin is blocked, even for a manager.

### How POS determines the margin

To calculate the margin, POS needs the cost of the item. When margin check runs, POS retrieves the cost from Commerce headquarters through Real-time Service. Headquarters returns the on-hand cost price of the product variant at the store's warehouse, based on the item's financial inventory dimensions. If no cost is found at that level, it uses the item-level cost instead. It then converts the cost from the item's inventory unit to the sales unit on the transaction line.

POS can't determine the margin in the following situations:

- Headquarters can't be reached, for example because the store is offline.
- The product, the warehouse, or the inventory dimensions on the transaction line can't be found or aren't valid.
- The item is tracked by owner, but no owner is specified.
- No unit conversion exists between the sales unit and the inventory unit of the item.

In these situations, the **When margin is unavailable** setting on the **Pricing management parameters** page determines whether the change can go ahead. Learn more in the [Configure margin check parameters](#parameters) section of this article.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Commerce version 10.0.50 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *Unified pricing management* – Learn more in [Turn on the Unified pricing management module for your system](upm-pricing-management-enable.md).
    - *Unified pricing margin check on POS*

## Set up margin check in POS

Set up the margin check in Commerce headquarters, and then synchronize the configuration to your stores. Before you begin, identify the POS permission group that represents store managers in your organization. Also identify the button grids that managers and sales associates use in POS.

Complete the following tasks in order (each task is described in detail in the following subsections):

1. [Configure margin check parameters](#parameters) – Turn on margin check, set the margin thresholds, choose what happens when the margin can't be determined, and decide how much margin information sales associates see.
1. [Add the margin check operations to POS](#operations) – Define the operations that POS uses to run margin checks and to record manager approvals.
1. [Add the Check margin button to a POS button grid](#button-grid) – Make the *Check margin* operation available to managers, or to sales associates who sign in with manager credentials.
1. [Configure POS permission groups](#permission-groups) – Set the discount limits that determine when a sales associate's request must be escalated to a manager.
1. [Review worker-specific permission overrides](#worker-overrides) – Make sure that individual workers don't have permission values that bypass your discount limits.
1. [Synchronize configuration to the channel](#sync) – Run the distribution schedules that send your changes to the channel database so that POS can use them.

> [!TIP]
> Set up and validate margin check in a sandbox environment before you configure it in production.

<a name="parameters"></a>

### Configure margin check parameters

The margin check parameters control whether POS evaluates margins, which thresholds it uses, what happens when the margin can't be determined, and how much margin information the requesting operator sees. To configure them, follow these steps.

1. Go to **Pricing management** > **Setup** > **Pricing management parameters**.
1. On the **General** tab, expand the **Margin check** FastTab.
1. Set the following fields:

    - **Enable margin check on POS** – Set this option to *Yes* to evaluate the resulting margin whenever a price override or a manual discount is entered in POS.
    - **When margin is unavailable** – Select what POS does when it can't determine the margin, for example when headquarters can't be reached to retrieve the inventory cost:
        - *Allow override* – The change goes ahead without a margin check.
        - *Don't allow override* – POS prevents the change.
    - **Show margin to the requester** – Set this option to *Yes* to show margin percentages and the minimum price to the operator who requests a price override or a manual discount. Set it to *No* to show the operator only whether the change exceeds the limit. The approving manager always sees the full figures. The default value is *Yes*.
    - **Enable margin alert** – Set to *Yes* to turn on margin alerts.
    - **Acceptable margin percentage** – Enter the lowest margin percentage that's acceptable without approval.
    - **Questionable margin percentage** – Enter the lowest margin percentage that a manager can approve. Margins below this value are unacceptable. This value can't be greater than the acceptable margin percentage.

1. On the Action Pane, select **Save**.

> [!NOTE]
> The fields in the **Margin thresholds** field group are shared with call center margin alerts on sales orders. They also appear on the **Margin alerts** tab of the **Accounts receivable parameters** page. If you change the thresholds on either page, the change affects both features.

<a name="operations"></a>

### Add the margin check operations to POS

POS uses two operations for margin check: *Check margin* runs a margin check, and *Approve margin override* records a manager's approval. Add both operations in headquarters so that you can assign them to button grids and control who can run them. Learn more about standard POS operations in [Online and offline point of sale (POS) operations](../../commerce/pos-operations.md).

To add the operations, follow these steps.

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **POS operations**.
1. If the list is filtered so that it shows only operations where **User operation** is set to *Yes*, clear the filter so that all operations are shown. Use the **Show filters** button (funnel icon) on the far-right pane to view and set the filter options.
1. On the Action Pane, select **New**, and add the following operations. The operation ID must match exactly. Use the recommended names unless you need localized names.

    | Operation ID | Operation name | Purpose | Permission ID | Check user access | User operation |
    |---|---|---|---|---|---|
    | 145 | Check margin | Runs the margin check from POS. | *0* for layout-controlled access, or your manager permission ID to require manager sign-in. | Applies only when a permission ID is set. See the table after this procedure. | *Yes* |
    | 146 | Approve margin override | Authorizes the margin override during the approval flow. | Your manager permission ID. | *Yes* | *No* |

1. On the Action Pane, select **Save**.

Don't add operation 146 to a button grid. POS invokes it automatically during the approval flow.

The following table explains how the permission settings for operation 145 affect access.

| Permission ID | Check user access | Result |
|---|---|---|
| 0 | Not applicable | Any user who can see the button can run the operation. Control access by adding the button only to the manager button grid. |
| Manager permission | *No* | A sales associate who doesn't have the permission is blocked. |
| Manager permission | *Yes* | A sales associate can start the operation, and POS prompts for manager sign-in. |

<a name="button-grid"></a>

### Add the Check margin button to a POS button grid

To let users run a margin check on demand, add a button for operation 145 to a POS button grid. The button grid that you choose determines who sees the button. Learn more about button grids in [Add POS operations to POS layouts by using Button grid designer](../../commerce/dev-itpro/add-POS-operations.md).

Use one of the following patterns:

- **Manager only (recommended)** – Add the button only to the manager button grid. Sales associates don't see the button.
- **Sales associate with manager sign-in** – Add the button to the sales associate button grid. For operation 145, set the manager permission ID, and set **Check user access** to *Yes*.

To add the button, follow these steps.

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Button grids**.
1. Select the button grid that the intended role uses. On the Action Pane, select **Designer**.
1. Add a button, and set its action to operation *145 – Check margin*.
1. Save the button grid.

<a name="permission-groups"></a>

### Configure POS permission groups

POS permission groups define how large a discount each operator can give without approval. Margin check combines these limits with the margin status to decide whether a change needs a manager's approval. Learn more about permission groups in [Create POS permission groups](../../commerce/tasks/create-pos-permission-groups.md).

To configure the discount limits, follow these steps.

1. Go to **Retail and Commerce** > **Employees** > **Permission groups**.
1. Select the sales associate (cashier) permission group. Set the **Maximum line discount percentage**, **Maximum line discount amount**, **Maximum total discount percentage**, and **Maximum total discount amount** fields according to your policy.
1. Select the manager permission group. Set limits that are high enough for the scenarios that managers must approve.
1. On the Action Pane, select **Save**.

Set sales associate limits lower than manager limits when you expect requests to be escalated. When a sales associate exceeds their limit, POS requests manager approval, provided that the request is within the manager's limits.

<a name="worker-overrides"></a>

### Review worker-specific permission overrides

A worker can have POS permission values that override the values that are inherited from their permission group. Worker-specific values take precedence over permission group values for the fields that are set, so they can bypass the limits that you configured in the previous section. To review these overrides before you test, follow these steps.

1. Go to **Retail and Commerce** > **Employees** > **Workers**.
1. Select the worker.
1. On the Action Pane, open the **Commerce** tab and select **POS permissions**.
1. Review any values that override the permission group. Adjust them as needed.

<a name="sync"></a>

### Synchronize configuration to the channel

POS reads its configuration from the channel database, so your changes take effect only after they're synchronized from headquarters. The following distribution schedules carry the settings that margin check uses:

- **1210** (*Unified pricing service*) – The margin check settings on the **Pricing management parameters** page.
- **1100** (*Product and price parameters*) – The fields in the **Margin thresholds** section.
- **1090** (*Registers*) – POS operations and button grids.
- **1060** (*Staff*) – POS permission groups and worker-specific POS permissions.

To synchronize the changes, follow these steps.

1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Select each distribution schedule that applies to the changes you made, and then, on the Action Pane, select **Run now**.
1. Verify that the jobs complete successfully before you test in POS.
1. If it's required, refresh or reactivate POS so that the button grid and configuration changes are applied.

## The sales associate experience

When you turn on margin check, sales associates enter price overrides and manual discounts in the usual way. POS evaluates each change after it's entered.

1. Sign in to Store Commerce, and add an item to the transaction.
1. Apply a price override, a manual line discount, or a total discount, and enter the amount or percentage. Learn more about these operations in [Pricing functions in POS](../../commerce/pos-pricing-functions.md).
1. POS evaluates the resulting margin status and the sales associate's discount limit, and then takes one of the following actions:

    - **Within policy** – If the margin is acceptable and the discount is within the sales associate's limit, the transaction continues without approval.
    - **Approval required** – If the margin is questionable, or the sales associate's discount limit is exceeded, POS starts the approval flow and prompts for manager sign-in.
    - **Blocked** – If the margin is unacceptable, POS blocks the change. A manager can't approve it.
    - **Margin unavailable** – If POS can't determine the margin, the **When margin is unavailable** setting on the **Pricing management parameters** page determines whether the change goes ahead.

If you set **Show margin to the requester** to *No*, the sales associate sees only whether the change exceeds the limit, not the margin percentage or minimum price.

If the **Check margin** button isn't on the sales associate's button grid, the sales associate doesn't see it. If the button is on the button grid, the permission settings for operation 145 apply.

## The store manager experience

Store managers work with margin check in two ways: they can check the margin of a transaction on demand, and they approve or reject requests that sales associates escalate.

- **Check margin** – When the **Check margin** button is on the manager button grid, sign in, and select **Check margin** in the transaction options.
- **Approve an escalated request** – When a sales associate's request requires approval, sign in at the POS approval prompt. Review the requested override or discount, and the margin or discount limit indicator. The approving manager always sees the full margin figures.
- **Approve or reject** – Approve the request if the margin is acceptable and the request is within your limits. Otherwise, reject it.

## Decision logic

The following table summarizes how POS responds to each combination of margin status and discount limits.

| Margin status | Sales associate limit | Manager limit | POS outcome |
|---|---|---|---|
| Acceptable | Within | Not applicable | Continue without approval. |
| Acceptable | Exceeded | Within | Prompt for manager approval because the sales associate's limit is exceeded. |
| Questionable | Any | Within | Prompt for manager approval. |
| Unacceptable | Any | Any | Block the request. A manager can't approve it. |
| Acceptable or questionable | Exceeded | Exceeded | The manager can't approve the request because it exceeds the manager's limits. |
| Unavailable | Any | Any | Continue without a margin check, or prevent the change, depending on the **When margin is unavailable** setting. |

## Related information

- [Unified pricing management module overview](upm-pricing-management-overview.md)
- [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md)
- [Pricing functions in POS](../../commerce/pos-pricing-functions.md)
- [Online and offline point of sale (POS) operations](../../commerce/pos-operations.md)
- [Create POS permission groups](../../commerce/tasks/create-pos-permission-groups.md)
- [Store Commerce app](../../commerce/dev-itpro/store-commerce.md)
