---

title: Business performance analytics self-help error - Missing journal entries
description: This article provides information about the Missing journal entries error (error code ERR00004) in business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 09/09/2023
ms.topic: welcome
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
---

# Business performance analytics self-help error - Missing journal entries

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing journal entries: Error code: ERR00004 - [Type: Warning]

Error code *ERR00004* is logged in the `Transform Log` table in Microsoft Dataverse when the `Recid` column of `generaljournalaccountentry.generaljournalentry` in Dynamics 365 Finance isn't found in the `Recid` column of the `generaljournalentry` table. These records are excluded and aren't transferred to fact tables. Some Microsoft reports might show empty or incomplete data. In these cases, you might have to create modified versions of the reports to address the gaps and ensure accurate reporting.

No immediate action is required, because this issue might be caused by a delay in data synchronization. We recommend that you observe the next few business performance analytics runs to see whether the issue is fixed.

If the issue persists, confirm that the entries are in the General journal entry table in Dynamics 365 Finance. If the records are in the table, contact the Microsoft Support team for further assistance.

Here's an example of a record:

> Can't find GeneralJournalEntry for 4 records in GeneralJournalAccountEntry - \[Row(GJAE_RECID=Decimal('5637144581')), Row(GJAE_RECID=Decimal('5637144582')), Row(GJAE_RECID=Decimal('5637144583')), Row(GJAE_RECID=Decimal('5637144584'))\]
