---
title: Improve performance and efficiency of sales invoice entities
description: This article describes changes that were made to improve the performance and efficiency of sales invoice entities.
author: leizi2015
ms.author: raynezou
ms.reviewer: twheeloc
ms.search.form:
ms.topic: how-to
ms.date: 08/08/2024
audience: Application User
ms.custom: 
  - bap-template

---
# Improve performance and efficiency of sales invoice entities

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

To significantly improve the performance and efficiency of our sales invoice entities, Microsoft has eliminated inefficient views and computed columns. This article provides an overview of the changes.

In previous implementations, nested views that duplicated larger tables caused inefficiencies. As a result, multiple queries were needed to fetch the required data. To address this issue, we removed all views from existing entities and introduced new versions, **Sales invoice headers V4** and **Sales invoice lines V4**. The new entities don't rely on inefficient views but fetch all columns directly from the data sources. Therefore, data retrieval is faster.
 
To further improve performance, we eliminated all computed columns that are responsible for row-by-row processing.

Previously, the **Total discount amount** column was in the header entity. In the latest version, this information is found in three separate columns: **Cash discount**, **End discount**, and **Total line discount**. The **Total discount amount** value is calculated as the sum of these three columns.

The **Product name** column is now two separate columns: **Product name** and **Product variant name**. This change eliminates the need for computed columns. Users can retrieve the product name from either the variant (if it exists) or the product itself.

In the **Sales invoice lines V4** entity, there are two new columns: **Line total charge amount** and **Line total tax amount**. Previously, these values were fetched from separate views. They're now sourced directly from the **CustInvoiceTrans** table. Calculation logic computes these values for new sales orders and free text invoices.

Similarly, in the header V4 entity, the **Invoice header tax amount** field that was previously obtained from the **CustInvoiceJourTotalTaxAmountView** view is now sourced from the **CustInvoiceJourTable** table. The removal of unnecessary views and refinement of data sources help improve performance.

To ensure a smooth transition, a **SysSetup** async script is available. This script updates the newly created columns for existing records in the **CustInvoiceJour** and **CustInvoiceTrans** tables. When customers upgrade to version 10.0.40, the **CustInvoiceTaxFieldsSysSetup** script automatically creates a batch job that updates the **Total tax**, **Total charge**, and **Header tax** fields in the appropriate tables.

> [!NOTE]
> The job may take three days or more to run to avoid potential system corruption.

> [!IMPORTANT]
> If you have Synapse configured, you will see a higher level record changes due to this update batch job touching all records. 

These necessary improvements address the performance issues that customers have reported. Users are encouraged to use the **Sales invoice headers V4** and **Sales invoice lines V4** entities for improved performance and efficiency.

Several incidents that have been reported are related to performance issues with **Sales invoice header** and **Sales invoice line** entities. Through the changes that are outlined in this article, we fixed these incidents to ensure a smoother experience for our customers.

For more information and updates about the status of the batch job, follow these steps.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Find the job description that contains "CustInvoiceTaxFieldsSysSetup."
