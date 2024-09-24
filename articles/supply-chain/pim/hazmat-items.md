---
title: Hazardous materials in products, orders, shipments, and loads
description: Learn how to set hazardous material properties for released products and how to include hazardous materials in a sales order, shipment, or load.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/10/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:
---

# Hazardous materials in products, orders, shipments, and loads

[!include [banner](../includes/banner.md)]

This article explains how to set hazardous material properties for released products, how to put stock limits on hazardous items, and how to include hazardous materials in a sales order, shipment, or load.

## Set hazardous material specifications for products

After you've defined a hazardous material regulation and set up the related reference codes as described in [Set up hazardous materials](hazmat-setup.md), you can associate this information with released items. The shipping text for shipping documents will be drawn from the hazardous materials information for the released items.

As part of the process of associating a released item with a hazardous material, you must specify the regulation code and the material. Different regulation codes might be associated with an item, depending on the modes of transport, and you can associate multiple regulations and material codes with each item.

To set up a released product as a hazardous material, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select or create a product to open its **Released product details** page.
1. On the **Manage inventory** FastTab, set the **Hazardous material** option to **Yes**. This setting identifies the item as a dangerous good and is used when shipping documentation is printed.
1. On the Action Pane, on the **Manage inventory** tab, in the **Compliance** group, select **Item hazardous material**.
1. Fill in the **Item hazardous materials** page for the selected item by using the fields that are described in the following subsections.

### Item hazardous materials header

The following table describes the fields that are available at the top of the **Item hazardous materials** page.

| Field | Description |
|---|---|
| Item number | The released product that you're working with. |
| Regulation code | Select the hazardous material regulation that applies to the product. The regulation defines how the printed shipping text is created for an item and the associated modes of delivery. After it's assigned, the code can't be edited on this page. However, you can assign a new regulation code by selecting **New**. |
| Material code | (Optional) Select the hazardous material code that applies to the product. The material code provides a template that includes default values for many other fields on this page. When you select a code, all its hazardous materials specifications will be copied to the current product. However, the system first prompts you to confirm that item material data should be filled in from the material code. |
| Group code | (Optional) Select the hazardous material classification group code that applies to the product. As for the **Material code** field, when you select a code, all its hazardous materials specifications will be copied to the current product. However, the system first prompts you to confirm that item class group data should be filled in from the group code. |

### <a name="hazmat-description"></a>Descriptions FastTab

The following table describes the fields that are available on the **Descriptions** FastTab.

| Field | Description |
|---|---|
| Proper shipping name | Enter the standard description for the material, as specified by the applicable regulation. You can provide translations for this value on the **Item ship text translation** FastTab, as described in the next section. |
| Technical name | Select the common or generic name for the material. This name might be a name that your company uses internally for the material. |
| N.O.S. | Select this check box to indicate that the **Proper shipping name** value is a not-otherwise-specific (N.O.S.) shipping name for the item. N.O.S. shipping names are used for groups of similar chemicals and materials that have specific end uses, but that might not be listed by name in the hazmat table in a specific regulation. |

### Item ship text translation FastTab

The **Item ship text translation** FastTab contains a grid that shows translations of the **Proper shipping name** values that are defined for the primary language on the **Descriptions** FastTab. These translations can be used in shipping print text for one or more additional languages.

The following table describes the fields that are available on the **Item ship text translation** FastTab.


| Field | Description |
|---|---|
| Language | The language code that the row uses. For example, **pt-br** indicates Brazilian Portuguese. |
| Shipping print text | The translated **Proper shipping name** value in the language that the row uses. |

To add or edit a translation, select **Translations** above the grid to open **Text translations** page. Then follow one of these steps:

- To add a new translation, on the Action Pane, select **Add**. Select the language to add, and then, in the **Translated text** field, enter the translated text.
- To edit an existing translation, select a target language in the **Language** field, and edit the translated text in the **Translated text** field, as required.

### <a name="material-management"></a>Material management FastTab

The following table describes the fields that are available on the **Material management** FastTab.

