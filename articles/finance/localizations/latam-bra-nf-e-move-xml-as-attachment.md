---
# required metadata

title: Move NF-e XML files as attachments
description: This topic provides information about enabling and using the NF-e custom certificate.
author: gionoder
ms.date: 11/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: 10.0.25

---

# Move NF-e XML files as attachments

[!include [banner](../includes/banner.md)] 
[!include [banner](../includes/preview-banner.md)] 

In the Brazilian localization, you can use this feature to free up database space that is consumed by the XML files created when electronic fiscal documents
(NF-e) are issued. These XML files are stored in the Dynamics 365 Finance and Dynamics 365 Supply Chain Management databases.

For a specified date range and a specific fiscal establishment, this feature moves the NF-e XML files from your Finance or Supply Chain Management database
to the BLOB storage from your Azure subscription. This movement makes the files available only as attachments. When the XML files are successfully moved to the BLOB storage, the original files are deleted from the Finance or Supply Chain Management database, releasing database space.

Complete the following steps to enable the NF-e XML move as attachment feature.

1. In Finance or Supply Chain Management, go to the **Feature management** workspace.
2. On the **All** tab, search for and select the feature, **NF-e XML move as attachment**.
3. Select **Enable now**

To move the NF-e XML files as attachments, complete the following steps.

1. Go to **Accounts receivable** > **Fiscal documents** > **Electronic fiscal documents** > **Move NF-e XML as attachments**.
2. In the **From date** and **To date** fields, select the start and end date.
3. In the **Fiscal establishment ID** field, select a value.
4. Select **OK**.

> [!IMPORTANT]
> This process isn't reversible. After you have moved the NF-e XML files, they can only be viewed by selecting **Attachments** on the top of **Fiscal document** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
