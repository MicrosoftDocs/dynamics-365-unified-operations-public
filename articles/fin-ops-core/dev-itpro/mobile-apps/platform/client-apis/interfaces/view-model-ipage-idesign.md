---
title: Design type
description: Learn about the design object type, which includes the alignItems, alignSelf, bindings, border, color, flexFlow, flexSize and other properties.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Design type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Design object type.
For more information on design, please reference the [Design Introduction](../../scenarios/client-api-design-overview.md).

### Hierarchy

Design <br>&nbsp;&nbsp;&nbsp;└─ [PageLinkDesign](view-model-control-pagelink-ipagelink-ipagelinkdesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControlDesign](view-model-control-container-icontainercontrol-icontainercontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControlDesign](view-model-control-basecontrol-iinputcontrol-iinputcontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [ImageDesign](view-model-control-image-iimage-iimagedesign.md) <br>

## Index

### Properties

* [alignItems](view-model-ipage-idesign.md#alignitems)
* [alignSelf](view-model-ipage-idesign.md#alignself)
* [bindings](view-model-ipage-idesign.md#bindings)
* [border](view-model-ipage-idesign.md#border)
* [color](view-model-ipage-idesign.md#color)
* [flexFlow](view-model-ipage-idesign.md#flexflow)
* [flexSize](view-model-ipage-idesign.md#flexsize)
* [fontSize](view-model-ipage-idesign.md#fontsize)
* [fontWeight](view-model-ipage-idesign.md#fontweight)
* [justifyItems](view-model-ipage-idesign.md#justifyitems)
* [label](view-model-ipage-idesign.md#label)
* [labelPosition](view-model-ipage-idesign.md#labelposition)
* [name](view-model-ipage-idesign.md#name)
* [padding](view-model-ipage-idesign.md#padding)
* [type](view-model-ipage-idesign.md#type)

## Properties

### alignItems

alignItems: string (optional) 

This property is an alias for the CSS property "align-items".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "align-items" property.


### alignSelf

alignSelf: string (optional) 




### bindings

bindings: any (optional) 




### border

border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional) 

The border behavior of a control. This property will not be inherited by the children.


### color

color: string (optional) 

The foreground color of the container.
This will modify the color of all headers, items, labels, and icons within the container.<br>
Consider setting the background color at the same time as necessary when setting this attribute.<br>
Note: if color is set to "theme", the theme color of the app will be used.<br>
The following colors are available: <br>
![Image of available colors.](../../../media/colors.PNG)


### flexFlow

flexFlow: string (optional) 

Specifying this property makes the component a flex container component.
This property is an alias for the CSS property "flex-flow".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "flex-flow" property.


### flexSize

flexSize: string (optional) 

One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.
This property is an alias for the CSS property "flex". Please refer to
[this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "flex" property.


### fontSize

fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional) 

The proportional text size


### fontWeight

fontWeight: "normal" &#124; "bold" (optional) 

Normal or bold text.


### justifyItems

justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional) 

This property is an alias for the CSS property "justify-content".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "justify-content" property.


### label

label: string (optional) 




### labelPosition

labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional) 

Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.


### name

name: string (optional) 




### padding

padding: "none" &#124; "small" &#124; "std" (optional) 

Allows specifying the component's padding behavior.
A component will inherit the padding behavior specified by its parent container components.


### type

type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The type of the control as a string.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
