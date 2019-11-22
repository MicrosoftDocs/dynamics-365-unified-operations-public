---
# required metadata

title: Configure a Commerce preview environment
description: This topic describes how to configure a Microsoft Dynamics 365 Commerce preview environment after provisioning.
author: psimolin
manager: annbe
ms.date: 12/02/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Configure a Commerce preview environment

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to configure a Microsoft Dynamics 365 Commerce preview environment after provisioning.

## Overview

Only proceed with the following instructions after your Commerce preview environment has been provisioned. To provision your Commerce preview environment, see [Provision a Commerce preview environment](provisioning-guide.md).

Once your Commerce preview environment has been provisioned end-to-end, there are additional post-provisioning configuration steps that must be completed before you can start evaluating the environment. These steps will need to be done using Microsoft Lifecycle Services (LCS), Microsoft Dynamics 365 Commerce, and Microsoft Dynamics 365 Retail.

## Before starting

1. Sign in to the [LCS portal](https://lcs.dynamics.com).
1. Navigate to your project.
1. From the top menu, select **Cloud-hosted environments**.
1. Select your environment from the list.
1. Click **Full details** from the environment info on the right.
1. Click **Login** to open a menu, then select **Log on to environment**.
1. Ensure that the **USRT** legal entity is selected (top right corner).

## Configure point of sale (POS) in LCS

### Associate a worker with your identity

To associate a worker with your identity in LCS, follow these steps.

1. Using the menu on the left, go to **Modules > Retail > Employees > Workers**.
1. In the list, find and select record **000713 - Andrew Collette**.
1. On the Action Pane, click **Retail**.
1. Click **Associate existing identity**.
1. In the **Email** field (to the right of **Search using email**), type your email address.
1. Click **Search**.
1. Select the record with your name.
1. Click **OK**.
1. Click **Save**.

### Activate Cloud POS

To activate Cloud POS in LCS, follow these steps.

1. From the top menu, select **Cloud-hosted environments**.
1. Select your environment from the list.
1. Click **Full details** from the environment info on the right.
1. Click **Login** to open a menu, choose **Log on to Cloud Point of Sale**, POS should load up.
1. Click **Next**.
1. Log in with your AAD account.
1. Under **Store name**, choose **San Francisco**.
1. Click **Next**.
1. Under **Register and device**, choose **SANFRAN-1**.
1. Click **Activate**.
1. You should be logged out and end up in the POS login screen.
1. You can now log in to the Cloud POS experience using Operator ID **000713** and password **123**.

## Set up your site in Commerce

To start setting up your preview site in Commerce, follow these steps.

1. Log in to the **site management tool** using the URL you noted earlier in the provisioning phase (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Click on the **Fabrikam** site to open the site setup dialog.
1. For domain, select the domain you entered earlier when initializing the e-Commerce.
1. For default channel, select **Fabrikam extended online store**. (Make sure you select the **extended** online store.)
1. For default language, select **en-us**.
1. Leave **Path** as it is.
1. Click **OK**.
1. You will be sent to the list of pages on the site.

## Enable jobs in Retail

To enable jobs in Retail, follow these steps.

1. Log in to the environment (HQ).
1. Using the menu on the left, go to **Retail > Inquiries and reports > Batch jobs**.
1. Perform the following steps for each of the jobs in the list below:
	* **Process retail order email notification**.
	* **Product availability**.
	* **P-0001**.
	* **Synchronize orders job**.
1. Use the Quick Filter to search for the job using its name (listed above).
1. If the Status of the job is **Withhold**, perform the following steps:
	1. Select the record.
	1. From the action pane, open **Batch job**-ribbon and click **Change status**.
	1. Select **Waiting** and Click **OK**.
	
### Run full data sync in Retail

To run full data sync in Retail, follow these steps.

1. Using the menu on the left, go to **Modules > Retail > Headquarters setup > Retail scheduler > Channel database**.
1. **Default** channel is selected from the list on the left. *Select the other available channel (named **scXXXXXXXXX**)*.
1. Click **Full data sync** from the action pane.
1. Enter **9999** as the distribution schedule.
1. Click **OK**.
1. Click **OK**.

### Test credit card information to perform test purchases

To perform test transactions on the site, you can use the following test credit card information:

- Card number: 4111-1111-1111-1111
- Expiration date: 10/20 
- Card verification value (CVV) code: 737

> [!NOTE]
> You should never under any circumstances attempt to use actual credit card information on the test site.

## Next steps

After the previous provisioning and configuration steps are completed, you are ready to start evaluating your preview environment. Use the Commerce site management tool URL to navigate to the authoring experience and the Commerce site URL to navigate to the retail customer site experience.

To continue configuring your Commerce preview environment with optional features, proceed to [Configure Commerce preview environment optional features](cpe-optional-features.md).

## Additional resources

[Commerce preview environment overview](cpe-overview.md)

[Provision a Commerce preview environment](provisioning-guide.md)

[Configure Commerce preview environment optional features](cpe-optional-features.md)

[Commerce preview environment FAQ](cpe-faq.md)

[Microsoft Lifecycle Services (LCS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](https://docs.microsoft.com/en-us/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/en-us/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)

[Help resources for Dynamics 365 Retail](../retail/index.md)
