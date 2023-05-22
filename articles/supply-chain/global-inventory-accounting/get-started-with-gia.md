---
title: Get started with Global Inventory Accounting
description: This article describes how to get started with Global Inventory Accounting.
author: JennySong-SH
ms.date: 06/18/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Get started with Global Inventory Accounting

[!include [banner](../includes/banner.md)]

Global Inventory Accounting lets you do multiple inventory accountings in the Global Inventory Accounting ledgers that you've set up. You must associate each Global Inventory Accounting ledger with a *convention*. A convention is a collection of the following types of accounting policies:

- Cost object
- Input measurement basis
- Cost flow assumption
- Cost element

> [!NOTE]
> Even after you turn on Global Inventory Accounting, you can still do inventory accounting in Microsoft Dynamics 365 Supply Chain Management in the usual way.

Global Inventory Accounting is an add-in. To make its features available, you must install it from Microsoft Dynamics Lifecycle Services (LCS). You can choose to evaluate it in a test environment before you turn it on for production environments.

Global Inventory Accounting doesn't currently support all the cost management features that are built into Supply Chain Management. Therefore, it's important that you evaluate whether the set of features that is currently available will meet your requirements.

## <a name="sign-up"></a>How to get the Global Inventory Accounting add-in

> [!IMPORTANT]
> To use Global Inventory Accounting, you must have an LCS-enabled high-availability environment (not a OneBox environment). Additionally, you must be running Supply Chain Management version 10.0.19 or later.

### Supply Chain Management version 10.0.19 to 10.0.26

To install Global Inventory Accounting for Supply Chain Management version 10.0.19 to 10.0.26, start by [installing the add-in](#install). Then send your LCS environment ID and company name by email to the [Global Inventory Accounting team](mailto:GlobalInvAccount@microsoft.com). The team will send you a follow-up email that contains your Global Inventory Accounting service endpoints.

### Supply Chain Management version 10.0.27 and later

To install Global Inventory Accounting for Supply Chain Management version 10.0.27 and later, just [install the add-in](#install). For these versions of Supply Chain Management, the Global Inventory Accounting service endpoints will be set up automatically, so you don't need to find them manually. If you do experience any issues while setting up the add-in, please contact the [Global Inventory Accounting team](mailto:GlobalInvAccount@microsoft.com).

## Licensing

Global Inventory Accounting is licensed together with the standard features of inventory accounting that are available for Supply Chain Management. You don't have to purchase an additional license to use Global Inventory Accounting.

## Prerequisites

### Set up Microsoft Power Platform integration

Before you can enable add-in functionality, you must integrate with Microsoft Power Platform by following these steps.

1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. In the **Power Platform Integration** section, select **Setup**.
1. In the **Power platform environment setup** dialog box, select the checkbox, and then select **Setup**. Typically, setup takes between 60 and 90 minutes.
1. After setup of the Microsoft Power Platform environment is completed, the page shows the name of your environment. Additionally, the **Power Platform Integration** section shows the statement, "Power Platform environment setup is complete." Global Inventory Accounting doesn't require a dual-write application.

For more information, see [Enable Power Platform Integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md), and follow the steps to connect either to a new Power Platform environment or to an existing Dataverse instance that you already manage.

## <a name="install"></a>Install or update the add-in and solution

Use the following procedure to install or update the Global Inventory Accounting add-in and solution. The part of the procedure you should follow depends on whether you are installing for the first time or just need to update the solution for an existing installation.

- If you have never installed the add-in before, follow the full procedure to install both the add-in and the solution.
- If you are already using Global Inventory Accounting but need to update the solution in the [Power Platform admin center](https://admin.powerplatform.microsoft.com), then do step 6 only and skip all of the other steps.

To install or update the add-in and solution:

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index).
1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. Go to **Power Platform Integration** and select **Setup**.
1. In the **Power platform environment setup** dialog box, select the checkbox, and then select **Setup**. Typically, setup takes between 60 and 90 minutes.
1. After the Microsoft Power Platform environment setup is complete, sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com) and then install or update the Global Inventory Accounting solution by doing the following steps:
   1. Select the environment where you want to install or update the solution.
   1. Select **Dynamics 365 apps**.
   1. Select **Install App**.
   1. Select **Dynamics 365 Global Inventory Accounting**.
   1. Select **Next** to install.
1. After the solution is completely installed, go back to LCS environment. On the **Environment add-ins** FastTab, select **Install a new add-in**.
1. Select **Global inventory accounting**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that Global Inventory Accounting is being installed. After a few minutes, the status should change from *Installing* to *Installed*. (You might have to refresh the page to see this change.) At that point, Global Inventory Accounting is ready to use.

If the default language of your Dataverse installation isn't English, follow these steps:

1. Go to **Advanced Setting \> Administration \> Languages**.
1. Select *English* (*LanguageCode=1033*), and then select **Apply**.

## Set up the integration

Follow these steps to set up the integration between Global Inventory Accounting and Supply Chain Management.

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Feature Management**.
1. Select **Check for updates**.
1. On the **All** tab, search for the feature that is named *Global inventory accounting*.
1. Select **Enable now**.
1. Go to **Global inventory accounting \> Setup \> Global inventory accounting parameters \> Integrations parameters**.
1. Depending on which version of Supply Chain Management you're running, do one of the following steps:
    - **Supply Chain Management version 10.0.19 to 10.0.26**: In the **Data service endpoint** and **Global inventory accounting endpoint** fields, enter the URLs that were sent to you by email from the Global Inventory Accounting team (see also [How to get the Global Inventory Accounting add-in](#sign-up)).
    - **Supply Chain Management version 10.0.27 and newer**: You don't need to enter the endpoints, so you can skip this step.

Global Inventory Accounting is now ready to use.
