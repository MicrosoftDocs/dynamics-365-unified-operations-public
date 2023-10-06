---
# required metadata

title: Working with advanced auto charges
description: The charges feature in Microsoft Dynamics 365 Supply Chain Management has been extended with additional capabilties covering the ability to do compounding for sales quotation and sales order header charges and apply a charge category type 'specific unit' and 'specific unit match' to calculate a line charge to sales and purchase line charges. 
author: Henrik Andersen
ms.date: 10/04/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: henrikan
ms.search.validFrom: 2023-10-01
ms.dyn365.ops.version: 10.0.38
---

# Sequence and compound 
[!include [banner](../includes/banner.md)]

Based on the customer that you're working with or the item that you're selling, you might want to apply specific additional charges for order headers and order lines. For sales quotations and sales orders it is possible to compound header charges. 
 
An auto charge of level header can be set to compound which controls the value base upon which the auto charge is calculated. All header level charges (where customer is debit or credit) with a sequence equal to or lower than the sequence for the compound charge is added to the sum of line net amounts. This sum is referred to as 'Value base'. The value base can be either "Sum of line net amounts only" or "Sum including charge amounts". Compound is applied when the charge category is precentage only.  

In order to be able to calculate a compounded header charge, a charge sequence is required. The sequence on a charge, which can only exist on level header, determines the sequence in which header charges are sequentially calculated building up an interim header charge total. More interim totals can exist. Depending on the 'value base for header charges' setting, An interim header charge total is applied on top of the sum of line net amounts, including all line charges, and sales taxes ("Sum including charge amounts") or the sum of line net amounts only ("Sum of line net amounts only") to constitute a value base upon which subsequent compound charges are calculated. The sequence exists on a header charge for a sales order and a sales quotation. A sequence is set on the auto charge setup for header level and is inherited to the header charge on a sales quotation and sales order. Sequence is a prerequisite for compound. Sequence only has an impact when you have one or more charges set to compound. 

In cases where more header charges with the same sequence is applied, a position on the header charges on a sales quotation and sales order controls the order. The position determines the order in which the header charges are summed within the context of compound. The position is added runtime and is applied to the header charges on sales quotation and sales order header. Position only has an impact when you have one or more charges set to compound in auto charges. 

## Enable sequence and compound 
In order to leverage the ability to compound header charges, enable the feature 'Sequence and compound for customer charges' in feature management.
When this feature is enabled, new settings are availble from accounts receivable parameters to control the compounding. Also when this feature is enabled, then the colums 'Sequence', 'Compound', and 'Position' become available on header charges on sales quotations and sales orders.  

Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
2. On the **Prices** FastTab, make the following settings:
    - **Find auto charges for header** – Set to 'Yes'
3. On the **Charges** fasttab, make the following settings:
    - **Re-search on posting** – Specify whether header auto charges on sales orders and sales quotations should be re-searched when documents are confirmed or posted. Other manually added charges won't be affected during the re-search process. Set this to 'Yes' to ensure that the header charges setup in auto charges are always applied. 
    - **combine charges on combined invoices** – The parameter controls how auto charges are calculated when multiple sales orders are combined into a single invoice using the "summary update" function. Set this to "Yes" to first calculate the grand total of all sales orders included in the combined invoice and then apply the auto charge to that total. Set this to "No" to calculate a separate auto charge for each sales order included in the combined invoice. 
    - **value base for header charges** – 	This parameter determines the value base for calculating percentage-based header charges. You can select the option "Sum of line net amounts only" to calculate charges based on the sum of line amounts only. Alternatively, choose the option "Sum including charge amounts" to calculate charges based on the sum of line amounts, including line charges. 
With the "Sum including charge amounts" option, users can also include tax amounts in the value base by specifying tax codes that should be used to determine the tax amount. This can be defined on an individual auto charge line by clicking the button "Include taxes in value base," which will automatically appear when this option is enabled. Set this to "Sum of line net amounts only" to ensure compatibilty with charges calculation prior to enabling the feature 'Sequence and compound for customer charges'. 

## Working with sequence and compound 
To apply a charge set as compound, you must first setup the auto charge.

Follow these steps:

