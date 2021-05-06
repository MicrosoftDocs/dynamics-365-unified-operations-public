---
# required metadata

title: Open the designer for the current tax configuration 
description: This topic provides troubleshooting information to help open the designer for the current tax configuration.
author: yungu
ms.date: 05/06/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---



# Open the designer for the current tax configuration 

[!include [banner](../includes/banner.md)]

This topic explains how to open the designer of the tax configuration currently in use. This topic will use the tax setup in standard environment as an example.

## Find version of current used tax configuration

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup**.
2. On the **Companies** FastTab, select the related company, and then select **Setup**.

     [![Companies FastTab, Setup butotn](./media/open-designer-configuration-Picture1.png)](./media/open-designer-configuration-Picture1.png)

3. Make a note of the configuration version listed in the tree. You will need this information later.

     [![Configuration version](./media/open-designer-configuration-Picture2.png)](./media/open-designer-configuration-Picture2.png)

## Open the designer of the currently used tax configuration

1. Go to **Workspaces** > **Electronic reporting** > **Tax configurations**.
2. Expand the **Taxable Document** node, and then expand **Taxable Document (India)** > **Tax (India GST)**.

     [![Expanded Taxable Document node](./media/open-designer-configuration-Picture3.png)](./media/open-designer-configuration-Picture3.png)

3. Select the currently used tax configuration that you noted earlier.

     [![Configurations page, selected tax configuration](./media/open-designer-configuration-Picture4.png)](./media/open-designer-configuration-Picture4.png)

4. Select **Designer**.

     [![Configurations page, Designer button](./media/open-designer-configuration-Picture5.png)](./media/open-designer-configuration-Picture5.png)

## Determine whether customization exists

If you've completed the steps in the previous section but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
