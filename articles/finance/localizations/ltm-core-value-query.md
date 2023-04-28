---
title: Value query for Latin America
description: This topic provides information about the Value query for Latin America. 
author: Fhernandez0088
ms.date: 03/22/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Value query for Latin America
You can consult the state of any value type document class posted in a transaction from the **Value query** page.

## Prerequisites
Create a value type document class and use that document class in a transaction with an action.

## Consulting values
1. Go to **Accounts payable** > **Inquiries and reports** > **LATAM** > **Value query**.
2. In the **Media type** and **Document class** fields, enter a value.
3. On the Action Pane, select **Apply filter** to show the documents from the query results.

## Optional query filters
There are more fields you can use to narrow down the query result of documents.

| Field                | Description                                                                |
|----------------------|----------------------------------------------------------------------------|
| Satus                | Select between **Open**, **History**, and **Both**.                                     |
| Currency             | Select the currency of the value.                                          |
| Cut date             | Select a limit date to filter the values.                                  |
| Document number from | Enter the lower limit of a range of numbers to filter the document number. |
| Document number to   | Enter the upper limit of a range of numbers to filter the document number. |
| From date            | Select a date to filter the start of the document date.                    |
| To date              | Select a date to filter the end of the document date.                      |
| From due date        | Select a date to filter the starting due date of the document.             |
| To due date          | Select a date to filter the final due date of the document.                |

- After you select the needed values in the fields, select **Apply** to filter and show the transactions.
