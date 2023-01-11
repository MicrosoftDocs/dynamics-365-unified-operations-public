---
# required metadata

title: Maintenance attribute types
description: This article explains how to create attribute types in Asset Management. 
author: johanhoffmann
ms.date: 06/24/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetFunctionalLocationTypeCopy, EntAssetAttributeType, EntAssetAttributeTypeValue, EntAssetFunctionalLocationType
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

# Maintenance attribute types

[!include [banner](../../includes/banner.md)]

 

This article explains how to create attribute types in Asset Management. Attributes are used to describe the properties of various elements. You can set up attributes on the following elements:

- [Functional location types](../setup-for-functional-locations/functional-location-types.md)
- [Create functional locations](../functional-locations/create-functional-locations.md)
- [Asset types](../setup-for-objects/object-types.md)
- Assets

The attributes that you can set up vary, depending on the element. For example, for a functional location, you can set up attributes for the configuration and physical size of the location. For an asset type or an asset, you can set up attributes for engine volume, power consumption, and maximum load capacity under different conditions.

## Create attribute types

You can create your own attribute types. Additionally, you can transfer product dimensions to the **Attribute types** page.

1. Select **Asset management** \> **Setup** \> **Attribute types**.
2. The first time that you set up attribute types, select **Create product dimensions** to automatically transfer standard product dimensions.
3. Select **New** to create a new attribute type.
4. In the **Attribute type** field, enter a name for the attribute type.
5. In the **Description** field, enter a description.
6. In the **Unit** field, select the relevant attribute unit, as required.
7. In the **Data type** field, select a data type for the unit.
8. If you selected **String** as the data type, follow these steps to create values for the attribute type:

    1. Select the attribute type, and then select **Values**.
    2. In the **Attribute values** field, select **New**.
    3. In the **Attribute type** field, select an attribute type (dimension).
    4. In the **Value** field, enter a related value.
    5. In the **Description** field, enter a description.
    6. Save the record.
    7. Return to the **Attribute types** page.

9. Save the record.

    The **Functional location types** field shows the number of functional locations that are using the attribute type. The **Asset types** field shows the number of asset types that are using it.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]