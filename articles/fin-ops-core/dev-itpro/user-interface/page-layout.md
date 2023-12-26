---
title: Page layout in the web client
description: This article discusses layout in the web client. Layout is a design process that specifies how controls appear on a page.
author: jasongre
ms.date: 01/22/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1cfa479c-71fa-4eb6-8d12-ad4d65c8ecf3
---

# Page layout in the web client

[!include [banner](../includes/banner.md)]

This article discusses layout in the web client. Layout is a design process that specifies how controls appear on a page. 

## Introduction

Layout is a design process that specifies how the controls on a page appear in the web client. Layout occurs within container controls. The following table lists the container controls.

| Container   | Description                                                                                                                                            |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Form.Design | The root of the page. It functions as a special kind of container.                                                                                     |
| Group       | The general-purpose container control. Group controls can be nested as required.                                                                       |
| Tab         | A control that contains TabPage controls and has many possible **Tab.Style** values, such as **Tab**, **FastTab**, **Vertical Tab**, and **Panorama**. |
| TabPage     | The appearance of each TabPage control depends on its **Tab.Style** value.                                                                             |
| ButtonGroup | A special type of Group control that contains buttons.                                                                                                 |

A grid is a special type of control that has some container behaviors, such as flexible sizing (**SizeToAvailable**). However, a grid has special visualizations and isn't a general-purpose container control.

## Layout: Dynamics AX 2012 vs. Finance and operations apps
### Layout in Dynamics AX 2012

In Microsoft Dynamics AX 2012, the arrangement of controls in containers is almost always vertical, and columns are manually set to provide some horizontal spread.

### Examples

**Columns**=**1** 1 2 3 **Columns**=**2** 1 4 2 5 3 In Dynamics AX 2012, sizing is achieved via the **Height** and **Width** properties. If **Height** and **Width** are set to **Auto**, the size is as large as the child controls require. If **Height** and **Width** are set to **Column**, the container is as large as it can be within the parent container. By default, **Height** and **Width** are set to **Auto** for every container.

### Layout in finance and operations apps 

In finance and operations apps, layout is controlled by the same basic properties that control layout in Dynamics AX 2012. However, additional options have been added to support a more responsive layout. In particular, the layout of a page is based on the following factors:

-   The arrangement method that is specified by the **ArrangeMethod** property.
-   The columns that are specified by the **Columns** property.
-   The sizing that is specified by the **HeightMode**, **WidthMode**, **Height**, and **Width** properties.

## ArrangeMethod property
The **ArrangeMethod** property specifies a base arrangement method for a container. For this property, finance and operations apps have all the options from AX 2012. However, they also have a **HorizontalWrap** option that is intended for tile layouts in panoramas. The following table describes the various options for the **ArrangeMethod** property.

| Option          | Description                                                                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vertical        | Controls are arranged vertically. If columns are also used, controls are arranged vertically inside the generated columns. This option is the default value for Groups and for TabPages where **Tab.Style** is set to a value other than **Panorama**. |
| HorizontalLeft  | Controls are arranged horizontally, and they are left-aligned and bottom-aligned inside the parent container. |
| HorizontalRight | Controls are arranged horizontally, and they are right-aligned and bottom-aligned inside the parent container. |
| HorizontalWrap  | Controls are arranged inside columns of fixed width that wrap horizontally. This option is typically used for tile layouts in panorama sections. It's the default value for TabPages where **Tab.Style** is set to **Panorama**. |

## ColumnsMode property
For the **ColumnsMode** property, finance and operations apps have a **Fill** option to support responsive layouts. When the property is set to this value, columns automatically flow as required. The following table describes the various options for the **ColumnsMode** property.

| Option | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fill   | Columns are generated to fill the available horizontal space or vertical space, depending on the container type. If the container is a Panorama-style tab, this option generates columns to fill it along the vertical axis. For all other containers (Groups, Tab-style Tabs, and all other styles of Tabs), this option generates columns to fill the container along the horizontal axis. |
| Fixed  | Specify the number of columns that the **Columns** property should generate. Controls are evenly distributed among the columns, and their order is maintained. If the controls can't be distributed evenly among the columns, the leftmost columns receive extra controls first. This option is the default value for all controls.                                                          |

## HeightMode/WidthMode properties
In finance and operations apps, sizing is done via two pairs of size properties: **WidthMode** and **Width**, and **HeightMode** and **Height**. The following table describes the various options for these properties.

| Option          | Description                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SizeToAvailable | Fill the available space along the vertical (or horizontal) axis inside the parent container. If the parent container has **SizeToContent** height (or width), the child's height (or width) is also **SizeToContent**, unless there is a sibling in the container that can provide a height (or width). This option is the default value for Grids and Tabs (of all styles). |
| SizeToContent   | The height (or width) of the container should be the height (or width) of its contents. This option is the default value for Groups and all other controls except Tabs. FastTabs that aren't always expanded also have **SizeToContent** height. |
| Manual          | The height (or width) is manually sized. Set **HeightMode** (or **WidthMode**) to **Manual**, and then set **Height** (or **Width**) to a fixed number of pixels.<p>**Note:** Microsoft doesn't recommend that you use manual heights and widths, because they don't adapt to changes in form density.</p> |

Note that if a value of **Auto** is used for these properties, the behavior is automatically determined at runtime. Typically, a value of **Auto** for these properties causes the same behavior as a value of **SizeToContent**, as in AX 2012.

