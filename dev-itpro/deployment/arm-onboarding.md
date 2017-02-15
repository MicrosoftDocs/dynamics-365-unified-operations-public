---
# required metadata

title: Azure Resource Manager onboarding
description: This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. 
author: kfend
manager: AnnBe
ms.date: 2016-08-17 02 - 29 - 41
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 141093
ms.assetid: bbf16514-70b3-4b09-9756-ea687c1241a2
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.dyn365.intro: Aug-16
ms.dyn365.version: Platform update 2

---

# Azure Resource Manager onboarding

This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. 

To deploy Azure Resource Manager (ARM) topologies, which include platform update 2 (August 2016), you must complete the ARM onboarding process for your connectors. To start the onboarding process, you require these things:

-   The Microsoft Azure subscription ID that you are deploying to **Note:** This subscription must be visible on the [old Azure portal](https://manage.windowsazure.com).
-   Ownership of the Azure subscription, or access to the subscription owner, to add contributor workflows through the Upload Management certificate **Note:** The Azure subscription must be owned by an Office 365 tenant
-   The tenant administrator, to work through the admin consent workflow

The following procedure must be completed by the administrator of the tenant.

1.  In Microsoft Dynamics Lifecycle Services (LCS), on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2.  On the **Project settings** page, on the **Azure connectors** tab, in the **Organization list** group, click **Authorize** to start the ARM Contributor workflow. This workflow sets up permissions for the Deployment Service Unit (DSU) to deploy to your subscription on your behalf.
3.  On the **Grant admin consent** page, click **Authorize**, and then, on the next page, click **Accept**. After you've accepted, the authorization is shown as completed.
4.  Return to the **Project** page, and then, in the **Environments** section, under **Azure connectors**, click **Add**.
5.  Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager** option to **Yes**. Then click **Next**.
6.  On the **Microsoft Azure setup** page, click **Download**. Make a note of the location of the downloaded certificate file, because you will use this information to upload the certificate to the Azure subscription.
7.  Open the [old Azure portal](https://manage.windowsazure.com), and then, in the left pane, click **Settings**.
8.  Filter to the Azure subscription that is used, and then, on the **Management Certificates** tab, click **Upload**.
9.  Select the management certificate that you downloaded in step 6, and then click **OK**.
10. Return to the LCS **Project** page, and click **Next**.
11. On the **Microsoft Azure setup** page, select the region to deploy to, and then click **Connect**.
12. After you're connected, you're directed to the Contributor workflow. Before you click **Next**, open the [new Azure portal](https://portal.azure.com), and complete the following steps. These steps include assigning the **Contributor** role for the application, **Dynamics Deployment Services \[wsfed-enabled\]**.
    1.  In the [new Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then click the line item. On the right-side of the page, click **All settings**.
    2.  In the **User settings** pane, click **Add**, select **Contributor**, and then click **OK**.
    3.  In the **Add users** pane, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**, and then click **Select**.
    4.  On the **Add access** page, click **OK**. The **Users** page opens, and you can see that the user is assigned as a **Contributor**.

13. Return to the LCS **Project** page, and click **Next** for the Contributor workflow. The ARM onboarding flow should now be completed, and you should see that the subscription has been added to the **Azure connectors** list.


