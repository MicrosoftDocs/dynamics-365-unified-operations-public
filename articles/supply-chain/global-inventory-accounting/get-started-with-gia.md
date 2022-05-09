---
title: Get started with Global Inventory Accounting
description: This topic describes how to get started with Global Inventory Accounting.
author: JennySong-SH
ms.date: 06/18/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
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
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!--KFM: Preview until 4/30/2022 -->

Global Inventory Accounting lets you do multiple inventory accountings in the Global Inventory Accounting ledgers that you've set up. You must associate each Global Inventory Accounting ledger with a *convention*. A convention is a collection of the following types of accounting policies:

- Cost object
- Input measurement basis
- Cost flow assumption
- Cost element

> [!NOTE]
> Even after you turn on Global Inventory Accounting, you can still do inventory accounting in Microsoft Dynamics 365 Supply Chain Management in the usual way.

Global Inventory Accounting is an add-in. To make its features available, you must install it from Microsoft Dynamics Lifecycle Services (LCS). You can choose to evaluate it in a test environment before you turn it on for production environments.

Global Inventory Accounting doesn't currently support all the cost management features that are built into Supply Chain Management. Therefore, it's important that you evaluate whether the set of features that is currently available will meet your requirements.

## <a name="sign-up"></a>How to get the Global Inventory Accounting public preview

> [!IMPORTANT]
> To use Global Inventory Accounting, you must have an LCS-enabled high-availability environment (not a OneBox environment). Additionally, you must be running Supply Chain Management version 10.0.19 or later.

To sign up for the Global Inventory Accounting public preview, send your LCS environment ID by email to the [Global Inventory Accounting team](mailto:GlobalInvAccount@microsoft.com). After you're approved for the program, the team will send you a follow-up email that contains a Global Inventory Accounting beta key and your service endpoints. After you receive the beta key, you can [install the add-in](#install).

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

For more information, see [Enable after environment deployment](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md#enable-after-deploy).

### Set up Dataverse

Before you set up Dataverse, add the Global Inventory Accounting service principles to your tenant by following these steps.

1. Install Azure AD Module for Windows PowerShell v2 as described in [Install Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/install-adv2).
1. Run the following PowerShell command.

    ```powershell
    Connect-AzureAD # (open a sign in window and sign in as a tenant user)

    New-AzureADServicePrincipal -AppId "7a1dd80f-c961-4a67-a2f5-d6a5d2f52cf9" -DisplayName "d365-scm-costaccountingservice"

    New-AzureADServicePrincipal -AppId "5f58fc56-0202-49a8-ac9e-0946b049718b" -DisplayName "d365-scm-operationdataservice"
    ```

Next, create application users for Global Inventory Accounting in Dataverse by following these steps.

1. Open the URL of your Dataverse environment.
1. Go to **Advanced Setting \> System \> Security \> Users**, and create an application user. Use the **View** field to change the page view to *Application users*.
1. Select **New**.
1. Set the **Application ID** field to *7a1dd80f-c961-4a67-a2f5-d6a5d2f52cf9*.
1. Select **Assign Role**, and then select *System Administrator*. If there is a role that is named *Common Data Service User*, select it too.
1. Repeat the preceding steps, but set the **Application ID** field to *5f58fc56-0202-49a8-ac9e-0946b049718b*.

For more information, see [Create an application user](/power-platform/admin/create-users-assign-online-security-roles#create-an-application-user).

If the default language of your Dataverse installation isn't English, follow these steps.

1. Go to **Advanced Setting \> Administration \> Languages**.
1. Select *English* (*LanguageCode=1033*), and then select **Apply**.

## <a name="install"></a>Install the add-in

Follow these steps to install the add-in so that you can use Global Inventory Accounting.

1. [Sign up](#sign-up) for the Global Inventory Accounting public preview.
1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index).
1. Go to **Preview feature management**.
1. Select the plus sign (**+**).
1. In the **Code** field, enter your add-in beta key for Global Inventory Accounting. (You should have received your beta key by email when you signed up.)
1. Select **Unblock**.
1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. Go to **Power Platform Integration**, and select **Setup**.
1. In the **Power platform environment setup** dialog box, select the checkbox, and then select **Setup**. Typically, setup takes between 60 and 90 minutes.
1. After setup of the Microsoft Power Platform environment is completed, on the **Environment add-ins** FastTab, select **Install a new add-in**.
1. Select **Global inventory accounting**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that Global Inventory Accounting is being installed. After a few minutes, the status should change from *Installing* to *Installed*. (You might have to refresh the page to see this change.) At that point, Global Inventory Accounting is ready to use.

## Set up the integration

Follow these steps to set up the integration between Global Inventory Accounting and Supply Chain Management.

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Feature Management**.
1. Select **Check for updates**.
1. On the **All** tab, search for the feature that is named *(Preview) Global inventory accounting*.
1. Select **Enable now**.
1. Go to **Global inventory accounting \> Setup \> Global inventory accounting parameters \> Integrations parameters**.
1. In the **Data service endpoint** and **Global inventory accounting endpoint** fields, enter the URLs from the email that the Global Inventory Accounting team sent when you signed up for the preview.

Global Inventory Accounting is now ready to use.
