---
# required metadata

title: Configure BOPIS in a Dynamics 365 Commerce preview environment
description: This topic explains how to configure BOPIS (buy online, pick up in store) in a Microsoft Dynamics 365 Commerce preview environment after it's provisioned.
author: rubendel
manager: annbe
ms.date: 04/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rubendel
ms.search.validFrom: 2020-04-20
ms.dyn365.ops.version: Release 10.0.5
---

# Configure a Dynamics 365 Commerce preview environment


[!include [banner](includes/banner.md)]

This topic explains how to configure BOPIS (Buy online, pickup in store) in a Microsoft Dynamics 365 Commerce preview environment after it's provisioned.

## Overview

Complete the procedures in this topic only after your Commerce preview environment has been provisioned. For information about how to provision your Commerce preview environment, see [Provision a Commerce preview environment](provisioning-guide.md).

After your Commerce preview environment has been provisioned end to end, additional post-provisioning configuration steps must be completed before you can start to evaluate the environment and perform buy online, pickup in store scenarios. To complete these steps, you must use Microsoft Dynamics Lifecycle Services (LCS) and Dynamics 365 Commerce.

## Before you start

1. Sign in to the [LCS portal](https://lcs.dynamics.com).
2. Go to your project.
3. On the top menu, select **Cloud-hosted environments**.
4. Select your environment in the list.
5. In the environment information on the right, select **Full details**.
6. Select **Login** to open a menu, and then select **Log on to environment**.
7. Make sure that the **USRT** legal entity is selected in the upper-right corner.

## Configure the point of sale 

### Associate a worker with your identity

To associate a worker with your identity, follow these steps.

1. Navigate to **Modules \> Retail and Commerce \> Employees \> Workers**.
2. In the list, find and select the following record: **000713 - Andrew Collette**.
3. On the Action Pane, select **Retail**.
4. Select **Associate existing identity**.
5. In the **Email** field to the right of **Search using email**, enter your email address.
6. Select **Search**.
7. Select the record that has your name.
8. Select **OK**.
9. Select **Save**.

### Configure Modern POS

BOPIS scenarios with a credit card payment require hardware station. The hardware station is built into the Modern POS for Windows and Android clients. If using Cloud POS or Modern POS for iOS, the point of sale client must be paired with a shared hardware station. This document describes how to configure BOPIS for Windows and Android clients. For information on setting up a shared hardware station, visit [Configure and install Retail hardware station](https://docs.microsoft.com/en-us/dynamics365/commerce/retail-hardware-station-configuration-installation).

1. Navigate to **Retail and Commerce \> Channel setup \> POS setup \> Registers**, select **SANFRAN-5**, and click **Edit**.
2. Select the **Hardware profile** and change from **HW002** to **HW001**, then click **Save**.
3. Syncronize the changes by navigating to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**
4. Select the distribution schedule **1090** and then click **Run now** in the action pane.
5. Click **Yes**, then **OK** to intiate the data sychronization. 

### Install Modern POS

1. Navigate to **Retail and Commerce \> Channel setup \> POS setup \> Devices** and select **SANFRANCIS-5**.
2. In the Action pane, click **Download**, then click **Configuration file**.
3. Next, click **Download**, then click **Retail Modern POS**. 
4. When the ModernPOSSetup.exe file download has completed, click **Open file**.

![Open file](./dev-itpro/media/Payments/openfile.png)

5. Click **Next** to proceed through installation. When installation is complete, click **Close**.

### Activate Modern POS

To activate Modern POS, follow these steps.

1. On the Windows desktop, click the **Start** button and type **Retail Modern POS**. 
2. Select the **Retail Modern POS** aplication to initiate activation. 
3. Click **Next**. The **Server URL**, **Device ID**, and **Register number** should be prefilled with details from the configuration filed downloaded at the same time as the Modern POS install file. 
4. Click **Activate**.
5. An authentication dialog will appear. Select the account with the email address previously associated with worker **000713 - Andrew Collette**.
6. When you are prompted to let your organization manage the device, select "**This app only**.
7. Click **Get started** when activation is complete. 

### Enable BOPIS in Modern POS

1. Log into the modern POS using Operator ID **000713** and password **123**.
2. when the introduction walkthrough video plays, check the two boxes in the bottom lefthand corner of the dialog, then close the dialog.
3. If you are not prompted to close the shift, scroll to the right on the Welcome screen and click **Close shift**, then log back into the point of sale.
4. Select **Perform a non-drawer operation** when prompted after login.
5. on the Welcome screen, scroll to the far right and select the **Select hardware station** operation.
6. Click **Manage**, set **Use hardware station** equal to **On**, then click **OK**. 
7. Log off of the point of sale, then log back in.
8. Upon login, select **Open a new shift**, then select **Drawer**.

## Set up your site in Commerce

To start to set up your preview site in Commerce, follow these steps.

1. Sign in to the site management tool by using the URL that you made a note of when you initialized e-Commerce during provisioning (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Select the **Fabrikam** site to open the site setup dialog box.
1. Select the domain that you entered when you initialized e-Commerce.
1. Select **Fabrikam extended online store** as the default channel. (Make sure that you select the **extended** online store.)
1. Select **en-us** as the default language.
1. Leave the value of the **Path** field as it is.
1. Select **OK**. The list of pages on the site appears.

## Enable jobs

To enable jobs in Commerce, follow these steps.

1. Sign in to the environment (HQ).
1. Use the menu on the left to go to **Retail and commerce \> Inquiries and reports \> Batch jobs**.

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

### Run full data synchronization

To run full data synchronization in Commerce, follow these steps.

1. Use the menu on the left to go to **Modules \> Retail and commerce \> Headquarters setup \> Retail scheduler \> Channel database**.
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
