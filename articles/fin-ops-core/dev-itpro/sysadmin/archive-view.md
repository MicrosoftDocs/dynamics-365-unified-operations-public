---
title: View or delete archived data in Dataverse long-term retention
description: Learn about how to view or delete archived data in Microsoft Dataverse long-term retention, including an overview on viewing data by using Fabric.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 05/31/2024
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
---

# View archived data in Dataverse long-term retention

This article describes how to view archived data in Microsoft Dataverse long-term retention.

## View data by using Fabric

You can use Fabric to view both the live (active) and archived (inactive long term retained) Dynamics 365 Finance and Operations application data. To use this capability, you must link your Dataverse environment to Fabric. If the setup for the link to Fabric isn't working, follow the steps in [Link to Microsoft Fabric](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric#link-to-microsoft-fabric).

Confirm that Fabric is enabled. If it isn't enabled, go to [https://app.fabric.microsoft.com](https://app.fabric.microsoft.com/) using at least a Conditional access administrator user account. In Microsoft Fabric, select the settings gear and go to **Admin portal** > **Tenant settings**. Enable the **Users can create Fabric items** setting.

> [!NOTE]
> If you don't have a Fabric subscription, you can use a Fabric trial to access data in a Dataverse-managed Azure data lake. After the trial period expires, you must have the Fabric capacity or Premium per capacity Power BI SKU for users.

### View archived data in the Dataverse-managed data lake

To view the archived data in Dataverse, follow these steps.

1. After the archival job is completed, go to the Power Apps maker portal.
1. Select **Azure synapse** \> **Microsoft one Lake**.
1. Select **View in Microsoft Fabric**. 

The data in the Dataverse-managed data lake is available in Dataverse tables that have the "mserp\_" prefix. In Dataverse tables that have this prefix, you can use the `msft\_datastate` column to filter the data through a SQL `WHERE` clause:

- To filter for inactive (archived) application data: `WHERE msft_datastate=1`
- To filter for active (live) application data: `WHERE msft_datastate=0 or msft_datastate=NULL'

You can also access archived data by using a model-driven app that's created in Power Apps and that uses Dataverse Advanced Find. Alternatively, you can build canvas apps in Power Apps.

For information about the limitations of these options, see [Limitations for retrieval of retained data](/power-apps/maker/data-platform/data-retention-view#limitations-for-retrieval-of-retained-data).

### Delete archived data from the Dataverse-managed data lake

For information about how to delete long term retained data from the Dataverse managed data lake, see [Delete data in bulk](/power-apps/developer/data-platform/delete-data-bulk?tabs=sdk).
