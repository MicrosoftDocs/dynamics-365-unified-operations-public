---
# required metadata

title: Configure a Dynamics 365 Commerce preview environment
description: This topic explains how to configure a Microsoft Dynamics 365 Commerce preview environment after it's provisioned.
author: psimolin
manager: annbe
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Configure a Dynamics 365 Commerce preview environment


[!include [banner](includes/banner.md)]

This topic explains how to configure a Microsoft Dynamics 365 Commerce preview environment after it's provisioned.

## Overview

Complete the procedures in this topic only after your Commerce preview environment has been provisioned. For information about how to provision your Commerce preview environment, see [Provision a Commerce preview environment](provisioning-guide.md).

After your Commerce preview environment has been provisioned end to end, additional post-provisioning configuration steps must be completed before you can start to evaluate the environment. To complete these steps, you must use Microsoft Dynamics Lifecycle Services (LCS), Dynamics 365 Commerce, and Dynamics 365 Retail.

## Before you start

1. Sign in to the [LCS portal](https://lcs.dynamics.com).
1. Go to your project.
1. On the top menu, select **Cloud-hosted environments**.
1. Select your environment in the list.
1. In the environment information on the right, select **Full details**.
1. Select **Login** to open a menu, and then select **Log on to environment**.
1. Make sure that the **USRT** legal entity is selected in the upper-right corner.

## Configure the point of sale in LCS

### Associate a worker with your identity

To associate a worker with your identity in LCS, follow these steps.

1. Use the menu on the left to go to **Modules \> Retail \> Employees \> Workers**.
1. In the list, find and select the following record: **000713 - Andrew Collette**.
1. On the Action Pane, select **Retail**.
1. Select **Associate existing identity**.
1. In the **Email** field to the right of **Search using email**, enter your email address.
1. Select **Search**.
1. Select the record that has your name.
1. Select **OK**.
1. Select **Save**.

### Activate Cloud POS

To activate Cloud POS in LCS, follow these steps.

1. On the top menu, select **Cloud-hosted environments**.
1. Select your environment in the list.
1. In the environment information on the right, select **Full details**.
1. Select **Login** to open a menu, and then select **Log on to Cloud Point of Sale** to open the point of sale (POS).
1. Select **Next**.
1. Sign in by using your Microsoft Azure Active Directory (Azure AD) account.
1. Under **Store name**, select **San Francisco**.
1. Select **Next**.
1. Under **Register and device**, select **SANFRAN-1**.
1. Select **Activate**. You're signed out and taken to the POS sign-in page.
1. You can now sign in to the Cloud POS experience by using operator ID **000713** and password **123**.

## Set up your site in Commerce

To start to set up your preview site in Commerce, follow these steps.

1. Sign in to the site management tool by using the URL that you made a note of when you initialized e-Commerce during provisioning (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Select the **Fabrikam** site to open the site setup dialog box.
1. Select the domain that you entered when you initialized e-Commerce.
1. Select **Fabrikam extended online store** as the default channel. (Make sure that you select the **extended** online store.)
1. Select **en-us** as the default language.
1. Leave the value of the **Path** field as it is.
1. Select **OK**. The list of pages on the site appears.

## Enable jobs in Retail

To enable jobs in Retail, follow these steps.

1. Sign in to the environment (HQ).
1. Use the menu on the left to go to **Retail \> Inquiries and reports \> Batch jobs**.

    The remaining steps of this procedure must be completed for each of the following jobs:

    * Process retail order email notification
    * Product availability
    * P-0001
    * Synchronize orders job

1. Use the Quick Filter to search for the job by name.
1. If the status of the job is **Withhold**, follow these steps:

    1. Select the record.
    1. On the Action Pane, on **Batch job** tab, select **Change status**.
    1. Select **Waiting**, and then select **OK**.

### Run full data synchronization in Retail

To run full data synchronization in Retail, follow these steps.

1. Use the menu on the left to go to **Modules \> Retail \> Headquarters setup \> Retail scheduler \> Channel database**.
1. In the list on the left, the **Default** channel is selected. Select the other available channel. This channel is named **scXXXXXXXXX**.
1. On the Action Pane, select **Full data sync**.
1. Enter **9999** as the distribution schedule.
1. Select **OK**.
1. Select **OK**.

### Test credit card information to do test purchases

To perform test transactions on the site, you can use the following test credit card information:

- **Card number:** 4111-1111-1111-1111
- **Expiration date:** 10/20
- **Card verification value (CVV) code:** 737

> [!IMPORTANT]
> Never, under any circumstances, try to use actual credit card information on the test site.

## Next steps

After the provisioning and configuration steps are completed, you're ready to evaluate your preview environment. Use the URL of the Commerce site management tool to go to the authoring experience. Use the URL of the Commerce site to go to the retail customer site experience.

To configure optional features for your Commerce preview environment, see [Configure optional features for a Commerce preview environment](cpe-optional-features.md).

## Additional resources

[Dynamics 365 Commerce preview environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce preview environment](provisioning-guide.md)

[Configure optional features for a Dynamics 365 Commerce preview environment](cpe-optional-features.md)

[Dynamics 365 Commerce preview environment FAQ](cpe-faq.md)

[Microsoft Lifecycle Services (LCS)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](https://docs.microsoft.com/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)
