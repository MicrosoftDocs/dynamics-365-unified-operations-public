---
# required metadata

title: Register fixed assets acquisitions (Russia)
description: This topic walks you through registering fixed assets acquisitions for Microsoft Dynamics 365 for Finance and Operations in Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 09/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Register fixed assets acquisitions (Russia)

[!include [banner](../includes/banner.md)]

## Register a fixed asset acquisition using an invoice journal 

You can register the purchase of a fixed asset using the vendor invoice journal, if the fixed asset is not a warehouse item, and if it is not not requiered  to incur receipt and issue transactions that must be tracked. Before you register purchase a fixed asset, the asset must be registered on the <STRONG>Fixed assets</STRONG> page ().

1.  Click **Fixed assets (Russia)** \> **Common** \> **Fixed assets**. On the **Action pane**, click **Fixed asset** to create a fixed asset, or select a fixed asset record.

2.  Press the **New** to create a fixed asset with a **Scheduled** status.
    
3.  Click **Accounts payable** \> **Invoices** \> **Invoice journal**.

4.  Create a new journal and in the **Name** field, select the journal name.

5.  Click **Lines** to open the **Journal voucher** form.

6.  Create a new line.
    
    > [!NOTE]
    > <P>The posting date and voucher number are displayed in the <STRONG>Date</STRONG> and <STRONG>Voucher</STRONG> fields.</P>

7.  In the **Account type** field, select the  **Vendor** account type. 
  
8.  In the **Account** field, select a vendor code.

9. In the **Invoice** field, enter the invoice number for the fixed asset purchase.

10. In the **Description** field, enter any notes about the invoice.

11. In the **Credit** field, enter the invoice amount.

12. In the **Offset account type** field, select the account type for the current account.

13. In the **Offset account** field, select the ledger account for the fixed asset before acquisition.

14. On the **General** tab in the **Currency** field, select the current invoice currency.

15. On the **Fixed asset** tab in the **FA inventory number** field, select the fixed asset number.

16. Click **Post** \> **Post** to generate the vendor and ledger transactions.
    
    > [!NOTE]
    > After posting the invoice, the status of the fixed asset is set to **Bought** (**Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**). If the fixed asset number is specified in the invoice journal line and the invoice journal is not posted, you can't use this fixed exxet in another invoice journal.
    
# (RUS) Register a fixed asset acquisition using a purchase order 

You can register the purchase of a fixed asset via creating a purchase order.

1.  Click **Product information management** \> **Common** \> **Released products**.

2.  Create a new item in the fixed assets item group.
    
    > [!NOTE]
    > For more information, see "Create an item" in the Applications and Business Processes Help.

3.  In the **Item type** field, select **Fixed assets**, and then click the **General** tab.
4.  In the **FA group** field, select the fixed asset group.
    
    > [!NOTE]
    > The information provided on the purchase line determines whether the fixed asset belongs to the specified fixed asset group.

5.  Press CTRL+S or close the form.
6.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.
7.  Press CTRL+N to create a new line.
    
    > [!NOTE]
    > For more information, see "Create a purchase order" in the Applications and Business Processes Help.

8.  Click the **Lines** tab in the lower pane.
9.  In the **Item number** field, select the fixed asset item number, and then click the **General** tab.
10. In the **FA number** field, select the fixed asset number.
    
    > [!NOTE]
    > <P>If the <STRONG>Association with warehouse</STRONG> check box in the <STRONG>Fixed Assets Parameters</STRONG> form is selected, you can enter only one fixed asset on each purchase line.</P>
    > <P>If the <STRONG>Association with warehouse</STRONG> check box is not selected, several purchases can be recorded on a purchase line. The number of fixed assets included on the purchase line must correspond to the fixed asset numbers in the <STRONG>FA number</STRONG> field. Even though one item might correspond to several fixed assets or inventory assets, records must be set up for each individual asset.</P>

11. In the **FA number** field, select the fixed asset number.
    
    > [!NOTE]
    > <P>If the fixed asset number is not created, then press CTRL+ALT+F4 to create a new fixed asset line in the <STRONG>Fixed assets</STRONG> form.</P>

12. Click **Posting** \> **Invoice** to post the purchase order invoice and generate vendor and ledger transactions.
    > [!NOTE]
    > <P>The invoice details are displayed in the <STRONG>Fixed assets</STRONG> form. The status is displayed as <STRONG>Bought</STRONG> in the <STRONG>Status</STRONG> field. If the fixed asset number is specified in the purchase order line, the purchase order must be posted or deleted in order create an asset or inventory transaction.</P>    
    
## Reverse a fixed asset acquisition transaction    
    
When you create a reverse transaction, the information and amount of the original transaction are saved. By default, the reversal date and the original transaction date are the same. However, when reversing transactions, you can specify a reversal date that is different from the original transaction date. You can also reverse an amortization transaction using this process. To change the fixed asset status to **Operation**, you must cancel the write-off for all value models.

1.  Click **Fixed assets** \> **Common** \> **Fixed assets** \> **Fixed assets**. click **Value Models**\> **Transactions** to open the **FA Transactions** form.

2.  Select the fixed asset acquisition transaction, and then click **Reverse transaction** to open the **Reverse transaction** form.

3.  In the **Reverse date**, select the transaction reverse date.

4.  Click **OK**. A transaction is created in the **FA transactions** form that reverses the original transaction.

5.  Click **Voucher** to view the transaction in the ledger in the **Operation codes** form.
    

    > [!NOTE]
    > To change the status to **Scheduled**, run the reverse acquisition transaction for all value models. If the asset that was reversed was built from warehoused components, transactions are created to record the return of the components to the warehouse. When you reverse an acquisition transaction, the cost price of the returned components may differ from the current warehouse cost price. However, after warehouse closure, the components will reflect the current pricing.



      
