---
title: Troubleshooting guide for some issues with the data reconciliation of Z report
description: This article describes some of the issues users might experience with the data reconciliation of Z report with Headquarters (HQ). It also provides the possible root causes and solutions to prevent such occurrences in future.
author: Shajain
ms.date: 12/04/2022
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31

---

# Troubleshooting guide for some issues with the data reconciliation of Z report 

[!include [banner](../../includes/banner.md)]

This article describes some of the issues users might experience with the data reconciliation of Z report with Headquarters (HQ). It also provides the possible root causes and solutions to prevent such occurrences in future.

## Symptom

- There is a mismatch between the amounts shown on the Z report and the totals shown on the calculated statement
- The transaction in HQ has incorrect number of line items or the line total and the total for the transaction are not matching
- The number of transactions in a shift shown in HQ are lesser than the number of transactions on Z report
- Statement posting failed because of one of the reasons mentioned above

## Root cause

The most common root cause of the symptoms mentioned above is the creation of duplicate transaction id's in the channel database. This could happen if the local database storage of Modern Point of Sale (MPOS) get corrupted, or a MPOS, which has some transactions in the offline mode, gets reactivated with an account that has no access to offline db, or it could be because of some customization related to the transaction ID generation.

## Prevention and next steps

The duplicate transaction ID occurs because traditionally, the transaction ID in the Dynamics 365 Commerce relied on the number sequence to provide the sequential transaction ID's and if for any reason the system becomes unaware of a used number sequence, then it will result in the duplicate transaction ID. So, to mitigate this issue in future, as of 10.0.19, a new feature named *"Enable new transaction id to avoid duplicate transaction ids"* has been introduced, which does not create sequential transaction ID's, but guarantees a unique transaction ID for each transaction. You can find more details on this feature here: [Prevent duplicate transaction IDs](https://learn.microsoft.com/en-us/dynamics365/commerce/channel-setup-retail#ensure-unique-transaction-ids).

For the current issue, please create a support ticket to see if the data can be fixed, but please note that in some cases no data fix might be possible or no data fix might be needed e.g. if there is no data loss in HQ.
