---
# required metadata

title: Check in for pickup module
description: This module provides a check-in confirmation and an optional more information experience for retailers who wish to enable a check-in experience for customers who choose a curbside mode of delivery for their order.
author: bicyclingfool
ms.date: 04/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.19


---

# Check in for pickup module

[!include [banner](includes/banner.md)]

This topic covers the check in for pickup module and explains how to configure it in Microsoft Dynamics 365 Commerce.

 

The check in for pickup module provides a confirmation page for customers who use the Dynamics 356 Commerce customer check-in capabilities to notify a store of their arrival. The module also allows you to configure a form that collects additional information from customers such as parking spot number, or vehicle make and model to facilitate order delivery. 

 

 

## Module properties

 

| **Property name**                            | **Values**       | **Description**                                              |
| -------------------------------------------- | ---------------- | ------------------------------------------------------------ |
| Confirmation  text                           | Heading  text    | Content  for the heading that displays on the check-in confirmation view. |
| Show  QR code                                | Yes/no           | When  checked, the check-in confirmation view displays a QR code that represents  the order confirmation ID |
| Additional  information heading              | Heading  text    | Content  for the heading that displays when additional information fields have been  configured. |
| Additional  information keys                 | Name/value  pair | Each key creates a  form field and associated label for collecting additional information from  customers. . |
| Additional  information keys: Resource ID    | String           | Identifies  the additional information key and is displayed as the label within the  instructions field within the task in point of sale (POS) |
| Additional  information keys: Resource value | String           | The  label for the text field                                |
| Additional  information keys: Required       | Yes/no           | Specifies  whether customers must fill in this field before they are allowed to  continue. When checked, an asterisk is rendered next to the form label, and a  null check is preformed that prevents customers from continuing if no value  is entered |

## Add the check in for pickup module to a page

This module will typically be added to a new page you create. The URL for the page on your e-commerce site will serve the additional information and/or check-in confirmation experience for customers who click the "I am here" button in their email. 

## Configure the additional information form

If no additional information keys are configured, the module will display the check-in confirmation page by default. As the check-in confirmation is displayed, a task is created in the point of sale for the store where the order is to be picked up from.

When one or more additional information keys are configured, customers will first be prompted to enter information. When they click the **Submit** button, they are shown the check-in confirmation and the point of sale task is created. 



## Additional resources

[Enable customer check-in notifications in point of sale (POS)](enable-customer-check-in.md)