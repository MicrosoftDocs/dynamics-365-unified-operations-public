---
# required metadata

title: Single voucher with multiple customer or vendor records
description: This topic provides an overview of what happens when you post a single voucher with multiple customer or vendor records. This functionality will be discontinued in future versions of Microsoft Dynamics 365 for Operations, as a result, we do not recommend using this method of posting because of the accounting impact to settlement processing. 
author: twheeloc
manager: AnnBe
ms.date: 2016-10-31 18 - 43 - 45
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 222534
ms.assetid: d4df11ce-4d36-4c66-8230-f5fc58e021bc
ms.search.region: global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Single voucher with multiple customer or vendor records

This topic provides an overview of what happens when you post a single voucher with multiple customer or vendor records. This functionality will be discontinued in future versions of Microsoft Dynamics 365 for Operations, as a result, we do not recommend using this method of posting because of the accounting impact to settlement processing. 

Some common examples where one voucher is used for multiple customers or vendors include balance transfers between customers, and netting balances between customers and vendors in the same organization. 

A voucher containing more than one customer or vendor can be entered using one of the following methods:

-   Using a journal that has the **One voucher number only** option selected so that every line added to the journal is included on the same voucher.
-   Using a multi-line voucher, where there is no offset ledger account, with more than one customer or vendor.
-   Entering a voucher with the account and offset account being vendor/vendor, customer/customer, vendor/customer, or customer/vendor.

This topic shows how settlement will be processed when one voucher  with multiple customer or vendor records is posted. Additionally, this topic provides workarounds to help you understand how to avoid using one voucher with multiple customers or vendors. In particular, there are examples which illustrate two common settlement scenarios that are impacted by the use of one voucher with multiple customers or vendors:

-   Cash discount accounting
-   Revaluation accounting

## How does settlement impact single voucher usage
When posting a voucher that contains multiple customer or vendor records, a single accounting voucher is created that contains multiple accounts receivable or accounts payable balances. During the settlement process, the original accounting entries are used to create accounting entries for the cash discount, unrealized gains and losses, realized gains and losses, and the relief of the original document’s summary account. For example, if a cash discount is taken when settling a vendor payment to an invoice, the cash discount accounting must post to the Accounts payable ledger account from the original invoice. If the original invoice was posted in a voucher that contains multiple vendor records, the original accounting is summarized. In this case, because there is no way to access the detailed accounting entry for each vendor transaction in the single voucher, there is no way to determine how the user intended the cash discount to be accounted for.

### One voucher with multiple vendors and the impact on cash discount accounting

In the following example, multiple vendor invoices are recorded in General ledger on a single voucher in the **General journal** page. These invoices are distributed across multiple account dimensions.

|             |                  |              |                 |           |            |
|-------------|------------------|--------------|-----------------|-----------|------------|
| **Voucher** | **Account type** | **Account**  | **Description** | **Debit** | **Credit** |
| GNJL001     | Vendor           | 1001         | INV1            |           | 100.00     |
| GNJL001     | Vendor           | 1001         | INV2            |           | 200.00     |
| GNJL001     | Vendor           | 1001         | INV3            |           | 300.00     |
| GNJL001     | Ledger           | 606300-001-- | INV1            |   50.00   |            |
| GNJL001     | Ledger           | 606300-002-- | INV1            |   50.00   |            |
| GNJL001     | Ledger           | 606300-003-- | INV2            | 200.00    |            |
| GNJL001     | Ledger           | 606300-004-- | INV3            | 300.00    |            |

After posting, one voucher is created.

|             |              |                  |                                    |
|-------------|--------------|------------------|------------------------------------|
| **Voucher** | **Account**  | **Posting type** | **Amount in transaction currency** |
| GNJL001     | 606300-001-- | Ledger journal   | 50.00                              |
| GNJL001     | 606300-002-- | Ledger journal   | 50.00                              |
| GNJL001     | 606300-003-- | Ledger journal   | 200.00                             |
| GNJL001     | 606300-004-- | Ledger journal   | 300.00                             |
| GNJL001     | 200110-001-  | Vendor balance   | -100.00                            |
| GNJL001     | 200110-001-  | Vendor balance   | -200.00                            |
| GNJL001     | 200110-001-  | Vendor balance   | -300.00                            |

Notice that the voucher contains three entries for the posting type of Vendor balance in the single voucher. There is no way to indicate that the 50.00 debit for 606300-001 and the 50.00 debit for 606300-002 are intended to offset the vendor balance entry of 200110-001. This is because the user entered the multiple vendor records in a single voucher.

