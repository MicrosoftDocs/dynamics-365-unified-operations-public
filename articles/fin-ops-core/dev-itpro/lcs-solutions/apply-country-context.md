---
title: Apply country/region context
description: This article provides information about how to apply country/region context to meet localization and translation requirements.
author: sericks007
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d02eee15-bbeb-4e0f-a59f-0313da9334da
---

# Apply country/region context

[!include [banner](../includes/banner.md)]

As part of the requirements for LCS solutions for localization and translation, localization ISV solution providers must implement all country-specific or region-specific functionality so that it can be controlled by country/region context. This article describes how to apply country/region context to meet these requirements. In this article you can find information how you should use country context property and what application objects control user interface elements.

## Country/region-specific functionality

You use country/region-specific functionality to help meet the legal, regulatory, and business requirements of individual geographies. A geography is any country or region that is identified by an International Organization for Standardization (ISO) country or region code. The following table highlights the main elements that you use to configure country/region-specific functionality.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Controlled entity</td>
<td>The controlled entity is a UI element that is hidden or shown, depending on whether its country/region context matches the country/region context of the controlling entity. To enable menus, menu items, and form controls that are based on country/region context to be hidden, a controlled entity includes a <strong>CountryRegionCodes</strong> property on some elements. You use this property to specify the country or region where the element is shown. You find the <strong>CountryRegionCodes</strong> property on the following Application Object Tree (AOT) elements:
<ul>
<li>Extended data type</li>
<li>Menu and menu items</li>
<li>Enum and enum value</li>
<li>Table and table field</li>
<li>Data entity and data entity field</li>
<li>View and view field</li>
<li>Map and map field</li>
<li>Form control</li>
<li>Tile</li>
</ul></td>
</tr>
<tr class="even">
<td>Controlling party</td>
<td>The controlling party’s role is used to determine whether country/region-specific functionality or UI elements are enabled. The controlling party is defined by the Organization model. Examples include legal entity, customer, vendor, bank, or worker. By default, the legal entity is used as the controlling party. If the country/region context of the controlling party matches the country/region context of the controlled entity, the functionality or UI elements are enabled. You set the country/region context of the controlling party. Any controlled entities that have a matching country/region context are shown.</td>
</tr>
</tbody>
</table>

## Using the CountryRegionCodes property
You create country/region context on a controlled entity by setting the ISO code value on the **CountryRegionCodes** property. You can find the list of ISO country and region codes on the [ISO website](https://www.iso.org/iso/country_codes/iso_3166_code_lists/country_names_and_code_elements.htm). The values of the **CountryRegionCodes** property are compared to the country/region context of the controlling party. If the values match, the element is shown. Otherwise, it's hidden.

> [!TIP]
> To add more than one ISO country and region code to the **CountryRegionCodes** property, use a comma-separated list.

## Using the legal entity as the controlling party
The **Country/region** value in the primary address of the legal entity determines the country/region context of the controlling party. The default value of the **Country/region** field is the locale of the system. The following illustration shows how to set the primary address of the legal entity. [![LE\_Edit\_address.](./media/le_edit_address-1024x570.jpg)](./media/le_edit_address.jpg)

## Setting another party as the controlling party
You can use another party, such as a customer, bank, or vendor, as a controlling party. For example, you can enable targeted functionality for customers of a specific country/region or require specific validation of vendors from a specific country/region. To set the controlling party, use the **CountryRegionContextField** property of the form, control, or other element. This property lets you select the entity that is the controlling party. The default value is the legal entity. The following illustration shows how to set the **CountryRegionContextField** property for a field. 
[![DE\_CountryRegionContextField.](./media/de_countryregioncontextfield.jpg)](./media/de_countryregioncontextfield.jpg) 

In this example, the customer becomes the controlling entity. The customer's address is compared with the value of the **CountryRegionCodes** field to determine whether the **GermanSpecifcSetting** field is displayed.

## Additional resources

[ISO codes](https://www.iso.org/iso/country_codes/iso_3166_code_lists/country_names_and_code_elements.htm)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
