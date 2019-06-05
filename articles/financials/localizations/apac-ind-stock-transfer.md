---
# required metadata

title: Stock transfers for India
description:  This topic describes the stock transfer functionality that is available for India in Microsoft Dynamics 365 for Finance and Operations.
author: EvgenyPopovMBS
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventTransferOrders, ReqParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0

---

# Stock transfers for India

[!include [banner](../includes/banner.md)]

## Stock transfer overview

## Configure stock transfers

### Configure transfer pricing

### Configure stock transfer posting

### Configure master planning parameters

You can define a default transfer order type and a default price type for transfer orders that are created when firming planned orders in the **Master planning** module. On the **Master planning parameters** page, tab **Standard update**, select **Transfer type** and **Price type** in the **Firm - Transfer** group.

## Using stock transfers

You can create and post shipment orders for goods that are transferred from a supply warehouse (From warehouse) to a receiving warehouse (To warehouse). When an item is transferred at a higher price than the cost price of the item, the difference between the cost price and the transfer price may affect the total inventory value of the ledger account, so the value of the physical inventory and the financial inventory of the transaction do not match. To balance the physical inventory and the financial inventory after a stock transfer transaction, select the **Interim Transit** field on the **Transfer order** tab in the **Posting** form. The price difference that occurs due to the posting of the shipment order and the receipt order of the stock transfer transaction, along with the tax amount, is added to the interim transit account.

Use the following procedures to create and post a stock transfer order.


> [!NOTE]
> <P>The tax registration numbers are defined only for the company addresses. If the warehouses for the company are treated as separate taxable entities with separate tax registration numbers, you must set up the addresses for the warehouses in the <STRONG>Legal entities</STRONG> form. For more information, see <A href="https://technet.microsoft.com/en-us/library/jj664569(v=ax.60)">(IND) Legal entities (modified form)</A>.</P>



## Create a stock transfer order

1.  Click **Inventory management** \> **Periodic** \> **Transfer orders**.

