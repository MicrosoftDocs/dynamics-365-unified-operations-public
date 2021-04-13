---
# required metadata

title: Check-in for pickup module
description: This topic covers the check-in for pickup module and explains how to configure it in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 04/23/2021
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

# Check-in for pickup module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the check-in for pickup module and explains how to configure it in Microsoft Dynamics 365 Commerce.

The check in for pickup module provides a confirmation page for customers who use the Dynamics 365 Commerce customer check-in capabilities to notify a store of their arrival. The check in for pickup module also allows you to configure a form that collects additional information from customers such as parking spot number and vehicle make and model to facilitate order delivery. 

## Module properties

| **Property name**                            | **Values**       | **Description**                                              |
| -------------------------------------------- | ---------------- | ------------------------------------------------------------ |
| Confirmation text                           | Text string    | Content for the heading that displays on the check-in confirmation view. |
| Show QR code                                | **True** or **False**           | When enabled, the check-in confirmation view displays a QR code that represents the order confirmation ID. |
| Additional information heading              | Text string  | Content for the heading that displays when additional information fields have been configured. |
| Additional information keys                 | **Resource ID**/**Resource value** pair | Each key creates a form field and associated label for collecting additional information from customers. |
| Additional information keys \> Resource ID    | Text string           | Each information key creates a form field and associated label for collecting additional information from customers. This property identifies the additional information key and is displayed as the label within the instructions field within the task in point of sale (POS). |
| Additional information keys \> Resource value | Text string  | Specifies the label for the text field within the task in point of sale (POS).  |
| Additional information keys \> Required       | **True** or **False** | Specifies whether customers must fill in this field before they are allowed to continue. When enabled, an asterisk is rendered next to the form label, and a null check is performed that prevents customers from continuing if no value is entered. |

## Add the check in for pickup module to a page

This module should be added to the new page you create for check-in confirmation, which will serve as the check-in confirmation experience for customers who select **I am here** in their email. 

## Configure the additional information form

If no additional information keys are configured, the module will display the check-in confirmation page by default. As the check-in confirmation is displayed, a task is created in the POS for the store where the order is to be picked up from.

When one or more additional information keys are configured, customers will first be prompted to enter information. When customers select **Submit** they are shown the check-in confirmation and the POS task is created. 

## Additional resources

[Enable customer check-in notifications in point of sale (POS)](enable-customer-check-in.md)
