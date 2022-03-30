---
# required metadata

title: Revenue split in Subscription billing
description: This topic explains how to setup revenue split templates for items that are sold as bundles. The bundle contains a parent item and a child item sold together as one item to customers. 
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---
# Revenue Split Template

Modules > Subscription billing > Recurring contract billing > Setup > Revenue split template

Use this page to set up templates for the revenue split functionality that consists of a parent item with child items. This type of item is often sold as a single item to customers. 

When creating the parent item, keep the following restrictions in mind: 
* An item can be specified as a parent item only once.
* The parent item can be selected as a child item within the same template. 
* A valid template requires one or more child items. 
* An item can be specified as a child item for more than one bundle item.
* Each parent-child relation must be unique.

</div><div>

## Example

A computer item can be created as follows: 

* **Parent item**: Subscription Silver
* **Line items**: 
   * Support 
   * Maintenance
   * License

## Processes

Create a parent item with child items: 
1. Select **New**. 
1. Select a **Parent item**.   
The **Variant number** is automatically updated, which can be change as needed. 
1. Select **Allocation method**. 
1. In the **Components items** list, select **Add** to add child items. 
   1. If **Allocation method** is **Percentage**,  specify the **Percentage**. 
   1. If **Allocation method** is **Equal amount**, the **Percentage** automatically updates to equal percentages. 
   1. If **Allocation method** is **Variable amount**, **Zero parent amount**,  or **Zero amount**, the **Percentage** remains as zero and cannot be changed. 
1. Select **Save**.

## Fields

This page contains the following fields:


| Field        | Description           |
| :------------- |:-------------| 
| **Parent item**     | Select an item number. <br />This item becomes the parent item for the bundle item that you create.  | 
| **Product name**     | isplays the product name.       |  
| **Allocation method**	  | Select the allocation method: <br />* **Equal Amount**: The allocation percentages are automatically calculated and equally split among the items within the template.<br />* **Percentage**: A percentage amount can be specified for the allocation. The sum of all percentages must equal 100. <br /> * **Variable Amount**: Child items are added with a zero (0) net amount. The price of the child items must be specified at the transaction level. <br /> * **Zero Amount**: The parent item retains its unit price and net amount. All child items have a zero (0) net amount.<br /> * **Zero parent amount**: The parent item has a fixed  zero (0) net amount. All child items are treated similar to standard items. Also, no validation is performed to verify that the sum of the child items equals the parent amount.       |    
| **Component items**     |  | 
| **Component item**     | Select an item number. This item is a child item.       |  
| **Variant number**	  | Select the variant number for the itme. <br />Variants are a standard Microsoft Dynamics 365 for Finance and Operations feature. For more information, see, **[Create predefined product variants](https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/tasks/create-predefined-product-variants)** ![New window icon](../../../Resources/images/icons/iNewWindow.png) in the Microsoft Dynamics 365 for Finance and Operations documentation.       |    
| **Product name**     | Displays the product name.  | 
| **Percentage**     | Displays the allocation percentage for the milestone: <br /> When **Allocation Method** is **Percentage**, you can specify the percentage. <br /> When **Allocation Method** is **Equal amount**, the percentage is automatically calculated in to equal percentages based on the number of items in the template. <br /> When **Allocation Method** is **Variable amount**, **Zero parent amount**, or **Zero amount**, the percentage is zero (0) and cannot be edited. <br />This value can be any positive number between zero and 100, but the total sum of all the percentages must equal 100%.      |  
| **Total percentage**	  | Displays the sum of the **Percentage** column. <br /> When **Allocation Method** is **Equal amount** or **Percentage**, the sum of all the percentages must equal 100%. <br /> When **Allocation Method** is **Variable amount**, **Zero parent amount**,  or **Zero amount**, the total percentage is zero (0).        |    

