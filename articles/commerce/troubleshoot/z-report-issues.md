---
title: Issues with the data reconciliation of a Z report
description: This article describes issues that users might experience with the data reconciliation of a Z report in Commerce headquarters. It also describes possible root causes and solutions that can help prevent future occurrences.
author: Shajain
ms.date: 02/09/2023
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.search.form: RetailStatements_Posting, RetailStatements_CustomerOrderCreation

---

# Issues with the data reconciliation of a Z report
Error code: SYS103633

[!include [banner](../../includes/banner.md)]

This article provides troubleshooting guidance that can help if you encounter issues with the data reconciliation of a Z report in Microsoft Dynamics 365 Commerce headquarters. It describes issues that users might experience with the data reconciliation, possible root causes, and solutions that can help prevent future occurrences.

## Description

- There's a mismatch between the amounts that are shown on the Z report and the totals that are shown on the calculated statement.
- The transaction in headquarters has an incorrect number of line items, or there's a mismatch between the line total and the total for the transaction.
- The number of transactions that are shown in a shift in headquarters is less than the number of transactions on the Z report.
- Statement posting failed for one of the preceding reasons.

### Root cause

The most common root cause of the previously described symptoms is the generation of duplicate transaction IDs in the channel database. Duplicate transaction IDs can be generated for the following reasons:

- The local database storage of Modern Point of Sale (MPOS) is corrupted.
- MPOS has some transactions in offline mode, and it's reactivated by using an account that has no access to the offline database.
- There's an issue with customization that's related to the generation of transaction IDs.

## Resolution

Usually, Commerce relies on a number sequence to generate sequential transaction IDs. If the system can't determine that a number sequence was used for any reason, a duplicate transaction ID is generated. 

To fix the duplicate transaction ID issue, create a support ticket to check whether the transaction data can be fixed. In some cases, such as when there's no data loss in headquarters, no data fix is possible or required.

To help prevent this issue in the future, you must enable the **Enable new transaction id to avoid duplicate transaction ids** feature in headquarters. This feature was introduced in Commerce version 10.0.19. It helps prevent the creation of sequential transaction IDs by ensuring that a unique transaction ID is created for each transaction. For more information about this feature, see [Prevent duplicate transaction IDs](../channel-setup-retail.md#ensure-unique-transaction-ids).
