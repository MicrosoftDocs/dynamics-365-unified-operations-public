---
title: Apply country/region context
description: Learn about how to apply country/region context to meet localization and translation requirements, including a table that defines various elements.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/10/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d02eee15-bbeb-4e0f-a59f-0313da9334da
---

# Apply country/region context

[!include [banner](../includes/banner.md)]

To meet the requirements for Lifecycle Services solutions for localization and translation, localization ISV solution providers must implement all country/region specific functionality so that country/region context controls it. This article describes how to apply country/region context to meet these requirements. In this article, you can find information about how you should use the country/region context property and what application objects control user interface elements.

## Country/Region specific functionality

Use country/region-specific functionality to help meet the legal, regulatory, and business requirements of individual geographies. A geography is any country or region that the International Organization for Standardization (ISO) identifies by a country or region code. The following table highlights the main elements that you use to configure country/region-specific functionality.

| Element | Description |
|---------|-------------|
| Controlled entity | The controlled entity is a UI element that is hidden or shown, depending on whether its country/region context matches the country/region context of the controlling entity. To enable menus, menu items, and form controls that are based on country/region context to be hidden, a controlled entity includes a **CountryRegionCodes** property on some elements. Use this property to specify the country or region where the element is shown. You find the **CountryRegionCodes** property on the following Application Object Tree (AOT) elements:<ul><li>Extended data type</li><li>Menu and menu items</li><li>Enum and enum value</li><li>Table and table field</li><li>Data entity and data entity field</li><li>View and view field</li><li>Map and map field</li><li>Form control</li><li>Tile</li></ul> |
| Controlling party | The controlling party's role is used to determine whether country/region-specific functionality or UI elements are enabled. The Organization model defines the controlling party. Examples include legal entity, customer, vendor, bank, or worker. By default, the legal entity is used as the controlling party. If the country/region context of the controlling party matches the country/region context of the controlled entity, the functionality or UI elements are enabled. You set the country/region context of the controlling party. Any controlled entities that have a matching country/region context are shown. |

## Using the CountryRegionCodes property

You create country/region context on a controlled entity by setting the ISO code value on the **CountryRegionCodes** property. You can find the list of ISO country and region codes on the [ISO website](https://www.iso.org/iso/country_codes/iso_3166_code_lists/country_names_and_code_elements.htm). The values of the **CountryRegionCodes** property are compared to the country/region context of the controlling party. If the values match, the element is shown. Otherwise, it's hidden.

> [!TIP]
> To add more than one ISO country and region code to the **CountryRegionCodes** property, use a comma-separated list.

## Using the legal entity as the controlling party

The **Country/region** value in the primary address of the legal entity determines the country/region context of the controlling party. The default value of the **Country/region** field is the locale of the system. The following illustration shows how to set the primary address of the legal entity. 

:::image type="content" source="./media/le_edit_address.jpg" alt-text="Screenshot of the legal entity edit address interface showing the primary address settings.":::

## Setting another party as the controlling party

You can use another party, such as a customer, bank, or vendor, as a controlling party. For example, you can enable targeted functionality for customers of a specific country or region, or require specific validation of vendors from a specific country or region. To set the controlling party, use the **CountryRegionContextField** property of the form, control, or other element. This property lets you select the entity that is the controlling party. The default value is the legal entity. The following illustration shows how to set the **CountryRegionContextField** property for a field. 

:::image type="content" source="./media/de_countryregioncontextfield.jpg" alt-text="Screenshot of the CountryRegionContextField property configuration for a field.":::

## Additional resources

[ISO codes](https://www.iso.org/iso/country_codes/iso_3166_code_lists/country_names_and_code_elements.htm)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
