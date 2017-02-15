---
# required metadata

title: Create and manage attributes
description: This article describes attributes in Microsoft Dynamics AX. Attributes let you describe a product and its characteristics through user-defined fields.
author: josaw1
manager: AnnBe
ms.date: 2015-12-04 02 - 16 - 20
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 16461
ms.assetid: f5b8252f-4716-4a6f-a5f7-73fe71a97247
ms.search.region: global
ms.search.industry: Retail
ms.author: prabhup
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Create and manage attributes

This article describes attributes in Microsoft Dynamics AX. Attributes let you describe a product and its characteristics through user-defined fields.

Attributes let you describe a product and its characteristics through user-defined fields. For example, you can specify the product's memory size and hard disk capacity, and indicate whether the product is Energy star–compliant. Attributes can be associated with various retail entities, such as product categories and retail channels, and default values can be set for them. Products inherit their attributes and the default values for those attributes when they are associated with product categories or retail channels. The default values can be overridden at the level of the individual product, at the retail channel level, or in a retail catalog.

#### Examples

Category

Attribute

Permissible values

Default value

TV & Video

Brand

Any valid **Brand** value

None

TV

Screen Size

**20"**–**80"**

None

Vertical Resolution

**480i**, **720p**, **1080i**, or **1080p**

**1080p**

Screen Refresh Rate

**60hz**, **120hz**, or **240hz**

**60hz**

HDMI Inputs

**0**–**10**

**3**

DVI Inputs

**0**–**10**

**1**

Composite Inputs

**0**–**10**

**2**

Component Inputs

**0**–**10**

**1**

LCD

3D Ready

**Yes** or **No**

**Yes**

3D Enabled

**Yes** or **No**

**No**

Plasma

Operating Temp From

**32**–**110** degrees

**32**

Operating Temp To

**32**–**110** degrees

**100**

Projection

Projection Tube Warranty

**6**, **12**, or **18** months

**12**

\# of Projection Tubes

**1**–**5**

**3**

## Attribute type
[![CreateAndManageAttribute (6)](./media/createandmanageattribute-6.png)](./media/createandmanageattribute-6.png) Attributes are based on attribute types. Attribute types identify the type of data that can be entered for a specific attribute. Currently, Microsoft Dynamics AX supports the following attribute types:

-   **Currency** – This attribute type supports currency values. It can be bounded (that is, it can support a value range), or it can be left open.
-   **DateTime** – This attribute type supports date and time values. It can be bounded (that is, it can support a value range), or it can be left open.
-   **Decimal** – This attribute type supports numerical values that include decimal places. It also supports units of measure. It can be bounded (that is, it can support a value range), or it can be left open.
-   **Integer** – This attribute type supports numerical values. It also supports units of measure. It can be bounded (that is, it can support a value range), or it can be left open.
-   **Text** – This attribute type supports text values. It also supports a predefined set of possible values (enumeration).
-   **Boolean** – This attribute type supports binary values (**true**/**false**).
-   **Reference**.

## Attribute
[![CreateAndManageAttribute (8)](./media/createandmanageattribute-8.png)](./media/createandmanageattribute-8.png) In addition to the name, friendly name, description, and Help text, one or more of the following types of information can be captured for an attribute:

-   Default value
-   Attribute metadata, such as metadata that indicates whether the attribute can be searched, refined, or sorted

## Attribute group
[![CreateAndManageAttribute (10)](./media/createandmanageattribute-10.png)](./media/createandmanageattribute-10.png) After attributes have been defined, they can be grouped into attribute groups. Attribute groups provide groupings of individual attributes, and can be assigned to retail categories or retail channels.

## Assigning attribute groups to retail categories
[![CreateAndManageAttribute (12)](./media/createandmanageattribute-12.png)](./media/createandmanageattribute-12.png) One or more attribute groups can be associated with category nodes in the retail product category hierarchy. When products have been categorized, they inherit the attributes that are included in the attribute groups.

## Assigning attribute groups to retail stores
[![CreateAndManageAttribute (13)](./media/createandmanageattribute-13-1024x576.png)](./media/createandmanageattribute-13.png) One or more attribute groups can be associated with one or more retail stores in the retail stores hierarchy. When products have been enriched for specific retail stores, they inherit the attributes that are included in the attribute groups.

## Overriding attribute values
### At the product level

[![CreateAndManageAttribute (14)](./media/createandmanageattribute-14-1024x576.png)](./media/createandmanageattribute-14.png) The default values of attributes can be overridden at the product level (that is, for individual products).

### In a retail catalog

[![CreateAndManageAttribute (2)](./media/createandmanageattribute-2.png)](./media/createandmanageattribute-2.png) The default values of attributes can be overridden for individual products in specific catalogs that are targeted for specific retail channels.

### At the retail channel level

[![CreateAndManageAttribute (1)](./media/createandmanageattribute-1.jpg)](./media/createandmanageattribute-1.jpg) The default values of attributes can be overridden for individual products in specific catalogs that are targeted for specific retail channels.