| Field | Description |
|---|---|
| Class | Select the hazardous material class that the product belongs to, as defined by the regulation that you're conforming to. You must assign both a division and a class to every product that includes hazardous materials. |
| Description | The description that is defined for the class that is selected in the **Class** field. This field is read-only. |
| Division | Select the hazardous material division that the product belongs to, as defined by the regulation that you're conforming to. The division is a subset of the class. You must assign both a division and a class to every product that includes hazardous materials. |
| Identification | Select the hazardous material identification code. Typically, this code is based on a United Nations (UN) standard. |
| Packing group | Select the packing group that applies to the current item. |
| Description | The description that is defined for the group that selected in the **Packing group** field. This field is read-only. |
| Packing Descriptions | Select the applicable packing description code. This code references a description that indicates how the product must be packed. |
| Hazardous material labels | Select a code that references the applicable dangerous goods label that should be applied to the product. |
| Limited quantity | Set this option to **Yes** to report the total product weight that is included in each load and on each load line. |
| Quantity | Enter the quantity of hazardous material in the product, in the specified unit. This value will be used to calculate the total hazardous material score for loads and shipments that include the product. |
| Multiplier | Enter the multiplier that is applied when the hazardous material score is calculated for each load line that includes the product. This value is specified by the applicable regulation, according to the type of hazardous material that is contained in the product. |
| Unit | Select the unit of measure that applies to the quantity of hazardous material in the product, as specified in the **Quantity** field. This value will be used to calculate the total hazardous material score for loads and shipments that include the product. |

#### How the hazardous material score is calculated

Several of the values that are specified on the **Material management** FastTab for a product are used to calculate a *hazardous material score* for each load line that includes that product. The score is calculated by using the following formula:

Hazardous material score = *&lt;LineQty&gt;* × *&lt;HazmatQty&gt;* × *&lt;UnitConversion&gt;* × *&lt;Multiplier&gt;*

Here is a key to the formula:

- *&lt;LineQty&gt;* is the quantity of product that is specified for a load line.
- *&lt;HazmatQty&gt;* is the quantity of hazardous material that is specified for a product in the **Quantity** field on the **Material management** FastTab.
- *&lt;UnitConversion&gt;* is a conversion factor for converting between the unit that is used for the load line quantity and the unit that is specified for a product in the **Unit** field on the **Material management** FastTab.
- *&lt;Multiplier&gt;* is the multiplier that is specified for a product in the **Multiplier** field on the **Material management** FastTab.

