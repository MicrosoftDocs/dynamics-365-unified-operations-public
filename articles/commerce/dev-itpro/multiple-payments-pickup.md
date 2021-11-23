---
# required metadata

title: Multiple available payment methods for in-store pickup
description: This topic covers the capabilities of Microsoft Dynamics 365 Commerce point-of-sale (POS) for when there are one or more pre-existing payment methods available to be used against a transaction.
author: BrianShook
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgriffin
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2021-11-15
ms.dyn365.ops.version: 

---

# Multiple available payment methods for in-store pickup

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic covers the capabilities of Microsoft Dynamics 365 Commerce point-of-sale (POS) for when there are one or more pre-existing payment methods available to be used against a transaction.

In many cases, when a customer creates an order and provides payment that has been authorized, the payment is against an order that will be picked up in store. When the customer arrives at the store and their transaction is brought up at POS, it is usually preferred to use any existing authorized payments over accepting a new payment method. Dynamics 365 Commerce helps the POS user identify and apply any available payment methods against the transaction.

## Prerequisites

In order to help POS users identify and apply any available payment methods against transactions, the following settings must be configured in Commerce headquarters:

1. Go to **Workspaces \> Feature management** and search for and enable **Omni-channel payments**.
1. Go to **Workspaces \> Feature management** and search for and enable **Display all preauthorized payments at checkout in POS**. The **Omni-channel payments** feature must first be enabled before this feature can be enabled.
1. If the hardware station for POS is active, in headquarters set the POS register **Card not present processing** setting to **Use hardware station**. Otherwise, set the POS register **Card not present processing** setting to **Use retail server**.

## Apply available payment methods in POS

When payment methodss are available to be used in a customer's POS transaction, POS provides indicators and flows to easily apply one or multiple available payments against a transaction. When in POS with the customer's order located, selecting the order and then selecting **Pick Up** will allow the POS user to select which items in the order can be picked up. After selecting the items and confirming the **Pick up** action, POS will then direct the user to the cart transaction screen.

### Available payment methods indicator

When in the POS cart transaction screen that shows existing payment methods available to be used, an information indicator will display above the cart lines that states "There are existing payment options available to apply to this order. Learn more at checkout." This informational banner alert helps to ensure that available payment methods are used instead of selecting a new payment method to process. If the POS user selects the **Pay Card** payment option, the **Amount due** total, or proceeds to checkout, the options for existing card payments will be displayed along with the option to choose a new payment method. Selecting any other payment methods from the transaction page will only display the option to choose a new payment method.

### Use available payment methods

To use available payment methods, the POS user should select the cart **Amount due** total that will bring up a dialog box showing the total due as well as the available payment methods.

>[!NOTE]
> Not all payment methods will prompt the available payments dialog box. Most commonly card operations will be shown as available payments if linked to the order. 

Users can then select either **Existing payment options** or **Choose a payment method**. The latter option allows the user to continue with normal processing of a new payment method.

If multiple existing payment methods are available, the **Existing payment options** section of the **Amount due** dialog box will show a **Use available payment** button with a number of how many existing payments are available. Selecting this button will update the dialog box to display the existing payment options available. If more than one payment option exists, an **Apply All** button will be displayed, as well as buttons for each specific payment method available. Selecting **Apply All** will use all of the pre-existing payment method amounts up to the total of the amount due for the transaction. For the specific existing payment buttons, the summarized total amount existing for the payment method, the payment method type (for example, "Visa"), and the last four digits of the payment method will be displayed on the button. When a specific available payment method is selected:

- If the amount is less than the transaction total, the payment amount selected will show as a payment line and will be applied against the total due.
- If the amount is equal to the transaction total, the amount due will be adjusted to zero and transaction will be completed automatically.
- If the amount is more than the transaction total, the available payments up to the total of the transaction will be used and the transaction will be completed automatically.

## Additional resources

[Omni-channel payments overview](../omni-channel-payments.md)

[Omni-channel Commerce order payments](commerce-payments.md)
