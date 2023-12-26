---
title: Vendor payments workspace
description: This article provides information about the Vendor payments workspace. The Vendor payments workspace shows information that is related to the processing of vendor payments.
author: abruer
ms.date: 10/16/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: shpandey
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
ms.assetid: 
ms.search.form: VendPaymentWorkspace
---

# Vendor payments workspace

[!include [banner](../includes/banner.md)]

The **Vendor payments** workspace shows information that is related to the processing of vendor payments. This workspace includes a **My work** view and an **Analytics** page. The **My work** view shows summary tiles, vendor transaction grids, and related vendor information. The **Analytics** page uses the capabilities of Microsoft Power BI to show visuals that are related to vendor payments.

## Setup needed to view Power BI content

The following setup needs to be completed for data to display in **Vendor payments** Power BI visuals.
1. Go to **System administration > Setup > System Parameters** to set **System currency** and **System Exchange Rate**.
2. Go to **General Ledger > Calendars > Fiscal calendars** to validate fiscal calendar dates assigned to the active time period.
3. Go to **General Ledger > Setup > Ledger**  to set **Accounting Currency** and **Exchange Rate Type**. 
4. Define exchange rates between transaction currencies and accounting currency, and accounting currency and system currency. To do this, go to **General Ledger > Currencies > Currency exchange rates**.
5. Go to **System administration > Setup > Entity Store** to refresh the latest version of **Vendor payment measure** aggregate measurement. For example, **Vendor payment measure V3** as of August 2023.

## My work view

### Summary tiles

The tiles in the **Summary** section give an overview of the state of your payment information. You can see payment journals that aren't yet posted, invoices that are past due, all vendors, and vendors that are on hold. From the **Summary** section, you can create a new pay run.

The information in the **Summary** section is for the company that you're signed in to.

### Vendor transactions grids

The **Vendor transactions** section contains grids that show the invoices that are past due and payments that aren't settled. From the **Invoices past due** grid, you can view the settlement history for a selected invoice. From the **Payments not settled** grid, you can view the settlement history for a selected invoice and settle an invoice.

Centralized payment clerks can use a filter that appears at the top of each grid to select a company. The grid is then filtered so that it shows only those companies that are defined in the centralized payment organizational hierarchy that the centralized payment clerk has rights to view.

The **Find transactions** tab in the **Vendor transactions** section lets you search for a vendor transaction.

### Related information

You can view the **Vendor aging** report and the **Payment summary by date** report by using the links in the **Related information** section of the workspace.

## Analytics page

The **Analytics** page provides important metrics, such as vendor invoices that are past due and vendor invoices that are due in the future. This page contains nine report pages. One page provides an overview, and the other eight pages provide details about Accounts payable payment metrics.

The following table shows the visualizations that are available on each report page.


|            Report page            |                                                                                                                                                                                Visualization                                                                                                                                                                                |
|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Vendor payments overview      | <ul><li>Invoices past due</li><li>Invoices due today</li><li>Discounts taken to discounts lost</li><li>Invoices due in future by cash discount date</li><li>Invoices due in future by due date</li><li>Invoices paid late to invoices paid on time</li><li>Payment workflow assignment</li><li>Vendor to customer balance</li><li>Open invoices with payment hold</li></ul> |
|         Invoices past due         |                                                                                             <ul><li>Invoices past due</li><li>Invoices past due details</li><li>Total open invoices</li><li>Invoices past due per vendor group</li><li>Invoices past due per company</li></ul>                                                                                              |
|        Invoices due today         |                                                                                                         <ul><li>Invoices due today</li><li>Invoices due today details</li><li>Invoices due today per company</li><li>Invoices due today per vendor group</li></ul>                                                                                                          |
| Discounts taken to discounts lost |                                                                             <ul><li>Discounts taken to discount lost</li><li>Discounts taken to discount lost details</li><li>Discounts taken to discount lost per company</li><li>Discounts taken to discount lost per vendor group</li></ul>                                                                              |
|      Invoices due in future       |                                                 <ul><li>Invoices due in future</li><li>Invoices due in future details</li><li>Invoices due in future per company</li><li>Invoices due in future per vendor group</li><li>Invoices due in future by cash discount date</li><li>Invoices due in future by due date</li></ul>                                                  |
|        Invoices paid late         |                                                         <ul><li>Invoices paid after due date</li><li>Invoices paid after due date details</li><li>Invoices paid after due date per company</li><li>Invoices paid after due date per vendor group</li><li>Invoices paid late versus invoices paid on time</li></ul>                                                          |
|         Payment workflow          |                                                                                <ul><li>Vendor payment workflow instances</li><li>Vendor payment workflow instances per approver</li><li>Vendor payment workflow instances per company</li><li>Average days in workflow by approver</li></ul>                                                                                |
|    Vendor to customer balance     |                                                                                                                   <ul><li>Vendor to customer balance</li><li>Vendor to customer balance per company</li><li>Vendor to customer balance details</li></ul>                                                                                                                    |
|    Invoices with payment hold     |                                                                                         <ul><li>Invoices with payment hold</li><li>Invoices with payment hold details</li><li>Invoices with payment hold per company</li><li>Invoices with payment hold per vendor group</li></ul>                                                                                          |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
