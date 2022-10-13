---
# required metadata

title: Invoice capture solution dashboard
description: This article explains the Invoice capture solution dashboard.
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

Dashboard provides an overview of the captured invoices with different charts. AP manager may see the high-level invoice process status and then drill down into 
detailed view by applying different filtering condition. This helps AP manager to better analysis the performance of invoice process. 

## Dashboard charts

1.	All captured invoice by status:
The chart shows the distribution of statuses for the captured invoice (Captured, Complete, In review, Obsoleted). User is able to quick navigate to the detailed list 
by clicking icon  , and by selecting the corresponding status to filter the captured invoices.

2.	Total captured invoice volume
The chart displays the number of captured invoices by the time granularity. User is able to switch the time-period by clicking the drop down of the view. 

3.	Captured invoice from top vendors
The chart displays the total number of invoices for the vendors. The vendors with biggest invoice volume will be displayed on the top. By clicking the , it will 
navigate to the captured invoice list. By clicking the bar, the captured invoices list will be filtered and displayed. 

4.	Days to complete per invoice with exceptions
The chart shows the average time by days to complete one captured invoice. This helps AP manager to check the trend of the time to process the invoice with manual 
intervention. In case the trend goes higher, AP manager needs to check the details and adjust the settings to make the improvement. 

5.	Incomplete invoices by pending time
The chart shows the pending days that captured invoice hasn’t yet been successfully generated in the ERP system. The larger the pending days, the more attention is 
acquired from AP manager. AP manager needs to drill down into the detailed captured invoices and take some action to make the invoice to be generated successfully in 
ERP system. 

>[!NOTE]
> Only the accounts payable clerk can access the Invoice capture dashboard.
