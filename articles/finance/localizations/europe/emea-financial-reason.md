---
title: Financial reason feature extension
description: Learn about the extension to the Financial reason feature, including a step-by-step process on setting up a predefined list of financial reasons.
author: liza-golub
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.validFrom: 2021-11-01
ms.dyn365.ops.version: AX 10.0.21
---

# Financial reason

[!include [banner](../../includes/banner.md)]

The **Financial reason** feature lets you set up a predefined list of financial reasons that can be used during document registration and posting in the system. This feature can be used globally in legal entities that have a primary address in any country or region.

1. Go to **Organization administration** \> **Setup** \> **Financial reasons**.
2. On the Action Pane, select **New** to create a financial reason.
3. In the **Reason code** column, specify a code to use for the financial reason when documents are registered and posted.
4. In the **Default comment** column, enter the comment that should be used as the default value in the **Reason comment** field for the financial reason. This comment should correspond to the reason code that is selected when documents are registered and posted.
5. In the **Ledger**, **Asset**, **Bank**, **Customer**, and **Vendor** columns, select the checkbox for each system module where the selected reason code must be available.

**Financial reason** feature is available in the following documents in all legal entities of your Finance environment:

- General journal (**General ledger** \> **Journal entries** \> **General journal**)
- Invoice journal (**Accounts payable** \> **Invoices** \> **Invoice journal**)
- Invoice register (**Accounts payable** \> **Invoices** \> **Invoices register**)
- Invoices approval journal (**Accounts payable** \> **Invoices** \> **Invoices approval**)
- Purchase order (**Accounts payable** \> **Purchase orders** \> **All purchase orders**)
- Sales order (**Account receivable** \> **Orders** \> **All sales orders**)
- Free text invoice (**Account receivable** \> **Invoices** \> **All free text invoices**)
- Project invoice proposal (**Project management and accounting** \> **Project invoices \> Project invoice proposal**)

When tax posting occurs, the values of the **Reason code** and **Reason comment** fields of the preceding documents are stored in the **Tax transactions** table.
