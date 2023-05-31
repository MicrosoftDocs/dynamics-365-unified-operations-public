---
# required metadata

title: Centralized payments for Accounts payable
description: Organizations that include multiple legal entities can create and manage payments by using a single legal entity that handles all payments. Therefore, the same payments don't have to be entered in multiple legal entities. This article provides examples that show how posting for centralized payments is handled in various scenarios.
author: abruer
ms.date: 02/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 7bd02e32-2416-4ac6-8a60-85525267fdb7
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Centralized payments for Accounts payable

[!include [banner](../includes/banner.md)]

Organizations that include multiple legal entities can create and manage payments by using a single legal entity that handles all payments. Therefore, the same payments don't have to be entered in multiple legal entities. This article provides examples that show how posting for centralized payments is handled in various scenarios.

In a centralized payments organization, there are many legal entities for operations, and each operating legal entity manages its own vendor invoices. Payments for all the operating legal entities are generated from a single legal entity, which is known as the legal entity of the payment. During the settlement process, the applicable due-to and due-from transactions are generated. You can specify which legal entity in the organization receives the realized gain or realized loss transactions, and how cash discount transactions that are related to a cross-company payment are handled. On the centralized payment journal line, the **Account type** should be set to Vendor. The **Offset account typ**e should be set to Bank or Ledger. The bank account should be in the current company. 

The following examples illustrate how posting is handled in various scenarios. The following configuration is assumed for all these examples:

-   The legal entities are Fabrikam, Fabrikam East, and Fabrikam West. Payments are made from Fabrikam.
-   The **Post cash discount** field on the **Intercompany accounting** page is set to **Legal entity of the invoice**.
-   The **Post currency exchange gain or loss** field on the **Intercompany accounting** page is set to **Legal entity of the payment**.
-   The vendor Fourth Coffee is set up as a vendor in each legal entity. The vendors from the various legal entities are identified as the same vendor because they share the same global address book ID.

| Directory ID | Vendor account | Name          | Legal entity  |
|--------------|----------------|---------------|---------------|
| 1050         | 3004           | Fourth Coffee | Fabrikam      |
| 1050         | 100            | Fourth Coffee | Fabrikam East |
| 1050         | 3004           | Fourth Coffee | Fabrikam West |

## Example 1: Vendor payment of invoice from another legal entity
Fabrikam East has an open invoice for vendor account 100, Fourth Coffee. Fabrikam enters and posts a payment to Fabrikam vendor account 3004, Fourth Coffee. The payment is settled with the open invoice.

### Invoice is posted in Fabrikam East for vendor 100

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Expense (Fabrikam East)          | 600.00       |               |
| Accounts payable (Fabrikam East) |              | 600.00        |

### Payment is generated and posted in Fabrikam for vendor 3004

| Account                     | Debit amount | Credit amount |
|-----------------------------|--------------|---------------|
| Accounts payable (Fabrikam) | 600.00       |               |
| Cash (Fabrikam)             |              | 600.00        |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Due from Fabrikam East (Fabrikam) | 600.00       |               |
| Accounts payable (Fabrikam)       |              | 600.00        |

**Fabrikam East posting**

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam East) | 600.00       |               |
| Due to Fabrikam (Fabrikam East)  |              | 600.00        |

## Example 2: Vendor payment of invoice from another legal entity with cash discount
Fabrikam East has an open invoice for vendor 100, Fourth Coffee. The invoice has a 20.00 cash discount available. Fabrikam enters and posts a payment of 580.00 for Fabrikam vendor 3004, Fourth Coffee. The payment is settled with the open Fabrikam East invoices. The cash discount is posted to the legal entity of the invoice, Fabrikam East.

### Invoice is posted in Fabrikam East for Fabrikam East vendor 100

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Expense (Fabrikam East)          | 600.00       |               |
| Accounts payable (Fabrikam East) |              | 600.00        |

### Payment is generated and posted in Fabrikam for Fabrikam vendor 3004

| Account                     | Debit amount | Credit amount |
|-----------------------------|--------------|---------------|
| Accounts payable (Fabrikam) | 580.00       |               |
| Cash (Fabrikam)             |              | 580.00        |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Due from Fabrikam East (Fabrikam) | 580.00       |               |
| Accounts payable (Fabrikam)       |              | 580.00        |

