---
# required metadata

title: Sales complementary fiscal documents for Brazil
description: This topic describes sales complementary invoice for the Brazilian localization.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: BrazilParameters, FBFiscalDocument_BR, SalesComplementaryInvoice, SalesComplementaryInvoiceCancel_BR, SalesComplementaryInvoiceListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269194
ms.assetid: 0c52b508-1044-48c1-9dfc-a590bbda5696
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Sales complementary fiscal documents for Brazil

[!include[banner](../includes/banner.md)]


This topic describes sales complementary invoice for the Brazilian localization.

Overview
--------

According to the fiscal regulations in Brazil, a specific fiscal document that is known as a complementary invoice (Nota fiscal complementar) is issued or received for correction purposes. For example, if the prices of goods or services from the original invoice were incorrectly registered, a complementary invoice is required in order to fix the error. Complementary invoices apply only if the difference is positive. In other words, they apply only if the current prices or taxes amounts are more than original prices or taxes amounts. Because fiscal invoices of this type are considered complements of the original invoices, the original invoices don’t have to be canceled. Companies are obligated to issue or receive complementary invoice for the following reasons:

-   Error in the price of the goods or services
-   Error in the quantity of the goods or services
-   Error in the tax percentage

## Sales complementary fiscal document
You must create a sales complementary fiscal document to adjust a sales fiscal document that was generated for an incorrect price, an incorrect Imposto sobre Produtos Industrializados (IPI) amount, or an incorrect Imposto sobre Circulação de Mercadorias e Serviços (ICMS) amount. A sales complementary fiscal document is issued to adjust only a positive difference. For example, a sales complementary fiscal document is generated if the price of an item on the original customer fiscal document is incorrect, and if the correct price for the item is more than the price that is recorded on the original customer fiscal document. You can create a sales complementary fiscal document to adjust an error in the price or quantity of items or services, the tax percentage, or the tax calculation. The sales complementary fiscal document is a sales fiscal document that complements the original sales fiscal document. All information, except information about charges, is updated from the original sales fiscal document. You can't add lines to or delete lines from a sales complementary fiscal document. The following types of sales complementary fiscal documents are available:

-   **Price** – This type of complementary fiscal document is created to adjust an incorrect price for a fiscal document. The correct price must be more than the price that is recorded on the original fiscal document. The price difference is charged to the customer.
-   **IPI** – This type of complementary fiscal document is created to adjust an incorrect IPI tax amount for a fiscal document. The IPI tax difference is charged to the customer.
-   **ICMS** – This type of complementary fiscal document is created to adjust an incorrect ICMS tax amount for a fiscal document. The ICMS tax difference is received by the legal entity and paid to the tax authorities.

You can create an ICMS complementary fiscal document only if the tax groups that you select for the sales complementary fiscal document include ICMS tax codes. Likewise, you can create an IPI complementary fiscal document only if the tax groups that you select for the sales complementary fiscal document include IPI tax codes. For example, if you create an IPI complementary fiscal document, but the existing tax groups don't have the IPI tax type, you must select a tax group that has an IPI tax code. You can cancel and inquire about a sales complementary fiscal document that has been posted on the **All sales complementary fiscal documents** page.

## Prerequisites
Before you can create or post sales complementary fiscal documents, the following parameters must be set up on the **Brazilian parameters** page:

-   **Complementary fiscal document** – Specify the default fiscal document source text.
-   **Sales tax code for COFINS** – Specify the sales tax code that is used for the Contribuição para o Financiamento da Seguraridade Social (COFINS) tax calculation amount.
-   **Sales tax code for PIS** – Specify the sales tax code that is used for the Programa de Integração Social (PIS) tax calculation amount.

## Examples
[![Examples of an original invoice and sales complementary fiscal documents of each of the three types](./media/salescomplementary-1024x409.png)](./media/salescomplementary.png)



