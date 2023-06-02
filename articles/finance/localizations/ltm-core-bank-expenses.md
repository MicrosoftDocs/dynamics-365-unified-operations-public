---
title: Bank expense posting for Latin America
description: This article provides information about posting bank expenses for Latin America. 
author: Fhernandez0088
ms.date: 06/02/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Bank expenses posting for Latin America
[!include [banner](../includes/banner.md)]

You can post journals for bank expenses directly into the banks account reconciliations for Latin American countries.

## Prerequisites
Before you post a bank expense journal with LATAM information, you must configure the following:

- Enable the Globalization LATAM feature with a valid country.
- Go to **Organization administration > Setup > LATAM > Bank Parameters – LATAM** enable the use of bank expenses and select a journal name to be used.
- Create a document class configured as a vendor invoice for the bank expenses.

## Post bank expenses with LATAM information
Complete the following steps to post a bank expense with LATAM information.

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts** and select a bank account.
2. On the Action Pane, select **Account reconciliation**.
3 Select or create a new record. 
4. Select **Transactions** and on the Action Pane, select **LATAM** > **Bank expenses**.
5. On the **Setup** tab, set the **Amounts include sales tax** slider to **Yes**.
6. On the Action Pane, select **Lines**.
7. Complete the new journal with the bank expenses to be posted using a ledger account.
8. Select a vendor to represent the bank.
9. On the **Invoice** tab, select a cash payment term.
10. Complete the LATAM required information for the vendor line.
11. Select the cash payment ledger account as the offset account for the bank line and then select **Post**.
 
## View LATAM information from the posted journal
You can view the LATAM information from the bank transactions or the general journals entries.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
