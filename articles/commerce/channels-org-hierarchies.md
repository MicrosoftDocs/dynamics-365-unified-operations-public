---
# required metadata

title: Organizational hierarchies overview
description: This topic presents an overview of Microsoft Dynamics 365 Commerce organizational hierarchies.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---
# Organizational hierarchies overview

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
* Go to **Navigation pane** > **Modules** > **Retail** > **Channel Setup** > **Organization hierarchies**.
* On the **Action pane**, click **New**.
* In the **Name** field, type a value.
* In the **Purpose** section, click **Assign purpose**.
* In the list, find and select the desired record. Select a purpose to assign to your organization hierarchy.
* In the **Assigned hierarchies** sectiom, click **Add**.
* In the list, mark the selected row. Find the hierarchy you just created.
* Click **OK**.

Below is a sample organizational hierarchy created for a ficticious "Adventure Works" set of stores.

![Example organizational hierarchy](media/organizational-hierarchies.png)

### Add organizations to the hierarchy
* In the list, find and select the desired record. Select your hierarchy.
* On the **Action pane**, click **View**.
  * Add organizations, as necessary.
  * To add an organization, click **Edit** and then **Insert** to add the organization. When you are done making changes you can **Save** a draft and/or **Publish** the changes.

In the below screen shot, a legal entity was added at the hierarchy root with four cost centers added for "Mall", "Outlet", "Online" and "Call Center" channels.  Various retail, call center and online channels can then be added to each.

![Example hierarchy designer](media/hierarchy-designer.png)
