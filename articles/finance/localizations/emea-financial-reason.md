---
# required metadata

title: Financial reason feature extension
description: This topic provides information about the extension to the **Financial reason** feature.
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

This topic provides information about the **Financial reason** feature extension that can be used globally in legal entities with a primary address in any country.

Generally, the **Financial reason** feature allows you to set up a pre-defined list of financial reasons to use during document registration and posting in the system. 

1. Go to **Organization administration** > **Setup** > **Financial reasons**.
2. On the Action Pane, select **New** to create a new finical reason.
3. In the **Reason code** column, specify a code for the financial reason to use when registering and posting documents.
4. In the **Default comment** column, specify a comment for the financial reason that will be used as default value in **Reason comment** field. This comment should correspond to the reason code that is selected when the documents are registrated and posted.
5. In the **Ledger**, **Asset**, **Bank**, **Customer**, and **Vendor** columns, select the check box for those modules of the system where the selected reason code must be available.

The feature, **Enable extended support of Financial reason code** enables the **Reason code** and **Reason comment** fields in an extended list of documents in Dynamics 365 Finance and stores their values in tax transactions that correspond to the posted document.

## Activate the Financial reason feature

The **Enable extended support of Financial reason code** feature is available in the **Feature management** workspace of following or later versions of Finance.

| **Finance version** | **Build**                                         |
|---------------------|---------------------------------------------------|
| 10.0.24             | All builds relevant to 10.0.24 version and higher |
| 10.0.23             | 10.0.1037.36                                      |
| 10.0.22             | 10.0.995.75                                       |
| 10.0.21             | 10.0.960.114                                      |

1.	Go to **Workspaces** > **Feature management**, and expand the **All** FastTab.
2.	Search for the **Enable extended support of Financial reason code** feature and select it.
3.	Select **Enable now** to enable the feature in your Finance environment.

After the feature is enabled, the **Enable extended support of Financial reason code** feature is available in all legal entities of your Finance environment in the following documents:

-	**General ledger** > **Journal entries** > **General journal**
-	**Accounts payable** > **Invoices** > **Invoice journal**
-	**Accounts payable** > **Invoices** > **Invoices register**
-	**Accounts payable** > **Invoices** > **Invoices approval**
-	**Accounts payable** > **Purchase orders** > **All purchase orders**
-	**Account receivable** > **Orders** > **All sales orders**
-	**Account receivable** > **Invoices** > **All free text invoices**
-	**Project management and accounting** > **Project invoices > Project invoice proposal**

When the **Enable extended support of Financial reason code** feature is enabled in Finance, the values specified enable the **Reason code** and **Reason comment** fields of the documents listed above are stored in the **Tax transactions** table as a result of tax posting.

