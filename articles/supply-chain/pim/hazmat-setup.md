---
title: Set up hazardous materials
description: Learn how to set up the data that is required to classify items as hazardous materials, including an outline on hazardous material regulations.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/10/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:
---

# Set up hazardous materials

[!include [banner](../includes/banner.md)]

To use hazardous materials functionality, you must first set up the data that is required to classify items as hazardous materials. Then, when you create a sales order that includes an item that is classified as a hazardous material, the system generates hazardous material documentation for that sales order when it's shipped.

## Turn on the hazardous materials feature for your system

As of Supply Chain Management version 10.0.21, this feature is turned on by default. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable or disable it if needed. Here, the feature is listed as:

- **Module:** *Product information management*
- **Feature name:** *Hazardous materials product information and shipping documentation*

## Hazardous material regulations

To use the hazardous materials processes, you must first create a regulation. Regulations define how the printed shipping text is created for an item. They also define the associated modes of delivery.

Here are some common regulations:

- **ADR** – Regulations that are related to the international carriage of dangerous goods by road
- **CFR 49** – Regulations in the United Sates for the carriage of dangerous goods
- **IMDG** – The International Marine Dangerous Goods (IMDG) code
- **IATA** – The International Air Transport Association (IATA) dangerous goods regulations

These regulations help determine what information should be shown when you print the shipping text for an item. You can define as many regulations as you must comply with.

> [!IMPORTANT]
> The functionality for setting up information codes that are related to hazardous materials doesn't make your company compliant with regulations. It's only a tool that helps you build processes for your company.

Typically, a regulation is available for a specific mode of transport, such sea freight, road freight, or air freight. Therefore, you can associate each regulation with a mode of delivery. The mode of delivery will be used when specific documents are printed in Warehouse management. In Warehouse management, each shipment is linked to a shipping carrier and carrier service that are set up in the **Transportation** module. The mode of delivery is associated with the shipping carrier and carrier service. When you run a report, the mode of delivery is used to find the shipping print text that is associated with a released item.

This setup data isn't specific to each legal entity (company). Therefore, you can have a common set of hazardous material information that is shared among all your legal entities.

For each regulation, you can define a materials list and use it as a template list that is associated with released items. For each regulation, you can also define a print setup. A print setup lets you define how the shipping text for an item is constructed. The print setup is used to construct the shipping print text for a released item.

To set up hazardous material regulations, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material regulation**. On the **Hazardous material regulation** page, you can create any number of regulations and configure each by using the fields that are described in the following subsections.

### Hazardous material regulation header

Each regulation has a code and a description. The following table describes the fields that are available on the header.

| Field | Description |
|---|---|
| Regulation code | Enter a code to identify the hazardous material regulation record. |
| Description | Enter a description of the hazardous material regulation. |

### Print setup FastTab

Each regulation can have any number of print setups. You define the print setups on the **Print setup** FastTab. The following table describes the fields that are available for each print setup.

