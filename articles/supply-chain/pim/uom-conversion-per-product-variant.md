---
# required metadata

title: Unit of measure conversion per product variant
description: This topic explains how to set up unit of measure conversions for product variants. It includes an example of the setup.
author: johanhoffmann
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: UnitOfMeasureConversion
ROBOTS: noindex, nofollow
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: 10.0

---

# Unit of measure conversion per product variant

[!include [banner](../includes/banner.md)]

This topic explains how to set up unit of measure conversions for various product variants.

You can use product variants to create variations of a product instead of creating several individual products that must be maintained. A product variant could, for example, be a T-shirt of a given size and color. Previously, it was only possible to set up the unit conversion on the product master, which meant that all product variants had the same unit conversion rules. With this feature, if your T-shirts are sold in boxes, and the number of t-shirts that can be packed in a box depends on the size of the t-shirts, you can now set up unit conversions between the different shirt sizes and the boxes used for packaging.

## Enable the feature on your system

If you don't already see this feature on your system, go to [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and enable the *Unit of measure conversions for product variants* feature.

## Set up a product for unit conversion per variant

Product variants can only be created for products that are **Product masters**. For more information, see [Create a product master](tasks/create-product-master.md). The feature is not enabled for products that are set up for catch weight processes.

To configure a product master to support unit conversion per variant:

1. Go to **Product information management > Products > Product masters**.
1. Create or open a product master to go to its **Product details** page.
1. Set **Enable unit of measure conversions** to *Yes*.
1. Open the **Product** tab on the action pane and then select **Set up > Unit conversions**.
1. Select **Unit conversions** on the action pane to open the **Unit conversions** page.
1. The **Unit conversions** page opens. Select one of the following tabs:
    - **Intra-class conversions** - <!-- KFM what is this? Why would I pick this? -->
    - **Inter-class conversions** - <!-- KFM what is this? Why would I pick this? -->
1. Select **New** to add a new unit conversion. Then set **Create conversion for** to one of the following:
    - **Product** - Lets you set up a unit conversion for the product master. This unit conversion will will serve as fallback for all product variants that don't have a unit conversion defined.
    - **Product variant** - Lets you select the specific variant that you want to set a unit conversion for. Use the **Product variant** field to choose the variant.

    ![Add a new unit conversion](media/uom-new-conversion.png "Add a new unit conversion")

1. Use the other fields provided here to set up your unit conversion. <!-- KFM: Is this sufficient? Do we have a topic we can link to for these details? -->
1. Select **OK** to save the conversion.

> [!TIP]
> You can open the **Unit conversions** settings in the context of a product or a product variant from any of the following pages:
> 
> - **Product details**
> - **Released products details**
> - **Released product variants**

## Example scenario

In this scenario, a company is selling T-shirts in sizes small, medium, large, and extra-large. The T-shirt is defined as a product, and the different sizes are defined as variants of that product. The shirts are packed in boxes and there can be five shirts in a box, except for the extra-large size, where there is only space for four shirts. The company wants to track the different variants of the T-shirts in the unit *Pieces*, but is selling them in the unit *Boxes*. The conversion between the inventory unit and the sales unit is 1 Box = 5 Pieces, except for the variant extra-large, where the conversion is 1 Box = 4 Pieces.

1. First, open the **Unit conversion** page from the **Release product details** page for **T-shirt.**

1. On the **Unit conversion** page, set up the unit conversion for the release product variant X-Large:

    | **Field**             | **Setting**             |
    |-----------------------|-------------------------|
    | Create conversion for | Product variant         |
    | Product variant       | T-Shirt : : X-Large : : |
    | From unit             | Boxes                   |
    | Factor                | 4                       |
    | To Unit               | Pieces                  |

1. The variants small, medium, and large all have the same unit conversion between the units box and pieces, which means that you can define the unit conversion for these product variants on the product master.

    | **Field**             | **Setting** |
    |-----------------------|-------------|
    | Create conversion for | Product     |
    | Product               | T-Shirt     |
    | From unit             | Boxes       |
    | Factor                | 5           |
    | To Unit               | Pieces      |

## Using Excel to update the unit conversions

If a product has many product variants with different unit conversions, it's a good idea to export the unit conversions to an Excel spreadsheet, update the conversions, and then publish them back to Supply Chain Management.

To export to Excel, go to the **Unit conversion** page and select **Open in Microsoft office** on the action pane.,
