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
You can consult the state of any value type document class posted in a transaction from here.
## Prerequisites
Create a value type document class and use that document class in a transaction with an action.
## Consulting values
1. Go to **Accounts payable > Inquiries and reports > LATAM > Value query**.
2. Complete at least the fields **Media type** and **Document class** and select **Apply filter** from the action pane to show the documents in the grid below.
## Optional query filters
There are more fields to be completed in order to narrow down the documents queried.

| Field                | Description                                                                |
|----------------------|----------------------------------------------------------------------------|
| Satus                | Select between open, history and both.                                     |
| Currency             | Select the currency of the value.                                          |
| Cut date             | Select a limit date to filter the values.                                  |
| Document number from | Enter the lower limit of a range of numbers to filter the document number. |
| Document number to   | Enter the upper limit of a range of numbers to filter the document number. |
| From date            | Select a date to filter the document date.                                 |
| To date              | Select a date to filter the document date.                                 |
| From due date        | Select a date to filter the document due date.                             |
| To due date          | Select a date to filter the document due date.                             |

After completing these fields select **Apply** filter to show the transactions in the grid below.
