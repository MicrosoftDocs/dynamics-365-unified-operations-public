---
# required metadata

title: Set up lease journal names
description: This article explains how to define lease journal names. Lease journal names specify the journals that entries that originate in Asset leasing are posted to.
author: moaamer
ms.date: 03/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeasePostingAccounts
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Set up lease journal names

[!include [banner](../includes/banner.md)]


Lease journal names specify the journals that Asset leasing transactions are posted to. Only journal names that are assigned to the **Asset leasing** journal type appear in the **Initial Recognition** and **Monthly Journal Name** fields on the **Asset leasing parameters** page. Only **vendor invoice recording** journal type can be assigned to the **Invoice journal name** field.

Certain financial fields are locked from being edited to prevent any variances between the transactions and the schedules. Some fields that are locked include: **Account**, **Amounts**, **Financial dimensions**, **Currency**, and **Transaction type**. Additionally, you won't be able to add or delete journal entry lines in any **Asset leasing journal entries**, as this might cause variances between the schedules and the transactions.


To configure lease journal names, complete the following steps.

1. Go to **Asset leasing \> Setup \> Asset leasing parameters**.
2. On the **General** tab, in the **Initial recognition journal name** field, and select a journal. All initial recognition journal entries will be posted to this journal name.
3. In the **Invoice journal name** field, select a journal. If the **Pay to vendor** option is set to **Yes** for the lease book, lease and expense payment invoices will be posted to this journal name.
4. In the **Lease journal name** field, select a journal. All depreciation, interest, and short-term reclassification entries will be posted to this journal name. If the **Pay to vendor** option is set to **No** for the lease book, lease payments and expense payment entries will also be posted to this journal name.
5. In the **Lease modification journal name** field, select a journal. Lease adjustment, termination, and impairment transactions will be posted to this journal name. The journal name that you select should not have a workflow or approval assigned to it. If the lease modification journal name isn't defined, lease adjustment, termination, and impairment transactions will be posted to the journal name that is selected in the **Lease journal name** field. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