Using this example, we can analyze the impact that using one voucher has on the downstream settlement accounting. Assume that you pay 197.00 of the 200.00 invoice, taking a cash discount of 3.00. Notice that the cash discount account value is allocated across all of the dimensions from the invoice voucher’s expense accounts. This is because one voucher was used to post the above invoice, with no indication of how the user intended the expense distributions to correlate to the vendor balance in the single voucher.

|             |              |                      |           |            |
|-------------|--------------|----------------------|-----------|------------|
| **Voucher** | **Account**  | **Posting type**     | **Debit** | **Credit** |
| APPAYM001   | 200110-001-  | Vendor balance       | 197.00    |            |
| APPAYM001   | 110110-001-  | Bank                 |           | 197.00     |
| 14000056    | 520200-001-- | Vendor cash discount |           | 0.25       |
| 14000056    | 520200-002-- | Vendor cash discount |           | 0.25       |
| 14000056    | 520200-003-- | Vendor cash discount |           | 1.00       |
| 14000056    | 520200-004-- | Vendor cash discount |           | 1.50       |
| 14000056    | 200110-001-  | Vendor balance       | 3.00      |            |

If the user is dissatisfied with the cash discount being allocated across all of the expense distributions from the original invoice, instead of one voucher, multiple vouchers should be used to record the invoices. Here’s an example of how multiple vouchers could be entered in General ledger, instead of using one voucher, as shown at the beginning of this example.

|             |                  |              |                 |           |            |                 |                    |
|-------------|------------------|--------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account**  | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| GNJL001     | Vendor           | 1001         | INV1            |           | 100.00     | Ledger          | &lt;blank&gt;      |
| GNJL001     | Ledger           | 606300-001-- | INV1            |   50.00   |            | Ledger          | &lt;blank&gt;      |
| GNJL001     | Ledger           | 606300-002-- | INV1            |   50.00   |            | Ledger          | &lt;blank&gt;      |
| GNJL002     | Vendor           | 1001         | INV2            |           | 200.00     | Ledger          | 606300-003--       |
| GNJL003     | Vendor           | 1001         | INV3            |           | 300.00     | Ledger          | 606300-004--       |

Now, when INV2 is paid, the following entry will be made. Notice that the cash discount’s financial dimensions follow the associated expense’s financial dimensions.

|             |              |                      |           |            |
|-------------|--------------|----------------------|-----------|------------|
| **Voucher** | **Account**  | **Posting type**     | **Debit** | **Credit** |
| APPAYM001   | 200110-001-  | Vendor balance       | 197.00    |            |
| APPAYM001   | 110110-001-  | Bank                 |           | 197.00     |
| 14000056    | 520200-003-- | Vendor cash discount |           | 3.00       |
| 14000056    | 200110-001-  | Vendor balance       | 3.00      |            |

### One voucher with multiple vendors and the impact on realized gain/loss accounting

|             |                  |             |                 |           |            |                  |              |
|-------------|------------------|-------------|-----------------|-----------|------------|------------------|--------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Account type** | **Account**  |
| GNJL001     | Vendor           | 1001        | INV1            |           | 100.00     | Ledger           | 606300-001-- |
| GNJL001     | Vendor           | 1001        | INV2            |           | 200.00     | Ledger           | 606300-002-- |

In the following example, multiple vendor invoices are recorded in General ledger on a single voucher in the **General journal** page. These invoices are distributed across multiple account dimensions. After posting, one voucher is created.

|             |              |                  |                                          |                                         |
|-------------|--------------|------------------|------------------------------------------|-----------------------------------------|
| **Voucher** | **Account**  | **Posting type** | **Amount in transaction currency (EUR)** | **Amount in accounting currency (USD)** |
| GNJL001     | 606300-001-- | Ledger journal   | 100.00                                   | 114.00                                  |
| GNJL001     | 606300-002-- | Ledger journal   | 200.00                                   | 228.00                                  |
| GNJL001     | 200110-001-  | Vendor balance   | -100.00                                  | -114.00                                 |
| GNJL001     | 200110-001-  | Vendor balance   | -200.00                                  | -228.00                                 |

Notice that the voucher contains two entries for the posting type of Vendor balance in the single voucher. There is no way to indicate that the debit for 606300-001 is intended to offset the vendor balance entry of 100.00 to 200110-001. This is because the user entered multiple vendor records in a single voucher. 

