---
# required metadata

title: POS Operations
description: This document details the POS Operations in Dynamics 365 for Retail, and specifies where in the application they can be invoked as well as whether or not the are available in offline mode.
author: jblucher
manager: AnnBe
ms.date: 09/27/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2017-09-27
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# POS Operations
Most actions taken by users in POS are considered Operations, which are configured and managed within the Dynamics 365 for Retail back office.  Many operations can be added to POS button grid buttons, which allows them to be invoked by touching or clicking the button to perform their function.  Other operations are part of the main POS application and are invoked from on screen buttons, or as part of other workflows or processes.

The table below details the list of available Operations in Retail Modern POS and Cloud POS for Dynamics 365 for Retail.  The table also includes from where in the application they can invoked, and if they are available when POS is in offline mode.  Some Operations are not currently available in Dynamics 365 for Retail Modern POS or Cloud POS.  These are either locale specific Operations that require additional extensions and configuration, or features from Dynamics AX 2012 that are not currently supported.

The following columns specify where the Operations can be invoked:
- Button grid:  These operations can be assigned to buttons in POS button grids, which are part of a POS screen layout.  
- Transaction screen:  These operations can be invoked from POS button grids that is configured on the POS transaction screen.
- Welcome screen:  These operations can be invoked from POS button grids that are configured on the POS welcome screen.

