---
# required metadata

title: Acquire assets through procurement
description: This article describes how to set up the integration between Fixed assets and Accounts payable to automatically create fixed assets from purchase orders or vendor invoices, or automatically post acquisition and acquisition adjustment transactions for fixed assets.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3481
ms.assetid: d4e73a3f-633b-48b2-b8db-7a4a59a4d7ec
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Acquire assets through procurement

This article describes how to set up the integration between Fixed assets and Accounts payable to automatically create fixed assets from purchase orders or vendor invoices, or automatically post acquisition and acquisition adjustment transactions for fixed assets.

 The following methods are available for integrating Fixed assets and Accounts payable, and you must use the same method for all fixed assets:
-   You manually create a fixed asset before you add the fixed asset number to the line on the purchase order or vendor invoice. An acquisition transaction automatically is posted for the asset when you post the vendor invoice. This is the default method.
-   You manually create a fixed asset before you add the fixed asset number to the line on the purchase order or vendor invoice. No acquisition transaction is posted for the asset when you post the vendor invoice.
-   A fixed asset automatically is created when you post a product receipt or vendor invoice that has the Create a new fixed asset check box selected. An acquisition transaction automatically is posted for the asset when you post the vendor invoice.
-   A fixed asset automatically is created when you post a product receipt or vendor invoice that has the Create a new fixed asset check box selected. No acquisition transaction is posted for the asset when you post the vendor invoice.

Select one of the first two methods if you prefer to manually create fixed assets, and then assign the fixed asset number to the purchase order or vendor invoice. Select one of the last two methods if you prefer a more flexible approach: sometimes you might create fixed assets manually, and sometimes you might automatically create a fixed asset based on the fixed asset information in the line item details. 

Whether you manually create fixed assets or use a more flexible approach, you must also decide whether an acquisition transaction can be posted only in Fixed assets, or whether it can be posted when you post a vendor invoice. Some organizations prefer that users manually create acquisition and acquisition transactions in Fixed assets by using manual journal entries or proposals. 

This topic discusses the details of each method.

## Methods for manually creating fixed assets
When you post a vendor invoice that has a fixed asset number entered in the lines, if the Allow asset acquisition from Purchasing option is selected in the Fixed assets parameters page, the acquisition is posted automatically, and the status of the asset changes to Open. 

If an acquisition cannot be posted, you can either manually enter an acquisition transaction in Fixed assets, or use an acquisition proposal in the Fixed assets journal to create multiple acquisition transactions at the same time.

> [!NOTE]                                                                                                                              
> If Fixed assets is set up to limit acquisition transaction posting to a specific user group, you must be a member of that user group to post acquisition transactions from invoices.

## Methods for automatically creating fixed assets
When you post a product receipt that has the Create a new fixed asset option selected for a line, a new fixed asset is created that has a status of Not yet acquired. Then, when you post a vendor invoice with a new fixed asset, an acquisition transaction is posted for the new asset and the asset status changes to Open, if Fixed assets is set up to allow for asset acquisitions from Accounts payable, and you are a member of a user group that can post acquisition transactions. 

If the New fixed asset? option was not selected on the purchase line when you posted the product receipt, but it was selected when you posted the vendor invoice, the new fixed asset is created and acquired with a status of Open, if Fixed assets is set up to allow for creating and acquiring. An additional asset is not created when you post a vendor invoice if one was already created when you posted the product receipt.

### Capitalization threshold

When you use a method where the asset is automatically created and acquired, you can set up the system to verify whether the purchase amount of the fixed asset meets a specified capitalization threshold for asset depreciation. If so, the Depreciation option will be selected in the books for the asset when it is created from Accounts payable. 

A capitalization threshold is a currency amount that determines whether assets are depreciated if they meet the specified amount. For example, if you purchase an asset and the purchase amount is less than the capitalization threshold, the asset is not designated to depreciate; if the purchase amount meets or exceeds the threshold, the asset is designated to depreciate. 

You can set up the capitalization threshold in the Fixed asset groups page.

## Scenario
The following scenario discusses a full cycle of a Fixed assets and Accounts payable integration. A sample setup is shown and the use of acquisition proposals is also described. 

In this scenario, the system is set up as follows:

-   Assets are automatically created during product receipt or vendor invoice posting, but Fixed assets is set up to prevent posting acquisition transactions from Accounts payable.
-   Accounts are specified in the Account type field for the Fixed asset receipt and Fixed asset issue account types in the Item groups page.
-   The capitalization threshold for the computers group (COMP) is 1,500.
-   Your task is to enter a purchase order for a new laptop that an employee will use, post the purchase order, verify that the shipping clerk posts a product receipt, post the vendor invoice, and then verify that the accountant updates the laptop asset to a status of Open.

To begin, you use the Purchase order page to enter details for the laptop, which costs 1,600. You select the New fixed asset? option on the Fixed assets FastTab of the purchase order lines, select COMP as the fixed asset group, and save the purchase order. 

When the laptop is received, a shipping clerk enters and posts a product receipt to record the receipt of the laptop. The laptop asset is created and has a status of Not yet acquired. The amount exceeds the capitalization threshold. Therefore, the Depreciation option is selected in the books for the laptop asset. The following transactions occurred.

| Description                               | Account             | Debit    | Credit   |
|-------------------------------------------|---------------------|----------|----------|
| Purchase, Product receipt purchase        | Uninvoiced receipts | 1,600.00 |          |
| Purchase, Product receipt purchase offset | Accrued purchases   |          | 1,600.00 |

Next, you post the vendor invoice for the laptop. The laptop status is not changed because Fixed assets is set up to prevent an asset acquisition transaction from being posted when a vendor invoice is posted. The Create a new fixed asset option was selected when the vendor invoice was posted. Therefore, the Fixed asset receipt account was used. The Fixed asset issue account was not used because no acquisition was posted; it will be used later when your organization's accountant posts an acquisition transaction in Fixed assets using acquisition proposals. 

The following transactions occurred.

| Description                               | Account             | Debit    | Credit   |
|-------------------------------------------|---------------------|----------|----------|
| Purchase, Product receipt purchase offset | Accrued purchases   | 1,600.00 |          |
| Vendor balance                            | Accounts payable    |          | 1,600.00 |
| Purchase, Fixed asset receipt             | Computer expense    | 1,600.00 |          |
| Purchase, Product receipt purchase        | Uninvoiced receipts |          | 1,600.00 |

Finally, the accountant reviews all fixed assets that have a status of Not yet acquired. Therefore, the new laptop asset is reviewed. The accountant then opens the Acquisition proposal page from the Fixed assets journal lines, and creates acquisition transactions for all assets that have an invoice but that still have a status of Not yet acquired. When the journal is posted, the status of the laptop asset is changed to Open. The Fixed asset issue account is credited and the asset acquisition account is debited. 

The following are variations for this scenario:

-   If Fixed assets is set up to allow for asset acquisition transactions to be posted when vendor invoices are posted, the accountant does not have to use acquisition proposals in Fixed assets because the acquisition transaction is created. Also, different accounts are updated when you post the vendor invoice. Instead of Computer expense, the Fixed asset receipt inventory account is debited, and two additional transactions occur: the asset acquisition account is debited and the Fixed asset issue inventory account is credited.
-   If the Create a new fixed asset option is not selected when the product receipt is posted, no asset is created at that time. If you select the Create a new fixed asset option before you post the vendor invoice, the asset is created and has a status of Not yet acquired, or a status of Open if you also post acquisition transactions when vendor invoices are posted.
-   If the laptop cost is 1,400 instead of 1,600, the capitalization threshold is not reached. Therefore, the asset is created and the Depreciation option is cleared.
-   If an invoice register is used, you use the Invoice approval journal page after the invoice register is posted to retrieve the voucher, link the purchase order to the vendor invoice, select the Create a new fixed asset option, and then post the vendor invoice. If you are a member of a user group that can create acquisition transactions, the acquisition is created and the asset has a status of Open.
-   If only a partial quantity is received, no asset acquisition is created for the first vendor invoice because of user group restrictions. The only way that an acquisition can be posted for the second vendor invoice that finishes the quantity ordered is if an acquisition transaction has already been entered for the first vendor invoice, and you are a member of the user group that can post acquisitions.


For more informations, see [Fixed assets integration](fixed-asset-integration.md).

