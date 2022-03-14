---
# required metadata

title: Billing schedule features
description: This topic explains some of the features available on a billing schedule such as pricing methods, escalation and discount, alignment dates, proration, reverse billing, and split item groups, 
  
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Pricing methods

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


You can use one of the following pricing methods to calculate the unit price of an item: 
* Flat (no example)
* Standard 
* Tier 
* Flat Tier

## Flat 

When the flat pricing method is used, the unit price for a billing schedule line item on the **All billing schedules** page can be edited to any value you want. When the flat pricing option is used, the **Price unit** is always 1. As a result, the **Unit price** and the **Net amount** for an item are the same. 

## Standard Price  (no Trade Agreement)

When the standard pricing method (without a trade agreement) is used, the unit price for a billing schedule line item is set up on the **Release product details** page under **Product information management**. Specifically, the unit price is from the **Base sales price** section and is calculated as follows: **Price** / **Price quantity**.

## Standard Price (with Trade Agreement)

The following example provides information using standard pricing calculations when a trade agreement exists. You can create trade agreements from the **Release product details** page.

An item has the following price brackets: 


| Qty From| Qty To| U of M|Price|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |100| Each|1.50|1|
|100|200 |Each|1.25|1|
|200|999999|Each|1.00|1|

Using the price brackets, assume the invoice quantity is 250. With the standard pricing method, the unit price is calculated as follows: 
* Quantity 250 is in the price quantity range 200 - 99999 , so the unit price is 1.00

>Net amount = (Quantity * Price) / Price unit = (250 * 1.00) / 100 = 2.50 

Another example for an invoice quantity of 100. With the standard pricing method, the unit price is calculated as follows: 
* Unit price = 1.50, which uses the price level that has the quantity of 100 
* Note: standard FROM and TO quantity matches if the quantity is >=FROM quantity and <TO quantity

>Net amount = (100 x 1.50) / 1 = 150

## Tier Price 

An item has the following price brackets: 

| Qty From| Qty To| U of M|Price|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |100| Each|1.50|10|
|100|200 |Each|1.25|10|
|200|999999|Each|1.00|10|

Using the price brackets, assume the invoice quantity is 250. With the tier pricing method, the net amount is calculated. After calculating the net amount, you can obtain the unit price by dividing the new amount by the quantity. Review the sequence of events to obtain the unit price: 
1. Get the prices of the items based on the pricing brackets: 
   * First hundred items: 100 x 1.50  = 150.00 
   * Second hundred items: 100 x 1.25 = 125.00
   * Remaining items: 50 x 1.00 = 50.00
1. Get the net amount. <br />Net amount =  (150.00 / 10) + (125.00 / 10) + (50.00 /10) = 15.00 + 12.50 + 5.00 = 32.50
1. Use the net amount and quantity to obtain the unit price. 
>Unit price = 32.50 / 250 = .13

## Flat Tier Price 

The price brackets are set as follows: 

| Qty From| Qty To| U of M|Flat tier amount|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |50| Each|100.00|50|
|50|200 |Each|150.00|200|

The following invoices show the unit prices with the different quantities purchased. The Net amount is calculated first, then the unit price.  

|Invoice|Quantity Purchased|Unit Price|Net Amount|
| :------------- |:-------------:| :------|------:|
|1|25| 2.00 / 25 = 0.08|100 / 50 = 2.00|
|2|20 |2.00 / 20 = 0.10|100 / 50 = 2.00|
|3|50|2.00 / 50 = 0.04|100 / 50 = 2.00|
|4|60|0.75 / 60 = 0.0125 = 0.01|150 / 200 = 0.75|


