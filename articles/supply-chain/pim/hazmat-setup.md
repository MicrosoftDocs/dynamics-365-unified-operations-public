---
# required metadata

title: Set up hazardous materials
description: To use hazardous materials functionality, you must first set up the data required to classify items as hazardous materials. When you create a sales order that includes an item classified as a hazardous material, the system generates hazardous material documentation for that sales order when it is shipped.
author: dasani-madipalli
manager: tfehr
ms.date: 06/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  HMIMStowageList, HMIMTunnelList, HMIMItemMatieralList, HMIMLabelList, HMIMRegulationList, HMIMCompatibilityGroupList, HMIMClassGroupList, HMIMDivisionList, HMIMIdentificationList, HMIMPackingInstructionList, HMIMItemList, HMIMTransportCategoryList, HMIMEMSList, HMIMRegPrintSetupList, 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Release 10.0.11
---

# Set up hazardous materials

[!include [banner](../includes/banner.md)]

To use hazardous materials functionality, you must first set up the data required to classify items as hazardous materials. When you create a sales order that includes an item classified as a hazardous material, the system generates hazardous material documentation for that sales order when it is shipped.

## Turn on the hazardous material feature for your system

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Product information management*
- **Feature name:** *Hazardous materials product information and shipping documentation*

## Hazardous material regulations

To use the hazardous materials processes, you must first create a regulation. The regulation defines how the printed shipping text is created for an item and the associated the delivery methods.

Common regulations include:

- **ADR** - Regulations concerning the international carriage of dangerous goods by road,
- **CFR 49** - Regulations in the United Sates for carriage of dangerous goods
- **IMDG** - International Marine Dangerous Goods code
- **IATA** - International Air Transport System

These regulations help determine what information you should display when you print the shipping text for an item. If you need other regulations, then you can define as many regulations as you need to comply with.

> [!IMPORTANT]
> The functionality for setting up information codes related to hazardous materials doesn't make your company compliant with regulations. It is only a tool that helps you build processes for your company.

Typically, a regulation is available for a specific mode of transport, such sea freight, road freight, or air freight. Therefore, you can associate each regulation with a mode of delivery. The mode of delivery will be used when certain documents are printed in warehouse management. In warehouse management, each shipment is linked to a shipping carrier and service set up in the transportation module, and the mode of delivery is associated with the shipping carrier and service. When you run a report, the mode of delivery is used to locate the shipping print text that is associated with a released item.

This setup data is not specific to each legal entity, so you can have a common set of hazardous material information that is shared among all your legal entities.

Each regulation allows you to define a materials list that you can use as a template list to associate with released items.

You can define a print setup for each regulation, which allows you to define how the shipping text for an item is constructed. The print setup will be used on the released item to construct the shipping print text.

To set up hazardous material regulations, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material regulation**. From here, you can create any number of regulations and configure each of them using the settings described in the following subsections.

### Hazardous material regulation header

Each regulation has a code and description. The following table describes the settings available in the header.

| Setting | Description |
| --- | --- |
| **Regulation code** | Identifies the hazardous material regulations record. |
| **Description** | Describes the hazardous material regulation. |

### Print setup

Each regulation can have any number of print setups, which you must define on the **Print setup** FastTab. The following table describes the settings available for each print setup.

