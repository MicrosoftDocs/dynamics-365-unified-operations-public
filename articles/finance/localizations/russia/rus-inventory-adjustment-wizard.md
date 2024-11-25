---
title: Inventory adjustment wizard
description: Learn about the Inventory adjustment wizard which is used to adjust on-hand inventory and transactions, including an outline on preliminary setup.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Inventory adjustment wizard

[!include [banner](../../includes/banner.md)]


The **Inventory adjustment** wizard is used to adjust on-hand inventory or inventory transactions. Before you adjust on-hand inventory, it must be closed. For more information about inventory closing, see [Inventory close](../../../supply-chain/cost-management/inventory-close.md) and [Inventory cost structure](rus-inventory-cost-structure.md).

You can adjust the amount of an item in the warehouse in a settlement with an arbitrary ledger account, and you can post a negative adjustment as a reversal.

In addition to adjusting the cost in the primary currency, you can adjust the cost in a secondary currency.

In the Russian localization, these features are available through the **Inventory adjustment** wizard. The wizard lets you use the following methods of adjustment: **Item cost price**, **Fixed cost price**, **Amount**, **Value**, **Percent**, and **From ledger account**. You can adjust the cost price of items by using miscellaneous charges. You can also use the wizard to determine the amount that must be allocated to the item cost price, based on the balance of the ledger account. You can select the set of dimensions to determine the account balance.

## Preliminary setup

Before you can adjust item cost by using miscellaneous charges and the **Inventory adjustment** wizard, verify that you've completed the prerequisites in the Inventory cost structure (here will be link to the article from content deliverable 148943) article.

Additionally, before you can adjust item cost in a secondary currency, verify that you've completed the prerequisites in the Inventory valuation in secondary currency (here will be link to the article from content deliverable 148936) article.

## <a name="adjust-item-cost-using-inventory-adjustment-wizard"></a>Adjust item cost by using the Inventory adjustment wizard

1. Go to **Inventory management \> Periodic tasks \> Closing and adjustment** or **Inventory management \> Periodic tasks \> Closing and adjustment in currency**.
2. On the Action Pane, select **Adjustment \> Wizard**.
3. On the **Welcome** page, select **Next**.
4. On the **Method of cost value adjustment** page, select the method of adjustment:

    - **On-hand** – Adjust on-hand inventory.
    - **Transactions** – Adjust transactions.

5. Select **Next**. Either the **Select on-hand inventory** page or the **Adjust transactions** page appears, depending on the method of adjustment that you selected.
6.  Specify a selection criterion, and then select **OK**.

    > [!NOTE]
    > If you know that both positive and negative adjustments will be made during the cost adjustment, this procedure should be completed in two separate stages: positive adjustment and negative adjustment.

7. On the **Selection result** page, you can view the on-hand items or item transactions that are selected for adjustment. Select the ellipsis button (**…**), and then select **Print** to print the list of lines for adjustment.
    
    ![Selection result page.](../media/1%20Selection%20result.png)