<table class="drcr"><col><col><col><col><thead><tr class="heading"><td>Invoice</td><td>Quantity Purchased</td><td>Unit Price</td><th>Net Amount</th></tr></thead><tbody><tr><td>1</td><td>25</td><td>2 / 25 = 0.08</td><td>100 / 50 = 2</td></tr><tr><td>2</td><td>20</td><td>2 / 20 = 0.1</td><td>100 / 50 = 2</td></tr><tr><td>3</td><td>50</td><td>2 / 50 = 0.04</td><td>100 / 50 = 2</td></tr><tr><td>4</td><td>60</td><td>0.75 / 60 = 0.0125 = 0.01</td><td>150 / 200 = 0.75</td></tr></tbody></table><div>

  ---

# Escalation and discount

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule line] > [click Escalation and discount]

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [click a billing schedule] > [click Escalation and discount] 


This topic explains how to apply and process an escalation or discount for a billing schedule or a billing schedule line. 
* An escalation is a price increase for a future billing period where the invoice has not yet been created.
* A discount is a price reduction for a future billing period where the invoice has not yet been created.

Escalations and discounts cannot be applied to a billing schedule retroactively. For example, you wanted to apply and process an escalation to a billing schedule three months in the past. In Subscription billing, it is not possible to "catch up" on a price increase that was to happen three months ago. 

You can apply the escalation or discount to a billing schedule or billing schedule line in one of the following ways: 
* from the **All/Active billing schedules** list 
* to the billing schedule displayed on the Billing schedule
* to a specific Billing schedule line

## Apply Escalation or Discount

To apply an escalation or discount to a billing schedule, follow these steps: 
1. Select a billing schedule or a billing schedule line.
2. Select **Escalation and discount** from either the Escalation and discount tab or the Escalation and discount action on the billing schedule line.
3. Select the **Consumer price index calculation** for the escalation or discount. This is only used if a consumer price index is used to calculate the escalation or discount. 
4. For each escalation or discount line you add, do the following: 
   a. Select **New**. 
   b. For a discount, select the **Discount** checkbox.   
   c. For an escalation, leave the **Discount** checkbox cleared. 
   d. Specify the **Start date** and select the **Frequency**. 
   e. For deferral items that use the unbilled revenue feature, specify the **End date**. 
   f. Specify the **Percentage**, **Amount**, or **Consumer price index schedule** for the escalation or discount. 
   g. Specify the **End date**.
5. Select **OK**.

## Fields

This page contains the following fields: 

|Field|Description|
|:-----|:-----|
|**Item number**|Displays the item number for the billing schedule line.  Available when this page is opened for a billing schedule line item. |
|**Consumer price index calculation**|Select to determine the method used for the Consumer price index escalation calculation:<br />* **Prior consumer price index**: Uses the previous Consumer price index value for the escalation calculation.<br />* **Base consumer price index**:  Uses the base Consumer price index value for the escalation calculation.|
**Line Grid**|
|**Discount**|Select whether the change in the amount is an escalation or discount:<br />* **Selected**: The change is to apply a discount to the billing schedule or billing schedule line. <br />* **Cleared**: The change is to apply an escalation to a billing schedule or a schedule line. <br />This value cannot be edited for items that use the unbilled revenue feature. Also, discounts cannot be applied to items that use revenue splitting. |
|**Start date**|Select the start date for the escalation or discount. |
|**Frequency**|Select the frequency of the escalation or discount: **None**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**. |
|**Percentage**|Type the percentage for the escalation or discount. |
|**Amount**|Type the escalation or discount amount.|
|**Consumer price index schedule**|Select the Consumer price index schedule that is used for the calculations. |
|**End date**|Select the end date for the escalation or discount. <br />This value is required for items that use the unbilled revenue feature. |
|**Deferral schedule number**|Displays the deferral schedule number. <br />Available only when this page is opened from the billing schedule line level. |
|**Journal batch number**|Displays the journal batch number. <br />Available only when this page is opened from the billing schedule line level. |
|**Total discount amount**|Displays the total sum of the discount amount for all lines in the grid. <br />Available only when this page is opened from the billing schedule line level. |
|**Current short-term unbilled revenue amount**|Displays the current short-term unbilled revenue amount. <br />This amount appears only when the a short-term deferral method is selected on the **Recurring Contract Billing Parameters** page and the accounts are set up on the **Unbilled Revenue Setup** page for the line item. |
|**Current long-term unbilled revenue amount**|Displays the current long-term unbilled revenue amount. <br />This amount appears only when the a short-term deferral method is selected on the **Recurring Contract Billing Parameters** page and the accounts are set up on the **Unbilled Revenue Setup** page for the line item. |

