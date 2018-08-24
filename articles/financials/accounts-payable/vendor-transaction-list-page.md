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

5. You can perform various tasks from this dialog box. Select one or more vouchers, and then select one of the following menus:

   - **View accounting** – All vouchers that are related to the selected documents appear. Select **Close** to close the dialog box.
   - **Export** – Export the selected vouchers to Microsoft Excel.
   - **View related payments** – All the payment journal transactions that were created in the payment journal that is related to the selected document appear. In addition, all the settlements that are related to those payments appear. The label of this menu also changes to **View settlements**. Select **View settlements** to show only the transactions that were shown when you first opened the  **View settlements** dialog box.
    - **Settle transactions** – This menu appears if the original document that was selected wasn't fully settled. When you select it, the **Settle transactions** dialog box appears, where you can select transactions for settlement.
    - **Undo settlements** – This menu appears if the original document that was selected was fully settled. When you select it, the **Undo settlements** dialog box appears, where you can undo the settlements that were done for that document.
