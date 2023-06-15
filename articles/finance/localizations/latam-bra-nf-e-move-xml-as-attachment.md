---
title: Move NF-e XML files as attachments
description: This article explains how to move NF-e XML files out of your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management database and make them available as attachments instead.
author: gionoder
ms.date: 11/11/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: 10.0.25
ms.assetid: 
ms.search.form: 
---

# Move NF-e XML files as attachments

[!include [banner](../includes/banner.md)] 


When electronic fiscal documents (NF-e) are issued, XML files are created and stored in the Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management databases. In the Brazilian localization, you can use the **NF-e XML move as attachment** feature to free up the database space that those XML files consume.

For a specific date range and fiscal establishment, the feature moves the NF-e XML files from your Finance or Supply Chain Management database
to the Blob storage from your Azure subscription. This movement makes the files available only as attachments. After the XML files are successfully moved to the Blob storage, the original files are deleted from the Finance or Supply Chain Management database. Therefore, the database space that those files used is released.

Follow these steps to enable the **NF-e XML move as attachment** feature.

1. In Finance or Supply Chain Management, open the **Feature management** workspace.
2. On the **All** tab, search for and select the **NF-e XML move as attachment** feature.
3. Select **Enable now**.

Follow these steps to move NF-e XML files as attachments.

1. Go to **Accounts receivable** \> **Fiscal documents** \> **Electronic fiscal documents** \> **Move NF-e XML as attachments**.
2. In the **From date** and **To date** fields, select the start and end dates.
3. In the **Fiscal establishment ID** field, select a value.
4. Select **OK**.

> [!IMPORTANT]
> This process isn't reversible. After you move the NF-e XML files, users can view them only by selecting **Attachments** at the top of **Fiscal document** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
