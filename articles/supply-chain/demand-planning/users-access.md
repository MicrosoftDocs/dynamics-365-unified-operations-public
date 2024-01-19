---
title: Security roles and access control in Demand planning (preview)
description: This article describes how to set up users, security roles, and access rules for the Demand planning app. It explains how to configure security roles and duties in Supply Chain Management and how to assign security roles for accessing the app on Power Platform. It also explains how to set up row-level accessing data within the Demand planning app.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: M01/19/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Security roles and access control in Demand planning (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article describes how to set up users, security roles, and access rules for the Demand planning app. It explains how to configure security roles and duties in Supply Chain Management and how to assign security roles for accessing the app on Power Platform. It also explains how to set up row-level accessing data within the Demand planning app.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Configure security roles and duties in Supply Chain Management

Demand planning features in Supply Chain Management are available only to users who have the required security roles and related duties. When you [enable Demand planning in Supply Chain Management](install-demand-planning.md), the feature adds a privilege named *Demand planning informational tile*. This privilege grants users access to a button that opens the Demand planning app from the home page of Supply Chain Management. The privilege is added to the out-of-box roles and duties that are listed in the following table. If you're using custom roles, you must manually assign the privilege to them after you enable the feature.

| Role name | Duty |
|---|---|
| Production planner | Maintain forecasts |
| Production planner | Maintain firming of planned orders |
| Production manager | Enable forecast process |
| Production planner | Maintain forecast planning |
| Production planner | Maintain demand forecasts |
| Sales manager | Maintain demand forecast |
| Production manager | Enable the demand planning process |

The feature also adds a new system role and user. A record inserted into the Microsoft Entra ID application enables data to be exchange between Demand planning and Supply Chain Management. <!-- KFM: What is this referring to? Can we name the new role and user? Or is this talking about the role in Power Platform (described in the next section)?-->

## Assign security roles for accessing the app on Power Platform

When you install Demand planning on Power Platform, it creates several new security roles to control access to its various features. To be able to access the Demand planning app, users must sign in a Power Platform user account that has the security roles for the features they need.

The following security roles are available for Demand planning: <!-- KFM: Are these all unique to DP, or are some standard (eg, Basic User and System Administrator) -->

- **Basic User** <!-- KFM: Mentioned in the video. Details needed -->

- **System Administrator**  
    - Install the app, add users, assign roles, manage teams, and so on.
    - View, create, and manage tables, relations, and data
    - Create and manage imports and exports
    - View and create transformations based on requests from the demand planning manager
    - Monitor jobs (imports, calculations, forecasts, transformations, and exports)

- **Demand Planning Manager**
    - Configure the demand planning app (role-level security, time fences, worksheets)
    - View and create planning data (forecasts and calculations)
    - View and create tables and import data from excel
    - View and create transformations
    - View and create worksheets
    - Export plans when they're ready to share with Supply Chain Management

- **Demand Planning Contributor**
    - View worksheets (see shared worksheets and save their own views)
    - Controlled by row-level access and can edit data they have access to
    - Collaborate using Microsoft Teams and in-app comments

- **Demand Planning Service Role** <!-- KFM: Do we still have this? How shall we describe it? -->

Use the Power Platform admin center to set up user accounts and assign security roles to them as needed. For more instructions, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).

## Set up row-level accessing data within the Demand planning app

Users who have the *Demand Planning Contributor* role (but not *Demand Planning Manager* or *System Administrator*) can access the Demand planning app, but they can only view and edit data that they're granted access to. You control this access using *row-level security*, which is set up in the Demand planning app. For example, a user might only be granted access to the specific products or product families they manage; or they might be restricted to only viewing data for a specific site or warehouse. By default, demand planning contributors can't see any data until they are granted access to it by a row-level access rule.

To set up row-level security, follow these steps:

1. Sign in to the Demand planning app using a system admin account.
1. On the navigation pane, select **Configuration** \> **Row level access**.
1. Do one of the following steps:
    - To add a new row-level access rule, select **New** from the top toolbar. This launches a setup wizard, where each page of the wizard maps to a tab in the edit dialog.
    - To edit an existing row-level access rule, select the rule in the list, and then select **Edit** from the grid toolbar.
1. On the **Crate rule** tab or wizard page, make the following settings:
    - **Name** – Enter a name for the rule.
    - **Description** – Enter a description for the rule.
1. On the **Conditions** tab or wizard page, set up the logic for which data tables and columns the rule grants access to. Use the buttons to add or remove conditions as needed. The following rules apply:
    - If you have more than one condition line, then the lines are combined with an AND operator, which means that users will only have access to data rows where all of the condition lines are true.
    - You can select more than one value in the **Value** field for each condition. These values are combined with an OR operator, which means that the condition line evaluates to true for data rows where any of the values are true.
1. On the **Users** tab or wizard page, add each user for whom the current row level access rule applies. If you assign the same user to multiple rules, then the user will have access to data rows that are granted by any of the rules (an OR operator is applies across rules).
1. On the **Activation** tab or wizard page, set **Activation** to *Active* or *Inactive*, as needed. Only active rules take effect, but you might set a rule to inactive if you're still working on it or if you want to temporarily disable it without deleting it.
