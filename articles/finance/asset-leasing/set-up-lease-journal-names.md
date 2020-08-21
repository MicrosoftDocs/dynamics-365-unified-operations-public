---
# required metadata

title: Set up lease journal names
description: This topic lists the steps for defining journal names, which indicate the journal that entries that originate in Asset leasing will post to. 
author: moaamer
manager: Ann Beebe
ms.date: 08/14/2019
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
ms.author: vstehman
ms.search.validFrom: 2019-08-14
ms.dyn365.ops.version: 10.0.6

---

# Set up Lease Journal Names (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Lease journal names specify the journal that Asset leasing transactions will post to. Only journal names that are assigned to the Asset leasing journal type will appear in the **Initial Recognition** and **Monthly Journal Name** fields on the **Asset leasing parameters** page. Only vendor invoice recording journal types can be assigned to the **Invoice journal name** field.

1.	To configure the journal names, open the **Asset leasing parameters** page (**Asset leasing > Setup > Asset leasing parameters**).

2.	In the **Initial recognition journal** name field, select a journal. All initial recognition journal entries will post to this journal name.

3.	In the **Invoice journal name** field, select a journal. Lease and expense payment invoices will post to this journal if the **Pay to vendor parameter** is enabled on the lease book.

4.	In the **Lease journal name** field, select a journal. All depreciation, interest, and short-term reclassification entries will post to this journal name. Lease payments and expense payment entries will also post to this journal if the Pay to vendor parameter is disabled on the lease book.