---
  
# Proration examples

This topic explains calculations for proration, which can be based on the number of days or number of months. The method used for the proration calculation is set on the **Recurring contract billing parameters** page. The proration method affects how the amounts are calculated for a billing schedule in the following situations: 
- Initial creation
- Application of an escalation or discount
- Termination
- Placement or removal a hold 
- Addition of support or renewal 

The proration method also affects the calculations in the monthly recurring revenue (MRR) report. 
</div><div>

## Example 1 proration

The annual amount of a billing schedule is $5000. The start date is August 12, 2019; the end date is December 22, 2019. The billing frequency is annually. 
- **Daily**
  - Number of days = End date - Start Date + 1 = 133 days
  - Number of days in the year = August 11, 2020 - August 12, 2019 + 1 = 366
  - Prorated amount = 5000 * (133/366) = 1816.84
- **Monthly**
  - Start month portion = (31 - 12 + 1)/31 = 20/31
  - Middle months = 3
  - End month portion = 22/31
  - Prorated amount = 5000/12 * [(20/31) + 3 + (22/31)] = 1814.52

## Example 2 proration

The annual amount of a billing schedule is $12000. The start date is August 1, 2019; the end date is December 31, 2019. The billing frequency is annually. 
- **Daily**
  - Number of days = End date - Start Date + 1 = 153 days
  - Number of days in the year = July 31, 2020 - August 1, 2019 + 1 = 366
  - Prorated amount = 12000 * (153/366) = 5016.39
- **Monthly (Full Month)**
  - Number of months = 5
  - Total months = 12
  - Prorated amount = (12000 * 5)/12 = 5000

---

# Reversing a period billing 

This topic provides an example that shows how to reverse the billing of a period for a schedule line. 

