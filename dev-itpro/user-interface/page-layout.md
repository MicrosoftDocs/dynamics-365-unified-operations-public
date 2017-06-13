---
# required metadata

title: Layout
description: This article discusses layout in the web client. Layout is a design process that specifies how controls appear on a page. 
author: jasongre
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 28251
ms.assetid: 1cfa479c-71fa-4eb6-8d12-ad4d65c8ecf3
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Layout

[!include[banner](../includes/banner.md)]


This article discusses layout in the web client. Layout is a design process that specifies how controls appear on a page. 

Introduction
------------

Layout is a design process that specifies how the controls on a page appear in the web client. Layout occurs within container controls. The following table lists the container controls.

| Container   | Description                                                                                                                                            |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Form.Design | The root of the page. It functions as a special kind of container.                                                                                     |
| Group       | The general-purpose container control. Group controls can be nested as required.                                                                       |
| Tab         | A control that contains TabPage controls and has many possible **Tab.Style** values, such as **Tab**, **FastTab**, **Vertical Tab**, and **Panorama**. |
| TabPage     | The appearance of each TabPage control depends on its **Tab.Style** value.                                                                             |
| ButtonGroup | A special type of Group control that contains buttons.                                                                                                 |

A grid is a special type of control that has some container behaviors, such as flexible sizing (**SizeToAvailable**). However, a grid has special visualizations and isn't a general-purpose container control.

## Layout: Dynamics AX 2012 vs. Microsoft Dynamics 365 for Finance and Operations, Enterprise edition
### Layout in Dynamics AX 2012

In Microsoft Dynamics AX 2012, the arrangement of controls in containers is almost always vertical, and columns are manually set to provide some horizontal spread.

### Examples

**Columns**=**1** 1 2 3 **Columns**=**2** 1 4 2 5 3 In Dynamics AX 2012, sizing is achieved via the **Height** and **Width** properties. If **Height** and **Width** are set to **Auto**, the size is as large as the child controls require. If **Height** and **Width** are set to **Column**, the container is as large as it can be within the parent container. By default, **Height** and **Width** are set to **Auto** for every container.

### Layout in Finance and Operations

In Finance and Operations, layout is controlled by the same basic properties that control layout in Dynamics AX 2012. However, additional options have been added to support a more responsive layout. In particular, the layout of a page is based on the following factors:

-   The arrangement method that is specified by the **ArrangeMethod** property.
-   The columns that are specified by the **Columns** property.
-   The sizing that is specified by the **HeightMode**, **WidthMode**, **Height**, and **Width** properties.

## ArrangeMethod property
The **ArrangeMethod** property specifies a base arrangement method for a container. In Finance and Operations, the old values were maintained. Additionally, a new property that is named **HorizontalWrap** was added primarily for panoramas, especially for tile layouts. The following table describes the various options for the **ArrangeMethod** property.

