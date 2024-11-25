---
title: Incoming VAT restoring
description: Learn how to restore previously deducted VAT amounts for fixed assets, including an outline on restoring VAT during export sales of goods and fixed assets.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Incoming VAT restoring
[!include [banner](../../includes/banner.md)]

You can restore previously deducted value-added tax (VAT) amounts in the following situations:

- During export sales of goods and fixed assets
- When fixed assets are used in VAT-free or export sales activities
- When fixed assets that were not fully depreciated are written off

## Restoring VAT during export sales of goods and fixed assets

Tax on export sales is restored in the period when the export sales occurred. Two methods can be used to determine the VAT amount that must be restored to the budget:

- **Direct method** – Use this method when you know the type of goods that were sold for export, and how much VAT was deducted for these goods.
- **Indirect method** – Use this method when you don't know the purpose that the product was purchased for, or whether VAT was deducted. In this case, the input VAT amount for each purchase invoice-facture of the current period is multiplied by the share of export revenue in the total revenue for the same period.

## Restoring VAT when fixed assets are used in VAT-free or export sales activities

- For fixed assets, the VAT amount is restored in the period when the export or non-taxable sales occurred. The VAT amount that must be restored is calculated by using the following formula:

    VAT amount to restore = VAT amount that was deducted from the purchase of the fixed asset × Export (non-taxable) ratio

    In this calculation, the export (non-taxable) ratio depends on the depreciation method that is used for the fixed asset:

    - For fixed assets that use the **Product output/mileage** depreciation method, the export (non-taxable) ratio is calculated by using the following formula:

        Export (non-taxable) ratio = **Output/run export** (or **Output/run nontaxable**) value of the current period ÷ Difference between the **Output/mileage** and **Output/run export** (or **Output/run nontaxable**) values of previous periods

    - For fixed assets that don't use the **Product output/mileage** depreciation method, the export (non-taxable) ratio is calculated based on the revenue of the current period.
    
- For realty objects, the VAT amount starts to be restored from the year when the event that caused the tax restoration occurred. It continues until the tenth year after the depreciation start date. The amount that must be restored is calculated by using the following formula:

    VAT amount to restore = VAT amount that was deducted from the purchase of the realty fixed asset × Cost of goods that were sold to export during the calendar year ÷ Total cost of goods that were sold in the calendar year

## Restoring VAT when fixed assets that were not fully depreciated are written off

The VAT amount that must be restored is calculated by using the following formula:

   VAT amount to restore = VAT amount that was deducted from the purchase of the fixed asset × Residual value of the fixed asset, excluding revaluation from the accounting value model ÷ Acquisition cost of the fixed asset from the accounting value model.

> [!NOTE]
> If a fixed asset was used for export or non-taxable activities during the period, and it was written off, the VAT amount that must be restored is calculated based on the write-off.

## Setup

### Set up parameters for VAT restoration

Use the **General ledger parameters page** to set up the parameters for VAT restoration.

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
2. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT restoration** section, set the following fields
  
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td> Revenue calculation method
</td>
<td> Select the method that is used for revenue calculation:
<ul>
<li> <strong>All</strong> – All customer invoices are included in the revenue calculation. </li>                            
<li> <strong>Indirect</strong> – Only customer invoices that don't have a direct relation to the purchase invoice are included in the revenue calculation. </li>
</ul>
</td>
</tr>
<tr>
<td> VAT restoring method 
</td>
<td> Select the method that is used for VAT restoration: 
<ul>
<li> <strong>Mixed</strong> – The VAT restoration amount is calculated differently, depending
on whether a direct connection with outgoing invoices is determined for
incoming invoices. 
    <ul>
    <li>   For incoming invoices where a direct connection with outgoing invoices is
    determined, the VAT restoration amount is calculated based on the proportion
    of the cost of goods that were sold to the cost of goods that VAT was
    deducted for. </li>
    <li>   For incoming invoices where a direct connection with the outgoing invoices
    isn't determined, the VAT restoration amount is calculated based on the
    export (non-taxable) ratio that is calculated for the current period. </li>
    </ul>
</li>
<li><strong>By factor</strong> – The VAT restoration amount is calculated based on the export
(non-taxable) ratio that is calculated for the current period.</li>
</ul>
</td>
</tr>
</tbody>
</table>

### Use fixed assets for export or VAT-free activities

1. On the **Fixed assets** page, select **FA usage**.
2. On the **Product/output mileage** page, in the **Output/run export** or **Output/run nontaxable** field, define how the fixed asset is used in export or non-taxable activities.

