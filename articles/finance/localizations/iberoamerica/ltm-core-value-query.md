---
title: Value query for Latin America
description: Learn about the Value query for Latin America, including prerequisites and outlines on review values and optional query filters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Value query for Latin America

From the **Value query** page, you can review the state of any value type document class that's posted in a transaction.

## Prerequisites

Create a value type document class, and use it in a transaction with an action.

## Review values

1. Go to **Accounts payable** \> **Inquiries and reports** \> **LATAM** \> **Value query**.
2. In the **Media type** and **Document class** fields, enter a value.
3. On the Action Pane, select **Apply filter** to show the documents in the query results.

## Optional query filters

You can use more fields to narrow down the documents in the query results.

| Field                | Description                                                                |
|----------------------|----------------------------------------------------------------------------|
| Status               | Select **Open**, **History**, or **Both**.                                 |
| Currency             | Select the currency of the value.                                          |
| Cut date             | Select a date limit to filter the values.                                  |
| Document number from | Enter the lower limit of a range of numbers to filter the document number. |
| Document number to   | Enter the upper limit of a range of numbers to filter the document number. |
| From date            | Select a date to filter the start of the document date.                    |
| To date              | Select a date to filter the end of the document date.                      |
| From due date        | Select a date to filter the starting due date of the document.             |
| To due date          | Select a date to filter the final due date of the document.                |

After you select the required values in the fields, select **Apply** to filter and show the transactions.
