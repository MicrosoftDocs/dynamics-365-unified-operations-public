---
# required metadata

title: Address setup
description: This topic describes setting up address formats for the global address book.
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
ms.author: jaredha
ms.search.validFrom: 2021-09-23
ms.dyn365.ops.version: AX 7.0.0

---

# Address setup

[!include [banner](../includes/banner.md)]

Global regions in which your organization operates may have different address format types. You must have the ability to adjust to the appropriate address format when displaying a postal address for each region. You can use the **Address setup** form to set up the postal address formats required for your organization.

## Define address parameters
Use the **Parameters** section of the **Address setup** form to define which fields must be validated when creating addresses in the application. You may select to require validation for **ZIP/postal code**, **District**, and **City** values. If, for each respective option, the option is not selected to validate the field, then no validation occurs for that field when creating new addresses in the global address book. The field is a free-text field in which the user can enter any value. If the option is selected to validate the respective field, then the value entered in the field when creating a new address in the global address book must be a value already created in address setup. 

For example, if the **City** option is selected under **Validate on creating addresses** section, then when creating a new address in the global address book, the **City** value entered for the new address must be selected from the list of cities set up in the **City** section of the **Address setup** form.

## Set up address formats
Use this section of the form to enter and set up address component information and formatting. As you enter address information for a selected address type, the **Preview** field in the upper-right pane displays how the address will appear.

1. In the **Address setup** form, select **Address format** in the left pane.
2. In the action ribbon of the pane, select **New** to add a new address format type.
3. Enter the address format type name and a brief description. For example, you might enter "NO" in the **Address format** field and enter "Norway" in the **Description** field.
4. In the lower pane, click **New** to configure a new address component for the address format type that is selected in the upper pane.
5. In the **Address application object** field, select the first object that must appear when an address for this format is displayed. For example, **Street**.
6. In the **Separator** field, enter the character that should separate this object from the next object when the address is displayed. For example, a comma.
7. Select the check boxes to indicate the following:
  - **New line** - Display this object on a new line.
  - **Data entry only** - Display this object only when entering the address. If this check box is selected, the object will not be displayed when the address is printed.
  - **Not active** - Do not use this object in an address for the selected format type.
  - **Expand** - Display the name of the country/region, state, or county instead of the assigned code.
  - **Special** - Indicates that the field countains the same separator characters.

## Set up country/region information
Use the **Country/region** section of the form to define country/region information for address setup.

1. In the **Address setup** form, select **Country/region** in the left pane.
2. Click **New** to create a new line.
3. Enter the code, a short name, and the full name of the country/region. For example, "DEU", "Germany", and "Federal Republic of Germany".
4. Select the address format, as defined on the **Address format** section of the form, to be used for the country/region. 
5. In the **Time zone** field, select the time zone of the country/region.
6. Enter the ISO code for the country/region.
7. If required for your financial, purchasing, or sales transactions, enter the **BACEN code**, **IOR facility ID**, **Code by OKSM**, and select whether the country/region is a member of customs union.
8. Select the **Use ZIP + 4 postal code validation rules** toggle to enable only valid 5-digit or 9-digit ZIP/postal codes.

## Set up state/province information
Use the **State/province** section of the form to define state/province information for address setup.

1. In the **Address setup** form, select **State/province** in the left pane.
2. In the **Country/region** filter, select the country/region for which you will be adding a state/province.
3. Select the **New** action to create a new line.
4. Enter the state/province code and the name of the state/province.
5. Select the time zone for the state/province.
6. Define the state code for the state/province, and any additional codes required for transactional information.
7. Select the **Default state/province** toggle to define whether the state/province will be the default for the selected country/region. The state/province that is selected as the default state/province will be the default value entered in state/province fields when a new county or city record is created.

## Set up county information
Use the following procedure to add county information to any existing country/regions or state/provinces.

1. In the **Address setup** form, select **County** in the left pane.
2. Click **New** to create a new line.
3. In the **Country/region** field, select the country/region in which the county is located.
4. In the **State or province** field, select the state where the county is located.
5. Enter the name and a brief description of the county.

## Set up city information
Use the following procedure to add city information to any existing countyr/regions or state/provinces.

1. In the **Address setup** form, select **City** in the left pane.
2. Click **New** to create a new line.
3. In the **Country/region** field, select the country/region to which you are adding the city information.
4. Enter the name of the city and a brief description.
5. Select the state or county where the city is located.

## Set up district information

1. In the **Address setup** form, select **District** in the left pane.
2. Use the filters to select the **Country/region**, **State/province**, **County**, and **City**, as appropriate, in which the district is located.
3. Click **New** to create a new line.
4. Enter the name of the district and a brief description.

## Set up ZIP/postal code information

1. In the **Address setup** form, select **ZIP/postal codes** in the left pane.
2. Use the filter to select the **Country/region** location for the ZIP/postal code.
3. Click **New** to create a new line.
4. Enter the ZIP/postal code and select the corresponding city.
5. Enter the street name, where the ZIP/postal code is effective.
6. Enter the lowest and highest street numbers that use the ZIP/postal code, and enter the number types. For example, the ZIP/postal code may apply only to odd numbered street addresses.
7. Select the **State/province**, **County**, **District**, and **Time zone** for the ZIP/postal code.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
