---
# required metadata

title: Configure BOPIS in a Dynamics 365 Commerce environment
description: This topic explains how to configure BOPIS (buy online, pick up in store) in a Microsoft Dynamics 365 Commerce environment after it has been provisioned.
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

# Perform BOPIS scenarios in a Dynamics 365 Commerce environment


[!include [banner](includes/banner.md)]

This topic explains how to configure BOPIS (Buy online, pickup in store) in a Microsoft Dynamics 365 Commerce environment after it has been provisioned.

## Overview

Complete the procedures in this topic only after your Commerce preview environment has been provisioned and configured. For information, see [Provision a Commerce environment](provisioning-guide.md) and [Configure a Dynamics 365 Commerce environment](https://docs.microsoft.com/en-us/dynamics365/commerce/cpe-post-provisioning).

After your Commerce environment has been provisioned and configured end to end, this document can be used to enable the BOPIS scenario.

## Configure the point of sale 

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

> [!NOTE]
> If you have not yet associated a worker with your identity, activation will fail. If this happens, re-visit the environment Visit the [Configure a Dynamics 365 Commerce environment](https://docs.microsoft.com/en-us/dynamics365/commerce/cpe-post-provisioning) article.

6. When prompted to let your organization manage the device, select "**This app only**.
7. Click **Get started** when activation is complete. 

### Enable BOPIS in Modern POS

1. Log into the modern POS using Operator ID **000713** and password **123**.
2. When the introduction walkthrough video plays, check the two boxes in the bottom lefthand corner of the dialog, then close the dialog.
3. If you are not prompted to close the shift, scroll to the right on the Welcome screen and click **Close shift**, then log back into the point of sale.
4. Select **Perform a non-drawer operation** when prompted after login.
5. on the Welcome screen, scroll to the far right and select the **Select hardware station** operation.
6. Click **Manage**, set **Use hardware station** equal to **On**, then click **OK**. 
7. Log off of the point of sale, then log back in.
8. Upon login, select **Open a new shift**, then select **Drawer**.

## Perform a BOPIS scenario

### Create a Storefront order for pick up in store

1. Navigate to the URL specified during the [Initialize e-commerce step](https://docs.microsoft.com/en-us/dynamics365/commerce/provisioning-guide#initialize-e-commerce) in the environment configuration article.
2. Select an item and click **Add to cart**.
3. On the shopping bag page, click **Pick this up** for the order line just added.
4. In the **Select a store** dialog, enter **San Francisco** and click the search icon. 
5. In the list of returned results, locate the San Francisco store and click **Pick up here**.
6. On the shopping bag page, click **Checkout as Guest**. 

> [!NOTE]
> In order to procede with checkout, you must accept the **Cookie notice**. This appears as a banner at the top of the checkout page.

7. For the credit card payment method, enter the following details:

- **Cardholder name:** *Any name
- **Card number:** 4111-1111-1111-1111
- **Expiration date:** 10/20
- **Card verification value (CVV) code:** 737

> [!IMPORTANT]
> Never, under any circumstances, try to use actual credit card information on the test site.

8. Proceed with checkout by entering billing address details, then click **Save and continue**.
9. Click **Checkout** once the order is ready to be placed. 

### Synchronize online orders to the back office

Follow steps noted in the [Posting of online sales and payments](https://docs.microsoft.com/en-us/dynamics365/commerce/tasks/posting-online-sales-payments) article to synchronize online orders. 

### Pick up in store

1. Log into the point of sale. 
2. Select **Order fulfillment** from the **Welcome screen**.
3. In the list of items for pickup, select the line from the order placed online. 
4. With the order line selected, click **Pick up**.
5. The line item will be added to the transaction screen with a balance due of **$0.00**.
6. Click the balance due of **$0.00** or select any payment method to conclude the transaction. 

## Troubleshooting

### Online orders retrieved in POS have non-zero balance due

If an order is retreived for pickup in store and the balance due is not equal to zero, check to ensure that the Modern POS in use and that the hardware station is active. Alternatively, if the Cloud POS or Moder POS for iOS are in use, check to ensure that a shared hardware station is active. Some form of active hardware station is requried to retreive payments that were made online.

### Checkout doesn't render credit card entry module

When checkout doesn't render the credit card entry module, it likely means there is a problem with the payment services setup or payment account setup for the online store. 

### General issues with capturing payment 

For all general issues, you should always consult the Modern POS or IIS Hardware Station event logs first. You can find these logs found under the following nodes in the Microsoft Windows event log:

- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-ModernPOS
- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station


## Additional resources

[Dynamics 365 Commerce preview environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce preview environment](provisioning-guide.md)

[Configure optional features for a Dynamics 365 Commerce preview environment](cpe-optional-features.md)

[Dynamics 365 Commerce preview environment FAQ](cpe-faq.md)

[Microsoft Lifecycle Services (LCS)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](https://docs.microsoft.com/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)

[Adyen payment connector](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)

[Saving online payment instruments with the Adyen connector](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector-listpi)

[Omni-channel payments overview](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments)

