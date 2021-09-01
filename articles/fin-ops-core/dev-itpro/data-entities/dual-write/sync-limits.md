---
title: Dual-write limits for live synchronization
description: This topic describes the limits when using dual-write to write data to Dataverse and Finance and Operations apps.
author: nhelgren
ms.date: 08/31/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2021-08-31
ms.dyn365.ops.version: AX 7.0.0
---

# Dual-write limits for live synchronization

To ensure consistent availability and performance, there are limits when using dual-write to write data to Dataverse and Finance and Operations apps. These limits are applied at the platform level and control dual-write transactions. These limits are designed to ensure seamless writes and to minimize failures.

Finance and Operations apps and Dataverse have many processes which span large numbers records and complex, multi-table transactions. Each environment has limits around the number of transactions, the numbers of records per single transaction, and the transaction time limits (the time it takes to process the transaction). It is important to understand these limits and their impact on the live sync capabilities with dual-write.

## Transaction patterns

A process can write data in two different transaction patterns:

- [Single transaction](#single-transaction): All data written as part of the process is part of single transaction.

- [Multiple transactions](#multiple-transactions): All the data written as part of the process is split into multiple transactions.

## Single transaction

In a single transaction, all data written as part of the process is part of single transaction. When there is a failure, the entire transaction is rolled back.

A common example is a process creating multiple invoices in a single transaction. In this case, either all invoices are committed in one transaction or if there is an error, all invoices are rolled back. The following code examples create multiple invoices in a single transaction.

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

## Multiple transactions

In multiple transactions: All the data written as part of this process is split into multiple transactions. When there is a failure, the entire group of multiple transactions is not rolled back. Each transaction is rolled back or committed independently. A transaction with a failure is rolled back. A transaction without a failure is committed.

A common example is a process creating multiple invoices. Each invoice is created in a separate transaction and if there is an error, only the invoice included in a specific transaction would roll back. The rest of the invoices would be committed successfully. The following code examples create multiple invoices, one per transaction.

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

When writing records using dual-write to Dataverse or Finance and Operations apps, each transaction needs to complete within a specific amount of time. If the transaction does not complete before the transaction timeout limit, then the records are not committed to Dataverse and Finance and Operations apps using dual-write. This results in a roll back of records within the timed out transaction in both the Finance and Operations and Dataverse environments.

For example, using dual-write to sync contract renewals from Finance and Operations apps to Dataverse, the clock starts when the business logic in Finance and Operations apps is completed and at the start of the Dataverse process. The clock ends the transaction is committed. The entire time spent in Dataverse includes the time to write as well as time for the standard and custom plugins to be processed. If the transaction exceeds the time limit, then the records would not be committed to Dataverse.

The same is true when you write data using dual-write in the other direction, from Dataverse to Finance and Operations apps.

## Dual-write live sync limits

The following tables describe the dual-write live sync limits while writing data between Dataverse and Finance and Operations apps. These limits are specific to the direction of flow of data; from Finance and Operations apps to Dataverse and from Dataverse to Finance and Operations apps.

## Finance and Operations apps To Dataverse time limits

The following limits apply:

Measure | Limits
---|---
Number of transactions | The total number of transactions you can make per day per tenant are governed by service protection API limits which are designed to detect when client applications make extraordinary demands on server resources.<br>For more information, see [Service protection API limits](/powerapps/developer/data-platform/api-limits.md)
Number of records per single transaction | 1000 records<br>For greater than 1000 records in a single transaction, consider splitting into multiple transactions. For more information, see the section [Transactions with more than 1000 records](#transactions-with-more-than-1000-records).
Transaction time limit | 2 minutes

## Dataverse to Finance and Operations limits

The following limits apply:

Measure | Limits
---|---
Number of transactions | The number of transactions may be impacted by priority-based throttling limits that are designed to prevent over-utilization of resources and preserve the systems responsiveness.<br>For more information, see [Priority-based throttling](../data-entities/priority-based-throttling.md).
Number of records per single transaction* | There is a payload size limit on Dataverse which limits how many records can be transferred over. The limit is 116.85 MB per transaction. For more information, see [Error: Message size exceeded when sending context to Sandbox](/powerapps/developer/data-platform/troubleshoot-plug-in#error-message-size-exceeded-when-sending-context-to-sandbox). The usage depends on the multiple factors like entity complexity, type of columns used, and mapped fields. Therefore, the limit cannot be expressed as a simple number of records.<br>Dataverse will reject the transaction (referred to as message) with the following error code:<br>*Error Code: -2147220970 Error Message: Message size exceeded when sending context to Sandbox. Message size: ### MB*<br>If there are more than 116.65 MB records in a single transaction, consider splitting into multiple transactions. For more information, see the section [Transactions with more than 1000 records](#transactions-with-more-than-1000-records).
Transaction timeout | 2 minutes

## Transactions with more than 1000 records

It is common to have scenarios with transactions of more than 1000 records. In these cases, we recommend splitting it into multiple transactions. The following examples demonstrate how to make multiple transactions based on record IDs.

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