**Fabrikam East posting**

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam East) | 580.00       |               |
| Due to Fabrikam (Fabrikam East)  |              | 580.00        |
| Accounts payable (Fabrikam East) | 20.00        |               |
| Cash discount (Fabrikam East)    |              | 20.00         |

## Example 3: Vendor payment of invoice from another legal entity with realized exchange rate loss
Fabrikam East has an open invoice for vendor 100, Fourth Coffee. Fabrikam enters and posts a payment for Fabrikam vendor 3004, Fourth Coffee. The payment is settled with the open Fabrikam East invoice. A currency exchange loss transaction is generated during the settlement process.

-   Exchange rate for euros (EUR) to U.S. dollars (USD) as of the invoice date: 1.2062
-   Exchange rate for EUR to USD as of the payment date: 1.2277

### Invoice is posted in Fabrikam East for Fabrikam East vendor 100

| Account                          | Debit amount            | Credit amount           |
|----------------------------------|-------------------------|-------------------------|
| Expense (Fabrikam East)          | 600.00 EUR / 723.72 USD |                         |
| Accounts payable (Fabrikam East) |                         | 600.00 EUR / 723.72 USD |

### Payment is generated and posted in Fabrikam for Fabrikam vendor 3004

| Account                     | Debit amount            | Credit amount           |
|-----------------------------|-------------------------|-------------------------|
| Accounts payable (Fabrikam) | 600.00 EUR / 736.62 USD |                         |
| Cash (Fabrikam)             |                         | 600.00 EUR / 736.62 USD |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                           | Debit amount            | Credit amount           |
|-----------------------------------|-------------------------|-------------------------|
| Due from Fabrikam East (Fabrikam) | 600.00 EUR / 736.62 USD |                         |
| Accounts payable (Fabrikam)       |                         | 600.00 EUR / 736.62 USD |
| Realized loss (Fabrikam)          | 0.00 EUR / 12.90 USD    |                         |
| Due from Fabrikam East (Fabrikam) |                         | 0.00 EUR / 12.90 USD    |

**Fabrikam East posting**

| Account                          | Debit amount            | Credit amount           |
|----------------------------------|-------------------------|-------------------------|
| Accounts payable (Fabrikam East) | 600.00 EUR / 736.62 USD |                         |
| Due to Fabrikam (Fabrikam East)  |                         | 600.00 EUR / 736.62 USD |
| Due to Fabrikam (Fabrikam East)  | 0.00 EUR / 12.90 USD    |                         |
| Accounts payable (Fabrikam East) |                         | 0.00 EUR / 12.90 USD    |

## Example 4: Vendor payment of invoice from another legal entity with cash discount and realized exchange rate loss
Fabrikam East has an open invoice for vendor 100, Fourth Coffee. The invoice has a cash discount available, and a sales tax transaction is generated. Fabrikam posts a payment for Fabrikam vendor 3004, Fourth Coffee. The payment is settled with the open Fabrikam East invoice. A currency exchange loss transaction is generated during the settlement process. The cash discount is posted to the legal entity of the invoice (Fabrikam East), and the currency exchange loss is posted to the legal entity of the payment (Fabrikam).

-   Exchange rate for EUR to USD as of the invoice date: 1.2062
-   Exchange rate for EUR to USD as of the payment date: 1.2277

### Invoice is posted and a tax transaction is generated in Fabrikam East for vendor 100

| Account                          | Debit amount            | Credit amount           |
|----------------------------------|-------------------------|-------------------------|
| Expense (Fabrikam East)          | 564.07 EUR / 680.38 USD |                         |
| Sales tax (Fabrikam East)        | 35.93 EUR / 43.34 USD   |                         |
| Accounts payable (Fabrikam East) |                         | 600.00 EUR / 723.72 USD |

### Payment is generated and posted in Fabrikam for vendor 3004

| Account                     | Debit amount            | Credit amount           |
|-----------------------------|-------------------------|-------------------------|
| Accounts payable (Fabrikam) | 588.72 EUR / 722.77 USD |                         |
| Cash (Fabrikam East)        |                         | 588.72 EUR / 722.77 USD |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                           | Debit amount            | Credit amount           |
|-----------------------------------|-------------------------|-------------------------|
| Due from Fabrikam East (Fabrikam) | 588.72 EUR / 722.77 USD |                         |
| Accounts payable (Fabrikam)       |                         | 588.72 EUR / 722.77 USD |
| Realized loss (Fabrikam)          | 0.00 EUR / 12.66 USD    |                         |
| Due from Fabrikam East (Fabrikam) |                         | 0.00 EUR / 12.66 USD    |