| Option          | Description                                                                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vertical        | Controls are arranged vertically. If columns is also used, controls are arranged vertically inside of the generated columns. This option is the default value for Groups and TabPages (where **Tab.Style** isn't set to **Panorama**). |
| HorizontalLeft  | Controls are arranged horizontally and are left-aligned inside the parent container.                                                                                                                                                   |
| HorizontalRight | Controls are arranged horizontally and are right-aligned inside the parent container.                                                                                                                                                  |
| HorizontalWrap  | Controls are arranged inside columns of fixed width that wrap horizontally. This option is typically used for tile layouts in panorama sections. This option is the default value for TabPages (where **Tab.Style**=**Panorama**).     |

## ColumnsMode property
In Finance and Operations, a new **Fill** option was added to support responsive layouts. When this property value is set, columns automatically flow as required. The following table describes the various options for the **ColumnsMode** property.

| Option | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fill   | Columns are generated to fill the available horizontal space or vertical space, depending on the container type. If the container is a Panorama-style tab, **Columns**=**Fill** generates columns to fill along the vertical axis. For all other containers (Group, Tab-style tabs, and all other styles of tabs), **Columns**=**Fill** generates columns to fill along the horizontal axis. |
| Fixed  | Specify the number of columns that the **Columns** property should generate. Controls are evenly distributed among the columns, and their order is maintained. If the controls can't be distributed evenly among the columns, the leftmost columns receive extra controls first. This option is the default value for all controls.                                                          |

## HeightMode/WidthMode properties
In Finance and Operations, sizing is still accomplished via the size properties **WidthMode**+**Width** and **HeightMode**+**Height**. The following table described the various options for these properties.

| Option          | Description                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SizeToAvailable | Fill the available space along the vertical (or horizontal) axis inside the parent container. If the parent container has **SizeToContent** height (or width), the child's height (or width) is also **SizeToContent**, unless there is a sibling in the container that can provide a height (or width). This option is the default value for Grids and Tabs (of all styles). |
| SizeToContent   | The height (or width) of the container should be the height (or width) of its contents. This option is the default value for Groups and all other controls except Tabs.  FastTabs that aren't always expanded also have **SizeToContent** height.                                                                                                                             |
| Manual          | The height (or width) is sized manually. Use **HeightMode**=**Manual** (or **WidthMode**=**Manual**), and set **Height** (or **Width**) to a fixed number of pixels. **Note:** We recommend that you not use manual heights (and widths), because they don't adapt to changes in form density.                                                                                |

Note that, currently, **Auto** still exists as an option. If this value is used, the behavior is determined automatically at run time. Typically, a value of **Auto** for these properties causes the same behavior as a value of **SizeToContent**, as in Dynamics AX 2012.

## Interactions between the ArrangeMethod and Columns properties
If **ArrangeMethod**=**HorizontalLeft** or **HorizontalRight**, the **Columns** property has no effect, because items are laid out in strict horizontal arrangement and no wrapping is used. If **ArrangeMethod**=**Vertical**, columns are arranged vertically, and the controls are either distributed evenly among the columns (**Fixed**), or distributed to fill the available horizontal or vertical space (**Fill**). If **ArrangeMethod**=**HorizontalWrap**, columns are arranged, and horizontal wrapping is used at a fixed column width of 280 px. Typically, this option is used to wrap tile layouts.

### Examples

#### ArrangeMethod=HorizontalWrap

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**1**

|     |     |
|-----|-----|
| 1 2 |     |
| 3 4 |     |
| 5   |     |

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**2**

|     |     |
|-----|-----|
| 1 2 | 6 7 |
| 3 4 | 8 9 |
| 5   |     |

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**Fill** For this example, we assume that only three lines of items can fit in the container height.

|     |       |       |
|-----|-------|-------|
| 1 2 | 7 8   | 13 14 |
| 3 4 | 9 10  | 15    |
| 5 6 | 11 12 |       |

#### ArrangeMethod=Vertical

**ArrangeMethod**=**Vertical** and **Columns**=**1**

|     |     |
|-----|-----|
| 1   |     |
| 2   |     |
| 3   |     |
| …   |     |

**ArrangeMethod**=**Vertical** and **Columns**=**2**

|     |     |
|-----|-----|
| 1   | 5   |
| 2   | 6   |
| 3   | 7   |
| 4   | 8   |

**ArrangeMethod**=**Vertical** and **Columns**=**Fill** For this example, we assume that only three lines of items can fit in the container height.

|     |     |     |
|-----|-----|-----|
| 1   | 4   | 7   |
| 2   | 5   | 8   |
| 3   | 6   |     |

**ArrangeMethod**=**Vertical** and **Columns**=**Fill** on a FastTab For this example, we assume that the width of the FastTab can fit four columns.

|     |     |     |     |
|-----|-----|-----|-----|
| 1   | 3   | 5   | 7   |
| 2   | 4   | 6   | 8   |

## Breakable groups
When you use **ColumnsMode**=**Fill** to dynamically create columns, based on the amount of available space, groups of fields can be split into multiple columns. The **Breakable** property that was added to Group controls helps developers guarantee that controls in a group aren't broken up across columns. The default value for this property is **Yes**, which indicates that the contents of the group can be split between groups. To keep a group together all the time, set **Breakable** to **No**. Note that **Breakable** applies only to the first level in nested groups.

## Guidelines for using layout properties
### ColumnsMode=Fill

-   Don't nest containers that have **ColumnsMode** set to **Fill**. Set **ColumnsMode** to **Fill** only on the direct parent container of the controls/fields that you want to responsively fill the available space.
-   Don't set **HeightMode** to **SizeToAvailable** on any child controls of a container that has **ColumnsMode** set to **Fill**. **ColumnsMode**=**Fill** tries to calculate an average height of all controls across columns to balance them as much as possible. However, our layout CSS and calculations can't handle **SizeToAvailable** children, and this setting doesn't necessarily make sense.
-   Don't set **WidthMode** to **SizeToAvailable** on any child controls of a container that has **ColumnsMode** set to **Fill**. Otherwise, the child controls will take up all the available width, and all controls will appear in one column.
-   Container that have **ColumnsMode**=**Fill** should have **WidthMode** set to **SizeToAvailable** (if you're using fill-width containers such as Tabs and Groups) or **HeightMode** set to **SizeToAvailable** (if you're using fill-height containers such as Panorama sections).

### HeightMode/WidthMode=SizeToAvailable

-    If you use **WidthMode**=**SizeToAvailable**, make sure that parent containers in the form have **WidthMode** set to **SizeToAvailable**, not **SizeToContent**. **SizeToAvailable** containers inside **SizeToContent** containers are overridden and become **SizeToContent** containers.


See also
--------

[User interface development home page](user-interface-development-home-page.md)



