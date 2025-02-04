---
title: Asset manufacturers and models
description: Learn how to set up asset manufacturers and related models in Asset Management, including a process for setting up product-model relations.
author: jodahlMSFT
ms.author: jodahl
ms.topic: article
ms.date: 06/26/2019
ms.reviewer: kamaybac
ms.search.form: EntAssetProductLookup, EntAssetModelLookup, EntAssetProduct
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
---

# Asset manufacturers and models

[!include [banner](../../includes/banner.md)]

 

This article explains how to set up asset manufacturers and related models in Asset Management. Models can be related to asset types.

## Set up product-model relations

1. Select **Asset management** \> **Setup** \> **Assets** \> **Manufacturer and model**.
2. Select **New** to create a new product.
3. In the **Manufacturer** field, enter a name for the asset manufacturer.
4. In the **Description** field, enter a description.
5. On the **Models** FastTab, select **Add** to create an asset model that should be related to the asset manufacturer.
6. In the **Model** field, enter a name for the asset model.
7. In the **Description** field, enter a description.
8. In the **Asset type** field, select the asset type that the manufacturer model should be related to.

    > [!NOTE]
    > You can also set up relations for asset types, manufacturers, and models in the **Asset types** lookup. Learn more in [Asset types](../setup-for-objects/object-types.md).

    In the **Details** FastTab, the **Models** field shows the number of asset models that are set up on the selected asset manufacturer. The **Assets** field shows the number of assets that are using the selected manufacturer.
    
    The **Assets** field shows the number of objects that are using the manufacturer model.

> [!NOTE]
> An asset type can have no asset manufacturer model relations, it can be related to one asset manufacturer model, or it can be related multiple asset manufacturer models. If an asset type is related to at least one manufacturer model, only the combinations that are set up in the **Manufacturer model** lookup can be selected on those Asset Management pages where a combination of an asset type, manufacturer, and model can be set up. These pages include **All assets**, **Asset service levels**, **Job type defaults**, and **Maintenance budget lines**. If some asset types aren't related to any manufacturer model, only those asset types, and manufacturer models that also have no relation to asset types, are shown on the pages.

## Select a manufacturer and model on an object

1. Select **Asset management** \> ***Assets** \> **All assets**.
2. In the **Asset** column, select the link for the asset. The **Details** page appears.
3. Select **Edit**.
4. On the **General** FastTab, select values in the **Manufacturer** and **Model** fields.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]