| Field | Description |
|---|---|
| Sequence | Define the order in which fields will be referenced in the shipping text. |
| Print field | Select the field to include in the shipping text. Not all fields for the hazardous material will be available to print. Only the common fields that are used to define shipping text in the various regulations will be available. You should define the first print field as a field separator that has a **Sequence** value of *0* (zero), so that it can be used as the separator between other fields. Only one reference to the field separator is required.<p>The following values are available:</p><ul></li><li>**Field separator** – This print field is used as the field separator for the text. Only one field separator is required in the sequence. Usually you should set the **Sequence** value for this print field to *0* (zero). The system will look for a field separator and use the first one that it finds in the list. The text value that is used in the string will come from the **Print after** field.</li><li>**Identification** – This print field puts the [identifying code and/or description](#identification) in the print text.</li><li>**Class** – This print field puts the [class code and/or description](#classes) in the print text.</li><li>**Division** – This print field puts the [division code and/or description](#divisions) in the print text.</li><li>**Packing group** – This print field puts the [packing group code and/or description](#packing-group) in the print text.</li><li>**Tunnel code and/or description** – This print field puts the [tunnel code and/or description](#tunnel) in the print text.</li><li>**Proper shipping name** – This print field puts the [proper shipping name](hazmat-items.md#hazmat-description) in the print text.</li><li>**Technical name** – This print field puts the [technical name and/or description](#technical-name) in the print text.</li><li>**Transport category** – This print field puts the [transport category code and/or description](#transport-category) in the print text.</li><li>**Stowage** – This print field puts the [stowage code and/or description](#stowage) in the print text.</li><li>**Fixed text** – This print field enters the text that is defined in the **Fixed text** field for this row.</li><li>**Label code and/or description** – This print field puts the [label code and/or description](#label) in the print text.</li><li>**Aircraft packing** – This print field puts the [aircraft packing instructions code and/or description](#packing-instruction) in the print text.</li><li>**Limited quantity** – This print field checks whether the item is marked as a [limited-quantity item](hazmat-items.md#material-management) and, if it is, enters the text that is defined in the **Fixed text** field for this row.</li><li>**Packing description** – This print field puts the [packing description](#packing-description) in the print text.</li></ul> |
| Print before | Enter the text that should be printed before the content that is defined by the **Print field** setting. |
| Print after | Enter text that should be printed after the content that is defined by the **Print field** setting. |
| Print with previous | Select this check box to prevent the field separator from being printed between the previous field and this field. Use this check box for print fields that are either optional or included with another print field. |
| Fixed text | If you set the **Print field** field to **Fixed text** or **Limited quantity**, enter the text that should be printed. |
| Include in print | Select which value or values from the selected print field should be printed for this row. You can print the code, the description, or both the code and the description. |

### Mode of delivery FastTab

The regulation is a shared table and isn't specific to each legal entity. However, modes of delivery are legal entity–specific. Therefore, when you set up a mode of delivery, you must select the relationship between the regulation, legal entity, and mode of delivery.

The following table describes the fields that are available on the **Mode of delivery** FastTab.

| Field | Description |
|---|---|
| Company | Select a legal entity to associate with this regulation. |
| Mode of delivery | Based on the legal entity that you selected, select the mode of delivery that should be associated with the regulation. |

### Country FastTab

For reference purposes, you can list the countries or regions that the regulation is relevant for. However, when shipment reports are run, only the mode of delivery is used to determine the regulation. When you review a warehouse shipment, there isn't a direct link to the mode of delivery. The shipment can be associated with a shipping carrier and carrier service. When you define a carrier service, you must associate it with a mode of delivery. This relationship will be used on shipment reports such as the bill of lading to find the shipping print text for an item.

The following table describes the field that is available on the **Country** FastTab.

| Field | Description |
|---|---|
| Country/region | Select a country/region to associate with the regulation. |

## <a name="hazmat-codes"></a>Material codes

Material codes establish settings that are related to a specific hazardous component that might be included in a released product. Each material code belongs to a specific hazardous material regulation, and its definition must conform to that regulation. When you apply a material code to a released product by using the **Material code** field, all the material code's hazardous materials settings are automatically applied to that product. Therefore, the process of setting up released products is faster and less prone to error.

To manage your hazardous material definitions, follow these steps.

1. Go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material regulation**.
2. Select the regulation to set up a hazardous material definition for.
3. On the Action Pane, on the **Setup** tab, select **Hazardous materials**.
4. In the **Material code** field, enter a material code for the hazardous material definition. You will select this value when you apply the material code to a released product.

    The **Regulation code** field is read-only and shows the regulation that you selected in step 2.

5. Use the remaining fields on this page to create and set up each hazardous material that applies to your selected regulation. The fields that are available are a subset of the hazardous material fields that are available for individual released products. Learn more in [Hazardous materials in products, orders, shipments, and loads](hazmat-items.md).

## <a name="classification-groups"></a>Hazardous material classification groups

Each hazardous material classification group defines a group of field values that establish a template. You can use this template later, when you set up hazardous material information for a released item.

When you assign the code for a hazardous material classification group to a released item, the information that is associated with that classification group will be copied into the appropriate fields of the item. Therefore, you can simplify the setup processes by establishing a set of related field values that you often use together.

This setup data isn't specific to each legal entity. Therefore, you can have a common set of hazardous material information that is shared among all your legal entities.

To set up hazardous material classification groups, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material classification group**. On the **Hazardous material classification group** page, you can create any number of groups and configure each by using the fields that are described in the following table.

| Field | Description |
|---|---|
| Group code | Enter a code to identify the group. |
| Description | Enter a description of the group. |
| Class code | Associate a hazardous material [class code](#classes) with the group. |
| Division code | Associate a hazardous material [division code](#divisions) with the group. |
| Packing group code | Associate a [packing group code](#packing-group) with the group. |
| Transport category code | Associate a [transport category code](#transport-category) with the group. |
| Multiplier | Enter the hazardous material multiplier that applies to the selected class and division of hazardous materials, according to the applicable regulation. This multiplier is used as part of the formula that calculates the total *hazardous material points* that are included in a load or shipment. For more information about hazardous material points and this multiplier, see [Material management FastTab](hazmat-items.md#material-management). |

## <a name="classes"></a>Hazardous material classes

A hazardous material class is typically mapped to the list of classes that is provided in the regulation that you're conforming to. For example, US regulation CFR 49 lists "class 3" as flammable and combustible liquids. You can set up the classes that are relevant to the materials that you must classify.

Each class will be assigned to a material setup in the materials list that is related to the regulation. You will assign a class to each released item as required, to describe the hazardous nature of a product.

This setup data isn't specific to each legal entity. Therefore, you can have a common set of hazardous material information that is shared among all your legal entities.

Hazardous material classes work together with divisions, groups, and compatibility groups in the following way:

- When you assign a hazardous material class to a released item, you must also assign a [hazardous material division](#divisions).
- You can use hazardous material classes together with [hazardous material classification groups](#classification-groups) to establish a template of codes for setting up items.
- You can use [hazardous material compatibility groups](#compatibility-groups) to establish which hazardous material classes and divisions can be shipped together.

To set up hazardous material classes, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material class**. On the **Hazardous material class** page, you can create any number of classes and configure each by using the fields that are described in the following table.

| Field | Description |
|---|---|
| Class code | Enter a code to identify this class. You define this code for the item. It will then be used in lookup lists when you assign a hazardous material class to a released item. |
| Description | Enter a description of the class. |

## <a name="divisions"></a>Hazardous material divisions

A hazardous material division is a subset of a hazardous material class. You must assign both a division and a class to every product that includes hazardous materials.

For classes that don't have any divisions, create a division where the code is *0*. For example, in the IATA regulation, class-7 radioactive materials have no subdivisions. In this case, you will create a *0* division that you can associate with a released product when you assign the class.

This setup data isn't specific to each legal entity. Therefore, you can have a common set of hazardous material information that is shared among all your legal entities.

Hazardous material divisions work together with classes, groups, and compatibility groups in the following ways:

- When you assign a hazardous material division to a released item, you must also assign a [hazardous material class](#classes).
- You can use hazardous material divisions together with [hazardous material classification groups](#classification-groups) to establish a template of codes for setting up items.
- You can use [hazardous material compatibility groups](#compatibility-groups) to establish which hazardous material classes and divisions can be shipped together.

To set up hazardous material divisions, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material division**. On the **Hazardous material division** page, you can create any number of divisions and configure each by using the fields that are described in the following table.

| Field | Description |
|---|---|
| Division | Enter a code to use as a reference number for the division. |
| Description | Enter a description of the division. |
| Class | Look up and assign the class that the division belongs to. |

## <a name="compatibility-groups"></a>Hazardous material compatibility groups

Hazardous material compatibility groups establish which hazardous material classes and divisions can be shipped together. When operators create warehouse loads or shipments, they can run a compatibility check that will issue a warning if the load or shipment includes items that don't all belong to the same compatibility group.

This setup data isn't specific to each legal entity. Therefore, you can have a common set of hazardous material information that is shared among all your legal entities.

To set up hazardous material compatibility groups, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material compatibility group**. On the **Hazardous material compatibility group** page, you can create any number of compatibility groups and configure each by using the fields that are described in the following subsections.

### Hazardous material compatibility group header

Each compatibility group has a code and a description. The following table describes the fields that are available on the header.

| Field | Description |
|---|---|
| Compatibility group | Enter a code to identify the compatibility group |
| Description | Enter a description of the compatibility group. |

### Compatibility group details

Each compatibility group establishes a list of classes and divisions of hazardous materials that can be shipped together.

| Field | Description |
|---|---|
| Class | Select a hazardous material class that is compatible with all other classes in the group. |
| Division | Select a hazardous material division that belongs to the selected class. |

## Hazardous material specification values

Microsoft Dynamics 365 Supply Chain Management provides several types of hazardous material specifications. For each type, you must establish a centralized set of values for each relevant field. Users can then select among those values when they configure hazardous material definitions or released products. Supply Chain Management provides a collection of pages where you can establish the values. Each page is dedicated to one type of specification. For a description of each available specification and information about how to establish the values that are available for it, see the following subsections.

One example of a hazardous material specification is the _stowage code_, which specifies how a given material can be stored during transport. By using the information in this section, you will establish a central collection of stowage codes. This collection will then be presented to users in a drop-down list when they set the stowage code for a released product.

These hazardous material specification values aren't specific to each legal entity, Therefore, you can have a set of common values that are shared among all your legal entities.

You will use [material codes](#hazmat-codes) to establish common collections of settings for each specification as it applies to a given regulation. You can then apply the appropriate code to each released product as required. For information about how to apply a hazardous material code to a specific released product, and how to configure individual settings of that product for any specification that is described here, see [Hazardous materials in products, orders, shipments, and loads](hazmat-items.md).

### Hazardous material emergency response

The *Hazardous material emergency response* specification indicates what should be done if something goes wrong while a product that contains a given hazardous material is being transported.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material emergency response**. On the **Hazardous material emergency response** page, you can create any number of values and configure each with a classification code and a short description.

### <a name="identification"></a>Hazardous material identification

The *Hazardous material identification* specification identifies the class or nature of a hazardous material. The value is typically a code that is based on a United Nations (UN) standard. Each class is identified by a code and a description, and it can set limits on transport methods. For example, to identify a flammable item or material, you create a hazardous material class that uses the code *FL* and the description *Flammable*. You also specify that the class must not be transported by air.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material identification**. On the **Hazardous material identification** page, you can create any number of values and configure each by using the fields that are described in the following table.

| Field | Description |
|---|---|
| Identification | Enter a code to use as a reference number that identifies this class of hazardous material. |
| Description | Enter a description of this class. |
| Restrict from air transport | Select this check box to indicate that this class of hazardous material should not be transported by air. |
| Restrict from sea transport | Select this check box to indicate that this class of hazardous material should not be transported by sea. |

### <a name="label"></a>Hazardous material label

The *Hazardous material label* specification identifies the dangerous goods label that must be applied to relevant released products. The labels themselves will describe how the product should be handled. For example, you have a product that contains a poisonous gas. In this case, you set up a label code that represents the poisonous gas label. You also build your business process so that it looks up this value when you ship products.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material label**. On the **Hazardous material label** page, you can create any number of labels and configure each with an identifying code and a short description.

### <a name="packing-description"></a>Hazardous material packing descriptions

The *Hazardous material packing descriptions* specification indicates how a hazardous item must be packed. For example, it might have to be packed in a specific type of steel drum or some other type of special packaging.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing descriptions**. On the **Hazardous material packing descriptions** page, you can create any number of packing descriptions and configure each with an identifying code and a short description.

### <a name="packing-group"></a>Hazardous material packing group

The *Hazardous material packing group* specification identifies the packing group for a hazardous item. The packing group lets you define a code and a description to indicate how hazardous material items must be packed during transportation or shipment. The packing group is assigned to the item through the **Item hazardous materials** page.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing group**. On the **Hazardous material packing group** page, you can create any number of packing groups and configure each with an identifying code and a short description.

### <a name="packing-instruction"></a>Hazardous material packing instruction

The *Hazardous material packing instruction* specification identifies packing instructions that must be followed when a given hazardous item is prepared for transportation by air.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material packing instruction**. On the **Hazardous material packing instruction** page, you can create any number of packing instruction identifiers and configure each with an identifying code and a short description.

### <a name="stowage"></a>Hazardous material stowage

The *Hazardous material stowage* specification indicates how a product must be stored on a ship when it's transported by sea freight.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material stowage**. On the **Hazardous material stowage** page, you can create any number of stowage identifiers and configure each with an identifying code and a short description.

### <a name="transport-category"></a>Hazardous material transport category

The *Hazardous material transport category* specification is typically used to group similar hazardous products on reports. For example, transport categories are used on the **Shipment summary** report, which you can print from the warehouse shipment record.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material transport category**. On the **Hazardous material transport category** page, you can create any number of transport categories and configure each with a display name and a short description.

### <a name="technical-name"></a>Hazardous material technical name

The *Hazardous material technical name* specification can be used to provide a commonly used or internal company name that describes each material.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material technical name**. On the **Hazardous material technical name** page, you can create any number of technical names and configure each with a display name and a short description.

### <a name="tunnel"></a>Hazardous material tunnel

The *Hazardous material tunnel* specification limits the types of tunnels that a hazardous material can be transported through by identifying the types of tunnels that must be used. Tunnel categories are established by applicable regulations for hazardous material transport. This specification usually applies only to road transport.

To set up values for this specification, go to **Product information management \> Setup \> Hazardous material shipping documentation \> Hazardous material tunnel**. On the **Hazardous material tunnel** page, you can create any number of tunnel identifiers and configure each with an identifying code and a short description.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]