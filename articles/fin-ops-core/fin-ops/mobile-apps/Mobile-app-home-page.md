---
title: Mobile app home page
description: Learn about the finance and operations (Dynamics 365) mobile app and provides links to resources that can help you implement it in your organization.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/21/2025
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4
ms.assetid: c99f818f-27b3-4e45-92b4-74272dad0e17
---

# Mobile app home page

[!include [banner](../../../finance/includes/banner.md)]
[!include [mobile app deprecation](../../dev-itpro/includes/mobile-app-deprecation-banner.md)]

This article describes the **Finance and operations (Dynamics 365)** mobile app and provides links to resources that can help you implement it in your organization.

## Overview

The mobile app enables your organization to make its business processes available on mobile devices. After your IT admin enables the mobile workspaces for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices. The mobile app includes the following features that can help increase productivity:

- Users can view, edit, and act on business data, even if they have intermittent network connectivity or their mobile devices are offline. When a device reestablishes a network connection, offline data operations are automatically synchronized.
- IT admins or developers can build and publish mobile workspaces that are tailored to their organization. The app uses your existing code assets. Therefore, you don't have to reimplement your validation procedures, business logic, or security configuration.
- IT admins or developers can easily design mobile workspaces by using the point-and-click workspace designer that's included with the web client.
- IT admins or developers can optionally optimize the offline capabilities of workspaces by using the Business logic extensibility framework. Because data continues to be processed while a device is offline, your mobile scenarios remain rich and fluid, even if devices don't have constant network connectivity.

## Elements of the mobile app
Navigation in the mobile app consists of four basic concepts: the dashboard, workspaces, pages, and actions. 

:::image type="content" source="../../dev-itpro/mobile-apps/media/mobilephoneapp1-1024x536.png" alt-text="Screenshot of navigation concepts in the mobile app.":::

1. When you start the app, you go to the **dashboard**.
1. On the dashboard, you can see a list of **workspaces** that are published.
1. In each workspace, you can see a list of **pages** that are available for that workspace.
1. After you're on a page, you can perform several actions. Here are some examples:

    - View detailed data.
    - Navigate to other pages for related data, such as entity details or lines.
    - See a list of **actions** that are available for that page. Actions let you create or edit existing data.

## Implementation process
The following illustration shows the process for implementing both mobile workspaces that are provided by Microsoft and custom mobile workspaces. 

:::image type="content" source="../../dev-itpro/mobile-apps/media/Mobile-implementation-process-5.png" alt-text="Screenshot of mobile apps implementation process.":::

The following table includes links to resources that can help you implement both mobile workspaces that are provided by Microsoft and custom mobile workspaces. The numbers in the first column correspond to the numbered steps in the previous illustration.

| Step | Role | Action | Resources to help you complete the action |
|---|---|---|---|
| 1 | System administrator | Implement the finance and operations app in your organization. | <ul><li>If you haven't yet deployed a version of Microsoft Dynamics 365, see [Deploy a demo environment](../../dev-itpro/deployment/deploy-demo-environment.md).</li><li>To see a list of mobile workspaces that can be used, see [Mobile workspaces recently released](mobile-workspaces-released.md).</li></ul> |
| 2 | System administrator | **If you're using Microsoft Dynamics 365 for Operations version 1611:** Download and install KBs that enable the mobile workspaces that are provided by Microsoft. | See the following articles for more information:<ul><li>[Cost controlling mobile workspaces](../../../finance/cost-accounting/cost-controlling-mobile-workspace.md)</li><li>[Inventory on-hand mobile workspace](../../../supply-chain/inventory/inventory-on-hand-mobile-workspace.md)</li><li>[Sales orders mobile workspaces](../../../supply-chain/sales-marketing/sales-orders-mobile-workspace.md)</li><li>[Vendor collaboration mobile workspace](../../../supply-chain/procurement/vendor-collaboration-mobile-workspace.md)</li><li>[Project time entry mobile workspace](/dynamics365/project-operations/prod-pma/project-time-entry-mobile-workspace)</li><li>[Expense management mobile workspace](/dynamics365/project-operations/prod-exp/expense-management-mobile-workspace)</li></ul> |
| 3 | System administrator | Publish the mobile workspaces that are provided by Microsoft. | [Publish a mobile workspace](../../dev-itpro/mobile-apps/publish-mobile-workspace.md) |
| 4 | Developer or independent software vendor (ISV) | Use the mobile platform to create custom mobile workspaces. | [Mobile platform](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md) |
| 5 | ISV | Create a deployable package that contains custom mobile workspaces, and upload the package to Microsoft Dynamics Lifecycle Services. | [Create a deployable package](../../dev-itpro/deployment/create-apply-deployable-package.md) |
| 6 | System administrator | Apply the deployable package that contains the custom workspaces that are provided by the independent software vendor (ISV). | [Apply a deployable package](../../dev-itpro/deployment/apply-deployable-package-system.md) |
| 7 | System administrator | Publish the custom mobile workspaces that are provided by the ISV. | [Publish a mobile workspace](../../dev-itpro/mobile-apps/publish-mobile-workspace.md) |
| 9 | User | Sign in, and use the mobile app. The app includes the mobile workspaces that have been published by the system administrator. | To see a list of mobile workspaces that are provided by Microsoft, see [Mobile workspaces recently released](mobile-workspaces-released.md). |

## Troubleshooting
[Mobile platform resources](../../dev-itpro/mobile-apps/platform/mobile-platform-home-page.md#troubleshooting-the-app)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