For more information about product/output mileage, see [Product/output mileage depreciation method](/dynamics365/unified-operations/financials/localizations/rus-depreciation-methods#product-output-mileage-depreciation-method).

## VAT restoration process

The VAT restoration process has two steps:

1. Calculate the VAT amounts that must be restored.
2. Process outgoing VAT, and include invoice-factures in the sales book.

### Calculate the VAT amounts that must be restored

Use the **VAT restoring journal** page to create, approve, and cancel VATrestoration amounts.

> [!NOTE]
> When you restore VAT amounts for fixed assets, the fixed asset depreciation for the period must be calculated and posted.

1. Go to **Accounts receivable \> Periodic tasks \> Sales book \> VAT restoring journal**. The **VAT restoring journal** page shows the data for incoming invoice-factures that VAT amounts must be restored for in the current period.

    ![VAT restoring journal page.](../media/1.%20VAT%20restoring%20journal.jpg)

2. In the **Date in the period** field, select the date in the reporting period to show the VAT details for.
3. Select **Restore VAT procedure \> 1. Update inventory links**, and then select **OK**.

    The Restore VAT procedure sets the connection between the incoming purchase invoices and the outgoing sales invoices. Make sure that the inventory is closed by the end of the period, because the connection between purchased and sold goods is identified based on inventory settlements during inventory closing.

4. Select **Restore VAT procedure \> 2. Update the journal** to update the data in the journal:

    - Set the **Update revenue amounts** option to **Yes** to update the revenue amount.
    - Set the **Delete previous calculation** option to **Yes** to recalculate previous calculations.

5.  Select **OK** to update the restored VAT amounts for the specified period. You can verify the following updated information:

    - The upper part of the **VAT restoring journal** page shows a list of incoming invoice-factures for which the VAT amount that was previously deducted is subject to restoration in the reporting period. For each incoming invoice, the **Direct VAT 18%**, **Direct VAT 10%**, **Indirect VAT 18%**, and **Indirect VAT 10%** fields show the VAT amounts that must be restored for goods. The **FA VAT 18%** and **FA VAT 10%** fields show the VAT amounts that must be restored for fixed assets.
    - The lower part of the **VAT restoring journal** page shows the lines of incoming VAT processing for the invoice. Based on updated inventory links, the system determines, for each line, whether the direct method or the indirect method should be used to calculate the VAT amount:

      - **Direct method** – The **Expense type** field is set to **Direct** (a connection between purchased and sold goods has been  established). The VAT amount that must be restored is calculated by using the following formulas:

          - **For goods:** VAT amount to restore (direct) = VAT amount that is deducted on the incoming invoice × Quantity of goods that are sold on export ÷ Total quantity that is purchased
          - **For fixed assets:** VAT amount to restore = VAT amount that is deducted from the purchase of the fixed asset × Export (non-taxable) ratio, where the export (non-taxable) ratio is calculated by using the following formula:

              Export (non-taxable) ratio = **Output/run export** (or **Output/run nontaxable**) value of the current period ÷ Difference between the **Output/mileage** and **Output/run export** (or **Output/run nontaxable**) values of previous periods

      - **Indirect method** – The **Expense type** field is set to **Indirect** (a connection between purchased and sold goods hasn't been established). The VAT amount that must be restored is calculated by using the following formula:

        VAT amount to restore (indirect) = VAT amount that is deducted in the current period × Export ratio (for the current period)

    Note the following information:
       
     - The preceding formulas are valid for the **Mixed** VAT restoration method. For the **By factor** VAT restoration method, the calculation formula for the indirect method is always applied.
     - In the lower part of the page, VAT amounts are grouped by expense type and tax type. In the upper part of the page, they are shown in the **Direct VAT** or **Indirect VAT** field. (VAT amounts that must be restored for fixed assets are shown in different fields.)
     - The **Fixed assets** tab shows information about the fixed asset object (inventory number and name) and the output/mileage (export and non-taxable) of the current period. The **FA VAT (export)**, **FA VAT (nontaxable)**, and **FA VAT (written-off)** fields show information about VAT amounts that are calculated for restoration.
     - You can include or exclude the incoming invoice-facture from the VAT restoration calculation by selecting or clearing the **Include** check box. VAT amounts will be recalculated.
     - For each line of an incoming invoice-facture where the **Expense type** field is set to **Direct**, you can review the line of the outgoing customer invoice on the **Customer invoice lines** tab.
     - Select **Inventory \> Cost explorer** to review the relation between sold items and bought items for lines where the **Expense type** field is set to **Direct**.
     - Select **Totals** to open the **VAT restoring journal total amounts** dialog box, where you can view the totals of all amounts that are calculated in the journal:

         - **Total revenue amounts** – The fields in this section show the amounts that are calculated on all invoices for the period. The **Export** field shows the amount that is calculated on export invoices for the period.

         - **Factors** – This section has two fields:

             - **Export, %** – The revenue share on export operations. This value is calculated by using the following formula:

                 Export, % = Export revenue ÷ Total revenue

             - **Nontaxable, %** – The revenue share on tax-exempt operations. This value is calculated by using the following formula:

                 Nontaxable, % = Tax-exempt revenue ÷ Total revenue
                
              > [!NOTE]
              > When revenue amounts are calculated, VAT amounts are excluded.

         - **VAT** – The fields in this section show the total VAT amounts that must be restored on export or non-taxable operations, and on fixed assets that aren't fully depreciated and are written off.
          - **Indirect costs**, **Direct costs**, and **Included fixed assets:** – The fields in these sections show the totals for direct and indirect VAT, including amounts for fixed assets that are used in export or non-taxable operations.

          ![VAT restoring journal total amounts.](../media/2%20VAT%20restoring%20journal%20totals.jpg) 

     - Select **Revenue calculation** to open the **Revenue calculation** dialog box, where you can view the list of customer invoices in the current period.  The list is generated based on the value of the **Revenue calculation method** field on the **General ledger parameters** page.

         ![Revenue calculation.](../media/3%20Revenue%20calculation.jpg)
           
         For each invoice in the **Revenue calculation** dialog box, you can perform the following actions:
         
          - Review revenue amounts in the **Total revenue**, **Export**, **Domestic market**, and **Not liable to VAT** fields.
              > [!NOTE]
              > For a domestic invoice, the **Sales tax code** field uses the **Standard VAT** or **Reduced VAT** sales tax type. For an export invoice, the **Sales tax code** field uses the **VAT 0%** sales tax type. For a non-taxable invoice, the **Sales tax code** field is blank.
           
          - Select or clear the **Include** check box to include or exclude an invoice from the calculation of revenue for the period. 
          - When you've finished, select **OK**. Then, on the **VAT restoring journal** page, select **Apply changes** to recalculate revenue amounts.

     - Select **VAT distribution** to open the **VAT distribution** dialog box, where you can view a list of export sales invoices. For each invoice, the system calculates the following information:

          - The amounts of VAT that were restored in the current period and distributed to each export invoice
          - The share of export invoice revenue in the total export revenue amount for the period

            ![Incoming VAT for indirect costs.](../media/4%20VAT%20distribution.jpg)
              
            This information is required to define the VAT amount that must be deducted when export is confirmed, or when the deadline for confirmation will expire but export isn't confirmed. This information is also used in the VAT declaration. For more information, see [VAT declaration (Russia)](/dynamics365/unified-operations/financials/localizations/rus-vat-declaration).

### Approve the VAT restoring journal

On the **VAT restoring journal** page, select **Restore VAT procedure \> 3. Approve the journal** to approve the journal.

After the journal is approved, no changes are allowed on this page, and you can go to the next procedure.

 > [!NOTE]
 > After the VAT restoring journal is approved in the period, you can no longer perform the following actions:
 >
 >  - Post customer invoices.
 >  - Run the **Incoming VAT processing** periodic task.
 >  - Run the **Canceling processed VAT** periodic task.

- If the VAT restoring journal isn't created for the period, a warning message appears during sales book closing.
- If the VAT restoring journal is created but isn't approved in the period, sales book closing is prohibited.
- If the VAT restoring journal is approved, but outgoing VAT processing isn't run, sales book closing is prohibited.

If no outgoing VAT is processed during a specific period, select **Restore VAT procedure \> Cancel approval of the journal** to cancel the approval of the VAT restoration journal.

### Outgoing VAT processing

Recoverable VAT amounts for incoming factures are approved on the **VAT restoring journal** page.

1. Go to **Accounts receivable \> Periodic tasks \> Sales book \> Parameters of VAT process** to configure the VAT processing parameters.
2. Create a new line, and enter the code for the incoming VAT processing operation.
3. In the **Operation type** field, enter **VAT restoration**.
4. In the **Restoration type** field, select one of the following values:

    -   **VAT restoring (export)** – The operation is a recovery that is caused by use for export.
    -   **VAT restoring (not liable to VAT)** – The operation is a recovery that isn't liable to VAT.
    -   **VAT restoring (FA writing-off)** – The operation is a recovery that causes a fixed asset write-off.

5. Set the **By default** option to **Yes** to indicate that this transaction is the default transaction for VAT processing.
6. Set the **Include in book** option to **Yes** to include factures that are processed by using this operation code in the sales book.
7. On the **Setup** FastTab, in the **Main account** field, specify the main account that is used to post processing operation codes. If the **Offset account** field is blank, the value from the posting group for the sales tax code is used instead. This value is set in the **Sales tax payable** field on **Ledger posting groups** page (**Tax \> Setup \> Sales tax \> Ledger posting groups**).
8. To process outgoing VAT, go to **Accounts receivable \> Periodic tasks \> Sales book \> Outgoing VAT processing**.

    When you post the outgoing VAT processing, the system generates tax and ledger transactions, and adds them to the **VAT processing log** page (**Accounts receivable \> Periodic tasks \> Sales book \> VAT processing log**).

    Processed factures are reflected in the sales book after it's updated.

    > [!NOTE]
    > If there is processed outgoing VAT in the period, the system doesn't allow you to cancel approvals by selecting **Restore VAT procedure \> Cancel approval of the journal** on the **VAT restoring journal** page. You must cancel outgoing VAT processing on the **Sales book (Canceling processed VAT)** page (**Accounts receivable \> Periodic tasks \> Sales book \> Canceling processed VAT**) and then cancel the approval of the VAT restoring journal.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
