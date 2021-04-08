---
# required metadata

title: Field value in invoice journal or voucher is wrong
description:
author: yungu
manager: beya
ms.date: 02/04/2021
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



# Field value in invoice journal or voucher is wrong

[!include [banner](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/finance/includes/banner.md)]

## **Symptom**

- The filed in posted sales tax (table TaxTrans) is wrong.
- The field in TaxDocumentRowTransaction is wrong.
- The field in TaxDocumentComponentTransaction is wrong.
- The field in voucher (table GeneralJournalAccountEntry) is wrong.

 

## **Trouble shooting guide**

**Here take free text invoice as an example.**

- **Step 1: Check tax document**

  Click tax document to check if it is tax calculation issue. If tax document is wrong as well, go to [Tax amount is wrong after calculation](./apac-ind-GST-troubleshooting-tax-amount-wrong-after-calculation.md); Otherwise, go to step 2.

  For example, check if tax amount of tax document is right or not:

  1. Check *Tax details*: Overview and Details.

     [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture1.png)](./media/field-value-invoice-journal-voucher-Picture1.png)

  2. By the way, for other fields issue, you can also check "View tax input" in lines to find more information, i.e., transaction date, invoice date, tax direction and so on.

      [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture2.png)](./media/field-value-invoice-journal-voucher-Picture2.png)

- **Step 2: Check voucher**

  Click Voucher to check if the amount is posted to other account. If yes, go to the [[India GST posting\] Posted ledger account error](onenote:#[India GST posting] Posted ledger account error&section-id={0C2E0F0D-BD8F-4B30-9A49-6E8095D85BDA}&page-id={E441746C-22F2-4E7E-BAA6-C11D83CFB436}&end&base-path=https://microsoftapc.sharepoint.com/teams/dynamicstaxengine/SiteAssets/Dynamics Tax Engine/Tax Integration/Rocks.one); Otherwise, go to Step 3.

   [![Direct taxes (tab)](./media/field-value-invoice-journal-voucher-Picture3.png)](./media/field-value-invoice-journal-voucher-Picture3.png)

- **Step 3: Check/Debug code to analyze the logic.**

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

- **Step 4: If no issue is found in above steps, check whether customization exists. If not, create a service request to Microsoft for further support.**



[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/includes/footer-banner.md)]