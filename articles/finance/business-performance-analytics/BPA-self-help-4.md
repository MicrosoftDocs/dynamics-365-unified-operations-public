---

title: Business performance analytics self help - Missing Missing Journal Entries:
description: This article provides information about common errors in business performance analytics.
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

# Business performance analytics self help error

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate
> in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing Journal Entries: Error Code: ERR00004 – [Type:Warning] 

Description: Error Code ERR00004 is logged in the BPA_SelfHelp_Log table when the Recid column in the generaljournalaccountentry.generaljournalentry of D365 Finance is not found in the recid column of the generaljournalentry table. These records are being excluded and won't be transferred to Fact tables. Certain pre-written Microsoft reports might show empty or incomplete data, prompting you to consider duplicating and modifying these reports. 

Resolution Steps: 

No immediate action is required. This issue might stem from data synchronization delays. We recommend observing the next 2-3 BPA runs to see if the error resolves itself. If the problem persists, follow these steps: 

Verify Entries in General Journal Entry Table: 

Confirm whether the entries exist in the General journal entry table in D365 Finance. If they are present in the source, proceed to the next step. 

Contact Microsoft Support: 

If the issue persists and the entries are indeed in the source, it's recommended to raise a support ticket with the Microsoft team for further assistance. 

Sample record 

Cannot find GeneralJournalEntry for 4 records in GeneralJournalAccountEntry - [Row(GJAE_RECID=Decimal('5637144581')), Row(GJAE_RECID=Decimal('5637144582')), Row(GJAE_RECID=Decimal('5637144583')), Row(GJAE_RECID=Decimal('5637144584'))] 

 
