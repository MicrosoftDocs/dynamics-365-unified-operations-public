---
# required metadata

title: Move, replace, and install assets
description: This article explains how to move, replace, and install assets in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectReplace, EntAssetObjectInstallLookup, EntAssetObjectMove, EntAssetObjectTableEditSubObjects
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

# Move, replace, and install assets

[!include [banner](../../includes/banner.md)]

 

This article explains how to move, replace, and install assets in Asset Management. You can create individual assets that have no relations to other assets, or you can create an asset structure that includes a parent asset (top-level asset) and related child assets (sub-assets). In Asset Management, there are three approaches to moving and changing the location of an asset:

- **Move** – Move an asset either to another asset structure or to another location in the same asset structure.
- **Replace** – Temporarily remove an asset from an asset structure so that it can be repaired or refurbished, and then add the refurbished asset back to the asset structure later. Alternatively, permanently replace a used asset with a new asset.
- **Install** – Install a parent asset and any related child assets on a functional location.

> [!NOTE]
> The asset that you move, replace, or install might be related to another functional location. In that case, the asset might use financial dimensions of the functional location. On the **Functional location types** page, you set up the handling of financial dimensions on functional locations.

## Move asset

Use the **Move asset** function to move an asset either to another asset structure or to another location in the same asset structure. You can also move an asset out of an asset structure so that it becomes a standalone asset that has no structure relations.

> [!NOTE]
> Don't use this function if assets are being repaired or temporarily replaced. Instead, use the **Replace asset** functionality that is described later in this article.

1. Select **Asset management** \> **Assets** \> **All assets** or **Active assets**.
2. In the list, select the asset to move. If the asset has child assets, you also move those assets.
3. Select **Move asset**.
4. To move the asset so that it becomes part of an asset structure, select the new parent asset in the **Parent asset** field. If you're moving a child asset, and you want to make it a standalone asset that has no structure relations, leave the **Parent asset** field blank.
5. By default, the **Effective** field is set to the current date and time. However, you can select a different date and time that the asset move is valid from.
6. Select **OK**.

## Replace asset

Use the **Replace asset** function in connection with repairs, refurbishment, or permanent replacement of a worn-out asset by a new asset. This function is used to replace child assets in an asset structure. For parent assets (that is, assets that don't currently have a parent asset), this replacement is done on a functional location. For more information about how to replace parent assets on a functional location, see [Install assets on functional locations](../functional-locations/install-objects-on-functional-locations.md).

> [!NOTE]
> If a repair shop is related to your production department, you can create functional locations such as **Repair**, **Scrap**, and **Storage** to handle the repair and replacement of assets.

1. Select **Asset management** \> **Assets** \> **All assets** or **Active assets**.
2. In the list, select the child asset to replace. If the asset has child assets, you also replace those assets.
3. Select **Replace asset**.

    The **Structure change** field shows the last date and time that the selected asset and related child assets were moved in the asset structure.

4. In the **Selected asset** section, in the **Target functional location** field, select the functional location to move the asset to. For example, select the **Repair** or **Scrap** location.

    In the **Parent asset** section, the **Effective** field shows the last date and time that the parent asset and related child assets were installed or moved on the current functional location.

5. In the **New asset** section, in the **Asset** field, select the asset to insert as a temporary or permanent replacement for the selected asset. This asset might currently be located on another functional location, such as **Storage**.
7. In the **Effective from** section, the **Effective** field is set to the current date and time by default. However, you can select a different date and time that the asset replacement is valid from.
8. Select **OK**.

## Install asset

Use the **Install asset** function to install an asset structure on a functional location.

> [!NOTE]
> Always select a parent asset. The parent asset and related child assets will be moved to the selected functional location.

1. Select **Asset management** \> **Assets** \> **All assets** or **Active assets**.
2. In the list, select the parent asset to install on another functional location.
3. Select **Install asset**.

    The **Attributes** section shows the asset attributes that are set up on the parent asset.

4. In the **Functional location** field, select the new location.
5. By default, the **Effective** field is set to the current date and time. However, you can select a different date and time that the installation on the asset structure is valid from.
6. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]