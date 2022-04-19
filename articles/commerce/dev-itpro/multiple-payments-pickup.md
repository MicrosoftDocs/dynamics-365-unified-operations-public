---
# required metadata

title: Multiple available payment methods for in-store pickup
description: This topic covers the capabilities of Microsoft Dynamics 365 Commerce point of sale (POS) when one or more pre-existing payment methods can be used against a transaction.
author: BrianShook
ms.date: 12/03/2021
ms.topic: article
ms.prod: 

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

This topic covers the capabilities of Microsoft Dynamics 365 Commerce point of sale (POS) when one or more pre-existing payment methods are available to be used against a transaction.

In many cases, when a customer creates an order and provides payment that is authorized, the payment is against an order that will be picked up in the store. When the customer arrives at the store, and their transaction is brought up in POS, the usual preference is to use any existing authorized payments instead of accepting a new payment method. Dynamics 365 Commerce helps the POS user identify any available payment methods and apply them against the transaction.

## Prerequisites

To help POS users identify available payment methods and apply them against transactions, you must configure the following settings in Commerce headquarters:

1. Go to **Workspaces \> Feature management**, and search for and enable the **Omni-channel payments** feature.
1. Search for and enable the **Display all preauthorized payments at checkout in POS** feature. The **Omni-channel payments** feature must be enabled before you can enable this feature.
1. If the hardware station for POS is active, set the **Card not present processing** field for the POS register to **Use hardware station**. Otherwise, set it to **Use retail server**.

## Apply available payment methods in POS

When payment methods are available in a customer's POS transaction, POS provides indicators and flows that make it easy to apply one or more available payments against that transaction. After the POS user finds and selects the customer's order in POS, and then selects **Pick Up**, they can select which items in the order can be picked up. After the user selects the items and confirms the **Pick up** action, POS directs them to the cart transaction page.

### Available payment methods indicator

On the POS cart transaction page that shows the existing payment methods that are available, an informational message above the cart lines will state, "There are existing payment options available to apply to this order. Learn more at checkout." This message helps ensure that the user selects available payment methods instead of a new payment method.

If the POS user selects the **Pay Card** payment option or the **Amount due** total, or moves on to checkout, the options for existing card payments will be shown together with the option to select a new payment method. If any other payment methods are selected on the transaction page, only the option to select a new payment method will be shown.

### Use available payment methods

To use available payment methods, the POS user should select the **Amount due** total in the cart. The dialog box that appears will show the total due and the available payment methods.

> [!NOTE]
> Not all payment methods will prompt the available payments dialog box. Usually, card operations will be shown as available payments if they are linked to the order.

The user can then select either **Existing payment options** or **Choose a payment method**. By selecting the **Choose a payment method** option, the user can continue with the regular processing of a new payment method.

If multiple existing payment methods are available, a **Use available payment** button in the **Existing payment options** section of the **Amount due** dialog box shows a count of the existing payments that are available. If the user selects **Use available payment**, the dialog box is updated so that it shows the existing payment options that are available.

If more than one payment option exists, an **Apply All** button is shown in addition a separate buttons for each existing payment method that is available. If the user selects **Apply All**, amounts for all pre-existing payment methods, up to the total amount that is due, will be used for the transaction. The button for each existing payment method shows the summarized total amount for the payment method, the type of payment method (for example, **Visa**), and the last four digits of the payment method. If the user selects a specific available payment method, the following logic is applied:

- If the amount is less than the transaction total, the selected payment amount will be shown as a payment line, and it will be applied against the total due.
- If the amount equals the transaction total, the amount due will be adjusted to 0 (zero), and the transaction will automatically be completed.
- If the amount is more than the transaction total, the available payments up to the total of the transaction will be used, and the transaction will automatically be completed.

## Additional resources

[Omni-channel payments overview](../omni-channel-payments.md)

[Omni-channel Commerce order payments](commerce-payments.md)
