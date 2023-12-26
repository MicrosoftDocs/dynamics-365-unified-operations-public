--- 
# required metadata 
 
title: Set up Accounts payable invoice matching validation
description: This article provides information on how to set up Accounts payable invoice matching validation. 
author: abruer
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up Accounts payable invoice matching validation

[!include [banner](../../includes/banner.md)]

Before you begin, make sure that the Invoice matching configuration key is selected. If your legal entity tracks expenses, such as freight, by using charges, make sure that the Charges configuration key is selected. Accounts payable invoice matching is the process of matching vendor invoice, purchase order, and product receipt information. Differences among these documents are called matching discrepancies. Matching discrepancies are compared with the tolerances that are specified. If a matching discrepancy exceeds the tolerance percentage or amount, match variance icons are displayed on the **Vendor invoice** page and the **Invoice matching details** page.

## Determine which invoice matching validation to use
Four different types of matching validation are available. 

- **Line level matching** – The most common type of matching is line matching. Line level matching can be two-way or three-way matching. The default line level matching can be specified for a legal entity on the **Accounts payable parameter** page. Two-way matching compares the unit price of the invoice to the unit price of the purchase order. Three-way matching additionally compares the invoice quantity to the matched product receipt quantity.
- **Invoice totals matching** – Match the total amounts on the invoice to the total amounts on the purchase order. This type of invoice matching includes the least amount of detail, so you can use this option to set up controls that minimize the staff time that is required to review invoice matching information. Six totals are compared, including Subtotal, Total discount, Charges, Sales taxes, Round off, and Invoice amount. The system will validate if any of these values on the invoice deviate from expected amounts by more than an acceptable variance.
- **Charges matching** – Match the charges information (amounts) on the invoice to the charges information (amounts) on the purchase order
- **Price totals for line item matching** – This type of matching is useful for companies that typically receive multiple invoices for a single purchase order line. If you typically receive only one invoice per purchase order line, this type of matching is not necessary. This matching requires that two-way or three-way matching is enabled and serves as a not-to-exceed net amount validation, based on a tolerance percentages and amounts. This type of matching compares price information for the net amount of each line on the invoice, and all pending and previously posted invoice lines, with the net amount of the corresponding purchase order line. The net amount is determined by the following formula: (Unit price * Line quantity) + Line charges - Line discounts. When matching price totals by percentage, the values will be compared using the transaction currency. When matching price totals by amount, the system compares the values using the accounting currency.

## Set up parameters to enable invoice matching validation
1. Go to **Accounts payable > Setup > Accounts payable parameters**.
2. Select the **Invoice validation** tab.
3. Select or clear the **Enable invoice matching validation** check box.
    * Select whether approval is required before an invoice that contains discrepancies for invoice matching can be posted. If set to **Allow with warning**, visual indication will display when a discrepancy for invoice matching exceeds the tolerance. However, you will be able to post the invoice. To use workflows together with invoice matching validation, make sure that the **Post invoice with discrepancies** field is set to **Allow with warning** to avoid having to approve multiple times.  
    * In the **Automatically update invoice header match status** field, select whether matching will be performed automatically during invoice data entry. The recommended setting is **Yes**, unless you are experiencing data entry performance concerns. Disabling automatic updates may enable faster system performance because the invoice matching validation will be bypassed during data entry. The data entry clerk will need to manually update the invoice's match status to see the invoice matching validation results when this is set to **No**.  
4. Set **Invoice totals matching**.
5. Select or clear the **Match invoice totals** check box to match actual invoice totals with expected totals.
    * Select whether an icon is displayed if a discrepancy for invoice matching exceeds the tolerance. You can select to display the icon when a positive discrepancy exceeds the tolerance, or when either a positive or a negative discrepancy exceeds the tolerance.  
    * For example, the tolerance is 5 percent, and the total invoice amount on the purchase order is 100.00. Therefore, a price match icon is displayed if the total invoice amount on the invoice exceeds 105.00. If you select **If greater than or less than tolerance**, the icon is also displayed if the invoice amount is less than 95.00.  
