---
# required metadata

title: Set up project resources
description: This topic provides information about setting up or requesting project resources.
author: Yowelle
manager: AnnBe
ms.date: 09/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProjProjectsListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 82022
ms.assetid: bd2fb375-84c6-428a-8e54-f0f719045898
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up project resources

[!include [banner](../includes/banner.md)]

You must set up a calendar and associate it with an employee or a worker. The calendar is used to schedule the project and the working time of the resources that are reserved for the project. During calendar setup, project managers can do resource leveling as part of resource optimization. Based on the calendar schedule, restrictions can be put on resources. You can set up a calendar on the **Calendars** page.

When you set up a worker as a project resource, you can select from workers who work in the company that you're setting up resources for. Alternatively, you can select workers from other companies in your organization. These workers are known as intercompany resources.

The following procedures explain how to set up a worker as a project resource in your company and how to set up an intercompany project resource.

## Set up a worker as a project resource

1. On the **Workers** page, in the **Workers** list, select the worker that you're adding as a project resource, and open the worker record.
2. On the Action Pane, select **Project** &gt; **Setup** &gt; **Project setup**.
3. Select a calendar, and then close the page.

You can also specify default projects for a resource as a type of pre-assignment. Pre-assignments can be used when the resource manager or project manager knows which projects the resource will be working on in advance. Pre-assignments can also be based on the request of a project sponsor or customer. To pre-assign a project, on the **Assign projects** page, on the **Projects** tab, in the **Remaining projects** list, select the appropriate project.

## Set up an intercompany resource

When you set up a worker as an intercompany resource, you must complete the setup in both the lending company and the borrowing company.

### In the lending company

1. In Finance, verify that the lending company is selected, and then complete the procedure in the previous section, "Set up a worker as a project resource."
2. On the **Intercompany accounting** page, select **New**.
3. In the **Legal entity ID** field, select the lending company. Fill in the remaining fields as appropriate, and then select **Save**.
4. On the **Transfer price** page, select **New**.
5. In the **Borrowing legal entity** field, select the appropriate company.
6. To lend the borrowing company only the resource that you created at the beginning of this section, in the **Resource** field, select the name of the resource that you created. To make all resources in the lending company available to the borrowing company, leave the **Resource** field blank.
7. On the **Project management and accounting parameters** page, on the **Intercompany** tab, set the **Enable intercompany resource scheduling and timesheets** option to **Yes**.

### In the borrowing company

- On the **Resources list** page, in the search filter, enter the name of the resource that you created for the lending company, to verify that the name is included in the resource list for the borrowing company.

## Request project resources
The functionality for project resource scheduling only lets resource managers distribute staffed resources on engagements or projects. To enable this functionality, complete the following tasks, or verify that they have been completed:

- Set up number sequences.
- Set up project management and accounting workflows.
- Enable resource request workflows.

After the preceding tasks have been completed, you can complete the following tasks as you require:

- Create a resource request from a soft-booked staffed resource.
- Monitor resource requests.
- Fulfill resource requests.
- Request a staffed resource from a WBS.
- Book resources to a project without having a request for a staffed resource.
