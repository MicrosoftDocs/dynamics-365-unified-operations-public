---
# required metadata

title: Service object groups 
description: Object groups are useful for sorting and filtering the data about objects for reports and statistics.
author: sorenva
ms.date: 05/11/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceObjectGroups
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Service object groups

[!include [banner](../includes/banner.md)]

Object groups are useful for sorting and filtering the data about objects for
reports and statistics. For example, you can group objects by geographical
location or by type.

## Group by geographical location

You can use this grouping method to show where the various different objects
that your company services are located. Grouping objects by geographical
location can also be useful if, for example, you must identify the objects that
your company already provides services for in a particular country/region.

## Example of grouping by geographical location

A customer from Belgium calls your service center and wants to create a service
agreement for an object, ABC. You have attached an object group for geographical
location, Belgium, to all objects that are serviced in Belgium. By using this
group as a filter, you can quickly search to see whether you already have a
record for ABC in the program, or whether you must set up a new object.

## Group by type

You can use this grouping method to show the types of objects that your company
services. Grouping objects by type can also be useful if, for example, you want
to create a new object based on similar objects that already exist in the
program.

## Example of grouping by type

A customer calls and wants to set up a service agreement for an air conditioning
machine, HIJ. You do not already have a record for this machine. However, you
have set up an object group titled Air Conditioners, and you have attached this
group to all air conditioning objects. Therefore, you can quickly search for and
identify all other air conditioning machines and use the template information
from these objects to create service agreement lines for HIJ. By using object
groups in this manner, you can quickly set up new objects and determine the
service tasks that must be performed on them.

## Create service object groups

Create groups that you can assign service objects to. Service objects are inventory items and other products for which services are performed. By grouping service objects, you can create reports for similar and related service objects. For example, a service object group might consist of two service objects: One service object is a kit, and the second service object is the service to install the kit.

To create service object groups, follow these steps:

1. Click **Service management > Setup > Service objects > Service object groups**.

2. Click **New** to create a new service object group.

3. Enter a unique name for the service object group and, optionally, a description.

You can assign service objects to the group by using the **Service objects** form. 

## See also

[Create service objects](create-service-objects.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]