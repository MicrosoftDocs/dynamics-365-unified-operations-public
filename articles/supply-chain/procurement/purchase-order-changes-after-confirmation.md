---
title: Review and accept changes to confirmed purchase orders
description: This article describes the Confirmed purchase orders with changes workspace, where you can review and accept changes to confirmed purchase orders, based on their downstream impact.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchOrderInReview, PurchOrderApproved, PurchOrderInDraft, PurchOrderAssignedToMe, VendPurchOrderJournalListPage, PurchTableWorkflowDropDialog, VendPurchOrderJournal
ms.topic: how-to
ms.date: 07/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Review and accept changes to confirmed purchase orders

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> Some or all of the functionality that's described in this article is available as part of a preview release. The content and the functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> **During this preview phase, the summaries of changes and downstream impacts are available only in environments that are hosted in the US**, and they are shown only in English. All other functionality is globally available.

<!--KFM: Preview until further notice -->

During procurement planning, any changes that are made to confirmed purchase orders can have a significant impact on downstream processes such as planned production, service work, or sales orders. The new **Confirmed purchase orders with changes** workspace makes it fast and easy to identify and reconfirm changes that have only a low risk of downstream impact. Therefore, procurement managers can focus on high-impact changes to assess downstream order impacts and communicate directly with vendors.

This article describes the **Confirmed purchase orders with changes** workspace where users can review and accept changes that suppliers make to confirmed purchase orders, based on the downstream impact of the changes.

## Enable the feature for your system

This section describes the steps that you must complete to enable the **Confirmed purchase orders with changes** workspace and the related Copilot support.

- Steps 1 and 2 enable the **Confirmed purchase orders with changes** workspace.
- Steps 3 through 6 enable the support by Copilot for this workspace that provides for example natural-language change summaries and communication drafts.

    These steps require that your environment is enabled for Power Platform integration. For more information, see [Enable Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).

### Step 1: Upgrade Supply Chain Management to the required build

You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.

This feature was added in builds that came out after the initial release of versions 10.0.34 and 10.0.35. If you're running one of those versions, you must update your version as described here:

- If you're running Supply Chain Management version 10.0.34, you must upgrade the Application Suite to version 10.25.1372 (or later). This version is included in build 10.0.1591.72 (or later) of finance and operations apps.
- If you're running Supply Chain Management version 10.0.35, you must upgrade the Application Suite to version 10.26.1075 (or later). This version is included in build 10.0.1627.33 (or later) of finance and operations apps.

### Step 2: Enable the workspace feature in Feature management

