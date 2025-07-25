---
title: Rebate management deal workflows
description: Learn how to set up a Rebate management deal workflow to approve and activate deals with an outline on creating and managing Rebate management deal workflows.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: WorkflowTableListPageRnr
ms.topic: how-to
ms.date: 07/21/2025
ms.custom:
- bap-template
---

# Rebate management deal workflows

[!include [banner](../includes/banner.md)]

To approve rebate deals, Rebate management uses the same workflow platform as other finance and operations apps. Two job processes are associated with every workflow:

- One element of the workflow approves the deal.
- One element of the workflow activates the deal so that the user or workflow process can approve the transactions.

Before you can use a rebate deal, it must be active in the **Rebate management** module. To activate a deal, you must first create and configure a *Rebate management deal workflow*.

Users can't manually approve deals. The workflow must always be used.

## Create and manage Rebate management deal workflows

To work with your Rebate management deal workflows, go to **Rebate management** \> **Setup** \> **Rebate management workflows**. There, you can view, create, and update workflows as required. Only one workflow of this type can be active at a time. For more information about workflows, how to work with the **Rebate management workflows** page, and how to create workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md) and its related articles.

## Use a workflow to activate a deal

To activate a deal through a workflow, open the deal (for example, on the **All rebate management deals** page). Then, on the Action Pane, select **Workflow** \> **Submit**. After the new deal has been processed and approved through the workflow, it will be active and ready to use.

After a deal has been activated, you can't change most of its setup. If you must change an active deal, first deactivate it, and then create a new deal. If the new deal should resemble the old deal, you can create it by copying the old deal.

You can change the following settings for a deal after it has been activated:

- Reconcile by
- Cumulative guarantee
- Posting profile
- Posting profile for guarantee
- Document notes
- Currency
- From date
- To date

In addition, rebate lines can be removed.

## Resubmit a workflow

Sometimes, you might have to resubmit a workflow for a deal because of missing or incorrect data, an activated or updated rebate deal, modified rebate rules, or an extension of the original rebate period. To resubmit a workflow, you must first deactivate the active deal, then edit it as required, and finally reactivate it.

### Prerequisites

Before you can deactivate and resubmit workflows for vendor rebate deals, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.43 or later.
- The feature that is named *Enable resubmission of workflows for vendor rebate deals* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Deactivate and resubmit a workflow

To deactivate and resubmit a workflow for a vendor rebate deal, follow these steps.

1. Go to **Rebate management** \> **Rebate management deals** \> **All rebate management deals**.
1. Find and select the deal that you want to deactivate, edit, and resubmit. The deal must already be active.
1. On the Action Pane, on the **Rebate management deals** tab, select **Deactivate**.
1. Edit the deal as required. Here are some examples of changes that you might make:

   - Change the due date for one or more deal lines.
   - Add one or more new deal lines.
   - Add a new rebate period for an existing deal line.

1. After you finish editing the deal, on the Action Pane, select **Workflow** \> **Submit**.

The resubmission works for both customer rebates and vendor rebates.
