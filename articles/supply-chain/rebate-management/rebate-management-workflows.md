---
# required metadata

title: Rebate management deal workflows
description: This topic explains how to set up a Rebate management deal workflow to make it possible to approve and activate deals
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WorkflowTableListPageRnr
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management deal workflows

[!include [banner](../includes/banner.md)]

Rebate management uses the same workflow platform to approve rebate deals as for other Finance and Operations apps. Each workflow has two job processes associated with it:

- One element of the workflow activates the deal so that the user/workflow process can approve the transactions.
- One element of the workflow approves the deal.

Before you can use a Rebate management deal, the deal must first be active in the module. To make it possible to activate a deal, you must create and configure a *Rebate management deal workflow*.

When a workflow is activated for Rebate management, users cannot manually approve deals; the workflow must be always used.

## Create and manage Rebate management deal workflows

To work with your Rebate management deal workflows, go to **Rebate management \> Setup \> Rebate management workflows**. From here you can view, create, and update workflows as needed. Only one workflow of this type can be active at a time. For more information about workflows, how to work with this page, and how to create workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md) and its related topics.

## Use a workflow to activate a deal

To activate a deal through a workflow, open the deal (for example, on the **All rebate management deals** page). Then, from the Action Pane, select **Workflow \> Submit**. Once the new deal has been processed and approved through the workflow, it will then be activated and ready for use.

Once a deal has been activated it is not possible to alter the setup of that deal. If you need to change an activated deal, deactivate it and then create a new one (possibly by starting with a copy of the original one if the new one is similar).

<!-- KFM: Let's add something about how to deactivate a deal. I guess it fits here. -->