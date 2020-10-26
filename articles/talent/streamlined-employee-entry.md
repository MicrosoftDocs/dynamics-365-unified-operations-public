---
# required metadata

title: Streamlined employee entry and navigation
description: Data entry for workers in Dynamics 365 Talent has been enhanced to allow quick entry for all employees, past, active or future. A simplified/consolidated navigation model has been updated to quickly find related information and view and make any necessary updates.
author: andreabichsel
manager: AnnBe
ms.date: 08/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang:   
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
ms.custom: 15681
ms.assetid: 6aee97ac-29f7-4b3c-8aa1-c65810de3090
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Talent October 2019 update

---

# Streamlined employee entry and navigation

Dynamics 365 Talent allows efficient entry of employee and employment data. You can quickly update work history information for past, active, and future employees and contractors.

You can also enable a simplified navigation experience to quickly find related information and make any necessary changes. This functionality is now available in all environments. To turn this feature on, navigate to **System administration > Feature Management > New > Streamlined employee entry > Enable**. This will enable these changes for all users. You can turn this option off at any time.

## View options

You can use **View options** on the worker form to select any combination of employees and contractors from a single list. These options allow you to view workers across legal entities or for the legal entity you're currently signed into. You can also view active, pending, and exited workers, and you can restrict results based on the type of worker (employee or contractor). If advanced security is enabled, you will only see those employees and contractors in the legal entities you have access to.

Columns in the list view change based on your selections. For example, when viewing exited employees, the termination date and reason codes display as additional columns in the list. 

[![View options](./media/Worker-view-option.png)](./media/worker-view-option.png)

## Navigation and banner

A banner displays key information for each worker. The banner for active workers displays the following fields:

- **Title**
- **Department**
- **Position type**
- **Worker type**
- **Manager**
- **Legal entity**

The banner for exited workers displays the following fields:

- **Exited date**
- **Reason**

The banner for pending employees displays the following fields:

- **Title**
- **Department**
- **Position type**
- **Manager**
- **Starting date**
- **Legal entity**

The action pane of the worker page has been re-organized to include fewer options. Information is now organized in the following categories: 

- Work
- Person
- Leave
- Compensation
- Benefits
- Compliance

In addition, a new **Links** tab on the main worker page gives users a central location to access all related information for a worker.

Due to these changes, information may appear in a different location than you're used to. For example, payroll information that previously displayed on the worker form now appears in the action pane under **Compensation > Payroll**, and the **Personal information** tab now has a **More information** button to hide fields that aren't accessed often.

[![Banner](./media/Banner.png)](./media/Banner.png)

## Work history

The **Work history** tab shows work history across all legal entities and is available for exited, active, and pending employees and contractors. You can now view all work history at once for the legal entities you have access to. In addition, you can edit information for each of the work history entries without changing the data context. You can update all information directly on the page. 

[![Work history](./media/Worker-work-history.png)](./media/Worker-work-history.png)

## Position history

The **Positions** tab on the main worker page provides a full view of all positions held within the organization, including past, present, and any future assignments. You can still navigate directly to the worker's position history in the action pane as well.

[![Positions](./media/Worker-position-history.png)](./media/Worker-position-history.png)

