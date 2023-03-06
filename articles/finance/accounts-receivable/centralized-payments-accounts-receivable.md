---
# required metadata

title: Centralized payments for Accounts receivable
description: Organizations that include multiple legal entities can create and manage payments by using a single legal entity that handles all payments. Therefore, the same transaction doesn't have to be entered in multiple legal entities. This article provides examples that show how posting for centralized payments is handled in various scenarios.
author: ShivamPandey-msft
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransCustPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Centralized payments for Accounts receivable

[!include [banner](../includes/banner.md)]

Organizations that include multiple legal entities can create and manage payments by using a single legal entity that handles all payments. Therefore, the same transaction doesn't have to be entered in multiple legal entities. This article provides examples that show how posting for centralized payments is handled in various scenarios. Additionally, the organization saves time, because the processes for payment proposals, settlements, and editing open and closed transactions for centralized payments are streamlined. 

In a centralized payment organization, there are many legal entities for operations, and each operating legal entity manages its own invoices receivable information. Payments for all the operating legal entities are received by a single legal entity, which is known as the legal entity of the payment. During the settlement process, the applicable due-to and due-from transactions are generated. You can specify which legal entity in the organization receives the realized gain or realized loss transactions, and how cash discount transactions that are related to a centralized payment are handled. On the centralized payment journal line, the **Account type** should be set to Customer. The **Offset account type** should be set to Bank or Ledger. The bank account should be in the current company. 

The following examples illustrate how posting is handled in various scenarios. The following configuration is assumed for all these examples:

-   The legal entities are Fabrikam, Fabrikam East, and Fabrikam West. Customer payments are entered into Fabrikam.
-   The **Post cash discount** field on the **Intercompany accounting** page is set to **Legal entity of the invoice**.
-   The **Post currency exchange gain or loss** field on the **Intercompany accounting** page is set to **Legal entity of the payment**.
-   Customer Northwind Traders is set up as a customer in each legal entity. The customers from the various legal entities are identified as the same customer because they share the same global address book ID.

| Address book ID | Customer account | Name              | Legal entity  |
|-----------------|------------------|-------------------|---------------|
| 4050            | 4000             | Northwind Traders | Fabrikam      |
| 4050            | 4000             | Northwind Traders | Fabrikam East |
| 4050            | 10000            | Northwind Traders | Fabrikam West |

## Example 1: Customer payment of invoice from another legal entity
Fabrikam receives a payment of 600.00 for Fabrikam customer account 4000, Northwind Traders. The payment is settled with an open invoice for customer account 4000 in Fabrikam East.

### Invoice is posted in Fabrikam East for customer 4000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam East) | 600.00       |               |
| Sales (Fabrikam East)               |              | 600.00        |

### Payment is received and posted in Fabrikam for customer 4000

| Account                        | Debit amount | Credit amount |
|--------------------------------|--------------|---------------|
| Cash (Fabrikam)                | 600.00       |               |
| Accounts receivable (Fabrikam) |              | 600.00        |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                         | Debit amount | Credit amount |
|---------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam)  | 600.00       |               |
| Due to Fabrikam East (Fabrikam) |              | 600.00        |

**Fabrikam East posting**

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Due from Fabrikam (Fabrikam East)   | 600.00       |               |
| Accounts receivable (Fabrikam East) |              | 600.00        |

## Example 2: Customer payment of invoice from another legal entity with cash discount
Fabrikam receives a payment of 580.00 for Fabrikam customer 4000, Northwind Traders. Fabrikam East has an open invoice for customer 4000. The invoice has a 20.00 cash discount available. The payment is settled with the open Fabrikam East invoices. The cash discount is posted to the legal entity of the invoice, Fabrikam East.

### Invoice is posted in Fabrikam East for Fabrikam East customer 4000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam East) | 580.00       |               |
| Sales (Fabrikam East)               |              | 580.00        |

### Payment is received and posted in Fabrikam for Fabrikam customer 4000

| Account                        | Debit amount | Credit amount |
|--------------------------------|--------------|---------------|
| Cash (Fabrikam)                | 600.00       |               |
| Accounts receivable (Fabrikam) |              | 600.00        |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                         | Debit amount | Credit amount |
|---------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam)  | 580.00       |               |
| Due to Fabrikam East (Fabrikam) |              | 580.00        |

**Fabrikam East posting**

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Due from Fabrikam (Fabrikam East)   | 580.00       |               |
| Accounts receivable (Fabrikam East) |              | 580.00        |
| Cash discount (Fabrikam East)       | 20.00        |               |
| Accounts receivable (Fabrikam East) |              | 20.00         |

