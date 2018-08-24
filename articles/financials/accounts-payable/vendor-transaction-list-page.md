---
# required metadata

title: Vendor transaction list page
description: This topic provides information about the Vendor transaction list page for Microsoft Dynamics 365 for Finance and Operations.
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
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4
---

# Vendor transaction list page

[!include [banner](../includes/banner.md)]

## View settlements

The **View settlements** tab on the action pane provides quick access to settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

1. Select **Accounts payable \> All vendors**.
2. Select a vendor that has transactions, and then select **Vendor \> Transactions**.
3. Select a transaction to research.
4. Select the **View settlements** tab on the action pane.

    The **View settlements** dialog box opens and shows the selected transaction and all documents that are settled against it. This dialog box resembles the settlement history view, but it includes all related documents.

5. You can perform various tasks from this dialog box. Select one or more vouchers, and then select one of the links:

    - **View related** – Click this link to display all the payment journal transactions that were created in the payment journal that is related to the selected document. In addition, all the settlements that are related to those payments appear. When you're viewing related payments, the label of this link changes to **View settlements**. Select **View settlements** to show only the transactions that were shown when you first opened the **View settlements** dialog box.
    - **View accounting** – All vouchers that are related to the selected documents appear. Select **Close** to close the dialog box.
    - **Export** – Export the selected vouchers to Microsoft Excel.
    - **Settle transactions** – This link appears if the original document that was selected wasn't fully settled. When you select it, the **Settle transactions** dialog box appears, where you can select transactions for settlement.
    - **Undo settlements** – This link appears if the original document that was selected was fully settled. When you select it, the **Undo settlements** dialog box appears, where you can undo the settlements that were done for that document.

## Global transactions

The Global transactions menu has been added to the Vendor form to allow you to view all transactions for a vendor across all legal entities. The customer transaction list will only show transactions for the legal entities that the user has access to based on their security settings.  

The list page will show all transactions for vendors that have the same party ID as the vendor that you started with. For example, if vendor US-001 in one legal entity has the same party ID as customer DE-001 in another legal entity, then all transactions for both customer IDs will be shown. 

The menus for the Vendor transactions list page will also change based on the legal entity for the transaction. For example, if a feature is only available for Swiss legal entities, then those menu choices will only appear when a Swiss transaction is selected.

To access the feature:
1. Open Accounts receivable > Vendor 
2. Select a cendor
3. Select Transactions > Global transactions

## More transaction filters 

The filter for showing open transactions has been replaced with a new filter that allows you to view more combinations of transactions. 
1. Show All will show all transactions for the selected vendors (open and closed).
2. Show Closed will show only transactions that have been fully settled and closed.
3. Show Open will show only transactions that have been not been fully settled.
4. Show Open as of will show only transactions that have been not been fully settled as of a date that you specify. When you make this selection, you can change the date shown next to the filter. Transactions that have a Last settlement date after the date that you specify will be shown in the list, even if the transaction is fully settled as of today. However, the balance represents the balances as of today, not as of the date selected.

A filter for removing currency translation transactions has also been added. Click on the check box and currency translation transactions will not be shown.

**Easier access to modifying the due date and discount dates**

It is possible to update due dates and discount dates for an open vendor transaction. We have improved the experience in 8.1 by allowing you to add the due date to the vendor transactions list page. You can also click on the due date and change due dates, discounts dates, payment terms, and cash discount terms in a single form.

***Activating the feature***
To add the due date to the vendor transaction form and change payment settings for a transaction using the new form:
1. Click on Accounts receivable > Setup > Accounts receivable parameters
2. Select Settlements
3. Click on Update due date and cash discount date. This selection will add the due date to the vendor transaction list and allow you to more easily modify the due date and the cash discount dates for the transaction.
4. To enable this feature, we have added new fields to the vendor transctions. We will fill in those fields when a new transaction is completed. We will also fill in those fields when you open the new due date form. However, if you want to update all existing transactions immediately, click on the BUTTON NAME HERE and the fields will be updated. Click on BUTTON NAME HERE if you only want to store the information for new transactions. 

## Modifying the payment settings

The vendor transactions list page shows all transactions for a vendor. When you click on a due date for a transaction, a form will appear, showing the base date for due date and discount calculations, the due date, the payment terms, the cash discount terms, and the cash discount dates. 

Each field will have a different effect on the transaction when you edit it:
1. Edit the base date: the due date and discount dates will be changed as if the base date is the document date
2. Edit the due date: only the due date will change
3. Edit the discount dates: only the discount dates will change
4. Edit the payment terms: the due date will change based on the base date and the payment terms
5. Edit the cash discount terms: the cash discounts will change based on the base date and the cash discount terms
6. Click Close to save your changes.