This score is reported for each load line that contains a product where these values are specified. Learn more in the [Shipments that include hazardous materials](#hazmat-shipments) and [Loads that include hazardous materials](#hazmat-loads) sections later in this article.

#### How the hazardous material weight is calculated

Loads and load lines that contain products where the **Limited quantity** option on the **Material management** FastTab is set to **Yes** will show the total hazardous material weight, as described in the [Shipments that include hazardous materials](#hazmat-shipments) and [Loads that include hazardous materials](#hazmat-loads) sections later in this article. The hazardous material weight is calculated by using the following formula:

Hazardous material weight = *&lt;LineQty&gt;* × *&lt;ProductWeight&gt;* × *&lt;UnitConversion&gt;*

Here is a key to the formula:

- *&lt;LineQty&gt;* is the quantity of product that is specified for a load line.
- *&lt;ProductWeight&gt;* is the net weight that is specified for the product, in the inventory unit that is specified for the product.
- *&lt;UnitConversion&gt;* is a conversion factor for converting between the unit that is used for the load line quantity and the inventory unit that is used for *&lt;ProductWeight&gt;*.

### Transport information FastTab

The following table describes the fields that are available on the **Transport information** FastTab.

| Field | Description |
|---|---|
| Transport category | Select the related transport category. |
| Tunnel Code | Select the related tunnel restriction code for the item. |
| Hazardous material stowage | Select the reference code that is used for sea freight stowage handling when the item is shipped by sea freight. |
| Aircraft type | Select the aircraft restriction that applies for the material when it's shipped by air freight. |
| Packing - cargo aircraft only | Based on the value that you selected in the **Aircraft type** field, select the packing instructions code that applies when the product can be shipped only by cargo aircraft. |
| Packing - passenger and cargo aircraft | Based on the value that you selected in the **Aircraft type** field, select the packing instructions code that applies when the product can be shipped by either cargo aircraft or passenger aircraft. |
| IATA Star | Set this option to **Yes** to indicate that the air transport specifications that are entered on this FastTab are related to the International Air Transport Association (IATA) dangerous goods standard. This field is for informational purposes only. |
| Emergence response | Select the code that references instructions for handling the material in an emergency. |

### Environmental information FastTab

The following table describes the fields that are available on the **Environmental information** FastTab.

| Field | Description |
|---|---|
| Environmentally dangerous | Set this option to **Yes** to indicate that the product is environmentally dangerous. Use this field for your own reporting purposes. |
| Marine pollutant | Set this option to **Yes** to indicate that the product is a marine pollutant. Use this field for your own reporting purposes. |

## <a name="stock-limits"></a>Set stock limits for hazardous products

For safety reasons, you might have to limit the total amount of a given product that can be stocked at a single location. To set stock limits for a released product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select a product to open its **Released product details** page.
1. On the Action Pane, on the **Manage inventory** tab, in the **Compliance** group, select **Reporting details**.
1. In the **Hazardous stock limit** and **Hazardous warning limit** fields, set appropriate values for the selected product.

The **Hazardous material stock limit** report lets you monitor the stock levels of the hazardous materials in your warehouse locations, to make sure that they remain under the safe limits that are established here. Learn more in [Hazardous material stock limit report](hazmat-reports.md#stock-limit-report).

## Sales order transactions that include hazardous materials

To include a product that is classified as a hazardous material on a sales order, you must associate the relevant shipping carrier with the sales order. Open the sales order, and then, on the **Delivery** FastTab, set the **Shipping carrier** and **Carrier service** fields as required.

The shipping carrier is also associated with the mode of delivery. Therefore, you must make sure that this information is aligned with the hazardous material regulation. In other words, the mode of delivery that is specified in the hazardous material regulation must match the specifications on the sales order header. In this way, the regulation, shipping carrier, and service are connected to the shipment lines that are used on a sales order.

After a sales order is finalized and ready to be shipped, it can be released to the warehouse to indicate the transfer between sales and warehouse operations.

## <a name="hazmat-shipments"></a>Shipments that include hazardous materials

### View hazardous material scores for each shipment line

The **Shipment details** page for a shipment shows the total hazardous material weight and point values that have been calculated for each load line that is included in that shipment. To view the scores and weights, follow these steps.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Select a shipment to open its **Shipment details** page.
1. On the **Load lines** FastTab, inspect the lines. For each line, you will see the hazardous material calculations in the following fields:

    - **Hazardous material points** – This field shows the hazardous material score for the load line. The value is calculated according to the rules and values that have been established for the applicable regulation and in the released product setup. The calculation takes the quantity on the load line and references the multiplier in the [material management setup](#material-management) for the released product.
    - **Limited quantity net weight** – For products that are marked as limited-quantity products because of their hazardous material content, this field shows the total net weight of hazardous content that is included on the load line. The calculation is based on the products that are marked as hazardous materials in the released product setup. If an item is marked as a limited-quantity item, the calculation takes the quantity on each load line and references the weight in the [material management setup](#material-management) for the released product.

### Check for compatibility among hazardous materials that are included in a shipment

The system can evaluate whether all the hazardous materials that are included in a shipment are suitable to be shipped together. To evaluate compatibility, the system checks the compatibility group that is assigned to each product that is included in the shipment. Learn more in [Hazardous material compatibility groups](hazmat-setup.md#compatibility-groups).

To run the compatibility check, follow these steps.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Select a shipment to open its **Shipment details** page.
1. On the Action Pane, on the **Shipments** tab, in the **Actions** group, select **Compatibility check**.

You receive a message that informs you of the results of the check.

## <a name="hazmat-loads"></a>Loads that include hazardous materials

### View hazardous material scores for each load line

The **Load details** page for a load shows the total hazardous material weight and point values that have been calculated for that load and for each load line. To view the scores and weights, follow these steps.

1. Go to **Warehouse management \> Shipments \> All loads**.
1. Select a load to open its **Load details** page. (You can also open load details by selecting a link from a related shipment.)
1. On the **Load** FastTab, you can review the total hazardous material scores and weights for the whole load by inspecting the following fields:

    - **Hazardous material points** – This field shows the hazardous material score for the load. The value is calculated according to the rules and values that have been established for the applicable regulation and in the released product setup. The calculation takes the quantity that is included in the load and references the multiplier in the [material management setup](#material-management) for the released product.
    - **Limited quantity net weight** – For products that are marked as limited-quantity products because of their hazardous material content, this field shows the total net weight of hazardous content that is included in the load. The calculation is based on the products that are marked as hazardous materials in the released product setup. If an item is marked as a limited-quantity item, the calculation takes the quantity in each load and references the weight in the [material management setup](#material-management) for the released product.

1. To review the scores and weights for individual lines, select the **Load lines** FastTab. The values that are provided for each line resemble the values that are provided for the whole load, as described in the previous step.

### Check for compatibility among hazardous materials that are included in a load

The system can evaluate whether all the hazardous materials that are included in a load are suitable to be shipped together. To evaluate compatibility, the system checks the compatibility group that is assigned to each product that is included in the load. Learn more in [Hazardous material compatibility groups](hazmat-setup.md#compatibility-groups).

To run the compatibility check, follow these steps.

1. Go to **Warehouse management \> Shipments \> All loads**.
1. Select a shipment to open its **Load details** page. (You can also open load details by selecting a link from a related shipment.)
1. On the Action Pane, on the **Loads** tab, in the **Actions** group, select **Compatibility check**.

You receive a message that informs you of the results of the check.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]