1. Go to **Accounts receivable \> setup \> Charges \> Auto charges**.
2. Select Level 'Header'
3. On the Action Pane, select **New** to create a charges.
4. In the header of the new record, set the following fields:
    - **Account code** – All
    - **Item code** – All
    - **Mode of delivery code** – All
    - **Charge description** – Enter the apropriate description.

5. On the Action Pane, select **Save**.
6. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Sequence** – 1
    - **Compound** – unchecked
    - **Currency** – USD
    - **Charges code** – Freight
    - **Category** – Fixed
    - **Charges value** – 100
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked

7. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Sequence** – 2
    - **Currency** – USD
    - **Charges code** – Handling
    - **Category** – Percentage
    - **Compound** – checked
    - **Charges value** – 2
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked

These charges can now be applied automatically onto a sales quotation or sales order. To apply the charges to a sales order, follow these steps:

1. Go to **Sales and Marketing \>  \> Sales orders \> All sales orders**.
2. On the Action Pane, select **New** to create a new sales order

Create the sales order for customer US-004, or any customer using USD as currency. 

3. In the header of the new sales order, select Header tab **Sell** and **Maintain charges** in the **Charges** group.

You will have two charge lines:
First line: Position=1, Sequence=1, Compound=unchecked, Charges code=Freight, Category=Fixed, Charges value = 100
Second line: Position=2, Sequence=2, Compound=checked, Charges code=Handling, Category=Percentage, Charges value = 2

Note, that the position equals the sequence from the auto charges setup. The position will differ from sequence in cases where there is a overlap in sequence numbering. it is the position which is used in the calcuation of the value base used for the charge set to compound. 

In this particular case, 2% charge os applied on top of the 100 USD fixed charge equalling 102 USD as total header charges (100+2). 

It is possible to change the assigned position, sequence, and compound values for a header charge applied from auto charges. It should however be done with caution as it will impact the the calcuation of the value base used for the charge set to compound. 

Consider a user doing the following changes to the below: 
Auto created first line: Position=1, Sequence=1, Compound=unchecked, Charges code=Freight, Category=Fixed, Charges value = 100
Autocreated second line: Position=2, Sequence=2, Compound=checked, Charges code=Handling, Category=Percentage, Charges value = 2

Change first line: Position=2, Sequence=1, Compound=unchecked, Charges code=Freight, Category=Fixed, Charges value = 100
Change second line: Position=1, Sequence=2, Compound=checked, Charges code=Handling, Category=Percentage, Charges value = 2

In this particular case, first 2% charge is applied. As the value base is 0, 2% results in a zero charge. Then the 100 USD fixed charge is added equalling 100 USD as total header charges (0+100). 

Alternatively do the following:

Change first line: Position=1, Sequence=1, Compound=unchecked, Charges code=Freight, Category=Fixed, Charges value = 100
Change second line: Position=2, Sequence=2, Compound=unchecked, Charges code=Handling, Category=Percentage, Charges value = 2

In this particular case first the 100 USD fixed charge is applied. As the 2% is not set to compound, they will calculated only based on the sum of the line amounts. Since the line amount is 0, 2% will equal a zero charge. Total sum of header charges will be 100 USD (100+0). 

In the case where a manipulation of the header charges automatically added from auto charge setup has been done and should be reverted, do the following: 

4. In the header of the new sales order, select Header tab **Header auto charges** in the **Calculate** group.

This action will restore the auto charges on the sales order header automatically added from auto charges to the values from the auto charge setup. Any manually added charges to the sales order header to will not be affected by this action. This action will not restore any order line charges. 

