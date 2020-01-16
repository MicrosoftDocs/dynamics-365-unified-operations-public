---
# required metadata

title: Organizational hierarchies
description: This topic presents an overview of Microsoft Dynamics 365 Commerce organizational hierarchies.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Organizational hierarchies

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents an overview of Microsoft Dynamics 365 Commerce organizational hierarchies.

## Overview

Before creating channels you'll want to ensure you have set up your organizational hierarchies.

For more information see
* [Organizations and organizational hierarchies overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies)
* [Plan your organization hierarchy](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/plan-organizational-hierarchy?toc=/dynamics365/commerce/toc.json)
* [Create an organization hierarchy](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/tasks/create-organization-hierarchy?toc=/dynamics365/commerce/toc.json)

## Create an organization hierarchy

Use the following procedure to create an organizational hierarchy. You can use organizational hierarchies to view and report on your business from various perspectives. For example, you can set up one hierarchy for tax, legal, or statutory reporting. You can then set up another hierarchy to report financial information that is not legally required, but that is used for internal reporting.

Before you create an organizational hierarchy, you must create organizations. For more information, see the [Create a new legal entity](channels-legal-entities.md) or “Create an operating unit” tasks. You can also create departments and teams.

### Create a hierarchy

To create a hierarchy, follow these steps.

1. Go to **Navigation pane** > **Modules** > **Retail** > **Channel Setup** > **Organization hierarchies**.
1. On the **Action pane**, click **New**.
1. In the **Name** field, type a value.
1. In the **Purpose** section, click **Assign purpose**.
1. In the list, find and select the desired record. Select a purpose to assign to your organization hierarchy.
1. In the **Assigned hierarchies** sectiom, click **Add**.
1. In the list, mark the selected row. Find the hierarchy you just created.
1. Click **OK**.

The following image shows an example organizational hierarchy created for a fictitious "Adventure Works" set of stores.

![Example organizational hierarchy](media/organizational-hierarchies.png)

### Add organizations to a hierarchy

To add organizations to a hierarchy, follow these steps.

1. In the list, find and select the desired record. Select your hierarchy.
1. On the **Action pane**, click **View**.
  1. Add organizations, as necessary.
  1. To add an organization, click **Edit** and then **Insert** to add the organization. When you are done making changes you can **Save** a draft and/or **Publish** the changes.

In the below screen shot, a legal entity was added at the hierarchy root with four cost centers added for "Mall", "Outlet", "Online" and "Call Center" channels.  Various retail, call center and online channels can then be added to each.

The following image shows

![Example hierarchy designer](media/hierarchy-designer.png)

## Additional resources
