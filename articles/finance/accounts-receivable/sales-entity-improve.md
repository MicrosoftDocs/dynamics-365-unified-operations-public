---
title: Improve performance and efficiency of Sales invoice entities
description: This article describes improvements of sales invoice entities.
author: prabhatb
ms.author: prabhatb
ms.reviewer: twheeloc
ms.search.form:
ms.topic: how-to
ms.date: 04/26/2024
audience: Application User
ms.custom: 
  - bap-template

---
# Improve performance and efficiency of sales invoice entities

[!include [banner](../includes/banner.md)]

To enhance the performance and efficiency of our sales invoice entities, significant improvements have been made by eliminating inefficient views, and computed columns. This article provides an overview of the
changes made.


## Overview

The previous implementations suffered from inefficiencies caused by nested views that duplicated larger tables, resulting in multiple queries to fetch the required data. To address this, all views are removed from existing entities and new versions **Sales invoice headers V4** and **Sales invoice lines V4** are introduced.

The new entities don't rely on inefficient views and directly fetch all columns from the data sources, allowing for faster data retrieval. In addition, all computed columns responsible for row-by-row processing were eliminated, further improving performance.

Previously, the **Total discount amount** column was in the header entity. In the latest version, this information is found in three separate columns: **Cash discount**, **End discount**, and **Total line discount**. The **Total discount amount** is now calculated as the sum of these three columns.

The **Product name** column is now two separate columns: **Product name** and **Product variant name**. This eliminates the need for computed columns and allows users to retrieve the product name from either the variant (if it exists) or the product itself.

In the **Sales invoice lines V4** entity, there are two new columns: **Line total charge amount** and **Line total tax amount**. Previously, these values were fetched from separate views, but now they are directly
sourced from the **CustInvoiceTrans** Table. Calculation logic computes these values for new sales orders and free text invoices.

Similarly, in the header V4 entity, the **Invoice header tax amount** field, previously obtained from the **CustInvoiceJourTotalTaxAmountView**, is now sourced from the **CustInvoiceJourTable**. By removing 
unnecessary views and refining data sources, performance is improved.

To ensure a smooth transition, a **SysSetup** async script is available to update the newly created columns for existing records in the **CustInvoiceJour** and **CustInvoiceTrans** tables. When customers
upgrade to version 10.0.41, the **CustInvoiceTaxFieldsSysSetup** script automatically creates a batch job responsible for updating the **Total tax**, **Total charge**, and **Header tax** fields in the respective tables. 

>[!NOTE]
> This script may take a few hours to complete.

To address the performance issues reported by customers, we have made these necessary improvements. Users are encouraged to utilize the **Sales invoice headers V4** and **Sales invoice lines V4** entities for improved performance and efficiency.

Several incidents have been reported that are related to performance issues with **Sales invoice header** and **Sales invoice line** entities. These incidents are resolved through the changes outlined, ensuring a smoother experience for our customers.

For more information and updates on the status of the batch job, follow these steps:

1. Go to **System administration > Inquiries > Batch jobs**.
2. Find the job description containing "**CustInvoiceTaxFieldsSysSetup**."

### Additional information

For more information, see [SalesInvoiceHeaderEntity or SalesInvoiceHeaderV2Entity performance issues](../../cloud-ai-platform/business-applications-and-platform/bap-ai-erp/aierp-finance/d365-finance-application-core-services/dynamics-365-ai-erp/tsgs/finance/accountsreceivable/salesorderinvoicing/salesorderinvoicingentities/salesinvoiceheaderentityorsalesinvoiceheaderv2entityperformanceissues).

For more information, see [Slow performance or high DTU for SalesInvoiceLineEntity and SalesInvoiceLineV2Entity](../../../cloud-ai-platform/business-applications-and-platform/bap-ai-erp/aierp-finance/d365-finance-application-core-services/dynamics-365-ai-erp/tsgs/finance/accountsreceivable/salesorderinvoicing/salesorderinvoicingentities/slowperformanceorhighdtuforsalesinvoicelineentityandsalesinvoicelinev2entity).