### Position, Sequence, and compound fields on header charges
**Position** is auto generated by system for all the auto charges line. It is an editable field and can be manually updated. Use this field to prioritize the calculation of the charge line, lower position charge line will be given higher priority.
**Sequence** is copied as-is from auto charges setup. It is possible to have overlap in sequence numbers in the auto charge setup. The order applied in determining the position number in case of sequence number overlap when applying charges from auto charge setup, is by most specific (customer) record first from the header level auto charge setup.
Sequence is an editable field and can be manually updated. To maintain the consistency with position, you should keep the sequence aligned in same order. 
**Compound** field can be edited for all the charges lines having category as “Percent”. Compounding will only be applied for auto created charge lines regardless. Note, that if a user checks Compound for a manually added charge line, then compounding is not performed for such a manually added charge line. Compound will be used to determine the value base for the charge line, if it is set to “Yes” then previously calculated header charges will also be summed in the value base. 

   
> [!NOTE]
        > It is possible to have overlaps of combined position and sequence number in scenarioes of deleting charges applied from auto charges, manually adding charges, followed by restoring the charges through the **Header auto charges** action. In such a case it will be the rec id of the charge record that determines the position when calculating the value base. It is recommended to avoid such scenarioes, as it will not be transparent to the user how the calculation of the value base is performed.


## Working with value base for header charges parameter setting
When calculation the absolute monetary charge amount resulting from a header charge of category type percentage, the calculation is performed on a value base. The value base can consist of the net amount accross all order lines or the net amoount accross all order lines including line changes, both with/without sales taxes. See below for examples of how the value base impacts the calculation. 

Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
2. On the **Charges** fasttab, make the following settings:
    - **value base for header charges** – 	Select the option "Sum of line net amounts only" to calculate charges based on the sum of line amounts only. 

With the auto charge setup done previously, do the following:
3. Go to **Sales and Marketing \>  \> Sales orders \> All sales orders**.
4. On the Action Pane, select **New** to create a new sales order

Create the sales order for customer US-004, or any customer using USD as currency. 
Create a sales line. Ensure that the line net amount is 100 USD
On the sales order line do the following:
5. Line ribbon **Financials**, **maintain charges**
6. Select **New** to add a line charge with the following values:
  - **Charge Code** – 	Freight
  - **Category** - Fixed
  - **charges value** - 10
  - **Currency** - USD
7. Select **Save**
8. On header action pane, tab **Sales order**, select **Totals**

