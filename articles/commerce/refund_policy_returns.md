---
title: Create and update a returns and refunds policy for a channel
description: Learn how to set up a returns and refunds policy for a channel in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/02/2025
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2020-01-21
---

# Create and update a returns and refunds policy for a channel

[!include [banner](includes/banner.md)]

This article explains how to set up a returns and refunds policy for a channel in Microsoft Dynamics 365 Commerce.

The channel return policy in Dynamics 365 Commerce enables retailers to set enforcements on which payment tenders are allowed for processing a return on a point of sale (POS) device.  

The scope of the policy is currently limited to setting the payment tenders that are allowed for a channel. The "allowed" list is based on the payment methods used to make the purchase. For example:

- If a purchase was made using a gift card, the store policy is to process refunds only to a new gift card or to give store credit. 
- If a sale is made using cash, the options allowed for refund are cash, gift card, and customer account, but not credit card. 

## Enable return policy

This feature is turned on by default. You can find it in the **Feature Management** workspace by searching for **Enable channel return policies** in the list of feature names.

## Configure return policy

To configure a return policy for a retail store or online retail channel, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** \> **Channel Setup** \> **Returns** \> **Channel return policy**.
1. Select **New** to create a new return policy template. To use an existing template, select the template in the left pane. For new templates, add a name and description that helps you identify the policy applied to the channel. If you want to allow store managers to select payment methods other than payment methods defined in the channel return policy, set the **Can managers override?** property to **Yes**. Learn more at [Override allowed payment methods](#override-allowed-payment-methods).
1. In the **Allowed refund payment methods** section, in the **Allowed return tender type** drop-down list, select a return tender type for each payment method as shown in the following example image.
   
    :::image type="content" source="media/channel-return-policy-new.png" alt-text="Channel return policy form showing Allow return tender type drop-down list options.":::
   
    > [!IMPORTANT]
    > - The payment methods are derived from the payment methods set for the organization.
    > - Adding an allowed return tender type for each listed payment method ensures that returns can be made to the allowed return tender type.
    
1. To associate the return policy template with the stores that use it, on the **Retail Channels** tab, select **Add**, and then associate the available channels. 

    1. In the **Choose organization nodes** dialog, select the stores, regions, and organizations that the template should be associated with.
    1. Only one return policy template can be associated with each store.
    1. Use the arrow buttons to select stores, regions, or organizations.
    1. The effective date on the policy is the date on which the policies are applied to the channels and the channel jobs are run. 

    :::image type="content" source="media/Return-policy-page3.png" alt-text="Choose organization nodes dialog.":::

1. On the **Distribution schedule** page, run the **1070** job to make the channel return policy available to the POS.

## Preview the channel return policy in the POS

To view the allowed return tender types in POS, Follow the steps in either of the following examples:

1. Sign in to the POS as a cashier or manager.
1. Under **Shift and Drawer**, select **Show journal**.
1. Select the transaction that's part of the return. 
1. Select **Amount Due** to display a list of all the allowed return tender types.
1. Select the items to refund, and then select the payment method.  
    - If the payment tender selected is in the allowed list of return tender types, the cashier can complete the transaction.
    - If the payment tender selected isn't allowed, an error message is displayed.

-or-

1. Sign in to the POS as a cashier or manager.
1. Select **Return Transaction** and enter the receipt ID using a barcode scan or by manual entry. 
1. Select the transaction that is part of the return. 
1. Select **Amount Due** to display a list of all the allowed return tender types.
1. Select the items to refund, and choose the payment method.  
    - If the payment tender selected is in the allowed list of return tender types, the cashier can complete the transaction.
    - If the payment tender selected isn't allowed, an error message is displayed.

:::image type="content" source="media/Return-policy-page5.png" alt-text="Return payment dialog showing refund types allowed.":::

## Override allowed payment methods

To handle scenarios where the standard refund payment method can't be applied, the system allows retailers to grant special permissions to designated store associates. These associates can override the return policy and refund customers using a payment method that isn't permitted otherwise.

To enable this capability, set the channel return policy **Can managers override?** property to **Yes**. With this option enabled, all store managers can choose any payment method for the refund. To enable this capability for nonstore managers, the **Allow using all payment methods for refund** POS permission is introduced starting in Commerce version 10.0.44. If channel return policy allows the override of the allowed payment methods, then all store managers and store associates with the **Allow using all payment methods for refund** permission are able to use any payment method for refund. 

> [!NOTE]
> Store associates who don't have the **Allow using all payment methods for refund** permission can use only the payment methods defined by the channel return policy. It isn't possible to have the store manager input their credentials for this process. The store manager or associates with the appropriate permissions must initiate such returns on their registers.

:::image type="content" source="media/refund-options-override.png" alt-text="POS Return payment dialog with Show all refund options highlighted":::

[!INCLUDE[footer-include](../includes/footer-banner.md)]
