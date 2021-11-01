---
# required metadata

title: Financial reason feature extension
description: This topic provides information about financial reason feature extension that can be used globally in legal entities with primary address in any country.
author: liza-golub
ms.date: 11/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 11/01/2021
ms.dyn365.ops.version: AX 10.0.21

---

# Financial reason feature extension

[!include [banner](../includes/banner.md)]

This topic provides information about financial reason feature extension that can be used globally in legal entities with primary address in any country.

Generally financial reason feature allows to set up pre-defined list of financial reasons that can be used during documents registration and posting in the system. 

1.	Go to **Organization administration** > **Setup** > **Financial reasons**.
2.	Click **New** on the Action pane, to create a new finical reason.
3.	In the **Reason code** column specify a code for the financial reason that will be used during documents registration and posting in the system.
4.	In the **Default comment** column specify a comment for the financial reason that will be used as default value in **Reason comment** field corresponding to the selected reason code during documents registration and posting in the system.
5.	In **Ledger**, **Asset**, **Bank**, **Customer**, **Vendor** columns mark a check box for those modules of the system where selected reason code must be available.

**Enable extended support of Financial reason code** feature enables **Reason code** and **Reason comment** fields in extended list of documents in Finance and provides storing of their values in tax transactions corresponding to the posted document.

## Activate the Financial reason feature

The **Enable extended support of Financial reason code** feature is available in the Feature management workspace of following or later versions:

| **Finance version** | **Build**                                         |
|---------------------|---------------------------------------------------|
| 10.0.24             | All builds relevant to 10.0.24 version and higher |
| 10.0.23             | 10.0.1037.36                                      |
| 10.0.22             |  |
| 10.0.21             | 10.0.960.114                                      |

1.	Go to Workspaces > Feature management, select All FastTab.
2.	Search the Enable extended support of Financial reason code feature and select it.
3.	Click Enable now button on the right bottom of the page to enable the feature in your Finance.

Once enabled,  **Enable extended support of Financial reason code** feature becomes available in all legal entities of your Finance in the following documents:

-	**General ledger** > **Journal entries** > **General journal**.
-	**Accounts payable** > **Invoices** > **Invoice journal**.
-	**Accounts payable** > **Invoices** > **Invoices register**.
-	**Accounts payable** > **Invoices** > **Invoices approval**.
-	**Accounts payable** > **Purchase orders** > **All purchase orders**.
-	**Account receivable** > **Orders** > **All sales orders**.
-	**Account receivable** > **Invoices** > **All free text invoices**.
-	**Project management and accounting** > **Project invoices > Project invoice proposal**.

When **Enable extended support of Financial reason code** feature is enabled in Finance, values specified in enables Reason code and Reason comment fields of the documents listed above are stored in tax transactions table as a result of tax posting.

