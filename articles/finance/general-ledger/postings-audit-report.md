---
title: Financial reporting posting audit
description: Learn about financial reporting posting audit in Microsoft Dynamics 365 Finance.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 10/28/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: FinancialReports
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3eae6dc3-ee06-4b6d-9e7d-1ee2c3b10339
---

# Financial reporting posting audit

[!include [banner](../includes/banner.md)]

Entering transactions accurately is important for proper reporting. Transactions should be posted to the correct accounts and dimensions with the correct amounts. 
This article explains how the Audit report helps evaluate how transactions were posted by providing a look a the details for each transaction in a straightforward way.

The Row Definition for the report contain a Dimension value set of several accounts that commonly have posting issues. Alternatively, a Row Definition similar to a trial balance containing all natural accounts 
could be used. The Column Definition contains the month-to-date amounts as well as several columns with specific transaction attributes. These attributes may vary: 

 - Transaction date
 - Audit trail code
 - Journal entry
 - Distribution reference
 - Source document
 - Series
 - Originating master record name

## Key features
Key features in the **Postings audit** report are:
 - Dimension value set displays a list of the accounts that should be reviewed.
 - Transaction attributes show the journal entry number and other key transaction details.
 - Downloading the report to Excel, where it's easier to review large amounts of data. 
 
