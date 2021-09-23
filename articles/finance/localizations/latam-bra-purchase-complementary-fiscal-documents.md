---
# required metadata

title: Purchase complementary fiscal documents for Brazil
description: This topic describes the concept of a purchase complementary invoice for the Brazilian localization.
author: sndray
ms.date: 08/08/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BrazilParameters, FBFiscalDocument_BR, PurchComplementaryInvoice, PurchComplementaryInvoiceCancel_BR, PurchComplementaryInvoiceListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 269154

ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Purchase complementary fiscal documents for Brazil

[!include [banner](../includes/banner.md)]

This topic describes the concept of a purchase complementary invoice for the Brazilian localization.

## Overview

According to the fiscal regulations in Brazil, a specific fiscal document that is known as a complementary invoice (Nota fiscal complementar) is issued or received for correction purposes. For example, if the prices of goods or services from the original invoice were incorrectly registered, a complementary invoice is required in order to fix the error. Complementary invoices are applicable only if the difference is positive. In other words, they are applicable only if the current prices or taxes amounts are more than original prices or taxes amounts. Because fiscal invoices of this type are considered complements of the original invoices, the original invoices don’t have to be canceled. Companies are obligated to issue or receive complementary invoices for the following reasons:

-   Error in the price of the goods or services
-   Error in the quantity of goods or services
-   Error in the tax percentage
-   Error in the tax calculation

## Purchase complementary fiscal document
You can create a purchase complementary fiscal document to adjust a purchase fiscal document that was generated for an incorrect price, an incorrect Imposto sobre Produtos Industrializados (IPI) amount, or an incorrect Imposto sobre Circulação de Mercadorias e Serviços (ICMS) amount. A purchase complementary fiscal document is issued only to adjust a positive difference. For example, a purchase complementary fiscal document is generated if the price of an item on the original purchase fiscal document is incorrect, and if the correct price for the item is more than the price that is recorded on the original purchase fiscal document. You can create a purchase complementary fiscal document to adjust an error in the price or quantity of items or services, the tax percentage, or the tax calculation. The purchase complementary fiscal document is a purchase fiscal document that complements the original purchase fiscal document. All information, except information about charges, is updated from the original purchase fiscal document. You can't add lines to or delete lines from a purchase complementary fiscal document. The following types of purchase complementary fiscal documents are available:

-   **Price** – This type of complementary fiscal document is created to adjust an incorrect price for a fiscal document. The correct price must be more than the price that is recorded on the original fiscal document. The price difference is charged to the vendor.
-   **IPI** – This type of complementary fiscal document is created to adjust an incorrect IPI tax amount for a fiscal document. The IPI tax difference is charged to the vendor.
-   **ICMS** – This type of complementary fiscal document is created to adjust an incorrect ICMS tax amount for a fiscal document. The ICMS tax difference is received by the legal entity and paid to the tax authorities.

You can create an ICMS complementary fiscal document only if the tax groups that you select for the purchase complementary fiscal document include ICMS tax codes. Likewise, you can create an IPI complementary fiscal document only if the tax groups that you select for the purchase complementary fiscal document include IPI tax codes. For example, if you create an IPI complementary fiscal document, but the existing tax groups don't have the IPI tax type, you must select a tax group that has an IPI tax code. You can cancel and inquire about a purchase complementary fiscal document that has been posted on the **All purchase complementary fiscal documents** page.

## Prerequisites
Before you can create and post purchase complementary fiscal document, the following parameters must be configured on the **Brazilian parameters** page:

-   **Complementary fiscal document** – Specify the default fiscal document source text.
-   **Sales tax code for COFINS** – Specify the sales tax code that is used for the COFINS tax calculation amount.
-   **Sales tax code for PIS** – Specify the sales tax code that is used for the PIS tax calculation amount.

## Examples
[![Example that shows an original invoice together with purchase complementary fiscal documents of each of the three types.](./media/purchcomplementary-1024x349.png)](./media/purchcomplementary.png)


For more information, see the following topics:

[Create and post a purchase complementary fiscal document (Brazil)](tasks/br-00026-1-create-post-purchase-complementary-fiscal-document.md)

[Cancel a purchase complementary fiscal document (Brazil)](tasks/br-00026-2-cancel-purchase-complementary-fiscal-document.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]