Using this example, we can analyze the impact that using one voucher has on the downstream settlement accounting. Assume that your accounting currency is USD and the above transactions were posted in a transaction currency of EUR. Assume that you fully pay the 200.00 EUR invoice but you encounter a realized loss due to a difference in the exchange rate between the time you posted your invoice and payment. Notice that the realized loss account value is allocated across all of the dimensions from the invoice voucher’s expense accounts. In this case, both dimension 001 and 002 were allocated, even though the user’s perception may be that only 002 belongs to the expense account from the invoice that is being settled. This is because one voucher was used to post the above invoice, leaving no way to indicate how the user intended the expense distributions to correlate to the vendor balance in the single voucher.

|             |             |                    |                                          |                                         |
|-------------|-------------|--------------------|------------------------------------------|-----------------------------------------|
| **Voucher** | **Account** | **Posting type**   | **Amount in transaction currency (EUR)** | **Amount in accounting currency (USD)** |
| APPAYM001   | 200110-001- | Vendor balance     | 200.00                                   | 230.00                                  |
| APPAYM001   | 110110-001- | Bank               | -200.00                                  | -230.00                                 |
| 14000056    | 801300-001- | Exchange rate loss | 0.00                                     | 0.67                                    |
| 14000056    | 801300-002- | Exchange rate loss | 0.00                                     | 1.33                                    |
| 14000056    | 200110-001- | Vendor balance     |                                          | -2.00                                   |

If the user is dissatisfied with the Exchange rate loss being allocated across all of the expense distributions from the original invoice, instead of one voucher, multiple vouchers should be used to record the invoices. Here’s an example of how multiple vouchers could be entered in General ledger, instead of using one voucher as shown at the beginning of this example.

|             |                  |             |                 |           |            |                 |                    |
|-------------|------------------|-------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| GNJL002     | Vendor           | 1001        | INV1            |           | 100.00     | Ledger          | 606300-001--       |
| GNJL003     | Vendor           | 1001        | INV2            |           | 200.00     | Ledger          | 606300-002--       |

Now, when INV2 is paid, the following entry will be made. Notice that the exchange rate loss financial dimensions follow the associated expense’s financial dimensions.

|             |             |                    |                                          |                                         |
|-------------|-------------|--------------------|------------------------------------------|-----------------------------------------|
| **Voucher** | **Account** | **Posting type**   | **Amount in transaction currency (EUR)** | **Amount in accounting currency (USD)** |
| APPAYM001   | 200110-001- | Vendor balance     | 200.00                                   | 230.00                                  |
| APPAYM001   | 110110-001- | Bank               | -200.00                                  | -230.00                                 |
| 14000056    | 801300-002- | Exchange rate loss | 0.00                                     | 2.00                                    |
| 14000056    | 200110-001- | Vendor balance     |                                          | -2.00                                   |

## One voucher for balance transfers and netting scenarios
Two commonly used scenarios that utilize one voucher that contains multiple customers or vendors include balance transfers from one customer/vendor to another customer/vendor, and netting of a customer and vendor that are the same organization. The following two examples illustrate the preferred method for entering these scenarios in Dynamics 365 for Operations, as an alternative to entering them in one voucher. 

A *balance transfer* is one voucher with multiple customers, entered for the purpose of transferring the balance from one customer to another customer (same for vendors). This scenario can occur when the responsibility for paying the invoice shifts to another party, such as a child company shifting the responsibility to a parent company. 

This example assumes a sale where the customer is eligible for a cash discount if payment is made within 10 days. The customer in this example utilizes an insurance company that will be responsible for paying the bill. The insurance company is set up as a second customer in the system. The original customer’s balance is transferred to the insurance company, who pays the bill, taking a 2% cash discount for paying within the discount period. 

To illustrate, assume the following sale is made to customer ACME. The following accounting entries represent the sale.

|                    |                  |           |            |
|--------------------|------------------|-----------|------------|
| **Ledger account** | **Posting type** | **Debit** | **Credit** |
| 401100-002-023-    | Revenue          |           | 100        |
| 130100-002-        | Customer balance | 100       |            |

Next, the user transfers the balance due from ACME to the insurance company, in one voucher in the Accounts receivable payment journal. In Dynamics 365 for Operations, the insurance company is set up as customer Insurance.

|             |                  |             |                 |           |            |                 |                    |
|-------------|------------------|-------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| ARPAYM001   | Customer         | ACME        | Transfer        |           | 100.00     | Customer        | Insurance          |

Notice that the above entry is contained in one voucher. This voucher contains two customer records. The following voucher is created when the above General ledger entry is posted.

|             |             |                  |                                    |
|-------------|-------------|------------------|------------------------------------|
| **Voucher** | **Account** | **Posting type** | **Amount in transaction currency** |
| ARPAYM001   | 130100-002- | Customer balance | 100.00                             |
| ARPAYM001   | 130100-002- | Customer balance | -100.00                            |

