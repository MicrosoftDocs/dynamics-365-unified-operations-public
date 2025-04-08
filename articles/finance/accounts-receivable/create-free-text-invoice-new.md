--- 
title: Create a free text invoice
description: Learn how to create free text invoices, including a step-by-step process that outlines creating a free text invoice, including an overview of copy lines. 
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 02/15/2022
ms.custom:
ms.reviewer: twheeloc    
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2018-08-30
ms.search.form:
ms.dyn365.ops.version: 8.0.4
---

# Create a free text invoice

[!include [banner](../includes/banner.md)]

This article explains how to create free text invoices. For the procedure, use the **USMF** demo company.

## Create a free text invoice

1. Go to **Accounts receivable \> Invoices \> All free text invoices**.
2. Select **New**.
3. In the **Customer account** field, select a value.

    * By default, the account that is selected as the customer account is used as the invoice account.
    * If the invoice isn't posted, the accounting status starts with **In process**.
    * The invoice number will be assigned when the invoice is posted.
    * If you're using Single Euro Payments Area (SEPA) mandates, the direct debit mandate is automatically entered when you select the customer account.

4. In the **Description** field, enter a value.
5. In the **Main account** field, specify an account number that doesn't have dimensions. You will enter dimensions later in this article.

    You can also enter one or more characters for the main account, and use the lookup to find the account.

6. Select the **Line details** FastTab to add dimensions to the main account.
7. Select the **Financial dimensions line** tab.

    * The dimensions are for the selected line only.
    * The sales tax group is filled in from the customer. If the customer doesn't have a sales tax group, the sales tax group from the main account is used.
    * The items sales tax group is filled in from the main account. If the main account doesn't have an item sales tax group, the item sales tax group that is specified in the sales tax parameters in General ledger is used.

8. Optional: In the **Quantity** field, enter a number.
9. Optional: In the **Unit price** field, enter a number.

    The amount is calculated as the quantity times the unit price. However, you can override that calculation by entering an amount.

10. Select **Sales tax** to view the sales tax that is calculated for the invoice.

    You can view the sales tax amounts on this page, or you can override the amounts on the **Adjustment** tab.

11. Select **OK**.
12. Select **Charges** to add a charge to the invoice.
13. In the **Charges code** field, enter a value.
14. In the **Charges value** field, enter a number.
15. Close the page.
16. Select **Totals** to view a summary of the invoice details and totals.
17. Select **Close**.
18. Select **Post** to post the invoice. You will still have an opportunity to cancel before you actually post.

    * You can change the timing of invoice printing. Select **Current** to print each invoice as it's updated. Select **After** to print after all invoices have been updated.
    * To change how the customer's credit limit is verified before the invoice is posted, change the value in the **Credit limit type** field.
    * You can select to stop free text invoice posting when an error occurs on the **Updates** tab on the **Accounts receivable parameters** page (**Accounts receivable > Setup > Accounts receivable parameters**). Select **Yes** for the **Stop posting of free text invoices on first error** parameter to stop the posting of free text invoices when an error occurs. If posting in a batch, an error will stop the posting process and the batch status will be set to **Error**. If this option is not selected, the posting process will skip an invoice with a posting error and will continue to post additional invoices. If posting in a batch, a posting error will not prevent other invoices from being posted. The batch status will be **Ended**. A detailed posting process report will be available for review in batch job history.
    * In Microsoft Dynamics 365 Finance 10.0.30, the **Free text invoice posting improvement for totals calculation** feature improves posting performance by allowing it to run more efficiently. When this feature is enabled, posting will save the calculated totals, instead of recalculating the totals multiple times during the posting process. 
    * In Microsoft Dynamics 365 Finance 10.0.31, the **Free text invoice batch posting process improvement** feature improves posting performance by allowing it to run more efficiently. When this feature is enabled, posting uses a pattern that self-manages the batch posting workload across a fixed number of threads, instead of assigning a fixed number of documents across an unlimited number of threads.
    * To print the invoice, set the option to **Yes**.
    * To post the invoice, set the option to **Yes**. You can print the invoice without posting it.

19. Select **OK**.

## Copy lines
To copy lines on a free text invoice, select one or more lines, and then select **Copy selected lines**. You can specify the number of copies to make, and you can also copy notes and attachments. You can either copy the distributions or let them be re-created when you post.

After you copy lines, you can edit the information as you require.

## Create a free text invoice from a template
You can create a free text invoice from a template. When you select **New from template** on the **Invoice** tab, you can select a template name and the customer account for the new free text invoice. Default values, such as the terms of payment and method of payment, can be automatically filled in from the customer, or you can use the values that were saved in the template.

A new free text invoice is created, and you can edit the values as you require.

## Resetting the workflow status for free text invoices from Unrecoverable to Draft
A workflow instance that has stopped because of an unrecoverable error will have a workflow status of **Unrecoverable**. When the status of a customer free text invoice workflow is **Unrecoverable**, you can reset it to **Draft** by selecting **Recall** from the workflow actions. You can then edit the customer free text invoice. This feature is available if the **Resetting the workflow status for free text invoices from Unrecoverable to Draft** parameter on the **Feature management** page is turned on.

You can use the **Workflow history** page to reset the workflow status to **Draft**. You can open this page from **Free text invoice** or from **Common > Inquires > Workflow**. To reset the workflow status to **Draft**, select **Recall**. You can also reset the workflow status to **Draft** by selecting the **Recall** action on the **Free text invoice** page or **All free text invoices** page. After the workflow status is reset to **Draft**, it becomes available for editing on the **Free text invoice** page.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
