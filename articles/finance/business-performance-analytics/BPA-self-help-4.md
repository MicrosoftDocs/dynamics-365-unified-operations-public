---

title: Business performance analytics self help - Missing journal entries
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
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing journal entries: Error code: ERR00004 – [Type:Warning] 
Error Code ERR00004 occures in the BPA_SelfHelp_Log table when the Recid column in the generaljournalaccountentry.generaljournalentry of Dynamics 365 Finance isn't found in the Recid column of the generaljournalentry table. These records are excluded and aren't transferred to Fact tables. Certain Microsoft reports might display empty or incomplete data. In such cases, you might need to create modified versions of these reports to address the gaps and ensure accurate reporting.  

No immediate action is required as the warning might be the result of a delay in data synchronization. It's recommended to observe the next couple of business performance analytics runs to see if the error resolves. 
If the problem persists, confirm that the entries are in General journal entry table in Dynamics 365 Finance. If the records are in the table, contact the Microsoft support team for further assistance. 

Sample record 

Cannot find GeneralJournalEntry for 4 records in GeneralJournalAccountEntry - [Row(GJAE_RECID=Decimal('5637144581')), Row(GJAE_RECID=Decimal('5637144582')), Row(GJAE_RECID=Decimal('5637144583')), Row(GJAE_RECID=Decimal('5637144584'))] 

 
