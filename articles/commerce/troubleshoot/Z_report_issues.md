---
title: Issues with the data reconciliation of a Z report
description: This article describes some of the issues users might experience with the data reconciliation of Z report with Headquarters (HQ). It also provides the possible root causes and solutions to prevent such occurrences in future.
author: Shajain
ms.date: 12/06/2022
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31

---

# Issues with the data reconciliation of a Z report 

[!include [banner](../../includes/banner.md)]

This article describes some of the issues users might experience with the data reconciliation of Z report with Headquarters (HQ). It also provides the possible root causes and solutions to prevent such occurrences in future.

This article provides troubleshooting guidance that can help if you encounter issues with the data reconciliation of a Z report in Microsoft Dynamics 365 Commerce headquarters.

## Description

- There is a mismatch between the amounts shown on the Z report and the totals shown on the calculated statement.
- The transaction in Commerce headquarters has incorrect number of line items, or there is a mismatch between the line total and the total for the transaction.
- The number of transactions in a shift shown in headquarter are les than the number of transactions on the Z report.
- Statement posting failed because of one of the reasons mentioned above.

### Root cause

The most common root cause of the symptoms mentioned above is the creation of duplicate transaction IDs in the channel database. This can happen for the following reasons:

- If the local database storage of Modern Point of Sale (MPOS) get corrupted.
- If MPOS has some transactions in the offline mode and is reactivated with an account that has no access to offline database.
- If there is an issue with customization related to transaction ID generation.

## Resolution

The duplicate transaction ID occurs because normally a transaction ID in Commerce relies on the number sequence to provide sequential transaction IDs. If for any reason the system becomes unaware of a used number sequence, the result is a duplicate transaction ID. 

To resolve the duplicate transaction ID issue, create a support ticket to check if the transaction data can be fixed. In some cases no data fix may be possible or needed, for example if there is no data loss in headquarters.

To prevent this issue in the future, in headquarters you must enable the **Enable new transaction id to avoid duplicate transaction ids** feature that was introduced in Commerce version 10.0.19. This feature prevents the creation of sequential transaction IDs by ensuring that a unique transaction ID is created for each transaction. For more information on this feature, see [Prevent duplicate transaction IDs](../channel-setup-retail#ensure-unique-transaction-ids.md).

