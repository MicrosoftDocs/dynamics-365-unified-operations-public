---
title: Architecture and design considerations for the mobile platform
description: Learn about architecture and design considerations for the mobile platform, including an overview on understanding navigation in the mobile app.
author: jasongre
ms.author: jasongre
ms.topic: overview
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Architecture and design considerations for the mobile platform

[!include [banner](../../includes/banner.md)]
[!include [mobile app deprecated](../../includes/mobile-app-deprecation-banner.md)]

The mobile app communicates with Application Object Server (AOS) to get the metadata for the mobile workspaces (and the pages and the fields that appear on the page), and to get the data for the fields on the pages. Each time that the mobile app requests data for a page, AOS creates a new session that uses the context of the user who is using the mobile app. AOS then uses the user's context to open the corresponding forms by using the corresponding menu items. AOS can open multiple forms in quick succession and perform actions on those forms, such as filtering, opening FactBoxes, changing tab pages, and clicking buttons. Any business logic on the forms also runs as usual. Through that process, AOS collects the data values from the requested fields and then sends that data back to the mobile app.

:::image type="content" source="media/mobilearchitecture.png" alt-text="Screenshot of the mobile architecture.":::

The mobile app platform doesn't assume connectivity to finance and operations apps. Activities such as navigation, data view, and data entry don't require server connectivity after data is cached.

## Understanding navigation in the mobile app

Navigation in the mobile app consists of four simple concepts: the dashboard, workspaces, pages, and actions.

:::image type="content" source="media/mobilephoneapp1.png" alt-text="Screenshot of navigation concepts in the mobile app.":::

- When you start the app, you land on the **dashboard**. On the **dashboard**, you can see a list of **workspaces** that are published in your environment.
- In each **workspace**, you can see a list of **pages** that are available for that workspace.
- On a **page**, you can view data that is collected from one or more forms.
- From a **page**, you can navigate to other **pages** for related data, such as an entity details or lines.
- On a **page**, you can see a list of **actions** that are available for that page.
- **Actions** let you create or edit existing data.

> [!NOTE]

At any time, you can pull-to-refresh in the mobile app to make the mobile app update its data or metadata. After you edit an existing workspace or publish a workspace, be sure to pull-to-refresh in the mobile app, in either the list of workspaces (if you added a workspace or business logic) or the list of pages (if you modified a page or an action). All users can see published workspaces. In Platform update 3, menu item security automatically hides pages that the user doesn't have access to. If a user doesn't have access to any pages in a workspace, the workspace itself is hidden.

## Using the mobile app designer

The mobile app designer lets you select the specific data fields from forms that appear in the mobile app.

**You can create a mobile workspace through the designer, by using X++ attribute APIs, or by using a combination of both. For more information about using X++ APIs for building a mobile workspace, see [Configure workspaces by using the SysAppWorkspace class](scenarios/mobile-workspace-configuration.md).**

:::image type="content" source="media/mobileappdesigner.png" alt-text="Screenshot of the mobile app designer.":::

1. Open the client.
1. Go to **Settings** &gt; **Mobile app**.
1. Create a new workspace, or select an existing workspace to edit.
1. Specify the name of the workspace, an icon, and a color.
1. Add pages to the workspace, or edit an existing page.
1. Specify the name of the page.
1. Select **Select Fields** to choose the data fields to add to the page.
1. Open the forms that have the data fields that you want to add, and then select the yellow plus sign (+) that appears next to the fields. The fields are added in the order that you select them in. You can add fields from multiple forms, in any order.
1. When you finish selecting fields, select **Done**.
1. If you add a field list to the page, you see that the **List** type is specified for one of the items in the field list. You can optionally add a details page for items in that list by following these steps:
    1. Select the list by clicking on it in the designer.
    1. Select **Add details page**.
    1. Repeat steps 6 through 10 as you require.

### Refreshing the app after you make changes

| Type of change     | Description                      |
|-------|----------------------------------------------|
| New workspaces, deleted workspaces, or changes to the name, color, or icon of a workspace | Pull-to-refresh from the main landing page (dashboard) of the app, where you see the list of workspaces.<br>:::image type="content" source="media/refreshworkspaces.png" alt-text="Screenshot of pull-to-refresh from the dashboard."::: |
| All other changes (new or changed pages or actions, or changes to business logic)         | Pull-to-refresh from the workspace that has the edited pages or actions.<br>:::image type="content" source="media/refreshpages.png" alt-text="Screenshot of pull-to-refresh from a workspace.":::                                             |

### Additional resources

[Page design guidelines](page-design-guidelines.md)

[Action design guidelines](action-design-guidelines.md)

[Form design requirements](form-design-requirements.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
