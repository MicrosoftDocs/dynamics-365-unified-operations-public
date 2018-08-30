---
# required metadata

title: Vendor transactions list page
description: This topic provides information about the Vendor transactions list page for Microsoft Dynamics 365 for Finance and Operations.
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  VendTrans
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Vendor transactions list page

[!include [banner](../includes/banner.md)]

## View settlements

The **View settlements** button on the Action Pane provides quick access to the settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

1. Select **Accounts payable \> All vendors**.
2. Select a vendor that has transactions, and then select **Vendor \> Transactions**.
3. Select a transaction to research, and then, on the Action Pane, select **View settlements**.

    The **View settlements** dialog box appears, and shows the selected transaction and all documents that have been settled against it. This dialog box resembles the settlement history view, but it includes all related documents.

4. In the dialog box, you can perform various tasks. Select one or more vouchers, and then select one of the following buttons:

    - **View related** – Show all the payment journal transactions that were created in the payment journal that is related to the selected document. In addition, all the settlements that are related to those payments are shown. While you're viewing related payments, the label of this button changes to **View settlements**. Select **View settlements** to show only the transactions that were shown when you first opened the **View settlements** dialog box.
    - **View history** – Show the settlement history for the vouchers. Select **Close** to close the dialog box.
    - **View accounting** – Show all vouchers that are related to the selected documents. Select **Close** to close the dialog box.
    - **Export** – Export the selected vouchers to Microsoft Excel.
    - **Settle transactions** – This button appears only if the original document that was selected wasn't fully settled. When you select this button, the **Settle transactions** dialog box appears, where you can select transactions for settlement.
    - **Undo settlements** – This button appears only if the original document that was selected was fully settled. When you select this button, the **Undo settlements** dialog box appears, where you can undo the settlements that were done for that document.

## Global transactions

The **Global transactions** button has been added to the vendor. This button lets you view all transactions for a vendor across all legal entities. The **Vendor transactions** list page shows transactions only for the legal entities that the user has access to, based on his or her security settings.

The list page will show all transactions for vendors that have the same party ID as the vendor that you started with. For example, if vendor US-001 in one legal entity has the same party ID as vendor DE-001 in another legal entity, all transactions for both vendor IDs are shown.

The menus on the **Vendor transactions** list page vary, depending on the legal entity for the transaction. For example, if a feature is available only for Swiss legal entities, the menu options for that feature appear only when a Swiss transaction is selected.

To access the feature, follow these steps.

1. Select **Accounts payable** \> **Vendors**.
2. Select a vendor, and then select **Transactions** \> **Global transactions**.

## More transaction filters

The filter for showing open transactions has been replaced with a new filter that lets you view more combinations of transactions. The following options are available in the **Show** field:

- **All** – Show all transactions for the selected vendors (open and closed).
- **Closed** – Show only transactions that have been fully settled and closed.
- **Open** – Show only transactions that haven't been fully settled.
- **Open as of** – Show only transactions that haven't been fully settled as of a date that you specify. When you select this option, you can change the date that is shown next to the filter. Transactions that have a **Last settlement date** value after the date that you specify are shown in the list, even if those transactions are fully settled as of the current date. However, the balance represents the balances as of the current date, not as of the selected date.

A filter has also been added that lets you hide currency translation transactions. Just select the check box.

## More easily modify due dates and discount dates

You can update due dates and discount dates for open vendor transactions. In release 8.1, the experience has been improved. You can now add due dates to the **Vendor transactions** list page. By selecting the due date, you can also change due dates, discounts dates, payment terms, and cash discount terms in one new dialog box.

### Activate the feature

To add due dates to the **Vendor transactions** list page and change payment settings for a transaction by using the new dialog box, follow these steps.

1. Select **Accounts receivable \> Setup \> Accounts receivable parameters**.
2. Select **Settlements**.
3. Select **Update due date and cash discount date**.
4. To enable this feature, new fields have been added to vendor transactions. Those fields will be filled in when a new transaction is completed. They will also be filled in when you open the new due date dialog box. To update all existing transactions immediately, select **BUTTON NAME HERE**. Alternatively, to fill in the fields only for new transactions, select **BUTTON NAME HERE**.

The due date is now added to the **Vendor transactions** list page, and you can more easily modify the due date and cash discount dates for transactions.

### Modify the payment settings

The **Vendor transactions** list page shows all transactions for a vendor. When you select the due date for a transaction, a dialog box appears. This dialog box shows the base date for due date and discount calculations, the due date, the payment terms, the cash discount terms, and the cash discount dates.

Each field has a different effect on the transaction when you edit it:

- **Edit the base date:** The due date and discount dates are changed as if the base date is the document date.
- **Edit the due date:** Only the due date is changed
- **Edit the discount dates:** Only the discount dates are changed.
- **Edit the payment terms:** The due date is changed, based on the base date and the payment terms.
- **Edit the cash discount terms:** The cash discounts are changed, based on the base date and the cash discount terms.

When you've finished editing the payment settings, select **Close** to save your changes.