## Interactions between the ArrangeMethod and Columns properties
If **ArrangeMethod**=**HorizontalLeft** or **HorizontalRight**, the **Columns** property has no effect, because items are laid out in strict horizontal arrangement and no wrapping is used. If **ArrangeMethod**=**Vertical**, columns are arranged vertically, and the controls are either distributed evenly among the columns (**Fixed**), or distributed to fill the available horizontal or vertical space (**Fill**). If **ArrangeMethod**=**HorizontalWrap**, columns are arranged, and horizontal wrapping is used at a fixed column width of 280 px. Typically, this option is used to wrap tile layouts.

### Examples

#### ArrangeMethod=HorizontalWrap

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**1**

<table>
  <tr><td>1 &nbsp; 2</td></tr>
  <tr><td>3 &nbsp; 4</td></tr>
  <tr><td>5 &nbsp; 6</td></tr>
  <tr><td>7 &nbsp; 8</td></tr>
  <tr><td>9</td></tr>
</table>

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**2**

<table>
  <tr>
    <td>1 &nbsp; 2</td>
    <td>6 &nbsp; 7</td>
  </tr>
  <tr>
    <td>3 &nbsp; 4</td>
    <td>8 &nbsp; 9</td>
  </tr>
  <tr>
    <td>5</td>
    <td></td>
  </tr>
</table>

**ArrangeMethod**=**HorizontalWrap** and **Columns**=**Fill**

For this example, we assume that only three lines of items can fit in the container height.

<table>
  <tr>
    <td>1 &nbsp; 2</td>
    <td>7 &nbsp; &nbsp; 8</td>
    <td>13 &nbsp; 14</td>
  </tr>
  <tr>
    <td>3 &nbsp; 4</td>
    <td>9 &nbsp; &nbsp; 10</td>
    <td>15</td>
  </tr>
  <tr>
    <td>5 &nbsp; 6</td>
    <td>11 &nbsp; 12</td>
    <td></td>
  </tr>
</table>

#### ArrangeMethod=Vertical

**ArrangeMethod**=**Vertical** and **Columns**=**1**

<table>
  <tr><td>1 </td></tr>
  <tr><td>2</td></tr>
  <tr><td>3</td></tr>
  <tr><td>...</td></tr>
</table>

**ArrangeMethod**=**Vertical** and **Columns**=**2**

<table>
  <tr>
    <td>1</td><td>5</td>
  </tr>
  <tr>
    <td>2</td><td>6</td>
  </tr>
  <tr>
    <td>3</td><td>7</td>
  </tr>
  <tr>
    <td>4</td><td>8</td>
  </tr>
</table>

**ArrangeMethod**=**Vertical** and **Columns**=**Fill**

For this example, we assume that only three lines of items can fit in the container height.

<table>
  <tr>
    <td>1</td><td>4</td><td>7</td>
  </tr>
  <tr>
    <td>2</td><td>5</td><td>8</td>
  </tr>
  <tr>
    <td>3</td><td>6</td>
  </tr>
</table>

**ArrangeMethod**=**Vertical** and **Columns**=**Fill** on a FastTab

For this example, we assume that the width of the FastTab can fit four columns.

<table>
  <tr>
    <td>1</td><td>3</td><td>5</td><td>7</td>
  </tr>
  <tr>
    <td>2</td><td>4</td><td>6</td><td>8</td>
  </tr>
</table>

## Breakable groups
When you set **ColumnsMode** to **Fill** to dynamically create columns, based on the amount of available space, groups of fields can be split into multiple columns. The **Breakable** property on Group controls lets developers ensure that controls in a group aren't distributed across columns. The default value for this property is **Yes**, which indicates that the contents of the group can be split between groups. To keep a group together all the time, set **Breakable** to **No**. Note that **Breakable** applies only to the first level in nested groups.

## Guidelines for using layout properties
### ColumnsMode=Fill

-   Don't nest containers that have **ColumnsMode** set to **Fill**. Set **ColumnsMode** to **Fill** only on the direct parent container of the controls/fields that you want to responsively fill the available space.
-   Don't set **HeightMode** to **SizeToAvailable** on any child controls of a container that has **ColumnsMode** set to **Fill**. **ColumnsMode**=**Fill** tries to calculate an average height of all controls across columns to balance them as much as possible. However, our layout CSS and calculations can't handle **SizeToAvailable** children, and this setting doesn't necessarily make sense.
-   Don't set **WidthMode** to **SizeToAvailable** on any child controls of a container that has **ColumnsMode** set to **Fill**. Otherwise, the child controls will take up all the available width, and all controls will appear in one column.
-   Container that have **ColumnsMode**=**Fill** should have **WidthMode** set to **SizeToAvailable** (if you're using fill-width containers such as Tabs and Groups) or **HeightMode** set to **SizeToAvailable** (if you're using fill-height containers such as Panorama sections).

### HeightMode/WidthMode=SizeToAvailable

-    If you use **WidthMode**=**SizeToAvailable**, make sure that parent containers in the form have **WidthMode** set to **SizeToAvailable**, not **SizeToContent**. **SizeToAvailable** containers inside **SizeToContent** containers are overridden and become **SizeToContent** containers.


## Additional resources

[User interface development home page](user-interface-development-home-page.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
