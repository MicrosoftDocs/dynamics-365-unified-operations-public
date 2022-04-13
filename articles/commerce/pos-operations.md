---
# required metadata

title: Online and offline point of sale (POS) operations
description: This topic provides details about the point of sale (POS) operations in Dynamics 365 Commerce. It specifies where in the application the operations can be invoked, and whether they are available in offline mode.
author: jblucher
ms.date: 02/16/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2017-09-27
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Online and offline point of sale (POS) operations

[!include [banner](includes/banner.md)]

Most actions that users take in the point of sale (POS) are considered operations. Operations are configured and managed in the Dynamics 365 Commerce back office. Many operations can be added to buttons in the POS button grid. Users can then select the buttons to invoke the operations and perform their function. Other operations are part of the main POS application, and are invoked either from on-screen buttons or as part of other workflows or processes.

The following table provides details about the operations that are available in Modern POS and Cloud POS. The table also specifies where in the application the operations can be invoked, and whether they are available when the POS is in offline mode.

Some operations aren't currently available in Modern POS or Cloud POS. Some of these operations are locale-specific operations that require additional extensions and configuration. Others are features from Microsoft Dynamics AX 2012 that aren't currently supported.

The following columns specify where the operations can be invoked:

- **Button grid** – The operation can be assigned to buttons in POS button grids, which are part of a POS screen layout.
- **Transaction screen** – The operation can be invoked from POS button grids that are configured on the POS transaction screen.
- **Welcome screen** – The operation can be invoked from POS button grids that are configured on the POS welcome screen.

> [!NOTE]
> The operations listed below apply to the latest version of Commerce. Some operations may have changed or may not be available in previous versions.