| ID | Operation | Description | Button grid | Transaction screen | Welcome screen | Available offline | Locale specific |
|------|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------|----------------|-------------------|-----------------|
| 707 | Activate device | Activates the current device by allowing an authenticated user to provide connection information and assign a device and register ID. | No | No | No | No | No |
| 134 | Add affiliation | Add a preselected affiliation to a transaction. Select the affiliation in the Button properties form. | Yes | Yes | No | Yes | No |
| 135 | Add affiliation from list | Add an affiliation to a transaction by selecting from a list. | Yes | Yes | Yes | Yes | No |
| 643 | Add coupon code | Add a coupon by entering its code in the POS | Yes | Yes | No | Yes | No |
| 117 | Add loyalty card | Prompts the user to enter a loyalty card number to be added to the current transaction | Yes | Yes | No | Yes | No |
| 136 | Add serial number | Allows the user to specify a serial number for the currently selected product | Yes | Yes | No | Yes | No |
| 1214 | Add shipping address | Operation not supported | NA | NA | NA | NA | No |
| 519 | Add to gift card | Add money to the specified gift card | Yes | Yes | No | No | No |
| 6000 | Allow skip fiscal registration | Operation not supported | NA | NA | NA | NA | Yes |
| 1212 | Bank drop | Record the amount of money that is sent to the bank and other information, such as the number of the bank bag. | Yes | Yes | Yes | Yes | No |
| 923 | Bank totals verification | Operation not supported | NA | NA | NA | NA | Yes |
| 915 | Blank operation | This operation represents a customizable button that can be programmatically changed by a software developer for any specialized operation that the business requires. | Yes | Yes | Yes | Yes | No |
| 1053 | Blind close shift | Sets the current shift to blind closed, and logs off the user.  A blind closed shift is closed to additional transactions, but is still open to drawer operations such as tender removal and tender declaration. | Yes | Yes | Yes | No | No |
| 310 | Calculate total | When discount calculation is delayed, this operation will initiate the calculation for the current transaction. | Yes | Yes | No | Yes | No |
| 642 | Carry Out All Products | Sets the mode of delivery for all lines to "Carryout" | Yes | Yes | No | Yes * | No |
| 641 | Carry Out Selected Products | Sets the mode of delivery for the selected lines to "Carryout" | Yes | Yes | No | Yes * | No |
| 1215 | Change password | Allows the POS user to change their password | Yes | Yes | Yes | No | No |
| 123 | Change unit of measure | Change the selected line item's unit of measure | Yes | Yes | No | Yes | No |
| 639 | Clear default sales representative on transaction | Removes the commission sales group (sales rep) from the transaction | Yes | Yes | No | Yes | No |
| 106 | Clear quantity | Resets the currently selected line's quantity to 1 | Yes | Yes | No | Yes | No |
| 640 | Clear sales representative on line | Removes the commission sales group (sale rep) from the currently selected line | Yes | Yes | No | Yes | No |
| 121 | Clear salesperson | Operation not supported | NA | NA | NA | NA | No |
| 1055 | Close shift | Closes the current shift, prints a Z report, and logs the user out of the system | Yes | Yes | Yes | No | No |
| 925 | Copy the bank check | Operation not supported | NA | NA | NA | NA | Yes |
| 620 | Create customer order | Converts the POS transaction into a customer order | Yes | Yes | No | Yes * | No |
| 621 | Create quotation | Converts the POS transaction into a sales quotation | Yes | Yes | No | Yes * | No |
| 636 | Create retail transaction | Allows the user to create a standard sales transaction, when the POS default behavior is to create customer orders | Yes | Yes | No | Yes | No |
| 600 | Customer | This operation adds the specified customer to the transaction | No | No | No | Yes | No |
| 1100 | Customer account deposit | Make a payment to a customer's account. | Yes | Yes | Yes | Yes | Yes |
| 612 | Customer add | Allows the user to create a new customer record | Yes | Yes | Yes | Yes ** | No |
| 603 | Customer clear | Removes the customer from the current transaction | Yes | Yes | No | Yes | No |
| 602 | Customer search | Allows the user to search for a customer record by navigating to the customer search page in POS. | Yes | Yes | Yes | Yes | No |
| 609 | Customer transactions | Operation not supported | NA | NA | NA | NA | No |
| 917 | Database connection status | Allows the user to view the current connection settings and switch between online and offline | Yes | Yes | Yes | Yes | No |
| 1200 | Declare start amount | Declare the amount that is in the cash drawer when the day or shift starts. | Yes | Yes | Yes | Yes | No |
| 132 | Deposit override | Override the default deposit for customer orders. | Yes | Yes | No | Yes * | No |
| 913 | Design mode disable | Operation not supported | NA | NA | NA | NA | No |
| 912 | Design mode enable | Operation not supported | NA | NA | NA | NA | No |
| 1217 | Disassemble kits | Disassemble a kit into its component products | Yes | Yes | Yes | Yes | No |
| 624 | Display refund amounts | Operation not supported | NA | NA | NA | NA | Yes |
| 513 | Display total | Displays the balance of the transaction on the customer display. | Yes | Yes | Yes | Yes | No |
| 623 | Edit customer | Edits the current customers details | Yes | Yes | No | No | No |
| 614 | Edit customer order | This operation recalls the selected order for modification in the POS | No | No | No | No | No |
| 615 | Edit quotation | This operation recalls the selected quotation for modification in the POS | No | No | No | No | No |
| 518 | Expense accounts | Record money that is removed from the cash drawer for occasional expenses. | Yes | Yes | Yes | Yes | No |
| 919 | Extended log on | Assign or remove permission to log on by scanning a bar code or by swiping a card | Yes | Yes | Yes | No | No |
| 1201 | Float entry | Allows the user to add additional money to the current drawer or shift | Yes | Yes | Yes | Yes | No |
| 1218 | Force unlock peripheral | This operation is used internally by the system to unlock POS peripherals | NA | NA | NA | NA | No |
| 520 | Gift card balance | Display the balance of a gift card | Yes | Yes | No | No | No |
| 708 | Inactivate device | Deactivates the current device, preventing it from being used as a POS register. | No | No | No | No | No |
| 517 | Income accounts | Record money that is put into the cash drawer for a reason other than a sale. | Yes | Yes | Yes | Yes | No |
| 801 | Inventory lookup |Look up available, on order, and ATP quantities for the current store and other available locations.  | Yes | Yes | Yes | No | No |
| 122 | Invoice comment | This operation allows a user to enter a comment about the current transaction | Yes | Yes | No | Yes | No |
| 511 | Issue credit memo | Issues a credit memo to provide a voucher in lieu of a refund. | Yes | Yes | No | No | No |
| 512 | Issue gift card | Issues a new gift card for the specified amount | Yes | Yes | No | No | No |
| 625 | Issue loyalty card | Issue a loyalty card to a customer so the customer can participate in the store\'s loyalty program | Yes | Yes | Yes | No | No |
| 300 | Line discount amount | Enter a discount amount for a line item in the transaction. This operation is used only for discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 301 | Line discount percent | Enter a discount percentage for a line item in the transaction. This operation is used only for discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 703 | Lock register | Locks the current register, preventing it from being used, without logging off the current user. | No | No | No | Yes | No |
| 701 | Log off | Logs the current user off of the register | Yes | Yes | Yes | Yes | No |
| 521 | Loyalty card points balance | This operation displays the points balance for the specified loyalty card | Yes | Yes | No | No | No |
| 914 | Minimize POS window | Operation not supported | NA | NA | NA | NA | No |
| 1000 | Open drawer | Performs a "no sale" operation and opens the currently selected cash drawer | Yes | Yes | Yes | Yes | No |
| 129 | Override line product tax | Override the tax on the selected line item, and use a different specified tax | Yes | Yes | No | Yes | No |
| 130 | Override line product tax from list | Override the tax on the selected line item, and use a tax that the user selects from a list | Yes | Yes | No | Yes | No |
| 127 | Override transaction tax | Override the tax on the transaction, and use a different specified tax | Yes | Yes | No | Yes | No |
| 128 | Override transaction tax from list | Override the tax on the transaction, and use a tax that the user selects from a list | Yes | Yes | No | Yes | No |
| 131 | Packing slip | This operation creates a packing slip for the selected order | No | No | No | No | No |
| 710 | Pair hardware station | Operation not supported | NA | NA | NA | NA | No |
| 201 | Pay card | Accept cards such as credit or debit as payment | Yes | Yes | No | Yes | No |
| 200 | Pay cash | Accept cash as payment | Yes | Yes | No | Yes | No |
| 206 | Pay cash quick | Complete the transaction in one touch, accepting the amount due in cash (exact change) | Yes | Yes | No | Yes | No |
| 204 | Pay check | Accept check as payment | Yes | Yes | No | Yes | No |
| 213 | Pay credit memo | Accept a credit memo (voucher) that was issued by the store. | Yes | Yes | No | No | No |
| 203 | Pay currency | Accept payment in various currencies | Yes | Yes | No | Yes | No |
| 202 | Pay customer account | Charge the transaction to the customer's account.  This payment method is not valid for customer order deposits. | Yes | Yes | No | No | No |
| 214 | Pay gift card | Accept a gift card that was issued by the store | Yes | Yes | No | No | No |
| 207 | Pay loyalty | Accept a loyalty card for payment and redeem points towards qualified products | Yes | Yes | No | No | No |
| 634 | Payments history | Displays the customers payment history for the current customer order | Yes | Yes | No | No | No |
| 803 | Picking and receiving | Opens the Picking and receiving form where you can select orders to pick or receive in the store | Yes | Yes | Yes | No | No |
| 632 | Pickup all products | Sets the fulfillment method to "Store pickup" for all lines | Yes | Yes | No | Yes * | No |
| 631 | Pickup selected products | Sets the fulfillment method to "Store pickup" for selected lines | Yes | Yes | No | Yes * | No |
| 400 | Popup menu | Operation not supported | NA | NA | NA | NA | No |
| 101 | Price check | Allows the user to look up the price for a specified product | Yes | Yes | Yes | Yes | No |
| 104 | Price override | Override the price of a product, if the product has been set up to allow price overrides | Yes | Yes | No | Yes | No |
| 1058 | Print fiscal X | Operation not supported | NA | NA | NA | NA | Yes |
| 1059 | Print fiscal Z | Operation not supported | NA | NA | NA | NA | Yes |
| 927 | Print item label | Operation not supported | NA | NA | NA | NA | No |
| 926 | Print shelf label | Operation not supported | NA | NA | NA | NA | No |
| 1056 | Print X | Prints and X report for the current shift | Yes | Yes | Yes | No | No |
| 103 | Product comment | Add a comment to the selected line item in the transaction. | Yes | Yes | No | Yes | No |
| 100 | Product sale | Add a specified product to the transaction | Yes | Yes | Yes | Yes | No |
| 108 | Product search | Allows the user to search for a product, by navigating to the product search page in POS. | Yes | Yes | Yes | Yes | No |
| 633 | Quote expiration date | Allows the user to view or modify the expiration date on a sales quotation | Yes | Yes | No | Yes * | No |
| 627 | Recalculate | This operation will recalculate all customer order lines and taxes based on the current configuration | Yes | Yes | No | Yes * | No |
| 515 | Recall order | Allows the user to search for and recall customer orders and sales quotations | Yes | Yes | Yes | No | No |
| 504 | Recall transaction | Allows the user to recall a previously suspended transaction from the current store | Yes | Yes | No | Yes # | No |
| 305 | Redeem loyalty points | Operation not supported | NA | NA | NA | NA | Yes |
| 635 | Refund shipping charges | This operation allows a user to refund shipping charges on a cancelled order | No | No | No | No | No |
| 644 | Remove coupon code | Prompts the user to remove coupons by selecting from a list that are currently associated with the transaction | Yes | Yes | No | Yes | No |
| 1057 | Reprint Z | Reprints the Z report for the previous or selected shift | Yes | Yes | Yes | No | No |
| 1216 | Reset password | Allows a user who has the password-reset permission to reset another employee's password by using a temporary password | Yes | Yes | Yes | No | No |
| 109 | Return product | Perform a return of individual products. The next scanned product is displayed as a returned product that has a negative quantity and price. | Yes | Yes | No | Yes | No |
| 114 | Return transaction | Recall a previous transaction by its receipt number to return some or all the products | Yes | Yes | Yes | Yes † | No |
| 1211 | Safe drop | Perform a safe drop to move money from the register to a safe. | Yes | Yes | Yes | Yes | No |
| 516 | Sales invoice | Allows customer to make payments towards the selected sales invoice | Yes | Yes | No | No | No |
| 502 | Salesperson | Allows the user to set the "Sales taker" value on a sales order for customer orders in POS. | Yes | Yes | No | Yes * | No |
| 2000 | Schedule management | Allows users to create, modify, or view employee schedules. | Yes | Yes | Yes | No | No |
| 2001 | Schedule requests | Allows user to request time off, swap shifts, or offer shifts to other employees | Yes | Yes | Yes | No | No |
| 622 | Search | Enables users to preconfigure POS buttons to perform searches by item, customer, or category. | Yes | Yes | Yes | Yes | No |
| 1213 | Search shipping address | Operation not supported | NA | NA | NA | NA | No |
| 709 | Select hardware station | Allows the user to choose from the list of available hardware stations | Yes | Yes | Yes | Yes | No |
| 637 | Set default sales representative on transaction | Allows the user to choose from eligible commission sales groups (sale reps) as the default for subsequently added lines | Yes | Yes | No | Yes | No |
| 105 | Set quantity | Change the quantity of a line item in the transaction. | Yes | Yes | No | Yes | No |
| 638 | Set sales representative on line | Allows the user to choose from eligible commission sales groups (sale reps) for the currently selected line | Yes | Yes | No | Yes | No |
| 630 | Ship all products | Sets the fulfillment mode to "Shipping" for all line items | Yes | Yes | No | Yes * | No |
| 629 | Ship selected products | Sets the fulfillment mode to "Shipping" for the selected lines | Yes | Yes | No | Yes * | No |
| 918 | Show blind closed shifts | View a list of shifts that have been blind closed. | Yes | Yes | Yes | No | No |
| 115 | Show journal | View the stores journal.  You can view transactions, reprint receipts and gift receipts, and recall for return | Yes | Yes | Yes | Yes ‡  | No |
| 802 | Stock count | Allows the user to create or modify stock counting journals for physical inventory or cycle counts. | Yes | Yes | Yes | No | No |
| 401 | Sub menu | This operation navigates the user to another linked button grid | Yes | Yes | Yes | Yes | No |
| 1054 | Suspend shift | This operation suspends the current shift, which allows a new or different shift to be activated on the current register | Yes | Yes | Yes | No | No |
| 503 | Suspend transaction | Suspends the current sales transaction to be recalled later within the store | Yes | Yes | No | Yes # | No |
| 1004 | Task recorder | Opens the task recorder to record procedural steps in POS | No | No | No | Yes | No |
| 1052 | Tender declaration | Allows the user to specify the amount of money in the drawer for each of the counted payment methods | Yes | Yes | Yes | Yes | No |
| 1210 | Tender removal | Allows the user to remove money from the current drawer/shift | Yes | Yes | Yes | Yes | No |
| 920 | Time clock | Allows users to punch in and out of work shifts and breaks | Yes | Yes | Yes | No | No |
| 302 | Total discount amount | Enter a discount amount for the transaction. This operation will only apply to discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 303 | Total discount percent | Enter a discount percentage for the transaction. This operation will only apply to discountable items and only within specified discount limits. | Yes | Yes | No | Yes | No |
| 501 | Transaction comment | Add a comment to the current transaction | Yes | Yes | No | Yes | No |
| 922 | View product details | Displays the product details page for the currently selected line item | Yes | Yes | No | Yes | No |
| 1003 | View reports | View the reports that have been configured for the current user | Yes | Yes | Yes | No | No |
| 921 | View time clock entries | View the time clock entries for all workers at the store | Yes | Yes | Yes | No | No |
| 211 | Void payment | Voids the currently selected payment line from the transaction | Yes | Yes | No | Yes | No |
| 102 | Void product | Voids the currently selected line item from the transaction | Yes | Yes | No | Yes | No |
| 500 | Void transaction | Voids the current transaction | Yes | Yes | No | Yes | No |
| 916 | Windows workflow foundation | Operation not supported | NA | NA | NA | NA | No |
| 924 | X report for bank cards | Operation not supported | NA | NA | NA | NA | Yes |

\* These operations are available in offline mode, only during creation of a customer order or sales quotation, when those features are configured to allow offline creation within the POS Functionality Profile.  These operations cannot be performed when creating orders using the Real-time Service or when recalling or editing an order.

\** This operation can only be performed in offline mode when POS is configured to allow offline creation of customers within the POS Functionality Profile.

\# When offline, suspended transactions can only be recalled from the current registers offline database.  Users will not be able to suspend and recall transactions across registers.

† When offline, only transactions within the current offline database can be recalled for return.

‡ When offline, only transactions within the current offline channel database will be shown in the journal.

