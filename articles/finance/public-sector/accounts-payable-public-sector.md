---
# required metadata

title: Accounts payable in the public sector overview
description: This article explains the public sector Accounts payable functionality that is integrated with Microsoft Dynamics 365 Finance. T
author: v-kiarnd
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetParameters, CustParameters, LedgerJournalTable, OMLegalEntity, PurchAgreementListPage, PurchTableListPage, SrmParameters, VendCertificationType, VendCoverPageLayout, VendOpenInvoicesListPage, VendParametersVendParameters, VendTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: b4c903dd-5ec7-4ec5-9dc9-77ba4f00fab8
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounts payable in the public sector overview

[!include [banner](../includes/banner.md)]

This article describes the public sector functionality for Accounts payable that's integrated with Dynamics 365 Finance. This functionality includes PO codes, posting definitions, one-time vendor invoicing, 1099 tax forms, cash discounts, vendor certification types, Project accounting activity summary, electronic payments, cover and signature pages for reports, PO line amounts, and vendor invoice journal pages. 

## What are the prerequisites for setting up Accounts payable in the public sector?

Before you begin to adjust the settings and enter your data, you should complete the following tasks:

-   Set up vendors.
-   Set up numbering systems for vendors, purchase orders, and so on.
-   Decide what purchase order (PO) codes and messages will be used.

After you’ve set up the prerequisites,  you might have to set up the following Accounts payable features:

- [Purchase order codes in the public sector](purchase-order-codes-public-sector.md) –  You can create codes and special messages for confirming purchase orders. A confirming purchase order bypasses the typical purchasing process. For example, you authorize an unplanned order by using a purchase order number at the time of a purchase, instead of by using a document that is provided before the item is required. 
  > [!NOTE]
  > This also applies to **Procurement and sourcing**.

- [Posting definitions in the public sector](posting-definitions-public-sector.md) – You can use posting definitions to create subledger journal lines for originating transactions that meet selected criteria. For example, you can use positing definitions to generate multiple balanced ledger entries, based on attributes such as transaction types and accounts. 
  > [!NOTE]
  > This also applies to **General ledger**, **Budgeting**, and **Accounts receivable**.


- [One-time vendors in the public sector](one-time-vendors-public-sector.md) – When approval or a contract in the form of a purchase order isn't required, you can quickly create one or more invoices at the same time that you create a record for the vendor. For more information, see [Plan for one-time vendors in the public sector](plan-one-time-vendors-public-sector.md).
- 1099 form overview in the public sector – If you do business with vendors that are subject to United States 1099 tax, you must track the amount that you pay to each vendor and report that information at the end of the calendar year. Public sector organizations use forms 1099-G and 1099-S.

> [!NOTE]
> This also applies to **Procurement and sourcing**.

## Additional public sector functionality
The remaining sections describe the Accounts payable functionality that is available for the public sector.

-   **Cash discounts** – Select the account to offset when cash discounts are applied to invoices.
-   **Vendor certification types** – Define a certification type for any vendor requirement that you want to track.
-   **Purchase agreement activity summary** – Enter summary details for activities that are related to a purchase agreement.
-   **Electronic payments** – Specify electronic payments to vendors. 
-   **Cover and signature pages for payments reports** – Specify what information should appear on cover and signature pages for a payment report.
-   **Purchase order line amounts** – View line amounts for a purchase order and any amounts that must still be invoiced, or for invoices that are pending.

### How can I apply cash discounts to vendor invoices?

You use the **Cash discounts** page in Accounts payable or Accounts receivable to select the account to offset when cash discounts are applied to invoices. You can do this for either an existing invoice or a new invoice that you create. Cash discount codes are linked to customer and vendor accounts, and are applied to sales orders and purchase orders. On the **Setup** FastTab, the **Discount offset accounts** field lets you offset either the specified main account for vendor discounts account or accounts that are specified on the invoice line.

### How do I specify and assign certification types for vendors?

You can create and assign vendor organizations any type of certification that those vendors have. This certification includes professional credentials, such as a professional engineer’s license or Microsoft SQL Server Certification. However, the certification can also specify that the vendors have liability insurance or minority status, or that they are in compliance with various environmental or consumer safety standards. You use the **Certification type** page to create certification types and descriptions.

### How do I view or enter summary information for purchase agreement activity?

You use the **Purchase agreements** page in Accounts payable or Procurement and sourcing to enter summary details for activities that are related to a purchase agreement. You can do this for either an existing purchase agreement or a new purchase agreement that you create. Examples include project milestones, planned dates for payments to a vendor, or the dates when items that are listed in a vendor contract are due for review.

#### Tips

-   You can set up a unique number for the activity on the **Legal entities** page in Organization administration or General ledger. When you select the activity in the purchase agreement, the number is assigned automatically.
-   You can also set up a unique identifier for the purchase agreement, in the **Number sequences** section on the **Procurement and sourcing parameters** page. When you create a purchase agreement, the number is assigned automatically.

### How do I specify electronic payments to vendors?

You can distribute the payment of an invoice to bank accounts for multiple vendors. You can select multiple bank accounts and allocate a percentage to each account. Based on the accounts that are selected, single or multiple open transactions are created against the invoice. You can create payments for each journal line without creating a partial payment for each vendor bank account.

#### Tip

For example, there’s an existing purchase order for $100, and Bank A is the default vendor bank account. In the payment disbursement table, Bank A has 100-percent allocation. (If there is no default vendor bank account, the table is blank.) You can change the allocation for Bank A to 30 percent and then add a new row. On the new row, you can select another vendor bank, such as Bank B, and the allocation for the new row is automatically updated to 70 percent.

### How can I create and print cover and signature pages for payments reports?

When you create cover and signature pages for a payment report, you can specify the information that should appear. This information includes the names and titles of the people who should approve the proposed payments.

### How do I view purchase order line amounts?

You can view line amounts for a purchase order. These amounts include the current ordered amount, and any amounts that have been received or invoiced. You can also view any amounts that must still be invoiced or amounts for invoices that are pending. Tip For example, you view a purchase order line that has purchases that are posted to two ledger accounts. One ledger account is for items that are ordered from a vendor for office furniture. The second ledger account is for office supplies. The ordered amount is equal to the sum of the invoiced, pending invoice, and invoice remaining amounts. The received amount is the part of the ordered amount that has been received from the vendor.


For more information, see the following topics:

[Add a certification type to a vendor](tasks/add-certification-type-vendor-public-sector.md)

[Control access to purchase agreements](tasks/control-access-purchase-agreements-public-sector.md)

[Create a one-time vendor and invoice](tasks/create-one-time-vendor-invoice-public-sector.md)

[Create a vendor certification type](tasks/create-vendor-certification-type-public-sector.md)

[Import and create multiple one-time vendors and invoices](tasks/import-multiple-one-time-vendors.md)

[Set up purchase agreement classifications](tasks/set-up-purchase-agreement-classifications-public-sector.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
