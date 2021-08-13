---
# required metadata

title: Enable order lookup for guest checkouts 
description: This topic describes how to set up order lookup for customers who check out as a guest.
author: stuharg
ms.date: 08/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2021-08-15
ms.dyn365.ops.version: Release 10.0.22

---


# Enable order lookup for guest checkouts

[!include [banner](includes/banner.md)]

This feature allows customers who make purchases as guest users to be able to look up their order. This capability is useful for customers who need to see the fulfillment status of products in the order, verify the address an order was shipped to, reorder a product, confirm which store to pick up an order at, as well as other scenarios. 

Customers who make purchases as registered users can already see their order details, but they need to be signed in which is not possible for a guest checkout. Customers who placed an order as a guest will use a form to provide the order confirmation ID for the order and the email address they specified at checkout.

A link or button can also be included in any order-related transactional email, which takes the customer directly to the order details page for their order. This link or button will work for orders that were placed both as registered and as guest users. 



## Enable order lookup for guest checkouts

To enable this feature, the following feature management switches need to be turned on

| **Feature management switch name**                           | **Purpose**                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Retail anonymous  user search order details opting feature   | This switch turns on the UI under Commerce parameters that allow you to enable the order lookup  API for unauthenticated users, and configure how personal data is displayed |
| Enable generation  of a stronger channel reference ID        | This switch generates a more secure 12 character channel reference ID (order confirmation  ID) which allows it to be passed in the query string when looking up an  order. |
| Generate a  consistent channel reference ID format across channels | This switch generates a secure channel reference ID for orders placed through e-commerce, point of sale and call center orders. To enable this switch, the Enable generation of a stronger channel reference ID switch must also be enabled. |

The API that supports unauthenticated order lookup must be enabled with a configuration switch that is found in Headquarters in the Order search tab within **Retail and Commerce** -> **Headquarters setup** -> **Parameters -> Customer orders**. 

![Screenshot of switch to enable order lookup and configure for whom to display personal data.](./media/orderLookup_enable.PNG)



## Managing the display of personal data

Dynamics 365 Commerce provides options for controlling whether or not personal information such as the customer's shipping address, and the last 4 digits of their credit card are displayed to customers. By default, personal information is not displayed to customers when unauthenticated order lookup is enabled. Once it is enabled, you can choose from one of three options below.

>[!Disclosure]
>This option will determine when personal data such as customer address and the last four digits of the credit card will be shown to anonymous users. The most secure option is to set this configuration to Never. To fully protect registered customer privacy, it is advised to set this configuration to Guest checkout orders only. 

| **Option**        | **Result**                                                   |
| ----------------- | ------------------------------------------------------------ |
| Never (default)   | Personal information is not displayed in order lookups. Registered users who are  signed in and looking up an order they created while signed in will be able  to see their personal information. |
| Guest orders only | Personal information is displayed in order lookups for orders created as a guest. If  the order was created by a registered user, they must sign in to see their  personal information. |
| All orders        | Personal information is included in all order lookups.       |

Once you have enabled unauthenticated order lookup and/or made any modifications to the Include personal data in guest order lookup setting, run job 1070 (Channel configuration.)



## Configure the order lookup module

The form that guest users will use to look up their order is included as a starter kit module called Order lookup. The Order lookup module can be included in the body slot of any page. Below is an example of the order lookup module:

![Screenshot of the order lookup module displayed on a page.](./media/orderLookup_module.PNG)



The Order lookup module provides the following options in the module configuration:

| Property name     | Value     | Description                                                  |
| ----------------- | --------- | ------------------------------------------------------------ |
| Heading           | Text      | The heading that displays at the top of the form. "Find your order" in the example  above. |
| Rich text         | Rich text | Optional  explanatory text that appears below the heading.   |
| Order status type | Enum      | Dropdown for  selecting the type of information the form will request from the customer in  addition to their order confirmation ID. The values currently supported are:<br />**Email** - provides a field for customers to provide the email addresses they entered when they placed their oder.   <br />**None** - no additional information besides Order confirmation ID is requested in the form. |



## Additional information

[Set up an email notification profile](email-notification-profiles.md)



