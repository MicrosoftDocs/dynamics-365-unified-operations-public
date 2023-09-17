---
# required metadata

title: Product configuration models overview
description: This article defines terms and concepts that are relevant to product configuration models. Product configuration models let you build a generic product structure that can be used to configure many product variants for a single product.
author: t-benebo
ms.date: 06/20/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata


ms.search.form: PCProductConfigurationModelDetails, PCProductConfigurationModelListPage, PCModalWaitDialog, PCTemplateConfigurationManager, PCConfigurationUIGrouping
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: ["4031"]
ms.collection: get-started
ms.assetid: 70b968e8-e550-4731-823d-d713b8910f7b
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Product configuration models overview

[!include [banner](../includes/banner.md)]

This article defines terms and concepts that are relevant to product configuration models. Product configuration models let you build a generic product structure that can be used to configure many product variants for a single product.

Product configuration models are created to represent a generic product structure. After you've set up a product configuration model, you can configure a distinct product variant that has a unique bill of materials (BOM) and a unique route. Product configuration models use both declarative constraints and imperative calculations to handle the relations and limitations between different product variants. You can configure items on sales orders, sales quotations, purchase orders, and production orders. The following table describes the table constraint–based terms and concepts.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Components</td>
<td>Components are the main building blocks of a product configuration model. Components are displayed in a tree structure on the <strong>Constraint-based product configuration model details</strong> page. Components can contain the following elements:
<ul>
<li>Attributes</li>
<li>Constraints</li>
<li>Calculations</li>
<li>Subcomponents</li>
<li>User requirements</li>
<li>BOM lines</li>
<li>Route operations</li>
</ul></td>
</tr>
<tr class="even">
<td>Attributes</td>
<td>Attributes describe all the features of the product configuration model. You can use attributes to specify the features that can be selected when a distinct product is configured. Attributes are used in constraints and conditions. When attributes are created and added to a product configuration model, the related attribute types are referenced. A default value can be set for an attribute. The default value is used in the configuration user interface (UI) when the product configuration model is configured. You can specify that an attribute is mandatory, read-only, or hidden.
<ul>
<li><strong>Mandatory</strong> – A value must be set for the attribute when the product is configured.</li>
<li><strong>Read-only</strong> – The attribute value is displayed during a configuration session, but it can&#39;t be changed.</li>
<li><strong>Hidden</strong> – The attribute value is included in constraints and conditions, but isn&#39;t displayed during a configuration session.</li>
</ul>
You can also specify a condition for attributes. If the condition is met, a value must be entered for the mandatory attribute. Conditions are expressions that must be met for attributes, BOM lines, and route operations to be included in a product configuration model. Any attribute that is referenced in a condition becomes mandatory. We recommend that you select attributes as mandatory on the <strong>Attributes</strong> tab. This can make it easier to identify mandatory attributes. Attribute values are an important part of reusing configurations. The system uses attribute values to determine whether a configuration exists that matches the selections that a user made during a configuration session.</td>
</tr>
<tr class="odd">
<td>Attribute types</td>
<td>Attribute types specify the set of data types for attributes that are used in a product configuration model. The following attribute types are used:
<ul>
<li><strong>Integer</strong> with or without a range</li>
<li><strong>Decimal</strong></li>
<li><strong>Text</strong> with or without a fixed list</li>
<li><strong>Boolean</strong></li>
</ul>
If the attribute type is <strong>Boolean</strong>, <strong>Integer</strong> with a range, or <strong>Text</strong> with a fixed list, the set of values is available when a product configuration model is set up. <strong>Note:</strong> The Product configuration solver recognizes only the following attribute types: <strong>Boolean</strong>, <strong>Text</strong> with a fixed list, and <strong>Integer</strong> with a range. Therefore, only these attribute types can be used in expression constraints and conditions.</td>
</tr>
<tr class="even">
<td>Constraints</td>
<td>Constraints describe the restrictions of the product model configuration. Constraints are used to guarantee that only valid values are selected when a product is being configured. Constraints can be either expression constraints or table constraints:
<ul>
<li>Expression constraints can be used only for the component that they are tied to. The expression constraints for a component can reference attributes of the component&#39;s subcomponents. The Product configuration solver is used to solve the constraints, and you must use the solver syntax when you write the constraints. For more information, see the article link about expression constraints and table constraints.</li>
<li>Table constraints must be defined before they can be applied to a component in a product configuration model. Table constraints can be either user-defined or system-defined. A user-defined table constraint is a type of matrix that can be used to describe the set of combinations for the attribute values that are defined by attribute types. For example, if speakers are produced, the matrix for a user-defined table constraint might have columns for the speaker finish and grill.</li>
</ul>
<strong>Example</strong> Speakers are available in four finishes: Black, Oak, Rosewood, and White. The speakers can have one of three front grills: Black, Metal, or White. The Black finish is available for all grills, but the other finishes are limited to specific grills. The following table shows an example of the information that is displayed on the <strong>Allowed combinations</strong> tab on the <strong>Edit table constraint</strong> page.
<table>
<thead>
<tr class="header">
<th>Cabinet finish</th>
<th>Front grill</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Black</td>
<td>Black</td>
</tr>
<tr class="even">
<td>Black</td>
<td>Metal</td>
</tr>
<tr class="odd">
<td>Black</td>
<td>White</td>
</tr>
<tr class="even">
<td>Oak</td>
<td>Black</td>
</tr>
<tr class="odd">
<td>Rosewood</td>
<td>White</td>
</tr>
<tr class="even">
<td>White</td>
<td>Black</td>
</tr>
<tr class="odd">
<td>White</td>
<td>White</td>
</tr>
</tbody>
</table>
A system-defined table constraint represents a mapping between an attribute type and a field in a Supply Chain Management table. A system-defined table constraint dynamically links the attribute type to the field. The link enables the attribute in a product configuration model to reflect the data of the field in the Supply Chain Management table.</td>
</tr>
<tr class="odd">
<td>Calculations</td>
<td>Calculations represent a supplement to constraints. You can use a calculation to perform arithmetic operations on attributes of the <strong>Decimal</strong> and <strong>Integer</strong> types, or logical operations that involve attributes of the <strong>Text</strong> with a fixed list and <strong>Boolean</strong> types. A calculation has a target attribute that will hold the result of the calculation expression. The calculation expression is built by using the expression editor.</td>
</tr>
<tr class="even">
<td>Subcomponents</td>
<td>Subcomponents reflect the tree structure of the product configuration model. You can use subcomponents to build the structure of the product configuration model. Subcomponents reference existing components. Therefore, subcomponents encourage the reuse of components in multiple product configuration models. On the <strong>BOM line details</strong> page for a subcomponent, you can select a distinct value for the subcomponent. Alternatively, you can select an attribute that the value is selected for when the product configuration model is set up. To include a product as a component or subcomponent, you must specify the following information on the <strong>Create product</strong> page when you create the product:
<ul>
<li>In the <strong>Product type</strong> field, select <strong>Item</strong>.</li>
<li>In the <strong>Product subtype</strong> field, select <strong>Product master</strong>.</li>
<li>In the <strong>Configuration technology</strong> field, select <strong>Constraint-based configuration</strong>.</li>
</ul>
You can view whether a released product can be used as a component or subcomponent on the <strong>General</strong> tab of the <strong>Released product details</strong> page. If <strong>Constraint-based configuration</strong> is selected in the <strong>Configuration technology</strong> field, the product can be used as a component or subcomponent. You can hide subcomponents so that they aren&#39;t displayed to the user during a configuration session. Attributes, subcomponents, and user requirements that are related to the subcomponent are also hidden.</td>
</tr>
<tr class="odd">
<td>User requirements</td>
<td>User requirements represent an abstraction between user requirements and specific components and attributes. You can&#39;t map a user requirement to an item. For example, a customer is shopping for a home theater system. The sales representative might ask about the size of the room where the customer plans to install the system, to determine how many watts are required. In this example, the room size can be a user requirement that helps determine the appropriate attribute value for a specific component. You can hide user requirements so that they aren&#39;t displayed to the user during a configuration session. Attributes, subcomponents, and user requirements that are related to the user requirement are also hidden. You can write a condition to control whether a user requirement can be hidden. You must write the condition by using Optimization Modeling Language (OML) syntax.</td>
</tr>
<tr class="even">
<td>BOM lines</td>
<td>BOM lines represent the individual materials of the components in the product configuration model. On the <strong>BOM line details</strong> page, all items are available for selection. A condition can be added to the BOM line, so that the BOM lines that are selected for a distinct product variant can vary, based on the user&#39;s selection when the product configuration model is set up. Conditions are expressions that must be met for attributes, BOM lines, and route operations to be included in a product configuration model. On the <strong>BOM line details</strong> page, you can select a distinct value. Alternatively, you can map to an attribute that the value is selected for when the product configuration model is set up.</td>
</tr>
<tr class="odd">
<td>Route operations</td>
<td>On the <strong>Route operation details</strong> page, you can select a distinct value. Alternatively, you can map to an attribute that the value is selected for when the product configuration model is set up. Conditions are written like expression constraints. Conditions are expressions that must be met for attributes, BOM lines, and route operations to be included in a product configuration model.</td>
</tr>
</tbody>
</table>







[!INCLUDE[footer-include](../../includes/footer-banner.md)]