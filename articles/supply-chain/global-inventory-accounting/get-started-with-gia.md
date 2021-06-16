---
title: Get started with the Global Inventory Accounting
description: This topics describes how to get started with the Global Inventory Accounting
author: AndersGirke
ms.date: 06/18/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Get started with the Global Inventory Accounting

[!include [banner](../includes/banner.md)]

Global Inventory Accounting lets you do multiple inventory accounting in the Global Inventory Accounting ledgers that you've set up. You must associate each Global Inventory Accounting ledger with a *convention*, which is a collection of the following types of accounting policies:

- Cost object
- Input measurement basis
- Cost flow assumption
- Cost element

> [!NOTE]
> Even after you've turned on Global Inventory Accounting, you can still do inventory accounting in Supply Chain Management as usual.

Global Inventory Accounting is an add-in. To make its features available, you must install it from Microsoft Dynamics Lifecycle Services (LCS). You can choose to evaluate it in a test environment before you turn it on for production environments.

Global Inventory Accounting doesn't currently support all of the cost management features that are built into Dynamics 365 Supply Chain Management. Therefore, it's important that you evaluate whether the set of features that is currently available will meet your requirements.

<a name="sign-up"></a>

## How to get the Global Inventory Accounting public preview

> [!IMPORTANT]
> To use the Global Inventory Accounting, you must have an LCS-enabled high-availability environment (not a OneBox environment), and you must be running Dynamics 365 Supply Chain Management version 10.0.19 or later.

To sign up for the Global Inventory Accounting public preview, please send your LCS environment ID by email to the [Global Inventory Accounting team](mailto:GlobalInventoryAccounting@service.microsoft.com). On approving you for the program, we will send you a follow up email that contains a Global Inventory Accounting beta key and your service end points. On receiving the beta key, you can proceed by [installing the add-in](#install).

## Licensing

Global Inventory Accounting is licensed together with the standard features of inventory accounting that are available for Supply Chain Management. You don't have to purchase an additional license to use Global Inventory Accounting.

<a name="install"></a>

## Install the add-in

To use Global Inventory Accounting, install the add-in as described in the following procedure.

1. [Sign up](#sign-up) for the Global Inventory Accounting public preview.
1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index).
1. Go to **Preview feature management**.
1. Select the plus sign (**+**).
1. In the **Code** field, enter your add-in beta key for the cost accounting service. (You should have received your key by email when you signed up.)
1. Select **Unblock**.
1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. Go to **Power Platform Integration** and select **Setup**.
1. In the **Power platform environment setup** dialog, select the check box, and then select **Setup** at the bottom of the dialog. Typically, the setup takes between 60 and 90 minutes.
1. After the Power Platform Environment setup is completed, scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Global inventory accounting**.
1. Follow the installation guide and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that Global Inventory Accounting is being installed. After a few minutes, the status should change from *Installing* to *Installed*. (You might have to refresh the page to see this change.) At that point, Global Inventory Accounting is ready for use.

## Set up the integration

To set up the integration between Global Inventory Accounting and Supply Chain Management:

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Feature Management**.
1. Select **Check for updates**.
1. Open the **All** tab and search for the feature named *Global inventory accounting*.
1. Select **Enable now**.
1. Go to **Global inventory accounting \> Setup \> Global inventory accounting parameters \> Integrations parameters**.
1. In the **Data service endpoint** and **Global inventory accounting endpoint** fields, enter the URLs that you received in the email from the Global Inventory Accounting team when you signed up for the preview.
1. Global Inventory Accounting is now ready for use.
