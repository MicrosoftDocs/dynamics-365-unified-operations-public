---
# required metadata

title: Invoice capture solution dashboard
description: This article describes the Invoice capture solution dashboard.
author: sunfzam
ms.date: 07/19/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution dashboard

[!include [banner](../includes/banner.md)]

In Invoice capture, the dashboard includes charts that provide an overview of invoices that have been imported. These charts can help the Accounts Payable (AP) manager analyze the performance of the invoice generation process. The AP manager can view the status of the invoice generation process and, by applying different filters, can also view details.

## Available charts

The following charts are available on the dashboard:

- **All captured invoice by status** – This chart shows the following statuses for a captured invoice. By selecting a status, users can filter the captured invoices in the detailed list.

    - Captured
    - Complete
    - In review
    - Obsoleted

- **Total captured invoice volume** – This chart shows the number of captured invoices by period. Users can change the period by using the drop-down list.
- **Captured invoice from top vendors** – This chart shows the total number of invoices per vendor. The vendors that have the most invoices appear at the top.
- **Days to complete per invoice with exceptions** – This chart shows the average number of days that are required to capture one invoice. This information can help the AP manager analyze the time to process an invoice when manual intervention is required. If there is an upward trend, users can review the process details and adjust settings to help reduce the number of days that are required.
- **Incomplete invoices by pending time** – This chart shows the number of days that a captured invoice hasn't been generated in the enterprise resource planning (ERP) system. The larger the number of pending days, the longer the invoice generation process. The AP manager can drill down into the detailed captured invoices and generate invoices in the ERP system.
