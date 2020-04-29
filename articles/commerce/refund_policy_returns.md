---
# required metadata

title: Create and update a returns and refunds policy for a channel
description: This topic explains how to set up a returns and refunds policy for a channel.
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2020-01-21
ms.dyn365.ops.version: Retail 10.0.9 update
---

# Create and update a returns and refunds policy for a channel

[!include [banner](includes/banner.md)]

## Overview

The channel return policy in Dynamics 365 Commerce enables retailers to set enforcements on which payment tenders can be allowed for processing a return on a point of sale (POS) device.  

This topic describes the steps to set up a returns and refunds policy for a channel.

The scope of the policy is currently limited to setting the payment tenders that can be allowed for a channel. The "allowed" list is based on the payment methods used to make the purchase. For example:

- If a purchase was made using a gift card, the store policy is to process refunds only to a new gift card or to give store credit. 
- If a sale is made using cash, the options allowed for refund are cash, gift card, and customer account, but not credit card. 


## Enable return policy

To enable the channel return policy functionality, do the following:

1. Go to the **Feature Management** workspace in Dynamics 365 Commerce.
2. Search for the **Enable channel return policies** feature in the list of feature names.
3. Select **Enable now**. 

## Configure return policy

Follow these steps to configure a return policy for a retail store or online retail channel.

1. Go to **Retail and Commerce** \> **Channel Setup** \> **Returns** \> **Channel return policy**.

2. Select **New** to create a new return policy template. To use an existing template, select the template in the left pane. For new templates, add a name and description that will help you identify the policy when it is being applied to the channel.

   ![Add new return policy](media/Return-policy-page1.png "Add new return rolicy")
     
   
3. In the **Allowed refund payment methods** section, define **Allowed** return payment tenders that are specific to each payment method.
   ![Add payment methods](media/Return-policy-page2.PNG "Set allowed payment methods per payment type")
   
    > [!IMPORTANT]
    > - The payment methods are derived from the payment methods set for the organization.
    > - Adding an allowed return tender type for each listed payment method will ensure that returns can be made to the allowed return tender type.
    
4. Associate the return policy template with the stores where it will be used. Select **Add** in the **Retail Channels** tab and associate the available channels. 

    - In the **Choose organization nodes** dialog box, select the stores, regions, and organizations that the template should be associated with.
    - Only one return policy template can be associated with each store.
    - Use the arrow buttons to select stores, regions, or organizations.
    - The effective date on the policy will be the date on which the policies are applied to the channels and the channel jobs are run. 

    ![Choose organization nodes dialog box](media/Return-policy-page3.PNG "Choose organization nodes dialog box")

5. On the **Distribution schedule** page, run the **1070** job to make the channel return policy available to the POS.

## Preview the channel return policy in the POS

Follow the steps in either of the following examples to view the allowed return tender types in POS.

1. Sign in to the POS as a cashier or manager.
2. Under **Shift and Drawer**, select **Show journal**.
3. Select the transaction that is part of the return. 
4. Select the items to refund, and choose the payment method.  
- If the payment tender selected is in the allowed list of return tender types, the cashier can complete the transaction.
- If the payment tender selected is not allowed, an error message is displayed.
- Select **Amount Due** to display a list of all the allowed return tender types.

-or-

1. Sign in to the POS as a cashier or manager.
2. Select **Return Transaction** and enter the receipt ID using a barcode scan or by manual entry. 
3. Select the transaction that is part of the return. 
4. Select the items to refund, and choose the payment method.  
- If the payment tender selected is in the allowed list of return tender types, the cashier can complete the transaction.
- If the payment tender selected is not allowed, an error message is displayed.
- Select **Amount Due** to display a list of all the allowed return tender types.

![Refund not allowed](media/Return-policy-page6.png "Refund type not allowed")



![List of payment methods](media/Return-policy-page5.PNG "Refund types allowed")
