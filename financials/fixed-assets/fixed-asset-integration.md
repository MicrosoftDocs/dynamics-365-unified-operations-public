---
# required metadata

title: Fixed assets integration
description: Fixed assets can be integrated with General ledger, Inventory management, Accounts receivable, and Accounts payable. You can also set up Fixed assets so that it is integrated with purchase orders.
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3501
ms.assetid: f0639053-d99c-432a-8ead-5c26e0d4eaec
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed assets integration

Fixed assets can be integrated with General ledger, Inventory management, Accounts receivable, and Accounts payable. You can also set up Fixed assets so that it is integrated with purchase orders.

General ledger
--------------

In General ledger, the value of all fixed assets is typically summarized in multiple main accounts that are required for financial reporting. However, on the **Fixed assets** page, you can create many fixed asset records. These records can include information such as the acquisition price, depreciation, and valuation. Each time that you post a transaction for a fixed asset, the appropriate main accounts are updated. The main accounts for fixed assets always show the updated value of the fixed assets.

On the **Fixed asset posting profiles** page, you define the main accounts that fixed asset book transactions are posted to. You also specify the types of fixed asset transactions that are posted to each main account. You can create various combinations of main accounts for fixed assets, depending on the level of detail that you want for fixed assets in the general ledger. Main accounts can be based on transaction types, books, and other main accounts.

## Inventory management
In the inventory journal for fixed assets, you can enter the acquisition of fixed assets that the legal entity has produced or constructed for itself. You can then transfer inventory items to fixed assets either as an acquisition or as part of an acquisition. 

You can also acquire assets by using purchase orders. When purchase orders contain inventory items that are designated as fixed assets, the setting of the **Allow asset acquisition from Purchasing** option on the **Fixed assets parameters** page determines whether an acquisition is posted for the fixed asset when the invoice is posted. The effect that the acquisition of fixed assets has on inventory depends on the setup of the legal entity. 

When an inventory item becomes a fixed asset acquisition through the inventory journal, a purchase order, or an acquisition proposal, a fixed asset book acquisition transaction is created. If a book acquisition includes a derived book, the derived book acquisition transaction is also created. 

Posting rules that are set up on the **Posting** page in Inventory management control the decrease in inventory when an acquisition is posted. However, you don’t always decrease inventory when you post invoices that are related to fixed assets. In some cases, the fixed assets might be purchased for internal use. An example is a laptop that is purchased for the sales department. When you work with purchase orders, you can use items that are set up for both resale and internal use. 

If you use specific receipt and issue accounts on item groups for fixed assets, you can use the same inventory item both for internal purchases and as stock for resale. 

Fixed assets that are for internal use are set up so that they have an account type of **Fixed asset receipt**. This account type is used to track the receipt of the fixed asset. When you post a vendor invoice, use the fixed asset receipt account if any of the following conditions is true:

-   The invoice line contains an existing fixed asset for internal purposes.
-   The **New fixed asset?** check box is selected for the product receipt line that is posted.
-   The **Create a new fixed** asset check box is selected for the vendor invoice line.

Typically, this account is an expense account. You can set up the **Fixed asset receipt** account type for either an item group or an individual item by using the **Purchase order** tab on the **Item group** or **Posting** page.

Similarly, fixed assets that are for internal use can be set up so that they have an account type of **Fixed asset issue**. This account type is used to track the issuing of the fixed asset to the recipient. When an asset is acquired by using a purchase order, the fixed asset issue account offsets the fixed asset debit account. The asset acquisition can be posted either when you post a vendor invoice or when you post the asset acquisition in the Fixed assets journal, possibly by using an acquisition proposal. You can set up the **Fixed asset issue** account type for either an item group or an individual item by using the **Inventory** tab on the **Item group** or **Item posting** page. 

Ultimately, the main accounts that are used for posting are determined by the options for ledger integration that are specified for the item model group. Additionally, the main accounts that are used vary, depending on whether an asset is assigned to the purchase order line. The accounts are derived from the posting profile for each item group. 
**Note:** If an inventory reservation exists when product receipts are posted, you can’t assign a fixed asset or create a fixed asset from the line. 

The accounts that fixed asset transactions are posted to depend on two factors: whether the assets are purchased or constructed by the legal entity, and the transaction type of the asset. 

The transaction type connects the inventory transaction to the posting profile in Fixed assets. Because the posting profile in Fixed assets defines which accounts are updated, the selection of a transaction type for a fixed asset is also, indirectly, the selection of the main accounts that the transaction is posted to. For both constructed and purchased fixed assets, the transaction type is typically **Acquisition** or **Acquisition adjustment**.

## Accounts receivable
The integration of Fixed assets with Accounts receivable uses posting profiles that are set up in Fixed assets. These posting profiles are activated when a fixed asset, book, and fixed asset transaction type are selected for a customer invoice before the customer invoice is posted. Because fixed assets aren’t part of Inventory management, you must use the **Free text invoice** page when you sell a fixed asset. 

If the book includes a derived book, the derived book transaction is created when you post the customer invoice.

## Accounts payable
Typically, fixed assets are acquired from external vendors. You can use the **Fixed assets parameters** page to specify whether asset acquisitions are always posted when you post vendor invoices, or whether asset acquisitions can be posted only from Fixed assets. If you enable asset acquisitions to be posted from Accounts payable, fixed asset accounts are updated whenever a vendor invoice for a fixed asset acquisition is posted. 

If the system is set up to post an asset acquisition when an invoice is posted, the transaction is posted according to the posting profiles that are set up in Fixed assets for the various fixed asset transaction types. The posting is controlled by the fixed asset, book, and fixed asset transaction type that are selected on the **Purchase order** page before the vendor invoice is posted. 

If the book includes a derived book, the derived book transaction is created when you post the vendor invoice.

The integration for each order line is activated on the **Fixed assets** tab on the **Line details** FastTab on the **Purchase order** page. You can send a purchase order for a fixed asset to the vendor. However, the fixed assets and main accounts are updated only when you post the vendor invoice after the fixed asset is received. Because purchase orders can contain only inventory items, the effect that the acquisition of fixed assets has on inventory depends on the setup of the legal entity.

## Project management and accounting
You can associate a project with an asset that is affected by the project. You can also associate each phase, task, or subproject to a different asset. One asset can be associated with each project record. You create the association when you enter a fixed asset number in the **Fixed asset** number field on the **Projects** page. The project type must be either **Internal** or **Cost project**. 

You can also use the **Projects** page to view details about assets that are associated with projects. To view the fixed asset record, on the **Setup** FastTab, click the asset link to open the **Fixed assets** page. Then click **Projects** &gt; **All projects** to view the projects that are associated with the fixed asset. 

Typically, you associate fixed assets with projects when the projects are related to work, maintenance, or improvements for the asset. When the project is completed, a write-up adjustment for the asset isn’t created automatically. Therefore, if a write-up adjustment is required, you must create it manually. 

To delete the association between a project and an asset, clear the **Fixed asset number** field on the **Projects** page. 

You can also designate a fixed asset that you’re creating or manufacturing as part of an estimate project. At the end of an estimate project, you can automatically post an asset acquisition transaction.

For more information, see [Acquire assets through procurement](acquire-assets-procurement.md)