Notice the amount for **Total Charges**. It contains the following: 10 USD (line charge fixed) + 100 USD (header charge fixed) + 4 USD (header charge percentage and compound (2% of 200: 100(line amunt)+100(header charge with lower position) = 114 USD

9. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
10. Open the **Prices** tab.
11. On the **Charges** fasttab, make the following settings:
    - **value base for header charges** – 	Change the option from "Sum of line net amounts only" to "Sum including charge amounts".

12. On the same sales order, on header action pane, tab **Sales order**, select **Totals**

Notice the amount for **Total Charges** has changed. It contains the following: 10 USD (line charge fixed) + 100 USD (header charge fixed) + 4.20 USD (header charge percentage and compound (2% of 210: 100(line amunt)+100(header charge with lower position)+10(line charge) = 114.20 USD

 > [!NOTE]
        > With **value base for header charges** set to "Sum including charge amounts", it is possible to have selective sales taxes included in the calculation of the value base. The sales taxes included in the value base used for calculating a percentage based header charge, is setup on the header level auto charge line setup under **include taxes in value base**. **Value base for header charges** set to "Sum including charge amounts# is is applicable for header charges of category percentage with/without compound.  

## Working with Re-search on posting parameter setting
Re-search on posting ensures that header charges are assessed against the auto charge setup for header level upon posting. The setting ensures auto charges setup as  tiered charges are automatically assessed. The assesment performed compares the header charges automatically applied against the setup in auto charges. It ensures that all the header charges automatically applied to a sales quotation and  sales order upon creation, are similar as setup in auto charges. Any automatically added header charge, which may have been manually changed or deleted, is retored on the sales quotation and sales order header. Any manually added header charge is left unchanged. The setting ensures that what is manifested in auto charge setup is always applied. 

> [!NOTE]
        >  Tiered charges are only supported for sales order, and as such is only included in the re-search for sales orders.

Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
2. On the **Charges** fasttab, make the following settings:
    - **Re-search on posting** – 	Select the option 'Yes'
    - Ensure that the **value base for header charges** is "Sum of line net amounts only".

With the auto charge setup done previously, do the following:
3. Go to **Sales and Marketing \>  \> Sales orders \> All sales orders**.
4. On the Action Pane, select **New** to create a new sales order

Create the sales order for customer US-004, or any customer using USD as currency. 
Create a sales line. Ensure that the line net amount is 100 USD
On the sales order header do the following:
5. Header ribbon **Sell**, **Maintain charges**
6. Select **Delete** to all the charges automatically added from auto charges
7. Select **New** to add a line charge with the following values:
  - **Charge Code** – 	Freight
  - **Category** - Fixed
  - **charges value** - 10
  - **Currency** - USD
7. Select **Save**
8. On header action pane, tab **Sales order**, select **Totals**

Notice the amount for **Total Charges**. It contains the following: 10 USD (charge fixed manually addeed) = 10 USD
 
9. Header ribbon **Sell**, **Confirm sales order**
10. Click **OK** to confirm the sales order

Back in  the sales order header do the following:
11. Header ribbon **Sell**, **Maintain charges**

Notice that the auto charges deleted previously have been re-applied on the sales order header. It contains the following: 10 USD (charge fixed manually added) + 100 USD (header charge fixed) + 4 USD (header charge percentage and compound (2% of 200: 100(line amunt)+100(header charge with lower position).

12. Close the form
Back in  the sales order header do the following:
11. Header ribbon **Sell**, **Totals**

Notice the amount for **Total Charges**. It contains the following: 10 USD (line charge fixed) + 100 USD (header charge fixed) + 4 USD (header charge percentage and compound (2% of 200: 100(line amunt)+100(header charge with lower position) = 114 USD

## Working with Combine charges on combined invoices parameter setting
This setting controls how header level auto charges are calculated when multiple sales orders are combined into a single invoice using the "summary update" function. Set this to "No" to have header level auto charges calculated per sales order included in the summary invoice, covering boh charge catery fixed and percentage, with/without compound. In scenarioes where header auto charges are setup with the intent of representing a per invoice charge rather than an per sales order charge, this may result in over charging. 

Consider the following scenario: 

Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
2. On the **Charges** fasttab, make the following settings:
    - **Re-search on posting** – 	Select the option 'Yes'
    - **Combine charges on combined invoices** – 	Select the option 'No'
    - Ensure that the **value base for header charges** is "Sum of line net amounts only".
    - 

2. Go to **Accounts receivable \> setup \> Charges \> Auto charges**.
3. Select Level 'Header'
4. On the Action Pane, select **New** to create a charges.
5. In the header of the new record, set the following fields:
    - **Account code** – All
    - **Item code** – All
    - **Mode of delivery code** – All
    - **Charge description** – Enter the apropriate description.

6. On the Action Pane, select **Save**.
7. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Sequence** – 1
    - **Compound** – unchecked
    - **Currency** – USD
    - **Charges code** – Freight
    - **Category** – Fixed
    - **Charges value** – 100
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked

8. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Sequence** – 2
    - **Currency** – USD
    - **Charges code** – Handling
    - **Category** – Percentage
    - **Compound** – checked
    - **Charges value** – 2
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked
      
9. Go to **Sales and Marketing \>  \> Sales orders \> All sales orders**.
10. On the Action Pane, select **New** to create a new sales order

Create **two** identitical sales orders for customer US-004, or any customer using USD as currency. 
Create a sales line. Ensure that the line net amount is 100 USD.
Pick and pack both sales orders.

11. In  **Sales and Marketing \>  \> Sales orders \> All sales orders** select the two sales orders
12. In header ribbon **Invoice**, Generate **Invoice**
13. In the **Posting invoice** page, set **Summary update for** to 'Invoice account' and **Arrange**
14. Press **OK**

Notice that the header charges are calculated per sales order. For each sales order a header charge of 100USD + 2% compound (equalling 4 USD) is applied creating a sum of 2x104=208 USD as total charges for the invoice. 

Repeat the same previous steps of creating two identical sales orders, pick and pack. Then do the following change:  
Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
2. On the **Charges** fasttab, make the following settings:
    - **Combine charges on combined invoices** – 	Change from 'No' to 'Yes'

3. In  **Sales and Marketing \>  \> Sales orders \> All sales orders** select the two sales orders created
4. In header ribbon **Invoice**, Generate **Invoice**
5. In the **Posting invoice** page, set **Summary update for** to 'Invoice account' and **Arrange**
6. Press **OK**

Notice that the header auto charges are re-searched and re-applied per the invoice. The customer will  be debited one instance of the fixed auto charge of 100USD instead of two instances of the 100USD fixed charge, since this charge is now applied on a per invoice and not on a per sales order. The charge total calculated for the invoice is one header charge of 100USD + 2% compound (equalling 6 USD (2% of off line amounts 100+100 and 100 fixed charge) = 106 USD as total charges. 

With this setup the fixed auto charge is applied once (per the invoice) and the percentage based charge set to compound is calculated from a value base which is 100 USD lower than compared to header charges calculated per sales order. 

7. Back in **Sales and Marketing \> Sales orders \> All sales orders**, lookup header ribbon **Sell** , **Maintain charges** for both sales orders.

Notice that, as part the combining charges on combined invoices, the auto charges only now are present on the first sales order. This is by intent to ensure that the combining of charges on combined invoices provides the correct charge calculation. 

> [!NOTE]
        > Auto charges are applied based on customer accounts on the sales orders, not invoice accounts for the invoice. In the cases where a summary update is done for sales orders for different customer accounts with the same invoice account, and where different header level auto charges are setup for the different customer accounts, then the customer account for the sales order, which is the **last** sales order for the summary update, will be the customer account upon which the header level auto charges are re-searched and re-applied upon invoicing. 

## Pricing management 
Feature “Sequence and compound for customer charges” works in conjunction with the 'Pricing management' feature. The “Pricing management" feature introduces changes to the setup and search of auto charges and changes to the behavior described in this topic. When “Pricing management feature” is enabled, then any charges setup using the auto charge setup available under **Accounts receivable \> Charges setup** will not apply. Only auto charges setup in the auto charge page specific to the “Pricing management" feature will be applied for sales orders and sales quotations. How to setup and work with auto charges in conjunction with the “Pricing management" feature see Pricing management.

## Limitations
The ability to compound charges and to define a value base upon which the compounding is performed, is available for sales quotation and sales order, not for purchase order. Similarly new capabilities are introduced which do not support all scenarioes. 

Therefore a few limitations exists of which the most important ones are listed below:

### Intercompany sales order sequence and compound auto charge application 
Feature “Sequence and compound for customer charges” is only supported for sales order and sales quotation. Not supporting purchase order has implications in intercompany scenarios, since the value base upon which to calculate header level charges with category percent will be different for purchase and sales and the concept of compounding is not supported for purchase order. In order not to block intercompany scenarios when feature “Sequence and compound for customer charges” is enabled, header charges for any sales order (also known as an intercompany sales order) which fulfils an purchase order will be applied and calculated as if the feature “Sequence and compound for customer charges” were not enabled. This means, that whether feature “Sequence and compound for customer charges” takes effect once enabled is contextual: In Intercompany scenarios, it does not take effect, in non-intercompany scenarioes it takes effect. This allows intercompany scenarios to flow seamlessly where the calculation logic for header charges will be the one used in purchasing. 

### Prorate and summary update
A header charge can be set to prorate. Sequence and compund provides the ability to re-search on posting and combine charges on combined invoices prevents the duplication of fixed charges from auto charges. Combining charges on combined invoices is  not supported for a header charge set to prorate. That means that a header charge (auto charge) set to prorate that is applied in a summary update scenario, will be re-searched and calculated based on the individual sales orders going into the summary update (the single invoice) always and not combined.

### Tiered charge and summary update
A header charge can be set to use amount tiers from/to. The tiers are evaluated based on the net amount for a sales order and the resulting header charge is applied to the sales order. Tiered charges together with Sequence and compund, work in the following manner: The tiers (from/to amounts) are assessed against the net amount for a sales order always. If the net amount for a sales order is within a tier, and the tiered charge is setup a category percentage, then the actual charge will be calculated from the 'Value base' selected while it has been assessed from the net amount only. For summary update, such as summary invoice, and when the system is configured to re-search on posting, then the tiers are assessed against the net amount for the first sales order included in the summary update only. The tiers are not assessed against the net amount across all order lines in the summary update. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]