In the [**Feature management**](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, turn on the feature that's named *(Preview) Review changes to confirmed purchase orders based on downstream impact*.

### Step 3: Upgrade the Finance and Operations Virtual Entity solution

Follow these steps to upgrade the *Finance and Operations Virtual Entity* solution.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Power Platform environment that's connected to your finance and operations app, and open the detail view.
1. In the **Resources** field, select **Dynamics 365 apps**.
1. Find the app that's named *Finance and Operations Virtual Entity*.
1. If the status is *Installed*, you're already running the latest version. If the status is *Update available*, you must update the solution by following these steps:

    1. Select the ellipsis button (**&hellip;**), and then select **Update**.
    1. Accept the terms of service, and then select **Update**.

You can follow the status of the update. During the update, the status is *Installing*. After the update is completed, the status changes to *Installed*.

### Step 4: Enable Supply Chain Management to access your Dataverse environment

Follow these steps to enable Supply Chain Management to access your Dataverse environment.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Dataverse environment that's connected to your Supply Chain Management environment, and open the detail view.
1. Select the **Settings** menu on the menu bar.
1. Go to **Product \> Features**.
1. Set the **Finance and Operations in Dataverse** option to *On*.

### Step 5: Install the Copilot application in Supply Chain Management

> [!NOTE]
> During this preview phase, the Copilot application can only be insalled for environments that are hosted in the US.

Follow these steps to install the Copilot application in your Supply Chain Management environment.

1. Go to the [Copilot in Microsoft Dynamics 365 Supply Chain Management](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamicsscmai-preview?flightCodes=f42a7338c806438f8fca820c4ed82b7c&tab=Overview) page in the Microsoft commercial marketplace.
1. Select **Get it now**.
1. The deployment process opens [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Select the Dataverse environment that's connected to your Supply Chain Management environment to install the Copilot application.
1. You can follow the status of the installation by opening the detail view of the environment. In the **Resources** field, select **Dynamics 365 apps**. The status of the Copilot application is *Installing*. After the installation is completed, the status changes to *Installed*. If an error occurs, the status changes to *Failed* and you can find details about the error in the **Notifications** field.

### Step 6: Enable the required security roles

Users who should have access to the functionality must be assigned the *AIB Roles* and *Finance and Operations AI* security roles in Dataverse.

In the detail view of the environment, in the **Access** field, select **Users** or **Teams**. Select the users or teams that should have access, and assign the *AIB Roles* and *Finance and Operations AI* security roles to them.

## The Confirmed purchase orders with changes workspace

To open the workspace, go to **Procurement and sourcing \> Workspaces \> Confirmed purchase orders with changes**.

[<img src="media/po-change-review-highimpact.png" alt="Screenshot of the Confirmed purchase orders with changes workspace." title="Screenshot of the Confirmed purchase orders with changes workspace" width="720" />](media/po-change-review-highimpact.png#lightbox)

The workspace lists all previously confirmed purchase orders that have been changed since confirmation. It helps the review process by identifying potential impacts on production work, service work orders, and sales orders.

At the top of the workspace, the three tiles summarize groups of changes to confirmed purchase orders and the related downstream impacts. 

In preview the grouping is predefined and limited to pegged orders that have been created by planning.

- **Low impact changes** – This tile highlights changes to purchase orders that have no known impact on downstream orders that have been created by planning, also called pegged orders. A summary of changes is generated to help you review and validate the purchase orders.
- **High impact changes** – This tile highlights purchase orders that have known downstream impacts on pegged orders. These high-risk changes are summarized together with the detected impacts, to help you investigate further and decide what action to take.
- **Impacted downstream orders** – This tile summarizes impacts on pegged orders by the number and type of orders, and it shows the purchase order changes that cause each impact. This information helps you review potential downstream impacts based on the latest master planning run.

Each tile provides a **Show** link, which lets you filter the list of purchase orders and purchase order lines. The list includes columns for the original and new quantities, original and new confirmed delivery dates, and so on.

## Review changes to confirmed purchase orders

Purchasers use the workspace to review and accept changes to confirmed purchase orders. They typically follow these steps.

1. Study all changes to confirmed purchase orders and their downstream impact.
1. Focus on changes that have a low risk of downstream impact.
1. Review changes that have a high risk of downstream impact.
1. Review the remaining downstream impact.

The following subsections describe these steps in more detail.

### Step 1: Study all changes to confirmed purchase orders and their downstream impact

The purchaser first opens the **Confirmed purchase orders with changes** workspace and studies all the changes that have been submitted through the purchase order change management process. Vendors can submit these changes through several channels.

When a purchase order that was previously confirmed is changed, it's moved back to the *Approved* state. The workspace shows all purchase orders that have been changed after confirmation.

The workspace shows two lists: one for the purchase orders and one for the purchase order lines.

The purchase order list shows the purchase order number, the vendor, and the requested receipt date from the purchase order header. To view the related records, select the purchase order or vendor link in the list.

The purchase order lines list shows information about each line that has proposed changes. This information includes the item number, product name, original quantity, new quantity, original confirmed delivery date, and new confirmed delivery date. The workspace also provides a hierarchical view of any downstream impact. The **Reference** field indicates the type of downstream impact, such as a planned kanban for a production order, a sales order, or a maintenance work order.

### Step 2: Focus on changes that have a low risk of downstream impact

To take action effectively and efficiently, you typically start by focusing on low-impact changes. These changes have no known downstream impact according to the current plan.

The **Low impact changes** tile at the top of the workspace provides an AI-generated, natural-language summary of the changes that have a low risk of impact. Select the **Show** link to open the corresponding filtered view.

The purchaser reviews the changes and can then accept them by selecting individual or multiple purchase orders and then selecting **Confirm purchase orders** on the toolbar above the list. The procedure for confirming the changes is the same as the procedure for confirming a purchase order for the first time, and it supports batch processing. Any extension that's registered for purchase order confirmation will also be run.

After the selected purchase orders are reconfirmed, they're moved back to the *Confirmed* state.

### Step 3: Review changes that have a high risk of downstream impact

The purchaser will spend more time on changes that have a high risk of downstream impact. These changes have downstream orders allocated to them, and the downstream impact has been identified.

The **High impact changes** tile provides an AI-generated, natural-language summary of the changes that have a high risk of impact. Select the **Show** link to open a filtered view where you can focus on those impacts and take action.

> [!NOTE]
> Only direct downstream impacts are considered. Indirect downstream impacts, such as product work that depends on other production work, aren't yet considered.

From this view, you can contact a vendor via email or Microsoft Teams. The system uses the contact details of the vendor contact person to generate proposed message text and add it to a new email message or Microsoft Teams chat. You can then review, update, and send the message.

[<img src="media/po-change-review-highimpact-one-selected.png" alt="Screenshot of the Confirmed purchase orders with changes worskapce, where one purchase order that has changes and downstream impact is selected." title="Screenshot of the Confirmed purchase orders with changes worskapce, where one purchase order that has changes and downstream impact is selected" width="720" />](media/po-change-review-highimpact-one-selected.png#lightbox)

After you've communicated with the vendor, you can update the order further and then send it back to the vendor for confirmation. Alternatively, you might cancel the order and plan for alternative supply.

### Step 4: Review the remaining downstream impact

After most of the order changes have been addressed, the purchaser can review the overall downstream impact of the remaining open order changes.

The **Impacted downstream orders** tile provides a summary of the downstream impact. Select the **Show** link to open a filtered view where you can focus on those impacts and take action.

In this view, you can analyze the changes from the perspective of downstream impact and identify the purchase order changes that are causing the impact. You can then take action on those purchase orders.

[<img src="media/po-change-review-downstream-impact.png" alt="Screenshot of the Confirmed purchase orders with changes worskapce, where filtering is applied to show the most pressing downstream impact by purchase order changes." title="Screenshot of the Confirmed purchase orders with changes worskapce, where filtering is applied to show the most pressing downstream impact by purchase order changes" width="720" />](media/po-change-review-downstream-impact.png#lightbox)

A good way to focus on the most pressing downstream impact is to sort and filter the list by the date of impact (the requested date in the downstream order). You can then take action by communicating with downstream stakeholders. Those stakeholders might, in turn, contact affected customers and replan the downstream orders.

## Frequently asked questions

### How does the Copilot technology work?

The system summarizes changes to purchase orders, such as changed quantities and confirmed delivery dates, and identifies downstream impacts. It uses the Text-davinci-003 generative AI model to generate natural-language change summaries and suggested content for email and Teams conversations.

### What if I'm not satisfied with the generated content?

Text that Copilot generates isn't intended to be used without manual review or supervision.

> [!NOTE]
> If inappropriate content is generated, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report/abuse?ThreatType=URL&IncidentType=Responsible%20AI&SourceUrl=https://dynamics.microsoft.com/supply-chain-management/overview/). Your feedback will help improve the functionality.
