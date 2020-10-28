---
# required metadata

title: Set up lease journal names
description: This topic explains how to define lease journal names. Lease journal names specify the journals that entries that originate in Asset leasing are posted to.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

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

To configure lease journal names, follow these steps.

1. Go to **Asset leasing \> Setup \> Asset leasing parameters**.
2. On the **General** tab, in the **Initial recognition journal name** field, and select a journal. All initial recognition journal entries will be posted to this journal name.
3. In the **Invoice journal name** field, select a journal. If the **Pay to vendor** option is set to **Yes** for the lease book, lease and expense payment invoices will be posted to this journal name.
4. In the **Lease journal name** field, select a journal. All depreciation, interest, and short-term reclassification entries will be posted to this journal name. If the **Pay to vendor** option is set to **No** for the lease book, lease payments and expense payment entries will also be posted to this journal name.
