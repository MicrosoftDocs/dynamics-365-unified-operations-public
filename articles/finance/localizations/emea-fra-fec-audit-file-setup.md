---
# required metadata

title: How to prepare your Dynamics 365 Finance to generate FEC
description: This topic describes how to prepare your Dynamics 365 Finance to generate FEC.
author: liza-golub
ms.date: 28/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# How to prepare your Dynamics 365 Finance to generate FEC

Before you can generate a FEC audit file, you must:

1.  Import the latest versions of the following Electronic reporting (ER)
    configurations:

| **ER configuration**     | **Type**      | **Description**                                                                              |
|--------------------------|---------------|----------------------------------------------------------------------------------------------|
| Data export model        | Model         | Unified data model for data exporting                                                        |
| French FEC model mapping | Model mapping | Configuration that collects data from different data sources to prepare it for FEC reporting |
| FEC audit file (FR)      | Format        | Exporting format in the structure of FEC                                                     |

Note:

After all the ER configurations from the preceding table are imported, set
the **Default for model mapping** option to **Yes** for the **French FEC model
mapping** configuration on the **Configurations** page.

For more information about how to download ER configurations from the Microsoft
global repository, see [Download ER configurations from the Global
repository](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo).

2.  Starting in version **10.0.20** of Dynamics 365 Finance, to use the **FEC
    audit file (FR)** format, define the ER configuration name in a new General
    ledger parameter. Go to **General ledger** \> **Ledger setup** \> **General
    ledger parameters**.

3.  Expand the **Electronic reporting** FastTab and then select
    the **Ledger** tab.

4.  In the **Ledger transactions export** group, in the **Ledger transactions
    export** field, select the format **FEC audit file (FR)**, and then save the
    new setting.