| ID | Operation | Description | Button grid | Transaction screen | Welcome screen | Available offline | Locale-specific |
|----|-----------|-------------|-------------|--------------------|----------------|-------------------|-----------------|
| 707 | Activate device | Activate the current device by allowing an authenticated user to provide connection information and assign a device and register ID. | No | No | No | No | No |
| 134 | Add affiliation | Add a preselected affiliation to a transaction. Select the affiliation on the **Button properties** page. | Yes | Yes | No | Yes | No |
| 135 | Add affiliation from list | Add an affiliation to a transaction by selecting it in a list. | Yes | Yes | Yes | Yes | No |
| 137 | Add affiliation to customer | Add an affiliation to a customer on the **Customer details** page. | No | No | No | Yes | No |
| 138 | Remove affiliation from customer | Remove an affiliation on the **Customer details** page. | No | No | No | Yes | No |
| 643 | Add coupon code | Add a coupon by entering its code in the POS. | Yes | Yes | No | Yes | No |
| 141 | Add header charges | Add a misc charge to the order header. | Yes | Yes | No | No| No |
| 141 | Add line charges | Add a misc charge to a selected sales line. | Yes | Yes | No | No| No |
| 117 | Add loyalty card | Prompt the user to enter a loyalty card number that will be added to the current transaction. | Yes | Yes | No | Yes | No |
| 136 | Add serial number | This operation lets the user specify a serial number for the currently selected product. | Yes | Yes | No | Yes | No |
| 1214 | Add shipping address | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 519 | Add to gift card | Add money to the specified gift card. | Yes | Yes | No | No | No |
| 6000 | Allow skip fiscal registration | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 1212 | Bank drop | Record the amount of money that is sent to the bank and other information, such as the number of the bank bag. | Yes | Yes | Yes | Yes | No |
| 923 | Bank totals verification | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 915 | Blank operation | This operation represents a customizable button that a software developer can programmatically change for any specialized operation that the business requires. | Yes | Yes | Yes | Yes | No |
| 1053 | Blind close shift | Set the current shift to blind closed, and sign the user out. A blind-closed shift is closed to additional transactions but is still open to drawer operations, such as tender removal and tender declaration. | Yes | Yes | Yes | No | No |
| 310 | Calculate total | When discount calculation is delayed, this operation initiates the calculation for the current transaction. | Yes | Yes | No | Yes | No |
| 642 | Carry Out All Products | Set the mode of delivery for all lines to **Carryout**. | Yes | Yes | No | Yes\* | No |
| 641 | Carry Out Selected Products | Set the mode of delivery for the selected lines to **Carryout**. | Yes | Yes | No | Yes\* | No |
| 647 | Change mode of delivery | Change mode of delivery for preconfigured shipping sales lines. | Yes | Yes | No | No| No |
| 1215 | Change password | This operation lets the POS user change their password. | Yes | Yes | Yes | No | No |
| 123 | Change unit of measure | Change the unit of measure for the selected line item. | Yes | Yes | No | Yes | No |
| 639 | Clear default sales representative on transaction | Remove the commission sales group (sales rep) from the transaction. | Yes | Yes | No | Yes | No |
| 106 | Clear quantity | Reset the quantity on the currently selected line to **1**. | Yes | Yes | No | Yes | No |
| 640 | Clear sales representative on line | Remove the commission sales group (sale rep) from the currently selected line. | Yes | Yes | No | Yes | No |
| 121 | Clear salesperson | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 1055 | Close shift | Close the current shift, print a Z report, and sign the user out of the system. | Yes | Yes | Yes | No | No |
| 139 | Conclude transaction | Prompts user to select payment method | Yes | Yes | No | Yes | No |
| 925 | Copy the bank check | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 620 | Create customer order | Convert the POS transaction to a customer order. | Yes | Yes | No | Yes\* | No |
| 621 | Create quotation | Convert the POS transaction to a sales quotation. | Yes | Yes | No | Yes\* | No |
| 636 | Create retail transaction | Create a standard sales transaction when the default POS behavior is to create customer orders. | Yes | Yes | No | Yes | No |
| 600 | Customer | Add the specified customer to the transaction. | No | No | No | Yes | No |
| 1100 | Customer account deposit | Make a payment to a customer's account. | Yes | Yes | Yes | Yes | Yes |
| 612 | Customer add | Create a new customer record. | Yes | Yes | Yes | Yes† | No |
| 603 | Customer clear | Remove the customer from the current transaction. | Yes | Yes | No | Yes | No |
| 602 | Customer search | Search for a customer record by navigating to the customer search page in the POS. | Yes | Yes | Yes | Yes | No |
| 609 | Customer transactions | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 917 | Database connection status | View the current connection settings, and switch between online and offline modes. | Yes | Yes | Yes | Yes | No |
| 1200 | Declare start amount | Declare the amount that is in the cash drawer when the day or shift starts. | Yes | Yes | Yes | Yes | No |
| 132 | Deposit override | Override the default deposit for customer orders. | Yes | Yes | No | Yes\* | No |
| 913 | Design mode disable | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 912 | Design mode enable | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 1217 | Disassemble kits | Disassemble a kit into its component products. | Yes | Yes | Yes | Yes | No |
| 624 | Display refund amounts | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 513 | Display total | Show the balance of the transaction on the customer display. | Yes | Yes | Yes | Yes | No |
| 623 | Edit customer | Edit the current customer's details. | Yes | Yes | No | No | No |
| 614 | Edit customer order | Recall the selected order so that it can be modified in the POS. | No | No | No | No | No |
| 615 | Edit quotation | Recall the selected quotation so that it can be modified in the POS. | No | No | No | No | No |
| 518 | Expense accounts | Record money that is removed from the cash drawer for occasional expenses. | Yes | Yes | Yes | Yes | No |
| 919 | Extended log on | Assign or remove permission to sign in by scanning a bar code or swiping a card. | Yes | Yes | Yes | Yes | No |
| 1201 | Float entry | Add additional money to the current drawer or shift. | Yes | Yes | Yes | Yes | No |
| 1218 | Force unlock peripheral | The system uses this operation internally to unlock POS peripherals. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 520 | Gift card balance | Show the balance of a gift card. | Yes | Yes | No | No | No |
| 708 | Inactivate device | Inactivate the current device, so that it can't be used as a POS register. | No | No | No | No | No |
| 804 | Inbound operation | Access the features of inbound store inventory management. | Yes | No | Yes | No| No |
| 517 | Income accounts | Record money that is put into the cash drawer for a reason other than a sale. | Yes | Yes | Yes | Yes | No |
| 801 | Inventory lookup | Look up available, on order, and available-to-promise (ATP) quantities for the current store and other available locations. | Yes | Yes | Yes | No | No |
| 806 | Inventory adjustment | Adjust inventory in or out of store warehouse using adjustment or movement journal. | Yes | Yes | Yes | No | No |
| 807 | Inventory movement | Move items from one inventory location to another within a store warehouse. | Yes | Yes | Yes | No | No |
| 122 | Invoice comment | Enter a comment about the current transaction. | Yes | Yes | No | Yes | No |
| 511 | Issue credit memo | Issue a credit memo to provide a voucher instead of a refund. | Yes | Yes | No | No | No |
| 512 | Issue gift card | Issue a new gift card for the specified amount. | Yes | Yes | No | No | No |
| 625 | Issue loyalty card | Issue a loyalty card to a customer, so that the customer can participate in the store's loyalty program. | Yes | Yes | Yes | No | No |
| 300 | Line discount amount | Enter a discount amount for a line item in the transaction. This operation is used only for discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 301 | Line discount percent | Enter a discount percentage for a line item in the transaction. This operation is used only for discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 703 | Lock register | Lock the current register, so that it can't be used, but don't sign the current user out. | No | No | No | Yes | No |
| 701 | Log off | Sign the current user out of the register. | Yes | Yes | Yes | Yes | No |
| 521 | Loyalty card points balance | Show the balance of points for the specified loyalty card. | Yes | Yes | No | No | No |
| 142 | Manage charges | View and manage misc charges applied to transaction. | Yes | Yes | No | No| No |
| 918 | Manage shifts | Show a list of active, suspended, and blind closed shifts. | Yes | Yes | Yes | No | No |
| 914 | Minimize POS window | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 1000 | Open drawer | Perform a "no sale" operation, and open the currently selected cash drawer. | Yes | Yes | Yes | Yes | No |
| 928 | Order fulfillment | This operation allows users to pick, pack, ship, or recall orders for store picked up. | Yes | Yes | Yes | No | No |
| 805 | Outbound operation | Access features for managing shipments of outbound transfer orders. | Yes | No | Yes | No| No |
| 129 | Override line product tax | Override the tax on the selected line item, and use a different specified tax. | Yes | Yes | No | Yes | No |
| 130 | Override line product tax from list | Override the tax on the selected line item, and use the tax that the user selects in a list. | Yes | Yes | No | Yes | No |
| 127 | Override transaction tax | Override the tax on the transaction, and use a different specified tax. | Yes | Yes | No | Yes | No |
| 128 | Override transaction tax from list | Override the tax on the transaction, and use the tax that the user selects in a list. | Yes | Yes | No | Yes | No |
| 131 | Packing slip | Create a packing slip for the selected order. | No | No | No | No | No |
| 710 | Pair hardware station | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 201 | Pay card | Accept a card such as a credit card or a debit card as payment. | Yes | Yes | No | Yes | No |
| 200 | Pay cash | Accept cash as payment. | Yes | Yes | No | Yes | No |
| 206 | Pay cash quick | Complete the transaction in one touch, and accept the amount that is due in cash (exact change). | Yes | Yes | No | Yes | No |
| 204 | Pay check | Accept a check as payment. | Yes | Yes | No | Yes | No |
| 213 | Pay credit memo | Accept a credit memo (voucher) that the store issued. | Yes | Yes | No | No | No |
| 203 | Pay currency | Accept payment in various currencies. | Yes | Yes | No | Yes | No |
| 202 | Pay customer account | Charge the transaction to the customer's account. This payment method isn't valid for customer order deposits. | Yes | Yes | No | No | No |
| 214 | Pay gift card | Accept a gift card that the store issued. | Yes | Yes | No | No | No |
| 207 | Pay loyalty | Accept a loyalty card for payment, and redeem points toward qualified products. | Yes | Yes | No | No | No |
| 634 | Payments history | Show the customer's payment history for the current customer order. | Yes | Yes | No | No | No |
| 803 | Picking and receiving | Open the **Picking and receiving** page, where you can select orders to pick or receive in the store. | Yes | Yes | Yes | No | No |
| 632 | Pickup all products | Set the fulfillment method to **Store pickup** for all lines. | Yes | Yes | No | Yes\* | No |
| 631 | Pickup selected products | Set the fulfillment method to **Store pickup** for selected lines. | Yes | Yes | No | Yes\* | No |
| 400 | Popup menu | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 101 | Price check | This operation lets the user look up the price for a specified product. | Yes | Yes | Yes | Yes | No |
| 104 | Price override | Override the price of a product, if the product has been set up to allow for price overrides. | Yes | Yes | No | Yes | No |
| 1058 | Print fiscal X | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 1059 | Print fiscal Z | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 927 | Print item label | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 926 | Print shelf label | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 1056 | Print X | Print and X report for the current shift. | Yes | Yes | Yes | No | No |
| 103 | Product comment | Add a comment to the selected line item in the transaction. | Yes | Yes | No | Yes | No |
| 100 | Product sale | Add a specified product to the transaction. | Yes | Yes | Yes | Yes | No |
| 108 | Product search | Search for a product by navigating to the product search page in the POS. | Yes | Yes | Yes | Yes | No |
| 633 | Quote expiration date | View or modify the expiration date on a sales quotation. | Yes | Yes | No | Yes\* | No |
| 627 | Recalculate | Recalculate all customer order lines and taxes, based on the current configuration. | Yes | Yes | No | Yes\* | No |
| 143 | Recalculate charges | Recalculate the auto-charges applied to the order. | Yes | Yes | No | No| No |
| 515 | Recall order | Search for and recall customer orders and sales quotations. | Yes | Yes | Yes | No | No |
| 504 | Recall transaction | Recall a previously suspended transaction from the current store. | Yes | Yes | No | Yes‡ | No |
| 305 | Redeem loyalty points | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 635 | Refund shipping charges | Refund shipping charges on a canceled order. | No | No | No | No | No |
| 644 | Remove coupon code | Prompt the user to remove coupons by selecting them in a list of coupons that are currently associated with the transaction. | Yes | Yes | No | Yes | No |
| 1057 | Reprint Z | Reprint the Z report for the previous shift. | Yes | Yes | Yes | No | No |
| 1216 | Reset password | This operation lets a user who has the password-reset permission reset another employee's password by using a temporary password. | Yes | Yes | Yes | No | No |
| 1219 | Open URL in POS | Open an admin configured URL in POS. | Yes | Yes | Yes | Yes | No |
| 109 | Return product | Perform a return of individual products. The next scanned product is shown as a returned product that has a negative quantity and price. | Yes | Yes | No | Yes | No |
| 114 | Return transaction | Recall a previous transaction by its receipt number to return some or all of the products. | Yes | Yes | Yes | Yes§ | No |
| 1211 | Safe drop | Perform a safe drop to move money from the register to a safe. | Yes | Yes | Yes | Yes | No |
| 516 | Sales invoice | This operation lets the customer make payments toward the selected sales invoice. | Yes | Yes | No | No | No |
| 502 | Salesperson | Set the **Sales taker** value on a sales order for customer orders in the POS. | Yes | Yes | No | Yes\* | No |
| 2000 | Schedule management | This operation is not yet supported. | Yes | Yes | Yes | No | No |
| 2001 | Schedule requests | This operation is not yet supported. | Yes | Yes | Yes | No | No |
| 622 | Search | This operation lets users preconfigure POS buttons to perform searches by item, customer, or category. | Yes | Yes | Yes | Yes | No |
| 1213 | Search shipping address | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 709 | Select hardware station | Select a hardware station from a list of available hardware stations. | Yes | Yes | Yes | Yes | No |
| 637 | Set default sales representative on transaction | Select one of the eligible commission sales groups (sale reps) as the default sales rep for lines that are added later. | Yes | Yes | No | Yes | No |
| 105 | Set quantity | Change the quantity of a line item in the transaction. | Yes | Yes | No | Yes | No |
| 638 | Set sales representative on line | Select one of the eligible commission sales groups (sale reps) for the currently selected line. | Yes | Yes | No | Yes | No |
| 630 | Ship all products | Set the fulfillment mode to **Shipping** for all line items. | Yes | Yes | No | Yes\* | No |
| 629 | Ship selected products | Set the fulfillment mode to **Shipping** for the selected lines. | Yes | Yes | No | Yes\* | No |
| 115 | Show journal | Show the store's journal. You can view transactions, reprint receipts and gift receipts, and recall for return. | Yes | Yes | Yes | Yes\*\* | No |
| 802 | Stock count | Create or modify stock counting journals for physical inventory or cycle counts. | Yes | Yes | Yes | No | No |
| 401 | Sub menu | This operation takes the user to another linked button grid. | Yes | Yes | Yes | Yes | No |
| 1054 | Suspend shift | Suspend the current shift, so that a new or different shift can be activated on the current register. | Yes | Yes | Yes | No | No |
| 503 | Suspend transaction | Suspend the current sales transaction, so that it can be recalled later in the store. | Yes | Yes | No | Yes‡ | No |
| 1004 | Task recorder | Open Task recorder to record procedural steps in the POS. | No | No | No | Yes | No |
| 1052 | Tender declaration | Specify the amount of money in the drawer for each counted payment method. | Yes | Yes | Yes | Yes | No |
| 1210 | Tender removal | Remove money from the current drawer or shift. | Yes | Yes | Yes | Yes | No |
| 920 | Time clock | Punch in and punch out of work shifts and breaks. | Yes | Yes | Yes | No | No |
| 302 | Total discount amount | Enter a discount amount for the transaction. This operation applies only to discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 303 | Total discount percent | Enter a discount percentage for the transaction. This operation applies only to discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 501 | Transaction comment | Add a comment to the current transaction. | Yes | Yes | No | Yes | No |
| 922 | View product details | Open the product details page for the currently selected line item. | Yes | Yes | No | Yes | No |
| 1003 | View reports | Show the reports that have been configured for the current user. | Yes | Yes | Yes | No | No |
| 921 | View time clock entries | Show the time clock entries for all workers at the store. | Yes | Yes | Yes | No | No |
| 211 | Void payment | Void the currently selected payment line from the transaction. | Yes | Yes | No | Yes | No |
| 102 | Void product | Void the currently selected line item from the transaction. | Yes | Yes | No | Yes | No |
| 500 | Void transaction | Void the current transaction. | Yes | Yes | No | Yes | No |
| 916 | Windows workflow foundation | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | No |
| 924 | X report for bank cards | This operation isn't supported. | Not applicable | Not applicable | Not applicable | Not applicable | Yes |
| 311 | Remove system discounts from transactions | Remove all the system applied discounts, including coupon based discounts, from the transaction. This does not remove manual discounts. | Yes | Yes | Yes | Yes | No |
| 312 | Reapply system discounts | Reapply system discounts on the transaction if they were removed using the **Remove system discounts from transaction** operation. | Yes | Yes | Yes | Yes | No |

\* The operation is available in offline mode only when a customer order or sales quotation is being created, and only if offline creation of customer orders and sales quotations is configured in the POS functionality profile. The operation can't be performed when orders are created by using Real-time Service, or when orders are recalled or edited.

† The operation can be performed in offline mode only when the POS is configured to allow for offline creation of customers in the POS functionality profile.

‡ When the POS is offline, suspended transactions can be recalled only from the current register's offline database. Users can't suspend and recall transactions across registers.

§ When the POS is offline, only transactions in the current offline database can be recalled for return.

\*\* When the POS is offline, only transactions in the current offline channel database are shown in the journal.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