Next, assume that you receive a payment from the Insurance customer for 98.00 and you choose to settle the payment with the invoice created by the balance transfer. This will result in the following voucher being posted. There may be an expectation that settlement uses the financial dimensions from the original invoice, but that is not possible because there isn’t an invoice document for the Insurance customer. Notice that by default, the distribution dimensions on the cash discount come from the customer transaction created from the transfer, not from the original invoice’s revenue account. The default is a result of using one voucher to transfer the balances.

|             |             |                  |           |            |
|-------------|-------------|------------------|-----------|------------|
| **Voucher** | **Account** | **Posting type** | **Debit** | **Credit** |
| ARPAYM002   | 110110-002- | Bank             | 98.00     |            |
| ARPAYM002   | 130100-002- | Customer balance |           | 98.00      |

On the related voucher for cash discount, the default for the financial dimension comes from the customer transaction created from the transfer, because the transfer has more than one customer.

|             |             |                        |           |            |
|-------------|-------------|------------------------|-----------|------------|
| **Voucher** | **Account** | **Posting type**       | **Debit** | **Credit** |
| ARP-00001   | 403300-002- | Customer cash discount | 2.00      |            |
| ARP-00001   | 130100-002- | Customer balance       |           | 2.00       |

If the user is dissatisfied with the default for the financial dimensions for the cash discount, instead of one voucher, multiple vouchers should be used to record the balance transfer. This scenario should be accomplished by creating a credit memo for the customer that the balance is moved FROM, and a debit memo or invoice created for the customer to whom the balance is moved TO. The following example shows how multiple vouchers could be entered in the accounts receivable payment journal to transfer the balance, instead of using one voucher, as shown earlier in this example.

|             |                  |             |                 |           |            |                 |                    |
|-------------|------------------|-------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| ARPAYM001   | Customer         | ACME        |                 |           | 100.00     | Ledger          | 401100-002-023-    |
| ARPAYM002   | Customer         | Insurance   |                 | 100.00    |            | Ledger          | 401100-002-023-    |

This means that when the Insurance customer pays 98.00 with voucher ARPAYM02, the correct financial dimensions from voucher ARPAYM002’s ledger account entry will be used.

|             |             |                  |           |            |
|-------------|-------------|------------------|-----------|------------|
| **Voucher** | **Account** | **Posting type** | **Debit** | **Credit** |
| ARPAYM003   | 110110-002- | Bank             | 98.00     |            |
| ARPAYM003   | 130100-002  | Customer balance |           | 98.00      |

On the related voucher for cash discount, the financial dimensions will be used from the offsetting revenue account shown on ARPAYM002’s voucher.

|             |                 |                        |           |            |
|-------------|-----------------|------------------------|-----------|------------|
| **Voucher** | **Account**     | **Posting type**       | **Debit** | **Credit** |
| ARP-00001   | 403300-002-023- | Customer cash discount | 2.00      |            |
| ARP-00001   | 130100-002-     | Customer balance       |           | 2.00       |

### 

## One voucher with a netting for multiple customers and vendors
Netting can be useful when an organization purchases and sells to the same company. Rather than paying the vendor invoices and waiting to receive payment for the customer invoices, the vendor and customer invoices are netted. The netting transaction is settled against the outstanding balances. 

To illustrate, assume that vendor 1001 and customer US-008 are the same entity, so your organization wants to net the payables and receivables balances before paying/receiving the remaining balance. Assume that the customer record owes 75.00 EUR and the vendor record is owed 100.00 EUR, meaning that you would prefer to net the balances and only pay the vendor 25.00 EUR. Further assume that the accounting currency is USD. In this case, a netting transaction is entered in one voucher in the account payable payment journal.

|             |                  |             |                 |           |            |                 |                    |
|-------------|------------------|-------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| APPAYM001   | Vendor           | 1001        | Netting         |  75.00    |            | Customer        | US-008             |

To avoid unwanted issues with future settlements for this transaction, instead of using one voucher, multiple vouchers should be entered in the journal to record the netting transaction. Notice that the customer and vendor balances are offset with a single clearing account to avoid the use of one voucher that contains multiple customer and vendor balances.

|             |                  |             |                 |           |            |                 |                    |
|-------------|------------------|-------------|-----------------|-----------|------------|-----------------|--------------------|
| **Voucher** | **Account type** | **Account** | **Description** | **Debit** | **Credit** | **Offset type** | **Offset account** |
| 001         | Customer         | US-008      |                 |           |  75.00     | Ledger          | 999999---          |
| 002         | Vendor           | 1001        |                 |  75.00    |            | Ledger          | 999999---          |

 