6. In the **Invoice totals tolerance percentage** field, enter the percentage variance that is acceptable. This value is the default value for the company. This value can be overridden for specific vendors, using the **Invoice Totals Tolerances** page. For information about how to override the invoice totals tolerance percentage for a specific vendor, see the [Set up invoice totals matching tolerance for vendors](set-up-accounts-payable-invoice-matching-validation.md#set-up-invoice-totals-matching-tolerance-for-vendors) section later in this article.
7. Set **Price and quantity matching**.
8. In the **Line matching policy** field, select a value to be used as the default policy for the legal entity that you are working with. **Not required** means there is no verification of individual invoice line prices to purchase order price or invoice quantities to packing slip quantities required. **Two-Way Match** means that the verification of invoice lines is required but only the purchase order and the supplier's invoice documents are involved in the verification. The product receipt isn't factored into the matching validations. **Three-Way Match** means that the invoice net unit price will be compared to the purchase order's net unit price and the matching product receipt quantity will be compared to the invoice quantity.
9. To allow a different level of matching to be applied for an item, vendor, vendor and item combination, or purchase order line, select a value in the **Allow matching policy override** field. The legal entity line matching policy can be overridden for a specific vendor, item, or vendor and item combination in the **Matching policy** page.
    * If you use a line matching policy of **Two-way matching** or **Three-way matching**, you can set up price tolerance percentages for your legal entity, items, and vendors on the **Item price tolerance** page. The legal entity default price tolerance will be set to zero percent for two-way and three-way matching. When vendor invoices are compared with the information on purchase orders, the applicable price tolerance percentage is searched for.   
10. To match price totals for line items on invoices, select a value in the **Match price totals** field. This type of matching is useful when the vendor sends multiple invoices for the same purchase order line. You can compare price information for the net amount of each line on the invoice and all pending and previously posted invoice lines, with the net amount of the corresponding purchase order line. Options include **None**, **Percentage**, **Amount**, or **Percentage and amount**.
11. In the **Purchase price total tolerance percent** field, enter a percentage of the variance you will accept. This field is available when **Match price totals** is set to **Percentage** or **Percentage and amount**..
12. In the **Purchase price total tolerance** field, enter an amount in the accounting currency. This field is available when **Match price totals** is set to **Amount**, or **Percentage and amount**.
13. In the **Display price total match icon** field, select when an icon is displayed if a discrepancy for invoice matching exceeds the tolerance. The icon can be displayed when a positive discrepancy exceeds the tolerance, or when either a positive or a negative discrepancy exceeds the tolerance.
For example, the tolerance is 5 percent, and the line price total on the purchase order is 10.00. Therefore, a price match icon is displayed if the line price total on the invoice exceeds 10.50. If you select **If greater than or less than tolerance**, the icon is also displayed if the line price total on the invoice is less than 9.50.
13. Set the **Charges matching**.
14. To match actual charges with expected charges, based on information on the purchase order, select the **Match charges** check box.

## Set up unit price tolerance percentages
Go to **Accounts payable > Setup > Invoice matching setup > Price tolerances** to define allowed price tolerance percentages. If you use a line matching policy of **Two-way matching** or **Three-way matching**, you can set up price tolerance percentages for your legal entity, items, and vendors. When vendor invoices are compared with the information on purchase orders, the applicable price tolerance percentage is searched for. The following is the default search order:
* Table/Table
* Table/Group
* Table/All
* Group/Table
* Group/Group
* Group/All
* All/Table
* All/Group
* All/All

The default legal entity price tolerance is 0 percent, and this price tolerance is applied to all items and all accounts (All, All). You can't delete the record for the default legal entity price tolerance.

By default, negative price discrepancies are allowed. However, you can't enter a negative number as the price tolerance percentage. To track negative price tolerance percentages, select **If greater than or less than tolerance** in the **Display unit price match icon** field on the **Accounts payable parameters** page. Then enter price tolerance percentages on the **Price tolerances** page.

## Set up matching policy override

Go to **Accounts payable > Setup > Invoice matching setup > Matching policy** to define the default entry for the **Matching policy** field for lines in the **Purchase order** page. This is an optional setup. Use this page to set up two-way matching or three-way matching for items, vendors, or item and vendor combinations. These entries allow you to define more granular matching policies than the legal entity matching policy that you defined on the **Accounts payable parameters** page. The default legal entity line matching policy applies to all items and vendors except those for which a different line matching policy is specified on this page.

On this page, select the **Matching policy level**. Select the level in the matching policy hierarchy to set line matching policies for.

- **Item and vendor** – Specify the matching policy for specific items that are purchased from specific vendors.
- **Item** – Specify the matching policy for specific items that are purchased from any vendor, except those that are specified at the item and vendor level.
- **Vendor** – Specify the matching policy for all items that are purchased from specific vendors, except those that are specified at the item and vendor and item levels.
  
The following hierarchy is used to determine the matching policy that is used:
  *  Item and vendor
  *  Item
  *  Vendor
  *  Legal entity
  
## Set up invoice totals matching tolerance for vendors

Go to **Accounts payable > Setup > Invoice matching setup > Invoice totals tolerances** to specify vendor-specific tolerances for invoice totals matching. The matching calculation uses the invoice totals tolerance percentage from the vendor account that is specified as the order account on the vendor invoice. If the vendor account doesn't have a specified tolerance percentage for invoice totals, the invoice totals tolerance percentage that's specified for the legal entity in the **Accounts payable parameters** page is used.

1. To specify tolerances for individual vendors that override the default tolerance, select a **Vendor account**.
2. Enter the variance percentage that you will accept for this vendor.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
