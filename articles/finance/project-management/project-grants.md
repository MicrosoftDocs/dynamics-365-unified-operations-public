---
# required metadata

title: Project grants
description: This topic explains how to create or modify a grant. 
author: RadhikaRS
manager: AnnBe
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15

---

# Project grants

[!include [banner](../includes/banner.md)]

A grant is a gift of money for a specific purpose or project. Usually, there are restrictions on how a grant can be spent. In Project management and accounting, you can enter and track grants, and define their relationships to projects and project contracts. For example, you can perform the following tasks:

- Associate grants with projects and funding sources through links to the **Project** and **Project contract details** pages.
- Enter and track changes to a grant as it moves from one status to another.
- Enter and track costs, requested amounts, and awarded amounts.
- Create master grants, and associate subgrants with them.

You can create a grant by entering all the details in a new record, or you can copy the details from an existing grant and then update them.

## Create a new grant

1. Go to **Project management and accounting** \> **Grants** \> **Grants**.
2. Select **New** \> **Grant**.
3. On the grant details page, on the **General** FastTab, in the **Grant ID** field, enter an alphanumeric identifier for the grant.
4. In the **Grant name** field, enter a name for the grant.
5. In the **Description** field, add details about the new grant.

    Most of the other fields on the page are optional, and you can enter as little or as much information as you want.

    The following list describes the information that is specified on each FastTab of the grant details page:

    - **General** – Enter the grant name, status, description, purpose, and amount.
    - **Contact information** – Enter details about staff members, the department that manages the grant, and the grant customer or organization source of the grant. You can also indicate whether your organization is a pass-through entity that receives the grant and then passes it on to another recipient. Select **Add** to add contact information such as telephone numbers and email addresses for the organization that provides the grant.
    - **Dates and deadlines** – Enter dates that are related to the grant and the grant application. Examples include the application due date, the submission date, and the date when the grant is approved or rejected.
    - **Associated projects and project contracts** – You can enter information on this FastTab only if the **Grant status** field on the **General** FastTab is set to **Active** or **Awarded**. Select among the following options to complete the related task:

        - **Add funding source** – Add a new funding source for the grant. You can enter all the details now, or you can use default information and then update it later.
        - **Add project contract** – Add or update project contract information.
        - **Add project** – Add or update project details.

    - **Setup** – Enter details about matching funds, if this information is required. Many organizations that award grants require that recipients spend a specific amount of their own money or resources, to match the amount that is awarded in the grant. In the **Local project or tracking ID** field, you can enter an identifier that differs from the project identifier.

        > [!NOTE]
        > If part of the grant will be awarded to a different organization, set the **Subgrantor** option to **Yes**. For grants that are awarded in the United States, you can specify whether a grant will be awarded under a state mandate or a federal mandate.

    - **Drawdown details** – Add or update information about how often grant funds can be withdrawn, billed for, or spent.

## Create a new grant from a copy

1. Go to **Project management and accounting** \> **Grants** \> **Grants**.
2. Select **New** \> **Copy from grant**.
3. Enter an alphanumeric identifier and a name for the new grant, and then select **OK**.
4. On the grant details page, review the details of the copied grant, and make any changes that are required. Most of the fields on the page are optional.

## View or modify grant details

1. Go to **Project management and accounting** \> **Grants** \> **Grants**.
2. Select the grant to modify.
3. On the Action Pane, on the **Grant** tab, in the **Maintain** group, select **Edit**.
4. Review the grant details, and make any changes that are required.
