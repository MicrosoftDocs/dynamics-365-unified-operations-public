(---
title: Can't apply a template to a released product
description: Can't apply a template to a released product 
author: t-benebo
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: EcoResProductDetailsExtended
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Can't apply a template to a released product

KB Number: 4612097

## Issue description
<!-- This isn't an issue description. Where is the issue? -->
<!-- Beatriz: the issue here is that the templates are not working as the customer is expecting them to work. He is using the "templates" functionality that is some functionality that is working for making templates in many places in the application. Below are the steps on how he is using them. -->
Click Product information and management – Products - Released products - new
Click options -record info
Select user template or company template
Enter description and save.
Click Released products – Products -  Released products -  New
Enter Product number and name and Drop down to Apply template.

## Resolution
<!-- It isn't clear what problem this is solving. What is the "record info functionality"? -->
<!-- Beatriz: the thing here is that that general templates that the customer is trying to use with the repro steps above does not work for making templates on products. Products have a specific functionality for making templates, so they should use this product specific functionality, with the repro steps shown below -->
To create an item template, use the product-specific templates, not the record info functionality. To create an item template:

1. Go to **Product information management \> Products \> Released products**.
1. On the Action Pane, open the **Product** tab and, from the **New** group, select either **Template \> Create personal template** or **Template \> Create shared template** as needed.
