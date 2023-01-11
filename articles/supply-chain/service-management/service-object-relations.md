---
# required metadata

title: Service object relations 
description: You can create service object relations between a service object and a service agreement or service order. 
author: sorenva
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceObjectRelation
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

# Service object relations 

[!include [banner](../includes/banner.md)]

You can create service object relations between a service object and a service
agreement or service order. When you create a relation, you attach the service
object to the service agreement or service order.

After the relation is created, you can attach the service object to any lines on
the service agreement or service order.

## Template BOMs

You can also specify a template BOM for the object relation. The template BOM is
a bill of materials for the object on which you perform service. If you replace
a component part of the service object during a service visit, you can register
this change in the service BOM by using the Service objects form.

## Example

You create a service agreement for servicing two elevators at a customer site.
The service agreement has the identifier ID SAL-001.

The elevators are set up in the Service objects form as objects, EL-S/1000 and
EL-L/1000.

You attach the service objects, EL-S/1000 and EL-L/1000, to the service
agreement.

You want to register changes in the BOM for the service object as you replace
component parts of the object, so you attach a service BOM to the service object
relation, as described in the following table.

| Service object | Relation – Service agreement | Service BOM   |
|----------------|------------------------------|---------------|
| EL-S/1000      | ID SAL-001                   | BOM-EL-S/1000 |
| EL-L/1000      | ID SAL-001                   | BOM-EL-L/1000 |

Because there are service object relations for the agreement, you can now create
service agreement lines with these objects, as shown in the following table.

| Transaction type | Category           | Service object |
|------------------|--------------------|----------------|
| Hour             | Inspection         | EL-S/1000      |
| Hour             | Gear box cleaning  | EL-S/1000      |
| Item             | Cleaning materials | EL-S/1000      |
| Hour             | Inspection         | EL-L/1000      |
| Hour             | Gearbox cleaning   | EL-L/1000      |
| Item             | Cleaning materials | EL-L/1000      |

On a service visit, you have to replace the gearbox for elevator EL-S/1000. To
replace a component part of the object, you can access the BOM Designer by using
the service object relation that you set up for the current service agreement.

Access the BOM Designer by using a service object relation

1. Service agreements
2. Double-click a service agreement, or click Service agreement to create a service agreement.
3. Click the Setup tab.
4. Click Service objects to attach a template BOM to the service agreement.
5. In the Service objects form, click Designer to open the Designer form to modify the template BOM.

## Automatically created service orders

If you automatically create service orders for a service agreement, the service
object relations in the agreement are also created in the service orders.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]