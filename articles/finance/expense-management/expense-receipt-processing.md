---
# required metadata

title: Expense receipt processing
description: This topic provides information about optical character recognition (OCR) processing for receipts. This feature is designed to improve the user experience when expense reports are created in Microsoft Dynamics 365 Finance.
author: stsporen
manager: AnnBe
ms.date: 11/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: stsporen
ms.search.validFrom: 2019-11-20 
ms.dyn365.ops.version: 10.0.8 
---

# Expense receipt processing

[!include [banner](../includes/banner.md)]

Expense entry has been enhanced through the introduction of optical character recognition (OCR) processing for receipts. This feature is designed to improve the user experience when expense reports are created.

## Key features

- The merchant name, date, and total amount are extracted from receipts.
- The feature tries to match unattached receipts to unattached expense transactions.
- Users can create manually entered expense transactions from receipts.

## Usage examples

- **Automatically attach receipts that include credit card transactions when an expense report is created.**

    1. Open the **Expense management** workspace.
    2. On the **Receipts** tab, verify that unattached receipts exist. You can also upload receipts on the **Receipts** tab.
    3. On the **Expenses** tab, verify that unattached expenses exist. Typically, the expense administrator imports these expenses from the credit card provider.
    4. Select **New expense report**. Notice that you can include expenses, and receipts, now as well, when you create an expense report. If you add both expenses and receipts, automatic matching of the receipts against the expenses is triggered.

- **Create an expense, or match an expense from a receipt.**

    1. On an expense report, on the **Receipts** tab, attach a receipt by selecting **Add receipts**.
    2. Under the uploaded image of the receipt, notice the **Create** and **Match** options.

        - Select **Create** to create a manually entered expense transaction and fill in the values that are extracted from the receipt.
        - If you select **Match**, the system tries to match an existing expense to the receipt.

## Installation

This feature works in combination with the **Expense reports re-imagined** feature to help simplify the expense experience.

To use these advanced expense capabilities, install the Expense Management Service add-in for Microsoft Dynamics 365 Finance, and turn on the features in your instance. You can access the add-in from your project in Microsoft Dynamics Lifecycle Services (LCS).

1. Sign in to LCS, and open the desired environment.
2. Go to **Full details**.
3. Select **Maintain**, or scroll down to the **Environment add-ins** FastTab.
4. Select **Install a new add-in**.
5. Select **Expense Management Service**.
6. Follow the installation guide, and agree to the terms and conditions.
7. Select **Install**.

In the **Feature management** workspace, turn on the following features:

- Expense reports re-imagined
- Auto-match and create expense from receipt

When you turn on these features the following actions occur:

- The existing **Expense management** workspace is replaced with the new workspace.
- A new menu item for expense field visibility is added.
- You can still open the former **Expense reports** page by going to **Expense management > My expenses > Expense reports**.
- Workflows and any approvals still take you to the existing expense reports page.
- Receipts will be processed through Microsoft Azure Cognitive Services, and metadata will be extracted and added.
- An option is added that lets you create an expense report that includes matched unattached receipts.
- An option that is added to expense reports lets you create an expense line from a receipt, or attempts to match an existing receipt to an existing expense line.

For more information about the Expense reports re-imagined feature, see [Expense reports reimagined](ExpenseWorkspaceNew.md).

## Frequently asked questions

**Does Microsoft use my data for its models?**

No, Microsoft has built a general machine learning model for its receipt processing service. This model isn't based on the receipts that you upload.

**Where is this feature available and processed?**

Currently, the United States is supported.

**Where do my receipts go?**

Finance will contact Cognitive Services to extract the field data. Cognitive Services will retain a copy of your receipt for up to 24 hours while processing occurs. After processing is completed, Cognitive Services will remove the receipt. Receipts are still stored in Finance.

For more information, see [Enable receipt understanding with Form Recognizer's new capability](https://azure.microsoft.com/blog/enable-receipt-understanding-with-form-recognizer-s-new-capability/).
