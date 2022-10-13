---
# required metadata

title: Invoice capture solution dashboard
description: This article describes the Invoice capture solution dashboard.
author: sunfzam
ms.date: 10/15/2022
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
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

In Invoice capture, the **Dashboard** provides an overview of invoices that have been imported. The Accounts Payable manager can see the status of the invoice process. The AP manager can view details by applying different filters. These charts can help the AP manager analyze the performance of the invoice generation process. 

## Charts available on the Dashboard: 

 - **All captured invoice by status**
This chart displays the following statuses for the captured invoice:
**Captured** 
**Complete** 
**In review** 
**Obsoleted** 

Users can select a status to filter the captured invoices in the detailed list.

 - **Total captured invoice volume**
This chart displays the number of captured invoices by time period. Users are able to change the time period by clicking the drop-down. 

 - **Captured invoice from top vendors**
This chart displays the total number of invoices per vendor. The vendors with largest number of invoices will be displayed on the top. 

 - **Days to complete per invoice with exceptions**
This chart displays the average number of days needed to capture one invoice. This helps the AP manager analyze the time to process an invoice with manual intervention. If there's an upward trend, users can check the process details and adjust settings to improve the days to complete. 

 - **Incomplete invoices by pending time**
This chart displays the number of days that a captured invoice hasn’t been generated in the ERP system. The larger the number of pending days, the longer the invoice generation process. The AP manager can drill into the detailed captured invoices and generate invoices in the ERP system. 