A billing schedule has the following one line only: 
- Billed monthly for 12 months from January to December. 
- Invoices have been created for all periods up to April (for example, the **Billed** check box is marked on the **View billing detail** page. 

You want to reverse the invoice for the April billing period. 

Since an invoice for the April billing period has been created, the **Billed** status for the detail cannot be removed. To be able to reverse the April billing, you must create an offsetting credit note for the line:
1. In the **All billing schedules** page, create a new schedule line for the same item. 
2. Change the **Quantity** of the item to a negative value of the original quantity. 
3. Set the **Billing frequency** to **One-time**. 
4. Set the start and end dates to the same as the billing detail line for which you want to create a credit note. In this example, 4/1/2019 to 4/30/2019.
5. Save the changes. 
6. Open the **Generate invoice** page and create the sales order with the credit note for this period.   
Optionally, you can select the option to post the invoice as well. 

When you review the line for the billing schedule, the new line has a link to the credit note.   
Also, the original line still has a link to the original April invoice. 

> **Note:** If the sales invoice had not been created for the April billing period, you could simply delete the sales order, and the **Billed** status would be cleared. But because the invoice had already been created, you must create the credit note by following the above steps. 

---

# Split item group examples

This topic provides examples split item groups to promote understanding of item group functionality in Subscription billing. 

## Customer Case

In this example, the setup is as follows: 
- On the **Recurring Contract Billing Parameters** page, **Split by item group** is selected and **Unique schedule type** is **Customer**. 
- The following item groups have been created: PREFIX, DATAHUB, and SPP. 
- Customer US-001 has multiple billing schedules where the item group is PREFIX or DATAHUB. 
- Customer US-002 has multiple billing schedules where the item group is PREFIX or SPP. 


| Billing Schedule Number| Customer|Item Group|
| :------------- |:-------------:| :-------------| 
| SCH001| 	US-001 |PREFIX |
| SCH002| 	US-001| DATAHUB |
| SCH003| 	US-002|  PREFIX|
| SCH004| 	US-002 | SPP|


Customer US-001 purchases a renewal item with item group PREFIX. This transaction is a new sales order: 

| Sales Order # | Customer|Main Item | Renewal Item | Renewal Item Group| Billing Schedule Number|
| :------------- |:-------------:| :-------------| :-------------| :-------------| :-------------| 
| #0001| 	US-001 |D0001 |D0002|PREFIX|SCH001|

When the invoice for the sales order is posted, the renewal item is automatically added to the existing billing schedule (SCH001) for the customer. This billing schedule uses the item group PREFIX. All renewal items that have the same item group are put into the same billing schedule.

**Header**
 
| Billing Schedule Number| Customer|Item Group|
| :------------- |:-------------:| :-------------| 
| SCH001| 	US-001 |PREFIX |

**Line**

| Billing Schedule Number| Customer|Item Group|
| :------------- |:-------------:| :-------------| 
| SCH001| 	US-001 |D0002 |

Customer US-001 purchases a renewal item with item group SPP. This transaction is a new sales order: 

| Sales Order # | Customer|Main Item | Renewal Item | Renewal Item Group| Billing Schedule Number|
| :------------- |:-------------:| :-------------| :-------------| :-------------| :-------------| 
| #0002| 	US-001 |D0003 |D0004|SPP||

Currently, customer US-001 does not have a billing schedule that uses the item group SPP. As a result, a new billing schedule is created: 

**Header**
 
| Billing Schedule Number| Customer|Item Group|
| :------------- |:-------------:| :-------------| 
| SCH005| 	US-001 |SPP |

**Line**

| Billing Schedule Number| Customer|Item Group|
| :------------- |:-------------:| :-------------| 
| SCH005| 	US-001 |D0004 |

## Multiple Billing Schedules, Same End User and Customer

In this example, the setup is as follows: 
* On the **Recurring Contract Billing Parameters** page, **Split by item group** is selected and **Unique schedule type** is **End user**. 
* On the **End users** page customer and end user relationships are set up. 

| Customer account| End user account|
| :------------- |:-------------| 
| US-001| US-221 | 

Multiple billing schedules are created for the customer and end user combination. With **Split by item group** selected on the **Recurring Contract Billing Parameters** page multiple billing schedules for the same customer and end user relationship can be created. 

| Billing schedule number| Customer|End user account|Header item group|
| :------------- |:-------------:| :-------------| :-------------| 
| SCH005| 	US-001 |	US-221 |	IG1|
| SCH006| 	US-001 |	US-221 |	IG2|
| SCH007| 	US-001 |	US-221 |	IG3|

On the **Item setup** page, create support and renewal item relationships.

| Item code  | Item relation|Support item|Renewal item| Renewal item group|
| :------------- |:-------------:| :-------------| :-------------| 
| Table| 	D001|	ITEM27 |D007|	IG1|
| Table| 	D002 |	ITEM28 |D005|	IG2|
| Table| 	D003 |	ITEM29 |D006|	IG3|

A sales order with items are from the **Item Setup** page are created for customer US-001. When creating the sales order, you can open the **Support and Renewal Process** page and specify the **End user account** and specify any other information for the renewal item. 

When the invoice for the transaction is created and posted, different billing schedules are created for the customer-end user and item group combination. More than one line in the same sales order can be assigned to the same billing schedule. 

| Sales order # | Customer|End user account | Main item | Support item |Renewal item| Billing schedule number|
| :------------- |:-------------:| :-------------| :-------------| :-------------| :-------------|:-------------| 
| #0001| 	US-001 |US-221|D001|ITEM27|D007|SCH005|
| #0001| 	US-001 |US-221|D002|ITEM28|D005|SCH006|
| #0001| 	US-001 |US-221|D003|ITEM29|D006|SCH005|


