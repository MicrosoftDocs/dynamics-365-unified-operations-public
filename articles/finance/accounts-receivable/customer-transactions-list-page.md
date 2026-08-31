---
title: Customer transactions list page
description: Learn about the Customer transactions list page for Microsoft Dynamics 365 Finance, including outlines on viewing settlements and global transactions.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form: CustTrans
ms.dyn365.ops.version: 8.0.4
---

# Customer transactions list page

[!INCLUDE [banner](../includes/banner.md)]

## View settlements

The **View settlements** button on the Action Pane provides quick access to the settlement history and detailed information about the settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they're payments that were created in the same payment journal.

1. Select **Accounts receivable > All customers**.
1. Select a customer that has transactions. On the Action Pane, on the **Customer** tab, select **Transactions**.
1. Select a transaction to research. On the Action Pane, select **View settlements**.

    The **View settlements** dialog box appears, and shows the selected transaction and all documents that are settled against it. This dialog box resembles the settlement history view, but it includes all related documents.

1. In the dialog box, you can perform various tasks. Select one or more vouchers, and then select one of the following buttons:

    - **View related** – Show all the payment journal transactions and general journal transactions for the customer that were created in the journals in which the documents shown in the list were created. For example, if a payment is shown, then all of the payments in the payment journal in which it was created are shown. If an invoice or payment is shown and it was created in a general journal, then all of the documents in the general journal in which it was created are shown. All the settlements that are related to list of documents are also shown. While you're viewing related payments, the label of this button changes to **View settlements**. Select **View settlements** to show only the transactions that were shown when you first opened the **View settlements** dialog box.
    - **View history** – Show the settlement history for the vouchers. Select **Close** to close the dialog box.
    - **View accounting** – Show all vouchers that are related to the selected documents. Select **Close** to close the dialog box.
    - **Export** – Export the selected vouchers to Microsoft Excel.
    - **Settle transactions** – This button appears only if the original document that you selected isn't fully settled. When you select this button, the **Settle transactions** dialog box appears, where you can select transactions for settlement.
    - **Undo settlements** – This button appears only if the original document that you selected was fully settled. When you select this button, the **Undo settlements** dialog box appears, where you can undo the settlements that were done for that document.

## Global transactions

The **Global transactions** button also appears on the **Customer transactions** list page. Use this button to view all transactions for a customer across all legal entities. The **Customer transactions** list page shows transactions only for the legal entities that you have access to, based on your security settings.

The list page shows all transactions for customers that have the same party ID as the customer that you started with. For example, if customer US-001 in one legal entity has the same party ID as customer DE-001 in another legal entity, the list shows all transactions for both customer IDs.

The menus on the **Customer transactions** list page vary, depending on the legal entity for the transaction. For example, if a feature is available only for Swiss legal entities, the menu options for that feature appear only when a Swiss transaction is selected.

To access the feature, follow these steps:

1. Select **Accounts receivable > All customers**.
1. Select a customer. On the Action Pane, on the **Customer** tab, in the **Transactions** group, select **Global transactions**.

## More transaction filters

A new filter replaces the filter for showing open transactions. Use the new filter to view more combinations of transactions. The following options are available in the **Show** field:

- **All** – Show all transactions for the selected customers (open and closed).
- **Closed** – Show only transactions that are fully settled and closed.
- **Open** – Show only transactions that aren't fully settled.
- **Open including closed on or after date** – Show only transactions that aren't fully settled on or after a date that you specify. When you select this option, you can change the date that is shown next to the filter. The list shows transactions that have a **Last settlement date** value on or after the date that you specify, even if those transactions are fully settled as of the current date. However, the balance represents the balances as of the current date, not as of the selected date.

Select the **Hide currency revaluations** check box to hide currency translation transactions.

## Modify due dates and discount dates

You can update due dates and discount dates for open customer transactions. In release 8.1, you can now add due dates to the **Customer transactions** list page. By selecting the due date in the **Customer transactions** list page, you can also change due dates, discount dates, payment terms, and cash discount terms in the **Update due date and cash discount dates**  dialog box.

### Activate the feature

To add due dates to the **Customer transactions** list page and change payment settings for a transaction by using the **Update due date and cash discount dates** dialog box, follow these steps:

1. Select **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Settlements** tab, set the **Show due date and allow edit** option to **Yes**.
1. To enable this feature, the system adds new fields to customer transactions. The system fills these fields when you complete a new transaction. The system also fills these fields when you open the **Update due date and cash discount dates** dialog box. When you set the **Show due date and allow edit** option to **Yes**, you see the **Update payment information** dialog box. To update existing transactions immediately, select **Update all existing transactions**. Alternatively, to fill in the fields only for new transactions, select **Continue without update**.

The due date is now added to the **Customer transactions** list page, so you can easily modify the due date and cash discount dates for transactions.

### Modify the payment settings

The **Customer transactions** list page shows all transactions for a customer. When you select the due date for a transaction, the **Update due date and cash discount dates** dialog box appears. This dialog box shows the base date for due date and discount calculations, due date, payment terms, cash discount terms, and cash discount dates.

Each field has a different effect on the transaction when you edit it:

- **Edit the base date** - The due date and discount dates change as if the base date is the document date.
- **Edit the due date** - Only the due date changes.
- **Edit the discount dates** - Only the discount dates change.
- **Edit the payment terms** - The due date changes, based on the base date and the payment terms.
- **Edit the cash discount terms** - The cash discounts change, based on the base date and the cash discount terms.

When you finish editing the payment settings, select **Close** to save your changes.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
