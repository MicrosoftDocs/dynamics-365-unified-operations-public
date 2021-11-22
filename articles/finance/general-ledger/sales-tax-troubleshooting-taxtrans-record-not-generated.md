---
# required metadata

title: TaxTrans record isn't generated
description: This topic provides troubleshooting information that can help when a TaxTrans record isn't generated.
author: qire
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# TaxTrans record isn't generated

[!include [banner](../includes/banner.md)]

If you select **Posted sales tax** for a transaction, but the **Posted sales tax** page either shows no tax lines or is missing a tax line, the **TaxTrans** record might not have been generated.

[![Posted sales tax page that has no line items.](./media/taxtrans-is-not-generated-Picture1.png)](./media/taxtrans-is-not-generated-Picture1.png)

To troubleshoot this issue, follow the steps in the following sections as required.

## Check the sales tax before you post the transaction

1. Before you post the transaction, on the **Posting invoice** page, select **Sales tax** to check the calculation.

    [![Sales tax button on the Posting invoice page.](./media/taxtrans-is-not-generated-Picture2.png)](./media/taxtrans-is-not-generated-Picture2.png)

2. On the **Temporary sales tax transactions** page, review the result of the calculation. If no tax is calculated, see [Tax isn't calculated or the tax amount is zero](sales-tax-troubleshooting-tax-not-calculated-amount-zero.md).

## Find the TaxTrans record in all posted sales tax

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** > **Posted sales tax**.
2. In the **Voucher** column heading, select the filter symbol to find the **TaxTrans** record.
3. If you find the sales tax records that you're looking for, check the date. If the date differs from the date of the journal header, create a Microsoft service request for additional support.

    [![Posted sales tax page.](./media/taxtrans-is-not-generated-Picture4.png)](./media/taxtrans-is-not-generated-Picture4.png)

## Debug to check details

1. For information about how to debug and determine whether **TmpTaxWorkTrans** and **TaxUncommitted** are correctly generated, see [Field value in TaxTrans is incorrect](sales-tax-troubleshooting-field-value-taxtrans-incorrect.md).
2. If **TaxTmpWorkTrans** or **TaxUncommitted** is correctly generated, add a breakpoint at **TaxPost::SaveAndPost()** and **Tax::SaveAndPost** to debug the reason why **TaxTrans** isn't inserted.

    [![Breakpoints added in code.](./media/taxtrans-is-not-generated-Picture5.png)](./media/taxtrans-is-not-generated-Picture5.png)

    [![Results of added breakpoints.](./media/taxtrans-is-not-generated-Picture6.png)](./media/taxtrans-is-not-generated-Picture6.png)

## Determine whether customization exists

If you've completed the steps in the previous sections but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
