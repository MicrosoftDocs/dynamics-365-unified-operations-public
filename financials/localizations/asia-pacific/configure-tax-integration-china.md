---
# required metadata

title: Configure tax integration for China
description: This topic describes the process for configuring tax integration for China.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-22 16 - 55 - 28
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 265264
ms.assetid: e5dbbbe1-935f-4fb4-a014-447916051628
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: leguo
ms.dyn365.ops.intro: 01-11-2016
ms.dyn365.ops.version: Version 1611

---

# Configure tax integration for China

This topic describes the process for configuring tax integration for China.

To configure tax integration for China, complete the following tasks.

1.  Create a new VAT invoice description on the **VAT invoice description** page. For example, you may need to set  the following parameters:
    -   **VAT invoice description ID** to InvoiceDescID01
    -   **Description** to 详见销售清单
    -   **Unit** to Box

2.  Create a new tax integration profile on the **Tax integration profiles** page. You can set up tax integration profiles to use when invoices are imported or exported. In the tax integration profile, you can specify the following:
    -   Sales tax code
    -   Maximum invoice amount
    -   Default description and unit for the golden tax invoice
    -   Whether to include non-deductible VAT invoices

The tax integration process is illustrated in the following diagram. [![IC666469](./media/ic666469.gif)](./media/ic666469.gif)

See also
--------

[Import the Chinese Golden Tax data entity](import-chinese-golden-tax-data-entity.md)

[Chinese tax integration modification for VAT customer invoices FAQ](chn-chinese-tax-integration-vat-customer-invoices.md)

