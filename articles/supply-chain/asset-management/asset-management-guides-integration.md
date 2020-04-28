---
# required metadata

title: Integrate Dynamics 365 Supply Chain Management (asset management) with Dynamics 365 Guides
description: Describes how to integrate the asset management module from Dynamics 365 Supply Chain Management with Dynamics 365 Guides to take advantage of mixed reality guides in your day-to-day service and maintenance workflows
author: kamaybac
manager: tfehr
ms.date: 04/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: dabourq
ms.search.validFrom: 2020-04-28
ms.dyn365.ops.version: Release 10.0.12
---

# Integrate Dynamics 365 Supply Chain Management (asset management) with Dynamics 365 Guides

You can integrate the asset management module from Dynamics 365 Supply Chain Management with Dynamics 365 Guides to take advantage of mixed reality guides in your day-to-day service and maintenance workflows. When a guide is associated with an asset management work order, the worker can see that a guide is available through the work order's maintenance checklist in the Supply Chain Management (Dynamics 365) mobile app. The worker can then find and open the guide from the HoloLens Guides app.

## Prerequisites

To be able to attach guides to asset management work orders, you must first:

- [Set up Dynamics 365 Supply Chain Management](../../fin-ops-core/fin-ops/index.md) version 10.0.9 or later.
- [Enable dual-write for Supply Chain Management apps](../../fin-ops-core/dev-itpro/data-entities/dual-write/enable-dual-write.md).
- [Enable flight](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md#features-flighted-in-data-management-and-enabling-flighted-features) for the "MRGuidesFeature" feature. (For production environments, you must first raise a support ticket to have your tenant added to the flighting group.)
- [Enable the following configuration keys](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/license-code-and-configuration-key-reference)  in the **License Configuration** form:
  - **Asset management \> Asset management mixed reality**
  - **Mixed reality \> Mixed reality guide**
- [Set up Dynamics 365 Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup#step-2-create-a-common-data-service-environment-and-install-the-dynamics-365-guides-solution), version 200.0.0.96 or later.

## Use Dynamics 365 Guides with asset management

To associate a guide, you use a maintenance checklist line in asset management. You can create the association through a maintenance checklist template, a maintenance job type, or a work order since they all contain maintenance checklist lines. Using a template can save time since the template can be associated with all maintenance job types that use the template. For example, a guide that's associated with a maintenance job type is automatically associated with all work orders that specify that job type. On the other hand, a guide that's associated directly with a work order only exists for that specific work order.

### Associate a guide with a maintenance checklist template

To associate a guide with a maintenance checklist template:

1. Author a guide using the Dynamics 365 Guides PC and HoloLens apps. For information on authoring a guide, see:
    - [Use the PC app to create a guide](https://docs.microsoft.com/dynamics365/mixed-reality/guides/pc-app-overview)
    - [Use the HoloLens app to place your holograms](https://docs.microsoft.com/dynamics365/mixed-reality/guides/hololens-app-overview)

1. In Supply Chain Management, [create a maintenance checklist template](setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md#create-a-maintenance-checklist-template)

1. Associate a guide with a **Maintenance checklist** line in your new template by doing the following:

    1. In the **Maintenance checklist lines** section, select the line you want to associate the guide with.

    1. In the **Associated guides** section, select **Add Guide**.  
    ![Associate a guide with a maintenance checklist](media/am-guides-integration-add-guide.png "Associate a guide with a maintenance checklist")

    1. In the **Name** list, select a guide, and then select **Save**.  
    ![Select a guide from the list](media/am-guides-integration-select-guide.png "Select a guide from the list")

1. Associate the **Maintenance Checklist template** with a job type by doing the following:

    1. [Create a maintenance job type](setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md#create-a-maintenance-job-type) or select an existing one.

    1. Select **Maintenance job type defaults**.  
    ![The Maintenance job type defaults button](media/am-guides-integration-job-defaults.png "The Maintenance job type defaults button")

    1. Create a new line, and then select **Save**.  
    ![Create a new line](media/am-guides-integration-add-line.png "Create a new line")

    1. Select **Maintenance checklist**.  
    ![The Maintenance checklist button](media/am-guides-integration-maintenance-checklist.png "The Maintenance checklist button")

    1. Add a new line in the **Maintenance checklist lines** section, and then change the **Type** to **Template**.  
    ![Maintenance checklist lines](media/am-guides-integration-checklist-lines.png "Maintenance checklist lines")

    1. In the **Line details** section, select the template you associated your guide with from the list, and then select **Save**.  
    ![The Line details section](media/am-guides-integration-checklist-line-details.png "The Line details section")

1. [Create a work order](work-orders/manually-created-workorders.md#create-work-order), and then select the maintenance job type that uses the **Maintenance checklist template** that you associated the guide with. This automatically associates the guide with the work order.  
    ![Select a maintenance job type](media/am-guides-integration-create-work-order.png "Select a maintenance job type")

1. View the guide associated with the work order and workers by doing the following:

    1. Launch the [Asset management mobile workspace](asset-management-mobile-workspace.md) to access their work order.

    1. [Go to the maintenance checklist](asset-management-mobile-workspace.md#view-maintenance-checklist-on-a-work-order-job) for the work order.

    1. Select a checklist line to see the associated guide.  
    ![Select a maintenance job type](media/am-guides-integration-show-guide.png "Select a maintenance job type")

    1. Open the guide on HoloLens.  
    ![Select a maintenance job type](media/am-guides-integration-hololens-select.png "Select a maintenance job type")

> [!NOTE]
> It's also possible to associate a guide directly in the maintenance checklist of a work order, or of a job type.

> [!IMPORTANT]
> There is a known issue where when you associate a **Maintenance Checklist template** to a **Maintenance job type default**, the guide that's tied to the template does not appear under the **Associated guides** section of the **Maintenance job type defaults**. The guide will be visible once that job type is applied to a work order under the **Associated guides** section.

### See also

- [Dual-write overview](../../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview.md)
- [Asset management overview](index.md)