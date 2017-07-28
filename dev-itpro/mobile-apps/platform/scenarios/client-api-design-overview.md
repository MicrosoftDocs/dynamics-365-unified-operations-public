---
# required metadata

title: Client-side design APIs overview
description: This topic provides an overview of the client-side design APIs and includes recommendations for using them.
author: makhabaz
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: makhabaz
ms.search.validFrom: 2017-07-20
ms.dyn365.ops.version: Platform update 3

---

# Client-side design APIs overview
This topic provides an overview of the client-side design APIs and includes recommendations for using them.

## Terminology
The following list includes some common terms that apply to using the client-side design APIs.

+ **design**: A property which can be optionally specified on a Page, Action or other Component to override it's default design.
+ **component**: A component is one of the following:
    - block container component (default): A container with CSS block behaviors (equivalent to CSS style "display: block"")
    - flex container component: A container with CSS flex behaviors (equivalent to CSS style "display: flex")
    - control reference component: A component which refers to a control that exists within the static metadata (xml) of the Page/Action.
    - new control component: A component which instantiates a new control (meaning the control does not already exist in the static metadata (xml) of the Page/Action)

    A component is represented in the design by a JSON object, whose properties represent the properties of the component. Virtually every JSON object in the design property hierachy is a component.
* **item**: Refers to a component which is nested within a container
* **Properties**: There are four types of properties which can be set on a component. Those types are:
    - container-specific
    - item-specific
    - control-specific
    - list-specific
    - generic (non-specific)

    Properties are specified on a component in the same way (they are just key-value pairs specified on a component's JSON object). But which of the properties is applicable depends on the type of component the property is applied to.

    For properties which have a pre-defined list of possible values, the first value displayed in the documentation is the default value for the property. In most cases, if you do not specify a property at all, by omitting it from the JSON object, then the property will behavir as if you set its default value.

    - Generic properties can be applied to all component types.
    - All property names should not be enclosed in quotes.
    - All property values must be enclosed in double quotes, unless otherwise specified.
* **Inheritance**: If color, font size, or font weight are applied to a control, all of the descendant controls will inherit the same property unless they are reassigned. If padding is applied to a control, it will be inherited by the item (non-container) descendants of the control. No other properties are inherited.

## How to use design APIs
A modified segment of business logic code from a Reservation Management example can be seen below. Specifically, it comes from a variable which specifies the design for a reservation details page. The code is commented to help highlight a few possibilities.

> [!NOTE]
> Any color, font size, or font weight applied to a given control will also apply to all of the children. Padding will be applied to the non-container children. No other properties will be inherited. Containers include lists, pages, groups, and parts.

Once a control is created without any further children or items, the control name only needs to be written in quotes (see **FMCustomer_FullName** in the code example). However, if any customization will be applied to that control then the code must be blocked and written as **FMCustomer_Image** is written below with the **name** label.

```
// Page root container
"flexFlow":"column nowrap",
"items":[
	// Upper third of page, contains 4 rows
	{
		"flexFlow":"column nowrap",
		"background":"theme", // set background color to the theme color
		"color":"light",      // set the foreground (e.g. font) color to light
		"fontSize":"small",
		"border": "none",
		"padding":"small",
		"items":[
			// Row 1/4 with customer image and name
			{
				"flexFlow":"row nowrap",
				"alignItems":"center",
				"justifyItems":"center",
				"labelStyle":"hidden", // don’t show label for field
				"fontSize":"large",
				"fontWeight":"bold",
				"items":[
					{
					// Customer image – since we’re modifying the imageStyle, etc. this
					// code must be blocked and the “FMCustomer_Image” must be labelled
					// with “name”.
						"name":"FMCustomer_Image",
						"imageStyle":"circular",
						height:3,
						width:3
					},
					// don’t need to create a new object or use the “name” label if
					// there is no customization
					"FMCustomer_FullName",
				]
			},
			// Row 2/4 with vehicle description
			. . .
		}
	}
```

The above code produces the customer image, customer name, font, background color, etc. as shown in the following image.

![sample image](../media/detail-page.PNG)