## Example 3: Customer payment of invoice from another legal entity with realized exchange rate gain
Fabrikam receives a payment of 600.00 euros (EUR) for Fabrikam customer 4000, Northwind Traders. The payment is settled with an open invoice for customer 4000 in Fabrikam East. A currency exchange gain transaction is generated during the settlement process.

-   Exchange rate for EUR to U.S. dollars (USD) as of the invoice date: 1.2062
-   Exchange rate for EUR to USD as of the payment date: 1.2277

### Invoice is posted in Fabrikam East for Fabrikam East customer 4000

| Account                             | Debit amount            | Credit amount           |
|-------------------------------------|-------------------------|-------------------------|
| Accounts receivable (Fabrikam East) | 600.00 EUR / 723.72 USD |                         |
| Sales (Fabrikam East)               |                         | 600.00 EUR / 723.72 USD |

### Payment is received and posted in Fabrikam for Fabrikam customer 4000

| Account                        | Debit amount            | Credit amount           |
|--------------------------------|-------------------------|-------------------------|
| Cash (Fabrikam)                | 600.00 EUR / 736.62 USD |                         |
| Accounts receivable (Fabrikam) |                         | 600.00 EUR / 736.62 USD |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                         | Debit amount            | Credit amount           |
|---------------------------------|-------------------------|-------------------------|
| Accounts receivable (Fabrikam)  | 600.00 EUR / 736.62 USD |                         |
| Due to Fabrikam East (Fabrikam) |                         | 600.00 EUR / 736.62 USD |
| Due to Fabrikam East (Fabrikam) | 0.00 EUR / 12.90 USD    |                         |
| Realized gain (Fabrikam)        |                         | 0.00 EUR / 12.90 USD    |

**Fabrikam East posting**

| Account                             | Debit amount            | Credit amount           |
|-------------------------------------|-------------------------|-------------------------|
| Due from Fabrikam (Fabrikam East)   | 600.00 EUR / 736.62 USD |                         |
| Accounts receivable (Fabrikam East) |                         | 600.00 EUR / 736.62 USD |
| Accounts receivable (Fabrikam East) | 0.00 EUR / 12.90 USD    |                         |
| Due from Fabrikam (Fabrikam East)   |                         | 0.00 EUR / 12.90 USD    |

## Example 4: Customer payment of invoice from another legal entity with cash discount and realized exchange rate gain
Fabrikam posts a payment for Fabrikam customer 4000, Northwind Traders, for an open invoice in Fabrikam East. The invoice has a cash discount available, and a sales tax transaction is generated. The payment is settled with the open Fabrikam East invoice. A currency exchange gain transaction is generated during the settlement process. The cash discount is posted to the legal entity of the invoice (Fabrikam East), and the currency exchange gain is posted to the legal entity of the payment (Fabrikam).

-   Exchange rate for EUR to USD as of the invoice date: 1.2062
-   Exchange rate for EUR to USD as of the payment date: 1.2277

### Free text invoice is posted and a tax transaction is generated in Fabrikam East for customer 4000

| Account                             | Debit amount            | Credit amount           |
|-------------------------------------|-------------------------|-------------------------|
| Accounts receivable (Fabrikam East) | 638.22 EUR / 769.82 USD |                         |
| Sales (Fabrikam East)               |                         | 600.00 EUR / 723.72 USD |
| Sales tax (Fabrikam East)           |                         | 38.22 EUR / 46.10 USD   |

### Payment is received and posted in Fabrikam for customer 4000

| Account                        | Debit amount            | Credit amount           |
|--------------------------------|-------------------------|-------------------------|
| Cash (Fabrikam)                | 626.22 EUR / 768.81 USD |                         |
| Accounts receivable (Fabrikam) |                         | 626.22 EUR / 768.81 USD |

### Fabrikam payment is settled with Fabrikam East invoice

**Fabrikam posting**

| Account                         | Debit amount            | Credit amount           |
|---------------------------------|-------------------------|-------------------------|
| Accounts receivable (Fabrikam)  | 626.22 EUR / 768.81 USD |                         |
| Due to Fabrikam East (Fabrikam) |                         | 626.22 EUR / 768.81 USD |
| Due to Fabrikam East (Fabrikam) | 0.00 EUR / 13.46 USD    |                         |
| Realized gain (Fabrikam)        |                         | 0.00 EUR / 13.46 USD    |

