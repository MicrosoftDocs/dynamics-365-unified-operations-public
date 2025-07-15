---
title: Overview of the default dashboard in finance and operations apps
description: Learn about the default dashboard in finance and operations apps that can be used as the basic navigation hub and how to personalize it.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.topic: overview
ms.date: 04/25/2025
ms.update-cycle: 1095-days
audience: Application User
ms.search.region: Global
ms.search.form: DefaultDashboard, SysUserSetup, WorkflowWorkListAssignedToMe
ms.custom: bap-template
ms.collection:
  - evergreen
---

# Default dashboard

[!include [banner](../includes/banner.md)]

This article describes the purpose and use cases for the default dashboard, its content (such as app tiles and workspaces), and how to personalize it.

:::image type="content" source="media/default-dashboard.png" alt-text="The default dashboard as it appears to an administrator." lightbox="media/default-dashboard.png":::

The default dashboard is a [dashboard](../../dev-itpro/user-interface/page-navigation.md#dashboard) page that is set as each user's [initial page](set-users-initial-page.md) by default. It comes preconfigured with a set of useful components that help you navigate to workspaces and other useful pages in the application. You'll only see components, such as workspaces and apps, that you have permission to access.

The default dashboard can be customized to show additional information or hide components. You can also [personalize it to match your own preferences](../../dev-itpro/get-started/personalize-user-experience.md).

## Out-of-the-box components in the default dashboard

The components that are included by default on the default dashboard are:

- A page header representing the current legal company.
- An **Apps** area that provides quick access to apps.
- A **Workspaces** area that provides quick access to workspaces.
- A search field for finding people.
- A calendar where you can set the current session date.
- A list of workflow work items assigned to you.

## Page header

The page header presents, by default, the name of the current legal entity and the default dashboard image. You can change the dashboard image to a [different banner or a logo](../get-started/tasks/change-banner-or-logo.md).

## Related apps

The **Apps** area shows tiles for finance and operations apps available to you so you can launch them quickly. It can also show links to documentation about how to set up the application.

## Workspaces

The **Workspaces** area shows one tile for each workspace that's available to you. Workspace tiles can also highlight information that you have pinned to the dashboard. To pin information to the dashboard, open the relevant workspace, right-click on a tile in the workspace, select **Personalize: &lt;tile name&gt;** and then select the **Pin to dashboard** checkbox (clear this checkbox to remove the information from your Immersive Home).

## People search

The **Search people** field helps human resource workers quickly find and access details about personnel in the **People** workspace of the [Dynamics 365 Human Resources](../../../human-resources/welcome.md) app.

## Session date picker

The session date picker lets you quickly change the current session date, which is relevant for many financial transaction functions. The picker component is a quick alternative to using the [Session date and time module](../../fin-ops/organization-administration/tasks/change-date-session.md).

## Assigned workflow items

The **Work items assigned to me** area presents a view of all work items that were generated and assigned to you from a workflow. The list provides an overview and links to the relevant pages where you can take action.

Learn more in the [Workflow system overview](../organization-administration/overview-workflow-system.md).
