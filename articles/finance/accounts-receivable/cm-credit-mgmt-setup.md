---
title: Credit management parameters setup
description: Learn about the options that you can use to configure Credit management to meet your business's requirements, including an outline on credit parameters.
author: russasaha
ms.author: twheeloc
ms.topic: install-set-up-deploy
ms.date: 04/13/2026
ms.custom:  
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---

# Credit management parameters setup

[!include [banner](../includes/banner.md)]

This article describes the options that you can use to configure Credit management to meet your business's requirements. To use Credit management features, set up the parameters on the **Credit and collections parameters** page (**Credit and collections \> Setup \> Credit and collections parameters**).

As of Microsoft Dynamics 365 Finance 10.0.43, the Credit management feature is a parameter in **Accounts receivable parameters**, **Credit management** tab. By default, the **Credit management** parameter is set to **Yes**. If the Credit management feature in Feature management is disabled, you see a message that it can't be enabled through Feature management and is controlled by the Accounts receivable parameter. You can set it to **No** in the Accounts receivable parameters if you don't want to use Credit management.

## Credit parameters

The **Credit** section contains four FastTabs where you can change the parameters that control Credit management: **Credit holds**, **Credit management checkpoint**, **Credit management statistics**, and **Credit limits**. The following sections describe the settings that are available on each FastTab.

### Credit holds

- Set the **Skip credit management blocking rules after order hold is released** option to **No** to require that the posting rules be checked again when sales orders are released from the credit management hold list.
- In the **Reasons for canceled orders** field, select the release reason that the system uses by default when a sales order that was on credit management hold is canceled.
- Set the **Check customer credit groups credit limit** option to **Yes** to check the credit limit of a customer credit group when the customer on a sales order belongs to a customer credit group. The credit limit for the group is checked first. If it's sufficient, the credit limit for the customer is checked.
- Set the **Check credit limit when payment terms are increased** option to **Yes** to check the payment terms rankings to determine whether the payment terms on the sales order differ from the default payment terms for the customer. If the new payment terms have a higher rank than the original payment terms, the order is put on credit management hold.
- Set the **Check credit limit when a settlement discount is increased** option to **Yes** to check the settlement discount rankings to determine whether the cash discount on the sales order differs from the default cash discount for the customer. If the new cash discount has a higher rank than the original cash discount, the order is put on credit management hold.
- In the **Reason for releasing modified orders** field, select the release reason that the system uses by default when modified orders are automatically released from credit management hold.
- Set the **Ignore credit limit expired blocking rule when expiration date is blank** option to **Yes** to control the behavior of the **Credit limit expired** rule. Set the option to **No** to block an order when the expiration date is blank.
- In Warehouse management, you can create loads at the time of sales order entry. Set the **Remove blocked load lines** option to **No** to leave sales order lines on the load when a sales order is on credit hold. The load can't be processed while the sales order is on hold. Set the option to **Yes** to remove sales order lines from the load when a sales order is on credit hold. The load can then be processed.
- Sales orders can be automatically released from credit management review. In the **Reason to release automatically** field, select the release reason that the system uses by default when sales orders are automatically released.
- Sales orders can be automatically released from credit management review. In the **Automatically release** field, select **Without posting** to release the hold on an order. You must manually run the process that put the order on hold. Select **With posting** to post the order by using the same posting process that was run when the sales order was put on hold.
- Set the **Skip the credit limit check when canceling a packing slip journal** option to **No** if you want to skip the credit limit check when a packaging slip needs to be cancelled.

### Credit management checkpoint

You can set the timing that is used to check sales orders for credit issues. The **Credit management checkpoint** FastTab identifies the document posting processes that include processing of credit management rules. You can also check the credit rules while you do either a pro-forma posting or a full posting of the sales order. Select the checkboxes to define the posting processes that should put an order on hold if an issue is found after the credit management blocking rules are processed.

You can also define the number of grace days before the credit rules are checked again. Although you can specify that the credit management rules are checked at posting, the rules won't be checked for the specified number of grace days. For example, you confirm a sales order on day one, and you specify two grace days for the confirmation step. In this case, credit rules won't be checked at the next posting step (for example, creation of a packing slip or invoicing of the order) until day four. On or after day four, the rules will be checked again when posting occurs, and the number of grace days will be changed to the value that is specified for the next posting checkpoint. Grace days are applied after the sales order is released from a credit hold. Grace days aren't used when a sales order is initially checked.

If you don't specify the number of grace days, the credit rules will be checked at every posting step that is set up to run credit management rules. If you release the sales order without posting and then run the same order processing step again, the credit rules will be checked again. For example, an order is put on hold after a confirmation, and you release it either with or without posting. In this case, the order will be put on hold again if you confirm it again. Use grace days if the order should move on to the next processing step without being held again.

> [!NOTE]
> If one posting checkpoint has a grace day entered, all checkpoints that are marked for posting need to have grace days.

- Select the **Posting** checkbox to run the credit management rules when the posting checkpoint that is shown on the line is run. If you don't select the checkbox, the rules will be checked only once during the whole posting process.
- If you select the **Posting** checkbox, specify the number of grace days that should pass before the blocking rules are checked again. You can't add grace days if the **Posting** checkbox is cleared.
- Select the **Pro forma** checkbox to run the credit management rules when the pro-forma posting checkpoint that is shown on the line is run. In most cases, the **Posting** field is set to **No** in the dialog box that appears when a sales order is posted.
- If you select the **Posting** checkbox, specify the number of grace days that should pass before the blocking rules are checked again. You can't add grace days if the **Posting** checkbox is cleared.

### Credit management statistics

Several credit management statistics are included in the **Customer credit management statistics** FactBox on the **Customer** page. You must specify several values that are required to calculate those statistics. Enter the number of months that is used to calculate the following values in the **Customer credit management statistics** FactBox:

1. Days Sales Outstanding 1
1. Days Sales Outstanding 2
1. Average balance 1
1. Average balance 2
1. Average credit limit %
1. Average exposure %

Set the **Calculate statistics for zero balance customers** to **Yes** to update the credit statistics for customers with no open transactions when running the aging snapshot process. This includes updating the open order amount. Selecting this option can slow down the aging process.

### Credit limits

- In Credit management, the customer credit limit appears in the customer's currency. You must define the exchange rate type for the credit limit in the customer's currency. In the **Credit limit exchange rate type** field, select the type of exchange rate that converts the primary credit limit to the customer's credit limit.
- Set the **Allow manual editing of credit limits** option to **No** to prevent users from editing credit limits on the **Customer** page. If you set this option to **No**, you can only change a customer's credit limit by posting credit limit adjustment transactions.
- Set the **Bypass inventory reservations** option to **Yes** to disregard inventory reservations when credit management blocking rules are checked. In this case, the system checks the quantities and enables checkpoint grace periods, regardless of the inventory reservation quantity.
- When you enable Credit management, the setting of the **Message when exceeding credit limit** field applies to only free text invoices. Although the system still adds messages to sales orders when customers exceed their credit limit, the presence of those messages doesn't block confirmation, printing of picking lists and packing slips, or posting of invoices.

    Credit management is enabled by default, but you can disable it. If you enable it, use the Credit management blocking rules and checkpoints to identify when customers exceed their credit limit. If you disable it, the messages that the system adds to sales orders based on the setting of the **Message when exceeding credit limit** field can help you identify when customers exceed their credit limit.

### Number sequences and shared number sequence parameters

A journal ID is required to process credit limit adjustments. You must add the credit limit adjustment number that generates the journal ID.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
