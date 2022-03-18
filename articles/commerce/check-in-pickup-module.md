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

This topic covers the check-in for pickup module and explains how to configure it in Microsoft Dynamics 365 Commerce.

The check-in for pickup module provides a confirmation page for customers who use the Dynamics 365 Commerce customer check-in capabilities to notify a store about their arrival. The check-in for pickup module also lets you configure a form that collects additional information from customers to facilitate order delivery. This information includes a customer's parking spot number, and the make and model of their vehicle. 

## Module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Confirmation text | Text string | Content for the heading that appears on the check-in confirmation page. |
| Show QR code | **True** or **False** | When this property is set to **True**, the check-in confirmation page shows a QR code that represents the order confirmation ID. |
| Additional information heading | Text string | Content for the heading that appears when additional information fields have been configured. |
| Additional information keys | Resource ID/resource value pair | Each key creates a form field and an associated label that are used to collect additional information from customers. |
| Additional information keys \> Resource ID | Text string | Each information key creates a form field and an associated label that are used to collect additional information from customers. This property identifies the additional information key. In the task that is created in point of sale (POS), the value of this property is shown as the label in the instructions field. |
| Additional information keys \> Resource value | Text string | The label for the text field in the task in POS. |
| Additional information keys \> Required | **True** or **False** | This property specifies whether customers must fill in the form field before they can continue. When this property is set to **True**, an asterisk is rendered next to the form label, and a null check is done to prevent customers from continuing if no value is entered. |

## Add the check-in for pickup module to a page

The check-in for pickup module should be added to the new page that you create for check-in confirmation. That page will serve as the check-in confirmation experience for customers who select the **I am here** link or button in their email. 

## Configure the additional information form

By default, if no additional information keys are configured, the module shows customers the check-in confirmation page. As the check-in confirmation is shown, a task is created in POS for the store where the order is being picked up.

When one or more additional information keys are configured, customers are first prompted to enter information. When they select **Submit**, they are shown the check-in confirmation, and a task is created in POS. 

## Additional resources

[Enable customer check-in notifications in point of sale (POS)](enable-customer-check-in.md)
