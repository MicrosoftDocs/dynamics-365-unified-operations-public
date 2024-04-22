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

To enhance the performance and efficiency of our sales invoice entities, we have made significant improvements by eliminating inefficient views, and computed columns. This article provides an overview of the
changes made and the benefits they bring.


## Overview

The previous implementation suffered from inefficiencies caused by nested views that duplicated larger tables, resulting in multiple queries to fetch the required data. To address this, we have removed all views 
from the existing entities and introduced new versions called Sales Invoice Headers V4 and Sales Invoice Lines V4.

The new entities no longer rely on inefficient views but instead directly fetch all columns from the data sources, allowing for faster data retrieval. In addition, we have eliminated all computer columns 
responsible for row-by-row processing, further improving performance.

Previously, the Total Discount Amount column was present in the header entity. In the latest version, we have exposed this information through three separate columns: Cash Discount, End Discount, and Total Line 
Discount. The Total Discount Amount can now be calculated as the sum of these three columns.

Another improvement is the exposure of the Product Name column as two separate columns: Product Name and Product Variant Name. This change eliminates the need for computed columns and allows users to retrieve the
product name from either the variant (if it exists) or the product itself.

In the Sales Invoice Lines V4 entity, we have introduced two new columns: Line Total Charge Amount and Line Total Tax Amount. Previously, these values were fetched from separate views, but now they are directly
sourced from the **CustInvoiceTrans** Table. Calculation logic has been implemented to compute these values for new sales orders and free text invoices.

Similarly, in the header V4 entity, the Invoice Header Tax Amount field, previously obtained from the **CustInvoiceJourTotalTaxAmountView**, is now sourced from the **CustInvoiceJourTable**. By removing 
unnecessary views and refining our data sources, we have significantly improved performance.

To ensure a smooth transition, we have created a **SysSetup** Async script that updates the newly created columns for existing records in the **CustInvoiceJour** and **CustInvoiceTrans** Tables. When customers
upgrade to version 10.0.41, the **CustInvoiceTaxFieldsSysSetup** script will automatically create a batch job responsible for updating the Total Tax, Total Charge, and Header Tax fields in the respective tables. 
Please note that this script may take a few hours to complete.

To address the performance issues reported by customers, we have made these necessary improvements. We encourage users to utilize the Sales Invoice Headers V4 and Sales Invoice Lines V4 entities for improved 
performance and efficiency.

Additionally, it is worth mentioning that we have encountered several incidents related to performance issues with our Sales Invoice Header and Sales Invoice Line entities. These incidents have been resolved 
through the changes outlined, ensuring a smoother experience for our customers.

For more information and updates on the status of the batch job, user can check the Batch Job page under -

**System Administration > Inquiries > Batch Jobs**. Look for the job description containing "**CustInvoiceTaxFieldsSysSetup**."

The performance and efficiency of our sales invoice entities have been significantly enhanced by eliminating inefficient views, computed columns, and introducing optimized versions. 

**Learn article:**  

[SalesInvoiceHeaderEntity or SalesInvoiceHeaderV2Entity performance issues | AI ERP (eng.ms)](https://eng.ms/docs/cloud-ai-platform/business-applications-and-platform/bap-ai-erp/aierp-finance/d365-finance-application-core-services/dynamics-365-ai-erp/tsgs/finance/accountsreceivable/salesorderinvoicing/salesorderinvoicingentities/salesinvoiceheaderentityorsalesinvoiceheaderv2entityperformanceissues)

[Slow performance or high DTU for SalesInvoiceLineEntity and SalesInvoiceLineV2Entity | AI ERP (eng.ms)](https://eng.ms/docs/cloud-ai-platform/business-applications-and-platform/bap-ai-erp/aierp-finance/d365-finance-application-core-services/dynamics-365-ai-erp/tsgs/finance/accountsreceivable/salesorderinvoicing/salesorderinvoicingentities/slowperformanceorhighdtuforsalesinvoicelineentityandsalesinvoicelinev2entity)

