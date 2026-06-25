---
title: Set up lease journal names
description: Learn about how to define lease journal names. Lease journal names specify the journals that entries that originate in Asset leasing are posted to.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeasePostingAccounts
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Set up lease journal names

[!include [banner](../includes/banner.md)]

Lease journal names specify the journals that Asset leasing transactions are posted to. Only journal names that are assigned to the **Asset leasing** journal type appear in the **Initial Recognition** and **Monthly Journal Name** fields on the **Asset leasing parameters** page. Only **vendor invoice recording** journal type can be assigned to the **Invoice journal name** field.

To prevent variances between the transactions and the schedules, certain financial fields are locked from being edited. Some locked fields include **Account**, **Amounts**, **Financial dimensions**, **Currency**, and **Transaction type**. Additionally, you can't add or delete journal entry lines in any **Asset leasing journal entries**, as this action might cause variances between the schedules and the transactions.

To configure lease journal names, complete the following steps.

1. Go to **Asset leasing \> Setup \> Asset leasing parameters**.
1. On the **General** tab, in the **Initial recognition journal name** field, select a journal. All initial recognition journal entries post to this journal name.
1. In the **Invoice journal name** field, select a journal. If you set the **Pay to vendor** option to **Yes** for the lease book, lease and expense payment invoices post to this journal name.
1. In the **Lease journal name** field, select a journal. All depreciation, interest, and short-term reclassification entries post to this journal name. If you set the **Pay to vendor** option to **No** for the lease book, lease payments and expense payment entries also post to this journal name.
1. In the **Lease modification journal name** field, select a journal. Lease adjustment, termination, and impairment transactions post to this journal name. The journal name that you select shouldn't have a workflow or approval assigned to it. If you don't define the lease modification journal name, lease adjustment, termination, and impairment transactions post to the journal name that you select in the **Lease journal name** field.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
