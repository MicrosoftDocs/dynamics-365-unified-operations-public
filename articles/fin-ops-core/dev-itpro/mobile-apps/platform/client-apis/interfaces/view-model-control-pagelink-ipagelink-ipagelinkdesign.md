---
title: PageLinkDesign type
description: Learn about the pagelink design object type, which includes the alignItems, alignSelf, background, bindings, border, color, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# PageLinkDesign type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Pagelink design object type.

### Hierarchy

[Design](view-model-ipage-idesign.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLinkDesign <br>

## Index

### Properties

* [alignItems](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#alignitems)
* [alignSelf](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#alignself)
* [background](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#background)
* [bindings](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#bindings)
* [border](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#border)
* [color](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#color)
* [excludeContext](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#excludecontext)
* [flexFlow](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#flexflow)
* [flexSize](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#flexsize)
* [fontSize](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#fontsize)
* [fontWeight](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#fontweight)
* [hideArrow](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#hidearrow)
* [icon](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#icon)
* [justifyItems](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#justifyitems)
* [label](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#label)
* [labelPosition](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#labelposition)
* [name](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#name)
* [navigation](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#navigation)
* [padding](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#padding)
* [showCount](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#showcount)
* [style](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#style)
* [type](view-model-control-pagelink-ipagelink-ipagelinkdesign.md#type)

## Properties

### alignItems

alignItems: string (optional) 

This property is an alias for the CSS property "align-items".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "align-items" property.

> Inherited from [Design](view-model-ipage-idesign.md).[alignItems](view-model-ipage-idesign.md#alignitems)


### alignSelf

alignSelf: string (optional) 



> Inherited from [Design](view-model-ipage-idesign.md).[alignSelf](view-model-ipage-idesign.md#alignself)


### background

background: string (optional) 

Sets the background color.
If "theme" is used, then the color will match the app's theme color. <br>
![Image of available background colors.](../../../platform/media/colors_pagelink.PNG)


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
![Image of available foreground colors.](../../../media/colors.PNG)

> Inherited from [Design](view-model-ipage-idesign.md).[color](view-model-ipage-idesign.md#color)


### excludeContext

excludeContext: boolean (optional) 




### flexFlow

flexFlow: string (optional) 

Specifying this property makes the component a flex container component.
This property is an alias for the CSS property "flex-flow".
Please refer to [this web page](https://css-tricks.com/snippets/css/a-guide-to-flexbox) for documentation on the "flex-flow" property.

> Inherited from [Design](view-model-ipage-idesign.md).[flexFlow](view-model-ipage-idesign.md#flexflow)


### flexSize

flexSize: string (optional) 

One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.
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


### hideArrow

hideArrow: boolean (optional) 

Allows an arrow ( > ) on a default styled navigation control to be hidden.
By default, arrows are present in a navigation control.<br>
This property can only be added through the design object.


### icon

icon: string (optional) 

Name of the icon that is displayed in the pagelink control.
Here is a [list of available icons](/dynamics/s-e/).


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


### navigation

navigation: [NavigationArgs](view-model-ipage-inavigationargs.md) (optional) 

Navigation object of the pagelink.


### padding

padding: "none" &#124; "small" &#124; "std" (optional) 

Allows specifying the component's padding behavior.
A component will inherit the padding behavior specified by its parent container components.

> Inherited from [Design](view-model-ipage-idesign.md).[padding](view-model-ipage-idesign.md#padding)


### showCount

showCount: boolean (optional) 

If true, shows a count of the records present in the list on the target page.
This property is only suitable when the navigation target is a Page which contains on a List control.


### style

style: string (optional) 

Determines the visual style of the pagelink control.
Options:
* "inline": takes up the full width its container, with the label in-line with the icon
* "button": takes up only as much width as needed by the label, with the label below the icon


### type

type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The type of the control as a string.

> Inherited from [Design](view-model-ipage-idesign.md).[type](view-model-ipage-idesign.md#type)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
