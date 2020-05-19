---
# required metadata

title: Configure export to Azure Data Lake
description: This topic explains .
author: MilindaV2
manager: AnnBe
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2018-12-03
ms.dyn365.ops.version: Platform Update 23

---

# Configure export to Azure Data Lake

[!include [banner](../includes/banner.md)]



# [Portal](#tab/portal)

Tab 1 text

# [Azure CLI](#tab/azure-cli)

Tab 2 text

# [PowerShell](#tab/powershell)

Tab 3 text



## Next section header

Overview
--------

Configuring Export to Data lake has several steps.

You must create a storage account in your own Azure subscription and use a key
vault to provide that account to the system.

Next, you must create an Azure Active Directory (Azure AD) application ID that
grants access to the root of your storage account. The system will use the Azure
AD application to gain access to storage – and create the folder structure and
write data.

Finally, you must create a key vault in your subscription, and provide
information about your storage account and the application to the Data Lake
offer in Microsoft Dynamics Lifecycle Services (LCS).


In **Azure portal**

1.  Create a Microsoft Azure Data Lake Storage Gen2 account (a storage account)
    in your subscription

2.  Create an Application in Azure Active Directory. Get the App ID and an
    generate an App secret.

3.  Create a Key vault and create 3 secrets that contain the storage account
    name as well as the application ID and App secret

4.  Authorize the Application you created earlier so that it can read the
    secrets in the key vault.

5.  Grant Access control roles so that your application can access the storage
    account

When following above process, the document will instruct you to save several
values such as Key vault details that are required for subsequent steps. Next
you are going to provide these values (via a key vault) to Finance and
Operations using the **Dynamics Life cycle services (LCS),** you will need
Administrator access to LCS in order to perform this step

1.  Install the **Export to Data Lake** add-in in **LCS**

In **Finance and Operations**,

1.  Turn on the **Export to Azure Data Lake** feature.

2.  Select data (that is, the tables and entities that should be staged in Data
    Lake).

3.  Monitor the tables in Data Lake.



