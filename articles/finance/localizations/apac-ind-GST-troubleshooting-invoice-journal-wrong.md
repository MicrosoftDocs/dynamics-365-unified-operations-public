---
# required metadata

title: Field value in an invoice journal or voucher is wrong
description: This topic provides troubleshooting information to help resolve the issue of incorrect field value in an invoice journal or voucher.
author: yungu
ms.date: 02/27/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---



# Field value in an invoice journal or voucher is wrong

[!include [banner](../includes/banner.md)]

When working with an invoice journal or voucher, you may find an incorrect field value in the following places:

- Posted sales tax (**TaxTrans** table)
- **TaxDocumentRowTransaction**
- **TaxDocumentComponentTransaction**
- Voucher (**GeneralJournalAccountEntry** table)

If this occurs, complete the sections in this topic to try to resolve the issue. In this topic, a free text invoice will be used as an example.


## Check the tax document

Check whether the tax calculation issue is also on the tax document. If the tax document is incorrect, see [Tax amount is wrong after calculation](./apac-ind-GST-troubleshooting-tax-amount-wrong-after-calculation.md). If it isn't, continue to the next section.

Complete the following steps to check if the tax amount on the tax document is correct.

1. On the **Tax document** page, expand the **Tax details** FastTab, and check the field information on the **Overview** and **Details** tabs.

     [![Tax details FastTab](./media/field-value-invoice-journal-voucher-Picture1.png)](./media/field-value-invoice-journal-voucher-Picture1.png)

2. In the lines view, select **View tax input** to check additional fields such as **Transaction date**, **Invoice date**, and **Tax direction**.

      [![View tax input button](./media/field-value-invoice-journal-voucher-Picture2.png)](./media/field-value-invoice-journal-voucher-Picture2.png)

## Check voucher

On the tax document, select **Voucher** to check if the amount is posted to other account. If the amount is posted to another account, see [[India GST posting\] Posted ledger account error](onenote:#[India GST posting] Posted ledger account error&section-id={0C2E0F0D-BD8F-4B30-9A49-6E8095D85BDA}&page-id={E441746C-22F2-4E7E-BAA6-C11D83CFB436}&end&base-path=https://microsoftapc.sharepoint.com/teams/dynamicstaxengine/SiteAssets/Dynamics Tax Engine/Tax Integration/Rocks.one). If the amount isn't posted to a different account, continue to the next section.

   [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture3.png)](./media/field-value-invoice-journal-voucher-Picture3.png)

##  Debug the code to analyze the logic

  1. If field in voucher (table GeneralJournalAccountEntry) is wrong, go to Microsoft.

  2. If filed in posted sales tax (table TaxTrans) is wrong. 

     1. Set breakpoint in the "TaxAccountingPostTaxTransHandlerBase".

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture4.png)](./media/field-value-invoice-journal-voucher-Picture4.png)

     2. Set breakpoints in the wrong  value assigned in "TaxAccountingPostTaxTransHandler". i.e., set breakpoints for "taxTrans.TaxAmount" 

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture5.png)](./media/field-value-invoice-journal-voucher-Picture5.png)

  3. If field in TaxDocumentRowTransaction is wrong. Set breakpoint as below, and check the logic.

  4. 1. Set breakpoint in the "TaxAccountingPostTaxTransHandlerBase".

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture6.png)](./media/field-value-invoice-journal-voucher-Picture6.png)

     2. Set breakpoints in the wrong  value assigned in "TaxAccountingPostTaxRowTransHandler". i.e., set breakpoints for "taxDocumentRowTransaction.BaseAmountCur" 

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture7.png)](./media/field-value-invoice-journal-voucher-Picture7.png)

  5. If filed in TaxDocumentComponentTransaction is wrong. Set breakpoint as below, and check the logic.

  6. 1. Set breakpoint in the "TaxAccountingPostTaxTransHandlerBase".

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture8.png)](./media/field-value-invoice-journal-voucher-Picture8.png)

     2. Set breakpoints in the wrong value assigned in "TaxAccountingPostTaxCompTransHandler". i.e., set breakpoints for "taxDocumentComponentTransaction.TaxAmount" 

         [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture9.png)](./media/field-value-invoice-journal-voucher-Picture9.png)

## Determine whether customization exists

If you've completed the steps in the previous section but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
