---
# required metadata

title: Vendor payments workspace
description: This topic provides information about the Vendor payments workspace. The Vendor payments workspace shows information that is related to the processing of vendor payments.
author: twheeloc
manager: AnnBe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update

---

# Vendor payments workspace

[!include[banner](../includes/banner.md)]

The **Vendor payments** workspace shows information that is related to the processing of vendor payments. This workspace includes a **My work** view and an **Analytics** page. The **My work** view shows summary tiles, vendor transaction grids, and related vendor information. The **Analytics** page uses the capabilities of Microsoft Power BI to show visuals that are related to vendor payments.

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

| Report page | Visualization |
|-------------|---------------|
| Vendor payments overview | <ul><li>Invoices past due</li><li>Invoices due today</li><li>Discounts taken to discounts lost</li><li>Invoices due in future by cash discount date</li><li>Invoices due in future by due date</li><li>Invoices paid late to invoices paid on time</li><li>Payment workflow assignment</li><li>Vendor to customer balance</li><li>Open invoices with payment hold</li></ul> |
| Invoices past due | <ul><li>Invoices past due</li><li>Invoices past due details</li><li>Total open invoices</li><li>Invoices past due per vendor group</li><li>Invoices past due per company</li></ul> |
| Invoices due today | <ul><li>Invoices due today</li><li>Invoices due today details</li><li>Invoices due today per company</li><li>Invoices due today per vendor group</li></ul> |
| Discounts taken to discounts lost | <ul><li>Discounts taken to discount lost</li><li>Discounts taken to discount lost details</li><li>Discounts taken to discount lost per company</li><li>Discounts taken to discount lost per vendor group</li></ul> |
| Invoices due in future | <ul><li>Invoices due in future</li><li>Invoices due in future details</li><li>Invoices due in future per company</li><li>Invoices due in future per vendor group</li><li>Invoices due in future by cash discount date</li><li>Invoices due in future by due date</li></ul> |
| Invoices paid late | <ul><li>Invoices paid after due date</li><li>Invoices paid after due date details</li><li>Invoices paid after due date per company</li><li>Invoices paid after due date per vendor group</li><li>Invoices paid late versus invoices paid on time</li></ul> |
| Payment workflow | <ul><li>Vendor payment workflow instances</li><li>Vendor payment workflow instances per approver</li><li>Vendor payment workflow instances per company</li><li>Average days in workflow by approver</li></ul> |
| Vendor to customer balance | <ul><li>Vendor to customer balance</li><li>Vendor to customer balance per company</li><li>Vendor to customer balance details</li></ul> |
| Invoices with payment hold | <ul><li>Invoices with payment hold</li><li>Invoices with payment hold details</li><li>Invoices with payment hold per company</li><li>Invoices with payment hold per vendor group</li></ul> |
