---
title: Invoice approvals mobile workspace
description: Learn about the Invoice approvals mobile workspace, including prerequisites and outlines and how to download and sign into the mobile app.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/21/2025
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form:
ms.dyn365.ops.version: July 2017 update 
---

# Invoice approvals mobile workspace

[!include [banner](../../../finance/includes/banner.md)]
[!include [mobile app deprecation](../../dev-itpro/includes/mobile-app-deprecation-banner.md)]

This article provides information about the **Invoice approvals** mobile workspace. This workspace provides a list of invoices that you receive through the vendor invoice header workflow process. 

Use this mobile workspace with the finance and operations mobile app.

## Overview

The **Invoice approvals** mobile workspace lets Accounts payable clerks and managers view invoices that the vendor invoice header workflow process assigns to them. You can view the invoice information, and even the line and distribution details, to help you make informed approval decisions. From the workspace, you can take action to move the invoice through the workflow process. 

## Prerequisites

Before you can use this mobile workspace, the following prerequisites must be met.

| Prerequisite | Role | Description |
|---|---|---|
| Microsoft Dynamics 365 Finance must be deployed in your organization. | System administrator | See [Deploy a demo environment](../../dev-itpro/deployment/deploy-demo-environment.md). |
| The **Invoice approvals** mobile workspace must be published. | System administrator | See [Publish a mobile workspace](../../dev-itpro/mobile-apps/publish-mobile-workspace.md). |

## Sign in to the mobile app

1. Start the app on your mobile device.
1. Enter your Microsoft Dynamics 365 URL.
1. The first time that you sign in, you're prompted for your user name and password. Enter your credentials.
1. After you sign in, the app shows the available workspaces for your company. If your system administrator publishes a new workspace later, you need to refresh the list of mobile workspaces.

    :::image type="content" source="../../dev-itpro/mobile-apps/media/pull-to-refresh-list-of-workspaces-183x300.png" alt-text="Screenshot of pull to refresh functionality.":::

## Approve invoices by using the Invoice approvals mobile workspace

1. On your mobile device, select the **Invoice approvals** workspace.
1. Select the invoice that the vendor invoice header workflow process assigned to you.
1. On the **Invoice details** page, review the invoice header information, such as the vendor and date information.
1. Select a line on the invoice to view more detailed information about it in the **Invoice line details** view.
1. In the **Invoice line details** view, select **Distributions** to show the line distributions. Here, you can view the accounting for the invoice line. The information that is shown includes the financial dimensions and the main account.
1. On the **Invoice details** page, select **Distributions** to show all distributions. Here, you can view the accounting for the whole invoice. The information that is shown includes the financial dimensions and the main accounts. 
1. Select **Attachments** to view any notes or files that are attached to the invoice.
1. On the **Invoice details** page, select the appropriate workflow action to complete your review process.
1. Select **Done**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]