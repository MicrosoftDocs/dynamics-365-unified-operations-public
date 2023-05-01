---
title: Dual-write limits for live synchronization
description: This article describes the limits when dual-write is used to write data to finance and operations apps and Microsoft Dataverse.
author: nhelgren
ms.date: 08/31/2021
ms.topic: article
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2021-08-31
ms.dyn365.ops.version: AX 7.0.0
---

# Dual-write limits for live synchronization

[!include [banner](../../includes/banner.md)]



For more consistent availability and performance, limits apply when dual-write is used to write data to finance and operations apps and Microsoft Dataverse. These limits control dual-write transactions and are applied at the platform level. They are designed to ensure seamless writes and to help minimize failures.

Finance and operations apps and Dataverse have many processes that span large numbers of records and complex, multi-table transactions. Each environment has limits on the number of transactions, the number of records per transaction, and transaction time (that is, the time that is required to process the transaction). It's important that you understand these limits and their effect on the live synchronization capabilities of dual-write.

## Legal Entities
Live synchronization supports up to 250 legal entities per transaction. This is different from initial synchronization which supports only 40 due to larger data volumes and related operations.

## Transaction patterns

A process can write data in two different transaction patterns:

- **[Single transaction](#single-transaction)** – All data that is written as part of the process is part of a single transaction.
- **[Multiple transactions](#multiple-transactions)** – All the data that is written as part of the process is split into multiple transactions.

### Single transaction

In a single transaction, all data that is written as part of the process is part of a single transaction. If a failure occurs, the whole transaction is rolled back.

A common example is a process that creates multiple invoices in a single transaction. In this case, either all invoices are committed in one transaction or, if an error occurs, all invoices are rolled back. The following code examples create multiple invoices in a single transaction.

```xpp
ttsbegin;// Transaction start
    Invoice1.create();
    Invoice2.create();
    Invoice3.create();
    // Additional invoices.
    InvoiceN.create();
ttscommit;// Transaction end
```

```xpp
ttsbegin;// Transaction start
    while (/* loop condition */)
    {
      InvoiceN.create();
    }
ttscommit;// Transaction end
```

### Multiple transactions

In multiple transactions, all the data that is written as part of the process is split into multiple transactions. If a failure occurs, the whole group of multiple transactions isn't rolled back. Instead, each transaction is independently rolled back or committed. Any transaction that has a failure is rolled back. Any transaction that has no failure is committed.

A common example is a process that creates multiple invoices. Each invoice is created in a separate transaction, and if an error occurs, only the invoice that is included in a specific transaction is rolled back. The remaining invoices are successfully committed. The following code examples create multiple invoices, one per transaction.

```xpp
ttsbegin; // Transaction start
    Invoice1.create();
ttscommit;// Transaction end

ttsbegin;// Transaction start
    Invoice2.create();
ttscommit;// Transaction end

ttsbegin;// Transaction start
    Invoice3.create();
ttscommit;// Transaction end

// Additional transactions.

ttsbegin;// Transaction start
    InvoiceN.create();
ttscommit;// Transaction end
```

```xpp
while (/* loop condition */)
{
    ttsbegin;// Transaction start
    InvoiceN.create();
    ttscommit;// Transaction end
}
```

## Transaction time limit

When dual-write is used to write records to finance and operations apps or Dataverse, each transaction must be completed within a specific amount of time. If a transaction isn't completed before the transaction time limit is reached, the records aren't committed to finance and operations apps and Dataverse by using dual-write. In this case, the records in the transaction are rolled back in both the finance and operations environment and the Dataverse environment.

For example, when dual-write is used to sync contract renewals from finance and operations apps to Dataverse, the timer begins when the business logic in finance and operations apps is completed and the Dataverse process is started. The timer ends when the transaction is committed. The whole time that is spent in Dataverse includes the time that is required to write, and also the time that is required to process the standard and custom plugins. If the transaction exceeds the time limit, the records aren't committed to Dataverse.

The same principle applies when dual-write is used to write data in the other direction, from Dataverse to finance and operations apps.

## Dual-write live synchronization limits

The following tables describe the dual-write live synchronization limits that apply when data is written between finance and operations apps and Dataverse. These limits are specific to the direction of the data flow: from finance and operations apps to Dataverse, or from Dataverse to finance and operations apps.

### From finance and operations apps to Dataverse

The following limits apply when data is written from finance and operations apps to Dataverse.

| Measure | Limits |
|---|---|
| Number of transactions | The total number of transactions that you can perform per day per tenant is governed by service protection API limits that are designed to detect when client applications make extraordinary demands on server resources. For more information, see [Service protection API limits](/powerapps/developer/data-platform/api-limits). |
| Number of records per single transaction | <p>1,000 records</p><p>If there are more than 1,000 records in a single transaction, consider splitting that transaction into multiple transactions. For more information, see the [Transactions with more than 1,000 records](#transactions-with-more-than-1000-records) section of this article.</p> |
| Transaction time limit | 2 minutes |

### From Dataverse to finance and operations apps

The following limits apply when data is written from Dataverse to finance and operations apps.

| Measure | Limits |
|---|---|
| Number of transactions | The number of transactions might be affected by priority-based throttling limits that are designed to help prevent over-utilization of resources and preserve system responsiveness. For more information, see [Priority-based throttling](../priority-based-throttling.md). |
| Number of records per single transaction | <p>A payload size limit on Dataverse limits the number of records that can be transferred. The limit is 116.85 megabytes (MB) per transaction. For more information, see [Error: Message size exceeded when sending context to Sandbox](/powerapps/developer/data-platform/troubleshoot-plug-in#error-message-size-exceeded-when-sending-context-to-sandbox). Use of this limit depends on the multiple factors, such entity complexity, the type of columns that is used, and mapped fields. Therefore, the limit can't be expressed as a simple number of records.</p><p>If the limit is exceeded, Dataverse rejects the transaction (referred to as a *message*), and the following error code is used:</p><p>*Error Code: -2147220970 Error Message: Message size exceeded when sending context to Sandbox. Message size: ### MB*</p><p>If the size of the records in a single transaction exceeds 116.65 MB, consider splitting the transaction into multiple transactions. For more information, see the [Transactions with more than 1,000 records](#transactions-with-more-than-1000-records) section of this article.</p> |
| Transaction timeout | 2 minutes |

## Transactions with more than 1,000 records

Scenarios where transactions have more than 1,000 records are common. In these scenarios, we recommend that you split single transactions into multiple transactions. The following code examples show how to make multiple transactions, based on record IDs.

```xpp
ttsbegin;// Transaction start.
    Invoice1.create();
    Invoice2.create();
    // Additional invoices.
    Invoice1000.create();
ttscommit;// Transaction end.

ttsbegin;// Transaction start.
    Invoice1001.create();
    Invoice1002.create();
    // Additional invoices.
    Invoice2000.create();
ttscommit;// Transaction end.

ttsbegin;// Transaction start.
    Invoice2001.create();
    Invoice2002.create();
    // Additional invoices.
    Invoice3000.create();
ttscommit;// Transaction end.

// Additional transactions.

ttsbegin;// Transaction start.
    Invoice(N)1.create();
    Invoice(N)2.create();
    // Additional invoices.
    Invoice(N+1)000.create();
ttscommit;// Transaction end.
```

```xpp
i = 1;
committPending = false;
while (/* loop condition */)
{
    if (i==1) 
    {
        ttsbegin;// Transaction start.
        committPending = true;
    }
    InvoiceN.create();
    if (i == 1000)
    {
        ttscommit;// Transaction end.
        committPending = false;
        i = 0;
    }

    i++;
}

if (committPending == true)
{
    ttscommit; // Transaction end.
}
```

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

