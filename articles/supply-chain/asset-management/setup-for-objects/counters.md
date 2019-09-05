---
# required metadata

title: Asset measures
description: The topic explains how to create asset measure types in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset measures

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

The topic explains how to create asset measure types in Asset Management. Asset measure types are used to make measurement registrations on assets, for example, regarding number of production hours, or quantity produced on the asset. Asset types are related to the asset measure types. This means that an asset measure can only be used on an asset if the asset measure is set up on the asset type used on the asset.

Before you can make measurement registrations on assets, you first create the asset measure types you want to use in **Counters**. Next, you can create measurement registrations on assets in **Asset measures**. 

Asset measures can be used on maintenance plans. A maintenance plan line can be of type "Counter", for example, relating to number of production hours or quantity produced. 

An asset measurement registration can be updated manually or automatically based on production hours or quantity produced. An asset measure can be set up to use one of three update methods (selected in the **Update** field in **Counters**):
  
- Manual - you must manually register asset measurement values.  
- Production hours - the counter is automatically updated based on number of production hours.  
- Production quantity - the counter is automatically updated based on number of quantity produced.  

>[!NOTE]
>If quantity produced is used, *all* registered items are included in the measurement registration, good quantity as well as error quantity. It is always possible to make manual asset measurement registrations, if required.

## Create counter types for asset counter registrations

1. Select **Asset management** > **Setup** > **Asset types** > **Counters**.
2. Select **New** to create a new asset measure type.
3. Insert an ID in the **Counter** field, and a counter name in the **Name** field.
4. On the **General** FastTab, select a measurement unit in the **Unit** field.
5. In the **Update** field, select the update method to be used for the asset measure.
6. Select "Yes" on the **Inherit counter values** toggle button if child assets in an asset structure should automatically inherit asset measure registrations made on the parent asset.
7. In the **Total aggregate** field, select the summation method to be used for an asset measure using this asset measure type. "Sum" is the standard selection used to continuously add registered values to the total value. "Average" can be used if an asset measure is set up to monitor a threshold, for example, regarding temperature, vibrations, or wear and tear on an asset. 
8. In the **Deviation over** field, insert the upper level in percent for validating if manual asset measure registrations are within an expected range. The validation is based on a linear increase in existing asset measure registrations.
9. In the **Deviation under** field, insert the lower level in percent for validating if manual asset measure registrations are within an expected range. The validation is based on a linear decrease in existing asset measure registrations.
10. In the **Type** field, select the type of message (information, warning, error) to be shown if deviations outside the defined range occur when you make manual asset measure registrations.
11. On the **Asset types** FastTab, add the asset types that should be able to use the asset measure.
12. On the **Related asset measures** FastTab, add the asset measures that you want to be automatically updated when this asset measure is updated.


>[!NOTE]
>A related asset measure is automatically updated only if the related asset measure has the asset type, to which it is related, in the asset measure setup. For example: You set up an asset measure for "Production hours" and add the asset type "Truck Engine". When that asset measure is updated, a related counter "Oil" is also updated with the same asset measure values. The setup in **Counters** includes the setup on "Hours". Also, on the "Oil" asset measure, the asset type "Truck Engine" should be added to the **Asset types** FastTab to ensure the asset measure relation. See the screenshots below for an example of the setup on the Hours and Oil asset measures.

When asset types are added to an asset measure type in **Counters**, that asset measure is automatically added to the asset types on the **Counters** FastTab in [Asset types](../setup-for-objects/object-types.md).

![Figure 1](media/071-setup-for-objects.png)