8. Select **Next**.
9. On the **Functions for calculating adjustment amounts** page, select the method for calculating adjustment amounts:

    - **Item cost price**
    - **Fixed cost price** (For more information, see the [Method for calculating an adjustment to a fixed cost price](#method-for-calculating-an-adjustment-to-a-fixed-cost-price) section.)
    - **Amount** (For more information, see the [Method for calculating an adjustment by using an amount](#method-for-calculating-an-adjustment-by-using-an-amount) section.)
    - **Value** (For more information, see the [Method for calculating an adjustment to a value](#method-for-calculating-an-adjustment-to-a-value) section.)
    - **Percent** (For more information, see the [Method for calculating a percentage adjustment](#method-for-calculating-a-percentage-adjustment) section.)
    - **From ledger account** (For more information, see the [Method for calculating adjustment amounts from a ledger account](#method-for-calculating-adjustment-amounts-from-a-ledger-account) section.)
        
     ![Functions for calculating adjustment amounts page where you can view items on hand or item transactions](../media/2%20Functions%20for%20calculating%20adjustment%20amounts.png)

10. Select **Next**.
11. Set the parameters for the selected method of adjustment. The parameters vary, depending on the method that you selected.
12. On the **Results of allocation** page, you can review the allocation results.

    - In the **Charges code** field, select a charge code for a line.

        > [!NOTE]
        > Alternatively, select the ellipsis button (**…**), and then select **Functions \> Charges code** to open the **Change Misc. charge code** page. Then, in the **Charges code** field, select the charges code for a line. To apply the charges code that you entered to all lines, set the **Apply to all** option to **Yes**.
        
        ![Results of allocation page.](../media/3%20Change%20misc.%20charge%20code.png)

    - In the **Amount of allocation** field, you can manually edit allocation amounts, except the amounts that are calculated by using the **From ledger account** method. When you manually edit this field, the allocation amount must be either negative for all lines or positive for all lines.
    
    ![Results of allocation page, Amount of allocation field.](../media/4%20Results%20of%20allocation.png)

13. Select **Next**.
14. On the **Posting** page, specify the details for posting the adjustment:

    - In the **Adjustment date** field, specify the date of the adjustment.
    - Set the **Storno** option to **Yes** to post vouchers to the general ledger as storno. This setting of this option can be changed only when the **Amount of allocation** value is negative. If the **Amount of allocation** value is negative, and the **Storno** option is set to **No**, the system posts the adjustment voucher as a reversal.
    - In the **Specification** field, select how transaction adjustments should be posted:

      - **Total** – Adjustments are posted for all items that have the same settings in the posting profile.
      - **Item group** – Adjustments are posted for all items that have the same item group.

         - **Item number** – Adjustments are posted for each item.

     -   In the **Note** field, enter a note for the adjustment.
     -   Set the **Corr. account profit/loss** option and the **Corr. account** field, depending on the account that an adjustment should be assigned to during posting:

         - If the miscellaneous charges code is entered on the item line, the adjustment is assigned to the offset account that is set up for the miscellaneous charges code.
         - If the miscellaneous charges code isn't entered on the item line, and the **Corr. account profit/loss** option on the **Posting** page is set to **Yes**, the adjustment is assigned in the standard manner to the offset profit or loss account that is set up on the **Inventory** tab of the **Posting** page (**Inventory management \> Setup \> Posting \> Posting**).
         - If the miscellaneous charges code isn't entered on the item line, and the **Corr. account profit/loss** option on the **Posting** page is set to **No**, the adjustment is assigned to the account that is specified in the **Corr. account** field.
                
     ![Posting page.](../media/5%20Posting.png)

15. Select **Next**.
16. On the **Finish** page, select the **Show ledger voucher list** check box to show the list of ledger vouchers that are posted, and then select **Finish** to post the adjustment.

To cancel adjustments that are done by the wizard, on the **Closing and adjustment** page, on the Action Pane, select **Cancellation**.

### Method for calculating an adjustment to a fixed cost price

1. Open the **Inventory adjustment** wizard, select the method of adjustment, and select on-hand items or item transactions, as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.
2. On the **Functions for calculating adjustment amounts** page, select **Fixed cost price**, and then select **Next**.
3. On the **Adjustment to fixed cost price** page, in the **Price** field, enter the fixed cost price, and then select **Next**.

    ![Adjustment to fixed cost price page.](../media/6%20Adjustment%20to%20fixed%20cost%20price.png)

4. Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.

### Method for calculating an adjustment by using an amount

1. Open the **Inventory adjustment** wizard, select the method of adjustment, and select on-hand items or item transactions, as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.
2. On the **Functions for calculating adjustment amounts** page, select **Amount**, and then select **Next**.
3. On the **Adjustment with amount** page, set the following fields:

    - In the **Amount** field, enter the amount.
    - In the **Allocation principle** field, select **Value** or **Quantity**.

    ![Functions for calculating adjustment amounts page where you select Amount and click Next](../media/7%20Adjustment%20with%20amount.png)

4. Select **Next**.
5. Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.

### Method for calculating an adjustment to a value

1. Open the **Inventory adjustment** wizard, select the method of adjustment, and select on-hand items or item transactions, as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.
2. On the **Functions for calculating adjustment amounts** page, select **Value**, and then select **Next**.
3. On the **Adjustment to value** page, set the following fields:

    - In the **Value** field, enter the value.
    - In the **Allocation principle** field, select **Value** or **Quantity**.

    ![Functions for calculating adjustment amounts page where you select Value and click Next.](../media/8%20Adjustment%20to%20value.png)

4. Select **Next**.
5.  Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard(#adjust-item-cost-by-using-the-inventory-adjustment-wizard) section.

### Method for calculating a percentage adjustment

1. Start the **Inventory adjustment** wizard, select the method of adjustment, and select on-hand items or item transactions, as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.
2. On the **Functions for calculating adjustment amounts** page, select **Percent**, and then select **Next**.
3. On the **Percentage adjustment** page, set the following fields:

    - In the **Percent** field, enter the percentage.
    - In the **Adjust** field, select **Positive on-hand inventory** or **On-hand inventory total**.

    ![Functions for calculating adjustment amounts page where you select Percent and click Next.](../media/9%20Percentage%20adjustment.png)

4. Select **Next**.
5. Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.

### Method for calculating adjustment amounts from a ledger account

This method lets you determine the adjustment amount based on the balance of the main account on a specific date. The adjustment amount can be all balances and the values of the selected combinations of financial dimensions. This method can be used, for example, to close specific accounts, such as procurement costs or warehouse maintenance costs, on the item cost price of inventory.

1. Open the **Inventory adjustment** wizard, select the method of adjustment, and select on-hand items or item transactions, as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.
2. On the **Functions for calculating adjustment amounts** page, select **From ledger account**, and then select **Next**.
3. On the **Balance from ledger account or dimensions** page, set the following fields:

    - In the **Main account** field, select the main account where the balance is determined.
    - In the **Balance on the date** field, specify the date when the balance is determined.
    - Select the **Balance account** option to determine the account balance, or select the **Balance from ledger account and dimensions** option to determine an account balance by using specific dimension values.
    - In the **Dimension set** field, select the set of dimensions to determine the account balance from. This field is available only if the **Balance from ledger account and dimensions** option is selected.

    ![Balance from ledger account or dimensions page.](../media/10%20Balance%20from%20ledger%20account%20or%20dimensions.png)

4. Select **Next**.
5. Select the amounts to include in the adjustment. You can use the **Select all** and **Deselect all** links to select and clear all lines.
6. In the **Allocation principle** field, select **Value** or **Quantity**.

    ![Balance from ledger account or dimensions page, Allocation principle field.](../media/11%20Balance%20from%20ledger%20account%20or%20dimensions.png)

7. Select **Next**.
8. Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section.

This method determines the balance of the account in the context of financial dimensions only to determine the amount of the adjustment. It doesn't automatically close the balance on the dimensions at the item cost price of the inventory.

#### Example

On account 26.100, the **Department** dimension accumulates the amounts that you want to allocate to the cost of inventory that is accounted for in specific warehouses. To complete this process in the system, follow these steps.

1. Close the inventory before the end of the closing period.
2. Open the **Inventory adjustment** wizard, select the **On-hand** method of adjustment, and then select **Next**.
3. On the **Select on-hand inventory** page, set the following fields:

    - On the **Parameters** FastTab, set the **Warehouse** option to **Yes**.
    - On the **Records to include** FastTab, select **Filter**, and specify a filter for a specific warehouse or warehouses.

4. Select **Next**.
5. On the **Functions for calculating adjustment amounts** page, select **From ledger account**, and then select **Next**.
6. On the **Balance from ledger account or dimensions** page, set the following fields:

    - In the **Main account** field, select main account **26.100**.
    - In the **Balance on the date** field, specify the date when the balance is determined.
    - Select the **Balance from ledger account and dimensions** option, and then, in the **Dimension set** field, select the dimension set.

7. Select **Next**.
8. On the next page, select the lines for the **Department** dimension values from which the balances should be assigned to the inventory of the selected warehouse or warehouses, and then select **Next**.
9. Set the **Corr. account profit/loss** option to **Yes**, and set the **Corr. account** field.
10. Complete the remaining steps of the adjustment as described in the [Adjust item cost by using the Inventory adjustment wizard](#adjust-item-cost-using-inventory-adjustment-wizard) section. Repeat the allocation operation for all warehouses and dimensions that you want to do allocation for.

As you've seen, the system lets you determine the adjustment amount based on the balance on the account in the context of the dimensions. You can also allocate it to the cost price of inventory or warehouse receipts.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
