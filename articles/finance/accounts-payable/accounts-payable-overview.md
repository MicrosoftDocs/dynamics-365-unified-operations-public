---
# required metadata

title: Configure Accounts payable overview
description: This article describes the pages that you use to set up basic and optional functionality for Accounts payable. It also describes setup steps that you must complete before you start to set up Accounts payable.
author: abruer
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankAccountTable, DeliveryMode, PaymTerm, VendGroup, VendParameters, VendPaymMode, VendTable, DeliveryReason, DeliveryTerms, DestinationCode
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 82561fe7-b2d6-464c-9347-79d0ce0f9743
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Accounts payable overview

[!include [banner](../includes/banner.md)]

This article describes the pages that you use to set up basic and optional functionality for Accounts payable. It also describes setup steps that you must complete before you start to set up Accounts payable.

## Prerequisites for Accounts payable setup

Before you can set up Accounts payable, you must complete the following setup:

-   In the General ledger:
    -   If you plan to use payment journals, set up payment journals.
    -   If you plan to run exchange rate adjustments, set up currency codes on the **Currencies** page, set up exchange rate types on the **Exchange rate types** page, and set up currency exchange rates on the **Currency exchange rates** page.
-   In Cash and bank management, set up bank accounts to use with methods of payment.

## Setup pages for Accounts payable

Use the following pages to set up the basic functionality of Accounts payable for each legal entity. The pages are listed in the recommended order of setup. To make the setup process easier, you can create templates from the first records that you create. In a template, values are typically entered in many fields to reflect the features that the organization wants to implement for a particular type of vendor.
1.  On the **Terms of payment** page, define the terms of payment that you assign to sales orders, purchase orders, customers, and vendors, and that determine invoice due dates. For more information, see [Define vendor payment fees](tasks/define-vendor-payment-fees.md).
2.  On the **Methods of payment - vendors** page, create and maintain information about how the organization pays its vendors.
3.  On the **Vendor groups** page, create and maintain groups of vendors that share important parameters for posting, settlement and payment, reporting, and forecasting.
4.  On the **Vendor posting profiles** page, define how vendor transactions are posted to the general ledger.
5.  On the **Accounts payable parameters** page, set up default settings that are applied if a more specific setting isn't specified, parameters for various kinds of functionality, and the various number sequences for Accounts payable.
6.  On the **Form setup** page, define the format of various documents that are related to vendors, and that the organization uses to keep track of receipts from vendors and enter reasons for the flow of payments to vendors.
7.  On the **Vendors** page, create and maintain vendor accounts, and also the tax authorities that your organization reports sales taxes to.

## Optional setup pages for Accounts payable
In addition to the basic functionality, Accounts payable has other functionality that you can set up.

The additional setup pages are organized by functionality.

**Policies**
-   On the **Vendor invoice policy** page, set up vendor invoice policies.

**Invoice matching**

-   On the **Invoice totals tolerances** page, set up tolerances for invoice totals.
-   On the **Matching policy** page, set up two-way and three-way matching policies.
-   On the **Price tolerances** page, set up tolerances for unit prices.
-   On the **Item price tolerance groups** page, set up tolerance groups for item prices.
-   On the **Vendor price tolerance groups** page, set up  tolerance groups for vendor prices.
-   On the **Charges tolerances** page, set up tolerances for charges.

**Workflow**

-   On the **Accounts payable workflows** page, set up workflow configurations for journal approvals and purchase requisitions.

**Reasons**

-   On the **Vendor reasons** page, set up reason codes.

**Charges**

-   On the **Charges code** page, set up codes for the charges that are used in purchase orders.
-   On the **Vendor charges group** page, create and maintain charges groups for vendors.
-   On the **Item charge groups** page, create and maintain charges groups for items.
-   On the **Auto charges** page, define the charges that are automatically assigned to orders.

**Supplementary items**

-   On the **Supplementary item groups - Vendor** page, create and maintain supplementary item groups for vendors.
-   On the **Supplementary item groups - Inventory** page, create and maintain supplementary item groups for items.

**Distribution**

-   On the **Terms of delivery** page, create and maintain the conditions for an item's transfer from seller to buyer.
-   On the **Modes of delivery** page, create and maintain the methods of transport that are used when an order is delivered from the seller to the buyer.
-   On the **Destination codes** page, create and maintain identifiers and descriptions for delivery destinations.

**Forms**

-   On the **Form notes** page, create the standard text that appears on various pages.
-   On the **Form sorting parameters** page, set up the sorting order for requisitions, receipt lists, packing slips, and invoices.
-   On the **Print management setup** page, set up print management information for originals and copies of pages.

**Payments**

-   On the **Cash discounts** page, set up and manage the terms for obtaining cash discounts. The cash discount codes are linked to vendors and are applied to purchase orders.
-   On the **Payment schedules** page, set up the payment schedules that are used to manage installment payments to vendors.
-   On the **Payment days** page, define the payment days that are used to calculate due dates, and specify payment days for a specific day of the week or month.
-   On the **Payment fee** page, create and maintain the payment fees that are associated with vendors.
-   On the **Payment instruction** page, create and maintain payment instructions.

**Statistics**

-   On the **Aging period definitions** page, set up user-defined intervals that are used to analyze the maturity distribution of vendor accounts.
-   On the **Line of business** page, create the line of business (LOB) codes that are assigned to vendors.

**Tax 1099**

-   On the **1099 fields** page, verify and update the minimum amounts that must be reported to the Internal Revenue Service (IRS), based on the latest IRS requirements.

## **Optional setup for other modules**
**Organization administration**

-   On the **Number sequences** page, set up number sequence groups for invoice numbers.
-   On the following pages, set up address information:
    -   **Address setup**
    -   **NAF codes**
    -   **Import ZIP/postal codes**

**General ledger**

-   On the **Financial dimensions** page, set up financial dimensions.
-   On the following pages, set up tax information:
    -   **Sales tax codes**
    -   **Sales tax groups**
    -   **Item sales tax groups**
    -   **Account group**
    -   **Sales tax exempt codes**
    -   **Sales tax jurisdictions**
    -   **Sales tax authorities**
    -   **Sales tax settlement periods**

**Cash and bank management**

-   On the **Payment purpose codes** page, set up the **Central Bank purpose code**.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
