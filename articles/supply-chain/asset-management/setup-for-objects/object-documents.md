---
# required metadata

title: Asset documents
description: This article explains asset documents in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectDocument
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset documents

[!include [banner](../../includes/banner.md)]

 

This article explains asset documents in Asset Management.

In Asset Management, you can set up documents so that they are automatically related to job types, asset manufacturers, asset types, or assets, for example. This functionality is useful when updated document versions are released. In that case, you just have to put the updated document in the standard location that you use for your Supply Chain Management documents, and attach the document to the asset document record that you've created. The updated document can then be accessed from the **All assets**, **Active assets**, **My active assets**, **All work orders**, and **Active work order jobs** menu items. The process for attaching documents to an asset document record uses the standard document handling system.

**Example 1:** A document that is related to a job type might describe a procedure for that job type.

**Example 2:** A document that is related to a combination of an asset type, manufacturer, and model might be the standard manual for the selected asset manufacturer model.

## Create asset document relation

1. Select **Asset management** \> **Setup** \> **Asset documents**.
2. Select **New** to create an asset document record.
3. Depending on how specific you want the document relation to be, make relevant selections in one or more of the following fields: **Asset type**, **Manufacturer**, **Model**, **Asset**, **Job type category**, **Job type**, **Job type variant**, and **Job requirement**. The options that are available in the **Job type variant** and **Job requirement** fields depend on your selection in the **Job type** field.

    > [!NOTE]
    > When the system searches for documents that should be related to an asset or a work order, Asset Management goes through all asset document records to check for a possible match. It always checks the most specific combination first. In other words, Asset Management first checks for a match for the **Job requirement** field. If no match is found, it checks for a match for the **Job type variant** field. If no match is found, it checks for a match for the **Job type** field, and so on. As you can see in the layout of the **Asset documents** page, this behavior means that, to find the most specific combination, Asset Management checks each record from right to left for a match. Several documents might be related to an asset or a work order. You can edit the service level on a maintenance request or a work order as you require.

4. Select **Attachments**. The standard **Document handling** page appears.
5. Set up the documents or notes that should be attached to the asset document record. After you attach documents, the **Attachments** field shows the number of documents that are related to the record.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]