**Fabrikam East posting**

| Account                             | Debit amount            | Credit amount           |
|-------------------------------------|-------------------------|-------------------------|
| Due from Fabrikam (Fabrikam East)   | 626.22 EUR / 768.81 USD |                         |
| Accounts receivable (Fabrikam East) |                         | 626.22 EUR / 768.81 USD |
| Accounts receivable (Fabrikam East  | 0.00 EUR / 13.46 USD    |                         |
| Due from Fabrikam (Fabrikam East)   |                         | 0.00 EUR / 13.46 USD    |
| Cash discount (Fabrikam East)       | 12.00 EUR / 14.47 USD   |                         |
| Accounts receivable (Fabrikam East) |                         | 12.00 EUR / 14.47 USD   |

## Example 5: Customer credit note with primary payment
Fabrikam receives a payment of 75.00 from customer 4000, Northwind Traders. The payment is settled with an open invoice for Fabrikam West customer 10000 and an open credit note for Fabrikam East customer 4000. The payment is selected as the primary payment on the **Settle transactions** page.

### Invoice is posted to Fabrikam West for customer 10000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam West) | 100.00       |               |
| Sales (Fabrikam West)               |              | 100.00        |

### Credit note is posted to Fabrikam East for customer 4000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Sales returns (Fabrikam East)       | 25.00        |               |
| Accounts receivable (Fabrikam East) |              | 25.00         |

### Payment is posted to Fabrikam for customer 4000

| Account                        | Debit amount | Credit amount |
|--------------------------------|--------------|---------------|
| Cash (Fabrikam)                | 75.00        |               |
| Accounts receivable (Fabrikam) |              | 75.00         |

### Fabrikam payment is settled with Fabrikam West invoice and Fabrikam East credit note

**Fabrikam posting**

| Account                           | Debit amount | Credit amount |
|-----------------------------------|--------------|---------------|
| Due from Fabrikam East (Fabrikam) | 25.00        |               |
| Accounts receivable (Fabrikam)    |              | 25.00         |
| Accounts receivable (Fabrikam)    | 100.00       |               |
| Due to Fabrikam West (Fabrikam)   |              | 100.00        |

**Fabrikam East posting**

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam East) | 25.00        |               |
| Due to Fabrikam (Fabrikam East)     |              | 25.00         |

**Fabrikam West posting**

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Due from Fabrikam (Fabrikam West)   | 100.00       |               |
| Accounts receivable (Fabrikam West) |              | 100.00        |

## Example 6: Customer credit note without primary payment
Fabrikam receives a payment of 75.00 from customer 4000, Northwind Traders. The payment is settled with an open invoice for Fabrikam West customer 10000 and an open credit note for Fabrikam East customer 4000. The payment isn't selected as the primary payment on the **Settle transactions** page.

### Invoice is posted to Fabrikam West for customer 10000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam West) | 100.00       |               |
| Sales (Fabrikam West)               |              | 100.00        |

### Credit note is posted to Fabrikam East for customer 4000

| Account                             | Debit amount | Credit amount |
|-------------------------------------|--------------|---------------|
| Sales returns (Fabrikam East)       | 25.00        |               |
| Accounts receivable (Fabrikam East) |              | 25.00         |

### Payment is posted to Fabrikam for customer 4000

| Account                        | Debit amount | Credit amount |
|--------------------------------|--------------|---------------|
| Cash (Fabrikam)                | 75.00        |               |
| Accounts receivable (Fabrikam) |              | 75.00         |

### Fabrikam payment is settled with Fabrikam West invoice and Fabrikam East credit note

**Fabrikam posting**

| Account                         | Debit amount | Credit amount |
|---------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam)  | 75.00        |               |
| Due to Fabrikam West (Fabrikam) |              | 75.00         |

**Fabrikam East posting**

| Account                              | Debit amount | Credit amount |
|--------------------------------------|--------------|---------------|
| Accounts receivable (Fabrikam East)  | 25.00        |               |
| Due to Fabrikam West (Fabrikam East) |              | 25.00         |

**Fabrikam West posting**

| Account                                | Debit amount | Credit amount |
|----------------------------------------|--------------|---------------|
| Due from Fabrikam (Fabrikam West)      | 75.00        |               |
| Accounts receivable (Fabrikam West)    |              | 75.00         |
| Due from Fabrikam East (Fabrikam West) | 25.00        |               |
| Accounts receivable (Fabrikam West)    |              | 25.00         |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
