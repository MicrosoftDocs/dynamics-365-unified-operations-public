---
# required metadata

title: Install assets on functional locations
description: This article explains how to install assets on functional locations in Asset Management.
author: johanhoffmann
ms.date: 06/25/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetFunctionalLocationObjectChange, EntAssetFunctionalLocationObjectInstall, EntAssetFunctionalLocationObject
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

# Install assets on functional locations

[!include [banner](../../includes/banner.md)]

 

After you've created functional location structures, the next step is to install assets on the relevant functional locations. This article explains how to install assets on those functional locations in Asset Management. For information about how to create assets, see [Introduction to assets](../objects/introduction-to-objects.md).

If you've created an asset structure, the whole asset structure must be installed on a functional location. Therefore, only parent assets (top-level assets that have no parent asset) can be selected on a functional location. All related child assets (sub-assets) will also be installed on the functional location. When you install assets on a functional location, the financial dimensions of the functional location might be automatically transferred to them, depending on the setup on the functional location type that is selected for the functional location. For more information about how to set up functional location types, see [Functional location types](../setup-for-functional-locations/functional-location-types.md).

> [!NOTE]
> You can set up asset types on the functional location type that is used for a functional location. In this case, when you install assets on the functional location, only parent assets that have the same asset type are shown in the list of assets that can be installed on the functional location.

After you've installed assets on a functional location, you can replace a parent asset or an asset structure as you require. As when you install assets, you select a parent asset to replace. All related child assets will also be replaced. 


## Install an asset structure on a functional location

1. Select **Asset management** \> **Functional locations** \> **All Functional locations** or **Active functional locations**.
2. Select the functional location to install an asset on.
3. Select **Install asset**.

    The **Attributes** section shows a list of the asset attribute requirements that are set up on the functional location type that is selected for the functional location. The attributes are for informational purposes only. The system doesn't validate the attributes against the asset attributes that are set up on the asset that you're installing. You must do that validation after you select an asset in the **Asset** field.

4. In the **Asset** field, select the parent asset to install. All related child assets are automatically included in the installation.

    The **Asset attributes** section to the right of the asset list shows the asset attributes that are related to the selected asset.

5. In the **Effective** field, select the date and time that the asset installation is valid from. After that date and time, costs for the asset and related sub-assets will be related to the functional location.

    > [!NOTE]
    > The asset attributes that are set up on the asset are added to the **Attributes** section. For example, the **Weight** attribute requirement has been added as a requirement on both the asset and the functional location. If the asset has attribute requirements of the same type as the functional location, the values of the asset's attribute requirements are entered in the **Value** fields. Therefore, you can validate the asset values against the attribute requirements that are set up on the functional location. The attribute requirements that are set up on the functional location are marked with a check mark.

6. Select **OK**.

    > [!NOTE]
    > To change the installation of an asset by installing it on a new functional location, follow steps 1 through 6 of this procedure. When you install an asset on a new functional location, the asset is automatically uninstalled from the previous functional location. Any active maintenance requests or work orders that were created on the asset before you installed it on a new functional location are **not** automatically transferred to the new functional location. If those maintenance requests and work orders are still required for the asset, you must manually re-create them after the asset is installed on the new location.

7. To view a list of all the assets, including sub-assets, that are installed on the functional location, select the functional location on the **All Functional locations** page, and then select **Assets**.
8. To view a list of active maintenance requests, active work orders, or fault registrations that are related to the assets that are installed on a functional location, select the functional location on the **All Functional locations** page, and then select **Requests**, **Work orders**, or **Faults**.

> [!NOTE]
> When asset-related data is changed, it's automatically updated on the functional location that the asset is installed on. This automatic update pertains to changes to maintenance requests, work orders, asset fault registrations, maintenance downtime registrations, and asset measure registrations.

## Automatically create one asset on a functional location

You can set up functional location stages and functional location types to handle the automatic creation of *one* asset on a functional location. The asset gets the same ID and name as the functional location. This functionality might be useful when you're handling maintenance on a large, static asset, such as a building.

Before you can automatically create an asset on a functional location, the following setup data must be available:

- Create a functional location type to handle the automatic creation of an asset. In the **Asset type** field, select an asset type. For more information, see [Functional location types](../setup-for-functional-locations/functional-location-types.md).
- Create a functional location lifecycle state to handle the automatic creation of an asset. Set the **Create asset** option to **Yes**. For more information, see [Functional location lifecycle states](../setup-for-functional-locations/functional-location-stages.md).

After the setup data is available, you're ready to create an asset.

1. On the **All Functional locations** page, make sure that the functional location where you want the asset to be automatically created uses the functional location type that you created for this purpose.
2. Select the functional location in the list.
3. Select **Update functional location state**, and then select the lifecycle state that you created for this purpose. One asset is now automatically installed on the functional location. This asset has the same name as the functional location.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]