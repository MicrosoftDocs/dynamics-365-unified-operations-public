---
# required metadata

title: Credit management setup
description: 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Credit management parameters setup
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the options available for configuring Credit management to fit your business' needs. To begin using Credit management features, setup the parameters in **Credit management > Setup > Credit management parameters**.

## Credit parameters

There are four FastTabs where you can change the parameters that control credit management: **Credit holds**; **Credit management checkpoint**; **Credit management statistics**; **Credit limits**. The following sections describe the settings that are available in each of them. 

### Credit holds

-	Select **Yes** for **Allow edit of sales orders value after order hold is released** to require the sales order to check the rules again if the sales order value (extended price) has been changed after being released from the on-hold hold list. Normally, if the posting rules have been set up with grace days, the order will only be placed on hold if it is processed within the number of grace days.

-	Select the default release reason for the **Reasons for canceled orders** field. This will be the default reason used when a sales order that was on credit management hold is cancelled.

-	Select **Yes** for the **Check customer credit groups credit limit** to check the credit limit of a customer credit group when the customer on a sales order belongs to a customer credit group. The credit limit for the group will be checked and, if the credit limit is sufficient, then the credit limit of the customer will be checked.

-	Select **Yes** for **Check credit limit when payment terms are increased** to check the payment terms rankings to see if the payment terms on the sales order are different from the payment terms on the sales order. If the ranking of the new payment term is higher than the original payment term, then the order is placed on credit management hold.

-	Select **Yes** for **Check credit limit when a settlement discount is increased** to check the settlement discount rankings to see if the cash discount on the sales order is different from the cash discount on the sales order. If the new cash discount ranking is higher than the original cash discount, the order is placed on credit management hold.

-	Select the default release reason for **Reason for releasing modified orders** that will be used when modified orders are automatically released from credit management hold.

-	Select **Yes** for **Ignore credit limit expired blocking rule when expiration date is blank** to control the behavior of the **Credit limit expired** rule. Select **No** to block an order when the expiration date is blank.

-	Within warehouse management, it is possible to create loads at sales order entry. Select **No** for **Remove blocked load lines** to leave the sales order lines on the load when a sales order is on credit hold. The load cannot be processed when the sales order is on hold. Select **Yes** to remove the sales order lines from the load when a sales order is on credit hold. The load can then be processed.

-	Sales orders can be automatically released from credit management review. Select the release reason for **Reason to release automatically** that will be used as the default entry when sales orders are released automatically.

-	Sales orders can be automatically released from credit management review. Select **Without posting** for **Automatically release** to release the hold on the order. You will need to manually execute that same process that placed the order on hold. Select **With posting** to post the order using the same posting process that was executed when the sales order was placed on hold.

### Credit management checkpoint

You can set the timing for checking sales orders for credit issues. The **Credit management checkpoint** FastTab is used to identify which document posting processes will include processing of credit management rules. You can also choose to check the credit rules while doing either a proforma posting or full posting of the sales order. Select each check box to define which posting processes will put an order on hold after if an issue is found after processing the credit management blocking rules.

You can also define the number of grace days before the credit rules are checked again. Although you may specify that the credit management rules are checked at posting, the rules will not be checked for the specified number of grace days. For example, if you confirm a sales order on day 1 and you specify 2 grace days for the confirmation step, then credit rules won't be checked at the next posting step, such as creating a packing slip, invoicing the order, and so on, until day 4. On or after day 4, the rules will be checked again when posting occurs and the number of grace days will be changed to the grace days value for the next posting checkpoint.

If you don't specify the number of grace days, the credit rules will be checked at every posting step that is set to execute credit management rules. If you release the sales order without posting and then execute the same order processing step again, it will check the credit rules again. For example, if an order is put on hold after a confirmation and you release it with or without posting, it will be placed on hold again if you confirm it again. Use grace days if you want the order to move on to the next processing step without being held again.

You can't specify grace days for some posting checkpoints and not for others. You must set up all posting checkpoints with grace days or set them all up with no grace days.

-	Select the check box in the **Posting** column to execute the credit management rules when the posting checkpoint shown on the line is executed. If you don't select the check box, the rules will only be checked once during the entire posting process.

-	If you selected the **Posting column** check box, add Grace days to identify how many days will pass before the blocking rules will be checked again. You can't add grace days when the check box is not selected.

-	Select the check box in the **Pro forma** column to execute the credit management rules when the proforma posting checkpoint shown on the line is executed. In most cases, the posting box is set to No on the dialog that shows when a sales order is posted.

-	If you selected the **Posting column** check box, add the number of grace days that identify how many days will pass before the blocking rules will be checked again. You can't add grace days when the check box is not selected.

### Credit management statistics

There are several credit management statistics included in the credit management statistics fact box on the **Customer** page. These statistics require you to specify several values that will be used to calculate those statistics. Enter the number of months used to calculate the following values shown in the **Customer credit management statistics** fact box:

1.	Days Sales Outstanding 1
2.	Days Sales Outstanding 2
3.	Average balance 1
4.	Average balance 2
5.	Average credit limit %
6.	Average exposure %

### Credit limits

-	In Credit management, the customer credit limit is shown using the customer's currency. You must define the exchange rate type for the credit limit using the customer's currency. Select the **Credit Limit exchange rate type** that will be used to convert the primary credit limit to the customer's credit limit.

-	Select **No** for **Allow manual editing of credit limits** to stop users from editing credit limits on the customer form. When this field is set to No, changes to a customer's credit limit can be only by posting credit limit adjustment transactions.

### Number sequences and shared number sequences parameters

You must add the **Credit limit adjustment number** that will be used to generate the journal ID needed for processing credit limit adjustments.
