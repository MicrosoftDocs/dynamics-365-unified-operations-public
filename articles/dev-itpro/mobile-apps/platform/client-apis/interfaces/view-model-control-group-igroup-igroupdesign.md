---
# required metadata
title: GroupDesign
description: Group design object type.
author: shadykdc
manager: AnnBe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# GroupDesign Type
Group design object type.

### Hierarchy

[ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ GroupDesign <br>

## Index

### Properties

* [alignItems](view-model-control-group-igroup-igroupdesign.md#alignitems)
* [alignSelf](view-model-control-group-igroup-igroupdesign.md#alignself)
* [allowScroll](view-model-control-group-igroup-igroupdesign.md#allowscroll)
* [background](view-model-control-group-igroup-igroupdesign.md#background)
* [bindings](view-model-control-group-igroup-igroupdesign.md#bindings)
* [border](view-model-control-group-igroup-igroupdesign.md#border)
* [color](view-model-control-group-igroup-igroupdesign.md#color)
* [flexFlow](view-model-control-group-igroup-igroupdesign.md#flexflow)
* [flexSize](view-model-control-group-igroup-igroupdesign.md#flexsize)
* [fontSize](view-model-control-group-igroup-igroupdesign.md#fontsize)
* [fontWeight](view-model-control-group-igroup-igroupdesign.md#fontweight)
* [itemBorder](view-model-control-group-igroup-igroupdesign.md#itemborder)
* [items](view-model-control-group-igroup-igroupdesign.md#items)
* [justifyItems](view-model-control-group-igroup-igroupdesign.md#justifyitems)
* [label](view-model-control-group-igroup-igroupdesign.md#label)
* [labelPosition](view-model-control-group-igroup-igroupdesign.md#labelposition)
* [name](view-model-control-group-igroup-igroupdesign.md#name)
* [padding](view-model-control-group-igroup-igroupdesign.md#padding)
* [type](view-model-control-group-igroup-igroupdesign.md#type)

## Properties

### alignItems

alignItems: string (optional) 

This property is an alias for the CSS property "align-items".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "align-items" property.

> Inherited from [Design](view-model-ipage-idesign.md).[alignItems](view-model-ipage-idesign.md#alignitems)


### alignSelf

alignSelf: string (optional) 



> Inherited from [Design](view-model-ipage-idesign.md).[alignSelf](view-model-ipage-idesign.md#alignself)


### allowScroll

allowScroll: string (optional) 

True if the container will allow scrolling when its items do not fit into the container's available space.
If a container has an item which may scroll, then set this property to false to prevent nested scrolling areas.

> Inherited from [ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md).[allowScroll](view-model-control-container-icontainercontrol-icontainercontroldesign.md#allowscroll)


### background

background: string (optional) 

The background color of the container.
Consider modifying the color attribute in the same container so that fonts overlaying the background color will appear appropriately.
Note: if background is set to "theme", the theme color of the app will be used.
The following colors are available: <br>
![sample image](../../../media/colors.PNG)

> Inherited from [ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md).[background](view-model-control-container-icontainercontrol-icontainercontroldesign.md#background)


### bindings

bindings: any (optional) 



> Inherited from [Design](view-model-ipage-idesign.md).[bindings](view-model-ipage-idesign.md#bindings)


### border

border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional) 

The border behavior of a control. This property will not be inherited by the children.

> Inherited from [Design](view-model-ipage-idesign.md).[border](view-model-ipage-idesign.md#border)


### color

color: string (optional) 

The foreground color of the container.
This will modify the color of all headers, items, labels, and icons within the container.<br>
Consider setting the background color at the same time as necessary when setting this attribute.<br>
Note: if color is set to "theme", the theme color of the app will be used.<br>
The following colors are available: <br>
![sample image](../../../media/colors.PNG)

> Inherited from [Design](view-model-ipage-idesign.md).[color](view-model-ipage-idesign.md#color)


### flexFlow

flexFlow: string (optional) 

Specifying this property makes the component a flex container component.
This property is an alias for the CSS property "flex-flow".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "flex-flow" property.

> Inherited from [Design](view-model-ipage-idesign.md).[flexFlow](view-model-ipage-idesign.md#flexflow)


### flexSize

flexSize: string (optional) 

One number or two numbers written as a string. E.g. "(size to grow) [(size-to-shrink)]" to accomodate available space in the immediate flex container.
This property is an alias for the CSS property "flex". Please refer to
[this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "flex" property.

> Inherited from [Design](view-model-ipage-idesign.md).[flexSize](view-model-ipage-idesign.md#flexsize)


### fontSize

fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional) 

The proportional text size

> Inherited from [Design](view-model-ipage-idesign.md).[fontSize](view-model-ipage-idesign.md#fontsize)


### fontWeight

fontWeight: "normal" &#124; "bold" (optional) 

Normal or bold text.

> Inherited from [Design](view-model-ipage-idesign.md).[fontWeight](view-model-ipage-idesign.md#fontweight)


### itemBorder

itemBorder: "solid" &#124; "none" (optional) 

If true, a border will appear around each row in the list.
This property is equivalent to applying the border property individually to all items in the container.

> Inherited from [ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md).[itemBorder](view-model-control-container-icontainercontrol-icontainercontroldesign.md#itemborder)


### items

items: string &#124; [Design](view-model-ipage-idesign.md) \[ \] (optional) 

An array containing the components to place inside of the container.

> Inherited from [ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md).[items](view-model-control-container-icontainercontrol-icontainercontroldesign.md#items)


### justifyItems

justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional) 

This property is an alias for the CSS property "justify-content".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "justify-content" property.

> Inherited from [Design](view-model-ipage-idesign.md).[justifyItems](view-model-ipage-idesign.md#justifyitems)


### label

label: string (optional) 



> Inherited from [Design](view-model-ipage-idesign.md).[label](view-model-ipage-idesign.md#label)


### labelPosition

labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional) 

Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.

> Inherited from [Design](view-model-ipage-idesign.md).[labelPosition](view-model-ipage-idesign.md#labelposition)


### name

name: string (optional) 



> Inherited from [Design](view-model-ipage-idesign.md).[name](view-model-ipage-idesign.md#name)


### padding

padding: "none" &#124; "small" &#124; "std" (optional) 

Allows specifying the component's padding behavior.
A component will inherit the padding behavior specified by its parent container components.

> Inherited from [Design](view-model-ipage-idesign.md).[padding](view-model-ipage-idesign.md#padding)


### type

type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The type of the control as a string.

> Inherited from [Design](view-model-ipage-idesign.md).[type](view-model-ipage-idesign.md#type)