2.  Press CTRL+N to create a transfer order. For more information, see [(IND) Transfer orders (modified form)](https://technet.microsoft.com/en-us/library/jj677831\(v=ax.60\)).
    
    The transfer number for the transaction is displayed in the **Transfer number** field, and the status is set to **Created** in the **Transfer status** field.

3.  In the **From warehouse** field, select the supply warehouse that the items are dispatched from.

4.  In the **To warehouse** field, select the receiving warehouse that the items are delivered to.
    
    The company address that is set up in the **Legal entities** form is displayed for both the supply warehouse and the receiving warehouse on the **From warehouse** tab and the **To warehouse** tab.

5.  In the **Transfer type** field, select **Stock transfer** to apply taxes for the transfer of items.
    

    > [!NOTE]
    > <P>If you select <STRONG>Transfer order</STRONG> in the <STRONG>Transfer type</STRONG> field, the shipment order is posted based on the standard transfer order process and the financial entries are not generated for the transaction. The <STRONG>Transfer type</STRONG> field is available in the <STRONG>Transfer orders</STRONG> form only when you select the <STRONG>Activate stock transfer</STRONG> check box in the <STRONG>Inventory and warehouse management parameters</STRONG> form.</P>



6.  On the **Dimensions** tab, in the **Configuration** and **Size** fields, update the inventory dimensions.
    

    > [!NOTE]
    > <P>The <STRONG>Dimensions</STRONG> tab is available only when you select <STRONG>Stock transfer</STRONG> in the <STRONG>Transfer type</STRONG> field.</P>



## Create and select shipment order details

1.  In the **Transfer orders** form, in the lower pane, on the **Lines** tab, press CTRL+N to create a new line.

2.  In the **Item number** field, select the item to transfer.

3.  In the **Transfer quantity** field, enter the quantity of the items to transfer.

4.  In the **Unit** field, modify the default unit of measurement, if required.

5.  In the **Price type** field, select the price type for the transaction, from the following options:
    
      - **Cost price** – The cost price, or the on-hand price, of the item is used for the transaction.
    
      - **Transfer price** – The transfer price that is set up for the item is used for the transaction.
    

    > [!NOTE]
    > <P>If the <STRONG>Price type</STRONG> is set to <STRONG>Transfer price</STRONG>, the quantity of the items that are defined for the combination of item and dimension in the <STRONG>Transfer price</STRONG> form is displayed in the <STRONG>Transfer quantity</STRONG> field, but it can be modified.</P>



6.  In the **Unit price** field, enter the cost price or the transfer price for one unit of the item.

7.  Click the **Tax information** tab to set up taxes for the transaction, and enter details. You can change the default information that is displayed in the fields.
    
    1.  In the **From warehouse** field group, the default sales tax registration number that is set up for the address on the **From warehouse** tab is displayed in the **Registration number** field.
    
    2.  The default taxpayer identification number (TIN) that is set up for the address on the **From warehouse** tab is displayed in the **Tax Identification Number (TIN)** field.
    
    3.  The default excise control code (ECC) that is set up for the address on the **From warehouse** tab is displayed in the **ECC number** field.
    
    4.  In the **To warehouse** field group, the default sales tax registration number that is set up for the address on the **To warehouse** tab is displayed in the **Registration number** field.
    
    5.  The default TIN that is set up for the address on the **To warehouse** tab is displayed in the **Tax Identification Number (TIN)** field.
    
    6.  The default ECC that is set up for the address on the **To warehouse** tab is displayed in the **ECC number** field.

8.  In the **From warehouse** field group, in the **Excise record type** field, select the excise record type for the supply warehouse.

9.  In the **To warehouse** field group, in the **Excise record type** field, select the excise record type for the receiving warehouse.
    
      - If the excise type that is selected for the From warehouse address and To warehouse address is **Manufacturer**, the **None**, **RG23A**, and **RG23C** options are available in the **Excise record type** field in the **From warehouse** field group and the **To warehouse** field group.
    
      - If the excise type that is selected for the From warehouse address and the To warehouse address is **Trader**, the **None** and **RG23D** options are available in the **Excise record type** field.
    
      - If the excise type that is selected for the From warehouse address and the To warehouse address is **None**, the **None**, **RG23A**, **RG23C**, and **RG23D** options are available in the **Excise record type** field.

10. In the **Tax** field group, in the **Tax group** field, select the tax group that applies to the transaction. The default item tax group that is set up for the item is displayed in the **Item tax group** field, but it can be modified.
    

    > [!NOTE]
    > <P>The taxes are calculated only for the tax codes that are commonly set up in both the <STRONG>Sales tax groups</STRONG> and the <STRONG>Item sales tax groups</STRONG> forms. If the default excise tariff code is set up for the item, it is displayed in the <STRONG>Excise tariff code</STRONG> field in the <STRONG>Excise</STRONG> field group, and it can be changed. The excise tariff codes are set up in the <STRONG>Excise tariff codes</STRONG> form.</P>



11. In the **Direct settlement** field, select the excise record type if the excise entries for the transaction use the direct settlement process.
    
      - If the excise type for the From warehouse address is set to **Manufacturer**, the **None**, **RG23A**, **RG23C**, and **PLA** options are available in the **Direct settlement** field.
    
      - If the excise type for the From warehouse address is set to **Trader** or **None**, only the **None** option is available in the **Direct settlement** field.
    
      - If the item that is selected on the **Lines** tab is a bill of materials (BOM) type and the company address with an excise type of **Manufacturer** is copied for the From warehouse, select the **DSA** check box to update the excise entries to the daily stock account (DSA). The **DSA** check box is editable only when the **Direct settlement** field is set to **None**. If the **DSA** check box is selected, the **Direct settlement** field is unavailable.

12. In the **VAT** field group, in the **Price type** field, select whether the value-added tax (VAT) retention is calculated based on the cost price of the item or the transfer price of the item.

13. In the **Retention %** field, enter the rate of VAT retention for the transaction.

14. In the **Retention tax code** field, select the VAT tax code to post the VAT retention percent. Based on the price type that is set up on the **Lines** tab and the **Tax information** tab, the retention percentage is posted to the VAT recoverable account for the selected VAT tax code.
    
      - If the **Price type** field on the **Lines** tab and the **Tax information** tab is set to **Cost price** or **Transfer price**, the VAT retention is calculated based on the net amount of the stock transfer transaction.
    
      - If the **Price type** field on the **Lines** tab is set to **Transfer price** and the **Price type** field on the **Tax information** tab is set to **Cost price**, the VAT retention is calculated based on the cost price of the item.
    
      - If the **Price type** field on the **Lines** tab is set to **Cost price** and the **Price type** field on the **Tax information** tab is set to **Transfer price**, the VAT retention is calculated based on the transfer price of the item.

15. In the **India sales tax** field group, in the **Form type** field, select the sales tax form type for the transaction.
    
    Based on the **From warehouse** address and the **To warehouse** address, the sales tax form types are available in the **Form type** field.

16. On the **Ship now** tab, in the **Ship now** field, enter the quantity of the items to transfer.

17. Click **Setup** \> **Tax** to open the **Temporary sales tax transactions** form. On the **Overview** tab, you can view the calculated tax amounts of the taxes that are applied to the transaction.

18. Click the **General** tab to modify the calculated tax amounts for the transaction.

19. Click **Formula designer** to view the formula that is defined for the item tax group that is selected on the **Tax information** tab in the **Transfer orders** form. Close the **Temporary sales tax transactions** form.

20. Click **Setup** \> **VAT retention** to open the **Temporary VAT retention** form to view the calculated VAT retention amount for the transactions.

21. Click **Posting** \> **Ship transfer order** to open the **Shipment** form. For more information, see [(IND) Transfer order shipment (modified form)](https://technet.microsoft.com/en-us/library/jj917355\(v=ax.60\)).

22. Select the **Edit lines** check box to edit the lines before posting and updating. The item lines that the **Ship now** field is updated for in the **Transfer orders** form are displayed on the **Lines** tab in the lower pane.

23. Click **OK** to post the shipment order for the specified quantity of items and return to the **Transfer orders** form. The price difference between the cost price and the transfer price of the item, along with the tax amount, is posted to the interim transit account. On the **Overview** tab, the transfer status is changed to **Shipped** in the **Transfer status** field.