**Fabrikam East posting**

| Account                          | Debit amount            | Credit amount           |
|----------------------------------|-------------------------|-------------------------|
| Accounts payable (Fabrikam East) | 588.72 EUR / 722.77 USD |                         |
| Due to Fabrikam (Fabrikam East)  |                         | 588.72 EUR / 722.77 USD |
| Due to Fabrikam (Fabrikam East   | 0.00 EUR / 12.66 USD    |                         |
| Accounts payable (Fabrikam East) |                         | 0.00 EUR / 12.66 USD    |
| Accounts payable (Fabrikam East) | 11.28 EUR / 13.61 USD   |                         |
| Cash discount (Fabrikam East)    |                         | 11.28 EUR / 13.61 USD   |

## Example 5: Vendor credit note with primary payment
Fabrikam generates a payment of 75.00 for vendor 3004, Fourth Coffee. The payment is settled with an open invoice for Fabrikam West vendor 3004 and an open credit note for Fabrikam East vendor 100. The payment is selected as the primary payment on the **Settle transactions** page.

### Invoice is posted to Fabrikam West for vendor 3004

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Expense (Fabrikam West)          | 100.00       |               |
| Accounts payable (Fabrikam West) |              | 100.00        |

### Credit note is posted to Fabrikam East for vendor 100

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam East) | 25.00        |               |
| Purchase returns (Fabrikam East) |              | 25.00         |

### Payment is posted to Fabrikam for vendor 3004

| Account                     | Debit amount | Credit amount |
|-----------------------------|--------------|---------------|
| Accounts payable (Fabrikam) | 75.00        |               |
| Cash (Fabrikam)             |              | 75.00         |

### Fabrikam payment is settled with Fabrikam West invoice and Fabrikam East credit note

**Fabrikam posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam)       | 25.00        |               |
| Due to Fabrikam East (Fabrikam)   |              | 25.00         |
| Due from Fabrikam West (Fabrikam) | 100.00       |               |
| Accounts payable (Fabrikam)       |              | 100.00        |

**Fabrikam East posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Due from Fabrikam (Fabrikam East) | 25.00        |               |
| Accounts payable (Fabrikam East)  |              | 25.00         |

**Fabrikam West posting**

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam West) | 100.00       |               |
| Due to Fabrikam (Fabrikam West)  |              | 100.00        |

## Example 6: Vendor credit note without primary payment
Fabrikam generates a payment of 75.00 for vendor 3004, Fourth Coffee. The payment is settled with an open invoice for Fabrikam West vendor 3004 and an open credit note for Fabrikam East vendor 100. The payment isn't selected as the primary payment on the **Settle transactions** page.

### Invoice is posted to Fabrikam West for vendor 3004

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Expense (Fabrikam West)          | 100.00       |               |
| Accounts payable (Fabrikam West) |              | 100.00        |

### Credit note is posted to Fabrikam East for vendor 100

| Account                          | Debit amount | Credit amount |
|----------------------------------|--------------|---------------|
| Accounts payable (Fabrikam East) | 25.00        |               |
| Purchase returns (Fabrikam East) |              | 25.00         |

### Payment is posted to Fabrikam for vendor 3004

| Account                     | Debit amount | Credit amount |
|-----------------------------|--------------|---------------|
| Accounts payable (Fabrikam) | 75.00        |               |
| Cash (Fabrikam)             |              | 75.00         |

### Fabrikam payment is settled with Fabrikam West invoice and Fabrikam East credit note

**Fabrikam posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Due from Fabrikam West (Fabrikam) | 75.00        |               |
| Accounts payable (Fabrikam)       |              | 75.00         |

**Fabrikam East posting**

| Account                                | Debit amount | Credit amount |
|----------------------------------------|--------------|---------------|
| Due from Fabrikam West (Fabrikam East) | 25.00        |               |
| Accounts payable (Fabrikam East)       |              | 25.00         |

**Fabrikam West posting**

| Account                              | Debit amount | Credit amount |
|--------------------------------------|--------------|---------------|
| Accounts payable (Fabrikam West)     | 75.00        |               |
| Due to Fabrikam (Fabrikam West)      |              | 75.00         |
| Accounts payable (Fabrikam West)     | 25.00        |               |
| Due to Fabrikam East (Fabrikam West) |              | 25.00         |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
