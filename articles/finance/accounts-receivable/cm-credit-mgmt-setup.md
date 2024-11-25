---
title: Credit management parameters setup
description: Learn about the options that you can use to configure Credit management to meet your business's requirements, including an outline on credit parameters.
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 05/07/2024
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

## Credit parameters

There are four FastTabs in the **Credit** section where you can change the parameters that control Credit management: **Credit holds**, **Credit management checkpoint**, **Credit management statistics**, and **Credit limits**. The following sections describe the settings that are available on each FastTab.

### Credit holds

- Set the **Allow edit of sales orders value after order hold is released** option to **No** to require that the posting rules be checked again if the sales order value (extended price) has been increased since the sales order was released from the on-hold list.
- In the **Reasons for canceled orders** field, select the release reason that will be used by default when a sales order that was on credit management hold is canceled.
- Set the **Check customer credit groups credit limit** option to **Yes** to check the credit limit of a customer credit group when the customer on a sales order belongs to a customer credit group. The credit limit for the group will be checked, and then, if it's sufficient, the credit limit for the customer will be checked.
- Set the **Check credit limit when payment terms are increased** option to **Yes** to check the payment terms rankings to determine whether the payment terms on the sales order differ from the default payment terms for the customer. If the new payment terms have a higher rank than the original payment terms, the order is put on credit management hold.
- Set the **Check credit limit when a settlement discount is increased** option to **Yes** to check the settlement discount rankings to determine whether the cash discount on the sales order differs from the default cash discount for the customer. If the new cash discount has a higher rank than the original cash discount, the order is put on credit management hold.
- In the **Reason for releasing modified orders** field, select the release reason that will be used by default when modified orders are automatically released from credit management hold.
- Set the **Ignore credit limit expired blocking rule when expiration date is blank** option to **Yes** to control the behavior of the **Credit limit expired** rule. Set the option to **No** to block an order when the expiration date is blank.
- In Warehouse management, loads can be created at the time of sales order entry. Set the **Remove blocked load lines** option to **No** to leave sales order lines on the load when a sales order is on credit hold. The load can't be processed while the sales order is on hold. Set the option to **Yes** to remove sales order lines from the load when a sales order is on credit hold. The load can then be processed.
- Sales orders can be automatically released from credit management review. In the **Reason to release automatically** field, select the release reason that will be used by default when sales orders are automatically released.
- Sales orders can be automatically released from credit management review. In the **Automatically release** field, select **Without posting** to release the hold on an order. You must manually run the process that put the order on hold. Select **With posting** to post the order by using the same posting process that was run when the sales order was put on hold.

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
2. Days Sales Outstanding 2
3. Average balance 1
4. Average balance 2
5. Average credit limit %
6. Average exposure %

Set the **Calculate statistics for zero balance customers** to **Yes** to update the credit statistics for customers with no open transactions when running the aging snapshot process. This includes updating the open order amount. Selecting this option can slow down the aging process. 

### Credit limits

- In Credit management, the customer credit limit is shown in the customer's currency. You must define the exchange rate type for the credit limit in the customer's currency. In the **Credit limit exchange rate type** field, select the type of exchange rate that should be used to convert the primary credit limit to the customer's credit limit.
- Set the **Allow manual editing of credit limits** option to **No** to prevent users from editing credit limits on the **Customer** page. If this option is set to **No**, changes to a customer's credit limit can be made only by posting credit limit adjustment transactions.
- Set the **Bypass inventory reservations** option to **Yes** to disregard inventory reservations when credit management blocking rules are checked. In this case, the quantities will be checked and checkpoint grace periods will be enabled, regardless of the inventory reservation quantity.
- When Credit management is enabled, the setting of the **Message when exceeding credit limit** field is used to process only free text invoices. Although messages are still added to sales orders when customers have exceeded their credit limit, the presence of those messages won't block confirmation, printing of picking lists and packing slips, or posting of invoices.

    Credit management is enabled by default, but you can disable it. If it's enabled, you use the Credit management blocking rules and checkpoints to identify when customers have exceeded their credit limit. If it's disabled, the messages that are added to sales orders based on the setting of the **Message when exceeding credit limit** field can help you identify when customers have exceeded their credit limit.

### Number sequences and shared number sequence parameters

A journal ID is required to process credit limit adjustments. You must add the credit limit adjustment number that should be used to generate the journal ID.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
