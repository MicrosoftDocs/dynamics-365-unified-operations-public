---
# required metadata

title: Address setup
description: This topic describes how to set up address formats for the global address book.
author: jaredha
ms.date: 09/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirPartyTable, DirPartyTableRoles
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-09-23
ms.dyn365.ops.version: AX 7.0.0

---

# Address setup

[!include [banner](../includes/banner.md)]

Global regions where your organization operates might have different address format types. You must be able to adjust to the appropriate address format when a postal address is shown for each region. You can use the **Address setup** page to set up the postal address formats that are required for your organization.

## Define address parameters

The **Parameters** tab of the **Address setup** page defines which fields must be validated when addresses are created. You can select options to require validation for **ZIP/postal code**, **District**, and **City** values.

If the option that corresponds to a field isn't selected, no validation is done for that field when new addresses are created in the global address book. In this case, the field is a free-text field where users can enter any value. If the option that corresponds to a field is selected, validation is done for that field when new addresses are created in the global address book. In this case, the value that is entered in the field must have been previously created in the address setup.

For example, the **City** option is selected in the **Validate on creating addresses** section. In this case, when a new address is created in the global address book, the **City** value for the new address must be selected in the list of cities that is set up in the **City** section of the **Address setup** page.

## Set up address formats

You can set up address component information and formatting on the **Address format** tab. As you enter address information for a selected address type, the **Preview** field in the upper-right pane shows how the address will appear.

1. On the **Address setup** page, on the **Address format** tab, select **New** to add a new address format type.
2. Enter the name of the address format type and a brief description. For example, you might enter **NO** in the **Address format** field and **Norway** in the **Description** field.
3. In the lower pane, select **New** to configure a new address component for the address format type that is selected in the upper pane.
4. In the **Address application object** field, select the first object that must appear when an address in this format is shown. For example, select **Street**.
5. In the **Separator** field, enter the character that is used to separate this object from the next object when an address in this format is shown. For example, enter a comma (**,**).
6. Set the following checkboxes as appropriate:

    - **New line** – Select this checkbox if the object should appear on a new line.
    - **Data entry only** – Select this checkbox if the object should be shown only when the address is entered. If this checkbox is selected, the object won't be shown when the address is printed.
    - **Not active** – Select this checkbox if the object should not be used in an address of the selected format type.
    - **Expand** – Select this checkbox to show the full name of the country/region, state/province, or county instead of the code when the address is printed.
    - **Special** – Select this checkbox if the field value contains the character that you specified as a separator.

## Set up country/region information

Use the **Country/region** tab to define the country/region information for the address setup.

1. On the **Address setup** page, on the **Country/region** tab, select **New** to create a new line.
2. Enter the country/region code, a short name for country/region, and the full name. For example, enter **DEU**, **Germany**, and **Federal Republic of Germany**, respectively.
3. In the **Address format** field, select an address format to use for the country/region. The address formats that are defined on the **Address format** tab of the page are available for selection. 
4. In the **Time zone** field, select the time zone of the country/region.
5. Enter the International Organization for Standardization (ISO) code for the country/region.
6. In the **BACEN code**, **IOR facility ID**, and **Code by OKSM** fields, enter values if they are required for your financial, purchasing, or sales transactions. Also select whether the country/region is a member of the customs union.
7. To enable only valid five-digit or nine-digit ZIP/postal codes, select the **Use ZIP + 4 postal code validation rules** option.

## Set up state/province information

Use the **State/province** tab to define the state/province information for the address setup.

1. On the **Address setup** page, on the **State/province** tab, in the **Country/region** filter, select the country/region that you're adding the state/province information to.
2. Select **New** to create a new line.
3. Enter the state/province code and the name of the state/province.
4. Select the time zone for the state/province.
5. Enter the IT state code for the state/province, and any additional codes that are required for transactional information.
6. To define the state/province as the default state/province for the selected country/region, select the **Default state/province** option. The default state/province will be entered by default in state/province fields when a new county or city record is created.

## Set up county information

Use the following procedure to add county information to any existing countries/regions or states/provinces.

1. On the **Address setup** page, on the **County** tab, select **New** to create a new line.
2. In the **Country/region** field, select the country/region where the county is located.
3. In the **State or province** field, select the state/province where the county is located.
4. Enter the name of the county and a brief description.

## Set up city information

Use the following procedure to add city information to any existing countries/regions or states/provinces.

1. On the **Address setup** page, on the **City** tab, select **New** to create a new line.
2. In the **Country/region** field, select the country/region that you're adding the city information to.
3. Enter the name of the city and a brief description.
4. Select the state/province or county where the city is located.

## Set up district information

1. On the **Address setup** page, on the **District** tab, use the filters to select the country/region, state/province, county, and city, as appropriate, where the district is located.
2. Select **New** to create a new line.
3. Enter the name of the district and a brief description.

## Set up ZIP/postal code information

1. On the **Address setup** page, on the **ZIP/postal codes** tab, use the filter to select the country/region for the ZIP/postal code.
2. Select **New** to create a new line.
3. Enter the ZIP/postal code, and select the corresponding city.
4. Enter the street name that the ZIP/postal code applies to.
5. Enter the lowest and highest street numbers that use the ZIP/postal code, and enter the number types. For example, the ZIP/postal code might apply only to odd-numbered street addresses.
6. Select the state/province, county, district, and time zone for the ZIP/postal code.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
