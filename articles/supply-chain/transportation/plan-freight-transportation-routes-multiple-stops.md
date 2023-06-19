---
# required metadata

title: Plan freight transportation routes with multiple stops
description: This article describes the various elements that you use to plan transportation routes in Dynamics 365 Supply Chain Management.
author: Weijiesa
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TMSHubMaster, TMSLoadBuildTemplates, TMSRateRouteWorkbench, TMSRouteGuide, TMSRoutePlan, TMSRouteWorkbench, WHSLoadTemplate, TMSRouteSchedule, TMSRouteRateDetail
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 50d6f58c-f1c8-4321-9e83-8445cec57a85
ms.search.region: Global
# ms.search.industry: 
ms.author: weijiesa
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Plan freight transportation routes with multiple stops

[!include [banner](../includes/banner.md)]

This article describes the various elements that you use to plan transportation routes in Dynamics 365 Supply Chain Management.

You can use route plans and route guides for complex transportation routes that have multiple stops. If the same route will be used on a regular basis, you can set up a scheduled route.

## Route plans
A route plan contains route segments that provide information about the stops that are visited on the route and the carriers that are used for each segment. You must define the stops on the route as hubs. A hub can be a vendor, a warehouse, a customer, or even just a reloading place where you change carrier. For each segment, you can define “spot rates” for various charges. Here are some examples:

-   Charges for travelling to the given segments
-   Charges for a picking up the goods
-   Charges for dropping off the goods

Each route plan must be associated with a route guide.

## Route guides
A route guide defines the criteria for matching a load to a specific route plan. For example, you can specify an origin hub and a destination hub, limits for the container volume or weight, and a shipping carrier, service, or group. Route guides are available on the **Rate route workbench** page, where loads can be matched to routes either manually or automatically. If the route guide is for a scheduled route, it's also available on the **Load building workbench** page.

## Scheduled routes
A scheduled route is a predefined route plan that has a schedule for the shipping dates. Scheduled routes and non-scheduled routes differ in the way that loads are assigned to them. If you assign a non-scheduled route by using the Rate route workbench, only the load and the route guide are validated. If you assign a scheduled route, the dates and addresses from the orders and the hubs, and the date on the route plan, are also considered. You don't have to use the Rate route workbench page to manually assign loads to a scheduled route. Instead, you can use the Load building workbench to suggest that loads be built based on the customer addresses and delivery dates from sales orders for a given scheduled route. For scheduled routes, the route plan will have fixed origin and destination hubs. Typically, the shipping carrier and service will be the same for all segments, but they can differ. The destination hubs are created by using the postal codes of the customers that are visited on the route. Several route schedules can be defined for one route plan. The route plan must be associated with a route guide. However, for scheduled routes, the plan can be associated with only one route guide. The route schedule is used only to create the actual routes on the **Route schedule** page. You can use the default load template when you propose loads on the Load building workbench.

## Load building workbench
The Load building workbench uses the customer addresses and delivery dates from sales orders, and the scheduled routes that are available, to propose a load. By default, the values from the route are entered on the workbench. However, you can select a "from" date that is earlier than the "from" date on the route. When a load is proposed, the delivery address and delivery date of all open sales orders are checked. If the postal code of the delivery address matches the postal code of a hub in the route plan, and if the delivery date is within the range that is selected in the criteria, the sales order is proposed for the load. The capacity of the load template is also considered. Only one load is proposed at a time. If you have a sales order that isn't included, you might have to use a different load template (for example, a load template for a bigger truck or container) or plan an extra delivery.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]