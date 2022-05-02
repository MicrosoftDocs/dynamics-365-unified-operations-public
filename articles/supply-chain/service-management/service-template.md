---
# required metadata

title: Service templates
description: You can define a service agreement as a template and copy the lines of the template later into another service agreement or into a service order.
author: sorenva
ms.date: 02/19/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAAgreementTable
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

# Service templates

[!include [banner](../includes/banner.md)]

You can define a service agreement as a template and copy the lines of the template later into another service agreement or into a service order.

## Example

A customer for whom you provide service has identical service elevators at five different locations.

You want to set up five service agreements for the customer, one for each site.
To limit repetitive setup work, and to make sure that the setup information in
the service agreements is identical, you create a service agreement and specify
it as a template for the service work on the elevators.

You can now copy the template lines into the five new service agreements, so
that each service agreement is populated with the lines from the template.

## Create a template

When you create a service template, you create a service agreement, create the
required lines on it, and attach the service agreement to a service-template
group.

> [!NOTE]
> A service agreement can be defined as a template only if it has no service
orders attached to it. Also, no service orders can be generated from a service
agreement that is defined as a template.

## Copy template lines

You can copy template lines from a service template into another service
agreement or into a service order.

When you copy template lines into your service orders or service agreements,
your template groups are displayed in a tree view in which each group can be
expanded. This display lets you view each template and template line.

It is easier to determine the service-template lines that you want to copy if
you have grouped the templates under names that reflect the use of the
templates.

## Related topics

[Copy service templates lines](copy-service-template-lines.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]