| Setting | Description |
| --- | --- |
| **Sequence** | Defines the order in which fields will be referenced in the shipping text. |
| **Print&nbsp;field** | Defines the field you wish to include in the shipping text. Not all fields on the material will be available to print here, just the common ones used in the various regulations for defining shipping text. You should define the first print field as sequence zero (0) to be the field separator. You only need one reference to the field separator that will be used between the fields.<p>The following values are available for **Print** field:</p><ul></li><li>**Field separator** - This represents the field separator to use for the text. There only needs to be one field separator in the sequence. Usually you should put this at sequence 0. The system will look for a field separator and use the first one in the list. The text value used in the string will come from the **Print after** field. </li><li>**Identification** - Places the [identification code and/or description](#identification) in the print text. </li><li>**Class** - Places the [class code and/or description](#classes) in the print text. </li><li>**Division** - Places the [division code and/or description](#divisions) in the print text. </li><li>**Packing group** - Places the [packing group code and/or description](#packing-group) in the print text. </li><li>**Tunnel code and/or description** - Places the [tunnel code and/or description](#tunnel) in the print text. </li><li>**Proper shipping name** - Places the [proper shipping name](hazmat-items.md#hazmat-description) in the print text.</li><li>**Technical name** - Places the [technical name and/or description](#technical-name) in the print text. </li><li>**Transport category** - Places the [transport category code and/or description](#transport-category) in the print text. </li><li>**Stowage** - Places the [stowage code and/or description](#stowage) in the print text.</li><li>**Fixed text** - Enter the text defined in the **Fixed text** field for this row. </li><li>**Label code and/or description** - Places the [label code and/or description](#label) in the print text. </li><li>**Aircraft packing** - Used to print the [aircraft packing instructions code and/or description](#packing-instruction) in the print text. </li><li>**Limited quantity** - Checks whether the item is marked as [limited quantity](hazmat-items.md#material-management) and, if so, it places the text defined in the **Fixed text** field for this row. </li><li>**Packing description** - Places the [packing description](#packing-description) in the print text.</li></ul> |
| **Print&nbsp;before** | Enter text to be printed before the content defined by the **Print field** setting. |
| **Print&nbsp;after** | Enter text to be printed after the content defined by the **Print field** setting.  |
| **Print with previous** | Select this check box to prevent printing the **Field separator** between the previous field and this one. Use this for print fields that are either optional or included with another print field. |
| **Fixed text** | If you set the **Print field** to **Fixed text** or **Limited quantity**, then enter the text to be printed here. |
| **Include in print** | Choose which value(s) from the selected **Print field** to print for this row. You can print the **Code**, **Description** or both (**Code & Description**). |

### Mode of delivery

The regulation is a shared table and isn't specific to each company (legal entity). However, the **Mode of delivery** is company-specific, so when you're setting up a mode of delivery, you must select the relationship between the regulation, company, and mode of delivery.

The following table describes the settings provided in the **Mode of delivery** FastTab.

| Setting | Description |
| --- | --- |
| **Company** | Select a company (legal entity) to associate with this regulation. |
| **Mode of delivery** | Based on the company that you have selected, look up the mode of delivery to associate with the regulation. |

### Country

For reference purposes, you can list the countries that this regulation is relevant for, but only the mode of delivery is used for determining the regulation when shipment reports are run. When reviewing a warehouse shipment, there isn't a direct link to the mode of delivery. The shipment can be associated with a shipping carrier and a carrier service. When you define a carrier service, it must be associated with a mode of delivery. This relationship will be used on shipment reports such as the bill of lading to locate the shipping print text for an item.

The following table describes the settings provided in the **Country** FastTab.

| Setting | Description |
| --- | --- |
| **Country/region** | Select a country/region to associate with the regulation. |

<a name="hazmat-codes"></a>

## Material codes

Material codes establish settings related to a specific hazardous component that could be included in a released product. Each material code belongs to specific hazardous material regulation and must be defined in conformity with that regulation. When you apply a hazardous material code to a released product (using its **Material code** setting), all of its hazardous materials settings are automatically applied to that product, which makes the process of setting up each released product faster and less error prone.

To manage your hazardous material definitions:

1. Go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material regulation**.
2. Select the regulation for which you want to set up a hazardous material definition.
3. On the Action Pane, open the **Setup** tab and select **Hazardous materials**.
4. Enter a **Material code** for the hazardous material definitions. This is the value you will select when you apply the material to a released product. The **Regulation code** is read-only and shows the regulation you selected previously.
5. Use the rest of settings on this page to create and set up each of the hazardous materials that apply for your selected regulation. The settings offered here are a subset of the hazardous material settings offered for individual released products; see [Hazardous materials in products, orders, shipments, and loads](hazmat-items.md) for details.

<a name="classification-groups"></a>

## Hazardous material classification groups

Each hazardous material classification group defines a group of field values that establish a template that you can use later when you set up hazardous material information for a released item.

When you assign a group code to a released item, the information associated with the classification group will be copied into the respective fields of that item. This lets you simplify the setup processes by establishing a set of related field values that you often use together.

This setup data is not specific to each legal entity, so you can have a common set of hazardous material information that is shared among all your legal entities.

To set up hazardous material classification groups, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material classification group**. From here, you can create any number of groups and configure each of them using the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Group code** | A code to be used to identify this group. |
| **Description** | Enter a description to describe the group. |
| **Class code** | Associate a hazardous material [class code](#classes). |
| **Division code** | Associate a hazardous material [division code](#divisions). |
| **Packing group code** | Associate a [packing group code](#packing-group). |
| **Transport category code** | Associate a [transport category code](#transport-category). |
| **Multiplier** | Enter the hazardous material multiplier that applies for this class and division of hazardous materials according to the applicable regulation. This multiplier is used as part of the formula for calculating the total *hazardous material points* included in a load or shipment. For more information about hazardous material points and this multiplier, see [Material management FastTab](hazmat-items.md#material-management) |

<a name="classes"></a>

## Hazardous material classes

A hazardous material class is a type of hazardous material that typically maps to the list of classes provided in the regulation that you are conforming to. For example, the US regulation 49 CFR lists "class 3" as flammable and combustible liquids. You can set up the classes that are relevant to the materials you need to classify.

Each class will be assigned to a material setup on the materials list related to the regulation. You will assign a class to each released item as needed so you can describe the hazardous nature of a product.

This setup data is not specific to each legal entity, so you can have a common set of hazardous material information that is shared among all your legal entities.

Hazardous material classes work together with divisions, groups, and compatibility groups as follows:

- When assigning a hazardous material class to a released item, you must also assign a [hazardous material division](#divisions).
- You can use hazardous material classes together with [hazardous material classification groups](#classification-groups) to establish a template of codes for setting up items.
- You can use [hazardous material compatibility groups](#compatibility-groups) to establish which hazardous material classes and divisions can be shipped together.

To set up hazardous material classes, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material class**. From here, you can create any number of classes and configure each of them using the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Class code** | A code to be used to define this class. This will be a code you define for the item to be used in lookup lists when assigning to a released item. |
| **Description** | Enter a description to describe the class. |

<a name="divisions"></a>

## Hazardous material divisions

A hazardous material division is a subset of a hazardous material class. You must assign both a division and class to each product that includes hazardous materials.

For classes that don't have any divisions, create a division of 0. For example, in the IATA regulation lists Class 7 Radioactive materials as having no subdivisions. In this case, you will create a 0 division to associate with a released product when assigning the class.

This setup data is not specific to each legal entity, so you can have a common set of hazardous material information that is shared among all your legal entities.

Hazardous material divisions work together with classes, groups, and compatibility groups as follows:

- When assigning a hazardous material division to a released item, you must also assign a [hazardous material class](#classes).
- You can use hazardous material divisions together with [hazardous material classification groups](#classification-groups) to establish a template of codes for setting up items.
- You can use [hazardous material compatibility groups](#compatibility-groups) to establish which hazardous material classes and divisions can be shipped together.

To set up hazardous material divisions, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material division**. From here, you can create any number of divisions and configure each of them using the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Division** | Enter a code to use as a reference number for this division. |
| **Description** | Enter a description of division. |
| **Class** | Look up and assign the class that this division belongs to. |

<a name="compatibility-groups"></a>

## Hazardous material compatibility groups

Hazardous material compatibility groups establish which hazardous material classes and divisions can be shipped together. When operators create warehouse loads or shipments, they can run a compatibility check that will provide a warning if the load or shipment includes items that are not included in the same compatibility group as one another.

This setup data is not specific to each legal entity, so you can have a common set of hazardous material information that is shared among all your legal entities.

To set up hazardous material compatibility groups, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material compatibility group**. From here, you can create any number of compatibility groups and configure each of them using the settings described in the following subsections.

### Hazardous material compatibility group header

Each compatibility group has a code and description. The following table describes the settings available in the header.

| Setting | Description |
| --- | --- |
| **Compatibility group** | A code that identifies this compatibility group |
| **Description** | Enter a description of the compatibility group. |

### Compatibility group details

Each compatibility group establishes a list of classes and divisions of hazardous materials that can be shipped together.

| Setting | Description |
| --- | --- |
| **Class** | Select a hazardous material class that is compatible with all other classes in this group. |
| **Division** | Select a hazardous material division that belongs to the selected class. |

## Hazardous material specification values

Dynamics 365 Supply Chain Management provides several types of hazardous material specifications. For each of these, you must establish a centralized set of values among which users can choose for each relevant field when configuring hazardous materials definitions and/or released products. Supply Chain Management provides a collection of pages where you can establish these values, with one page dedicated to a specify type of specification. See the following subsections for a description of each available specification and how to establish the values available for it.

One example of a hazardous material specification is its _stowage code_, which specifies how a given material can be stored during transport. Using the settings described in this section, you'll be able to establish a central collection of stowage codes, which will be presented to users in a drop-down list when setting the stowage code for a released product.

These hazardous material specification values aren't specific to each legal entity, so you can have a set of common values that are shared among all your legal entities.

Use [material codes](#hazmat-codes) to establish common collection of settings for each of these specifications as they apply to a given regulation. You can then apply the appropriate code to each released product as needed. For details about how to apply a hazardous material code to a specific released product, and how to make individual settings on that product for any of the specifications described here, see [Hazardous materials in products, orders, shipments, and loads](hazmat-items.md).

### Hazardous material emergency response

This specification identifies what to do if something goes wrong while transporting a product with a given hazardous material.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material emergency response**. From here, you can create any number of values and configure each of them with a classification code and a short description.

<a name="identification"></a>

### Hazardous material identification

This specification identifies the class or nature of a hazardous material. This is typically a code that is based on a United Nations (UN) standard. Each classification is identified using a code and a description, and can set limitations on transport methods. For example, you might create a hazardous material classification that uses the code "FL" and the description "Flammable" to identify a flammable item or material, and may also specify that it must not be transported by air.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material identification**. From here, you can create any number of values and configure each of them using the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Identification** | Enter a code to use as a reference number that identifies this class of hazardous material. |
| **Description** | Enter a description of this hazardous material classification. |
| **Restrict from air transport** | Mark this check box to indicate that this type of material should not be transported by air. |
| **Restrict from sea transport** | Mark this check box to indicate that this type of material should not be transported by sea. |

<a name="label"></a>

### Hazardous material label

This specification identifies the dangerous goods label that must be applied to relevant released products. The labels themselves will describe how the product should be handled. For example, you might have a product that contains a poison gas. You would therefore set up a label code that represents that poison gas label and build your business process to look up this value when you ship.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material label**. From here, you can create any number of labels and configure each of them with an identifying code and a short description.

<a name="packing-description"></a>

### Hazardous material packing descriptions

This specification identifies how a hazardous item must be packed. For example, if it needs to be packed in a specific type of steel drum or some other type of special packaging.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing descriptions**. From here, you can create any number of packing descriptions and configure each of them with an identifying code and a short description.

<a name="packing-group"></a>

### Hazardous material packing group

This specification identifies the packing group for a hazardous item. The packing group lets you define a code and description for how hazardous material items need to be packed during transportation or shipment. The packing group is assigned to the item through the Item hazardous materials form.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing group**. From here, you can create any number of packing groups and configure each of them with an identifying code and a short description.

<a name="packing-instruction"></a>

### Hazardous material packing instruction

This specification identifies packing instructions that must be followed when preparing a given hazardous item for transportation by air.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing instruction**. From here, you can create any number of packing instruction identifiers and configure each of them with an identifying code and a short description.

<a name="stowage"></a>

### Hazardous material stowage

This specification identifies how a product must be stored on a ship when it is transported by sea freight.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material stowage**. From here, you can create any number of stowage identifiers and configure each of them with an identifying code and a short description.

<a name="transport-category"></a>

### Hazardous material transport category

Hazardous material transport categories are typically used in reports to group similar hazardous products together. For example, this is used in the _Shipment summary_ report, which you can print from the warehouse shipment record.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material transport category**. From here, you can create any number of transport categories and configure each of them with a display name and a short description.

<a name="technical-name"></a>

### Hazardous material technical name

Hazardous material technical names provide common names to describe each material. You can use them to provide a commonly used or internal company name to describe the material.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material technical name**. From here, you can create any number of technical names and configure each of them with a display name and a short description.

<a name="tunnel"></a>

### Hazardous material tunnel

This specification restricts the types of tunnels that a hazardous material can be transported through by specifying which types of tunnels must be used. Tunnel categories are established by applicable hazardous material transport regulations. This normally applies only to road transport.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material tunnel**. From here, you can create any number of tunnel identifiers and configure each of them with an identifying code and a short description.
