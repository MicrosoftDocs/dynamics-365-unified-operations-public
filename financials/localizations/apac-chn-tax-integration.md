---
# required metadata

title: Configure tax integration for China
description: This topic describes the process for configuring tax integration for China.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 265264
ms.assetid: e5dbbbe1-935f-4fb4-a014-447916051628
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Configure tax integration for China

[!include[banner](../includes/banner.md)]


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

The tax integration process is illustrated in the following diagram.
[![IC666469](./media/ic666469.gif)](./media/ic666469.gif)

See also
--------

[Import the Chinese Golden Tax data entity](apac-chn-import-golden-tax-data-entity.md)

[Chinese tax integration modification for VAT customer invoices FAQ](apac-chn-tax-integration-vat-customer-invoices.md)



