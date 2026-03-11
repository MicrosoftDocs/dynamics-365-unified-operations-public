---
title: File formats for methods of payment
description: Learn about the two methods for getting file formats that you can use for methods of payment, including an outline on electronic reporting file formats.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Belgium, France, Germany, Norway, Spain, Sweden, Switzerland
ms.search.validFrom: 2016-11-30
ms.search.form: CustPaymMode, VendPaymMode
---

# File formats for methods of payment

[!include [banner](../../includes/banner.md)]

This article describes two methods for getting file formats that you can use for methods of payment.

You can use electronic reporting (ER) file formats or X++ file formats to get file formats for use with methods of payment. When you set up a method of payment for a customer or vendor, you indicate which file formats and standards to use for payments and how to process payments. You can select from the following types of formats:

- Export
- Import
- Return
- Remittance

### Method 1: Electronic reporting file formats

For file formats that are based on ER configurations, import the configurations from Lifecycle Services (LCS). For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md). After you import reporting configurations for those file formats, you can select the imported formats on the **Methods of payment** page. The process for importing and selecting file formats for Europe is similar to the procedure for Japan. For more details, see [Enable the JBA payment file format](../japan/jba-payment-file-format.md).

### Method 2: X++ file formats

To select file formats that are based on X++ code, complete the following steps.

1. Go to the **Methods of payment** page.
1. On the **File formats** FastTab, select **Setup**.
1. Select the tab that corresponds with the file format type.
1. Select a file format from the **Available** list and move it to the **Selected** list by using the arrow control.
1. Close the **File formats for methods of payment** page.
1. On the **File formats** FastTab, select the file format to use for the method of payment from the appropriate file format field. Set the General electronic reporting options to **No** for X++ file formats.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
