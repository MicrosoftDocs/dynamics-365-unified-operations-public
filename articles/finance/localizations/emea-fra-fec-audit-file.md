---
# required metadata

title: Generate the Standard Audit File for France (FEC)
description: This topic walks you through generating the Standard Audit File for France (FEC) in Microsoft Dynamics 365 Finance.
author: ShylaThompson
manager: AnnBe
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create Standard Audit File for France (FEC)

[!include [banner](../includes/banner.md)]

This procedure walks you through generating the Standard Audit File (FEC) for France in the electronic file format. French tax authorities require audit files that are generated in the FEC format.

Before you can generate a FEC audit file, you must 
1. Import the latest version of the Electronic reporting configuration **French FEC audit file**. 
For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
2. On the **Configurations** page, expand **Data export model**, select **French FEC model mapping**. Set **Default for model mapping** to **Yes**

## Generate the Standard Audit File for France
1. Go to **General Ledger** > **Periodic tasks** > **Data export** to open the **Data export** page.
2. In the **Format mapping** field, select *French FEC audit file*.
3. Click **OK**.
4. On the **Electronic report parameters** page, enter start and end dates of the period in the fields **Period - date from**, **Period - date to** and click **OK**.
5. Review the generated file.
