---
title: Plan freight transportation routes with multiple stops
description: Learn about the various elements that you use to plan transportation routes in Dynamics 365 Supply Chain Management with an outline on route plans.
author: lisascholz
ms.author: lisascholz
ms.topic: overview
ms.date: 11/28/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: TMSHubMaster, TMSLoadBuildTemplates, TMSRateRouteWorkbench, TMSRouteGuide, TMSRoutePlan, TMSRouteWorkbench, WHSLoadTemplate, TMSRouteSchedule, TMSRouteRateDetail
---

# Plan freight transportation routes with multiple stops

[!include [banner](../includes/banner.md)]

This article describes the various elements that you use to plan transportation routes in Dynamics 365 Supply Chain Management.

You can use route plans and route guides for complex transportation routes that have multiple stops. If you regularly use the same route, you can set up a scheduled route.

## Route plans

A route plan contains route segments that provide information about the stops that are visited on the route and the carriers that are used for each segment. You must define the stops on the route as hubs. A hub can be a vendor, a warehouse, a customer, or even just a reloading place where you change carrier. For each segment, you can define “spot rates” for various charges. Here are some examples:

- Charges for traveling to the given segments
- Charges for picking up the goods
- Charges for dropping off the goods

Each route plan must be associated with a route guide.

## Route guides

A route guide defines the criteria for matching a load to a specific route plan. For example, you can specify an origin hub and a destination hub, limits for the container volume or weight, and a shipping carrier, service, or group. Route guides are available on the **Rate route workbench** page, where loads can be matched to routes either manually or automatically. If the route guide is for a scheduled route, it's also available on the **Load building workbench** page.

## Scheduled routes

A scheduled route is a predefined route plan that has a schedule for the shipping dates. Scheduled routes and nonscheduled routes differ in the way that loads are assigned to them. If you assign a nonscheduled route by using the Rate route workbench, only the load and the route guide are validated. If you assign a scheduled route, the dates and addresses from the orders and the hubs, and the date on the route plan, are also considered. You don't have to use the Rate route workbench page to manually assign loads to a scheduled route. Instead, you can use the Load building workbench to suggest that loads be built based on the customer addresses and delivery dates from sales orders for a given scheduled route. For scheduled routes, the route plan has fixed origin and destination hubs. Typically, the shipping carrier and service are the same for all segments, but they can differ. The destination hubs are created by using the postal codes of the customers that are visited on the route. Several route schedules can be defined for one route plan. The route plan must be associated with a route guide. However, for scheduled routes, the plan can be associated with only one route guide. The route schedule is used only to create the actual routes on the **Route schedule** page. You can use the default load template when you propose loads on the Load building workbench.

## Load building workbench

The Load building workbench uses the customer addresses and delivery dates from sales orders, and the scheduled routes that are available, to propose a load. By default, the values from the route are entered on the workbench. However, you can select a "from" date that is earlier than the "from" date on the route. When a load is proposed, the delivery address and delivery date of all open sales orders are checked. A sales order is proposed for a load if the postal code of the delivery address matches the postal code of a hub in the route plan, and if the delivery date is within the range that is selected in the criteria. The capacity of the load template is also considered. Only one load is proposed at a time. If you have a sales order that isn't included, you might have to use a different load template (for example, a load template for a bigger truck or container) or plan an extra delivery.

## Sustainable transportation planning

Supply Chain Management offers sustainable transportation planning by integrating with Microsoft Sustainability Manager for the calculation of carbon emissions.

Sustainable transportation planning can help companies reduce their carbon footprint by optimizing routes, reducing fuel consumption, minimizing empty miles, and increasing the use of lower-emission transportation modes. Companies can achieve better visibility, control, and automation for their transportation operations. By reducing fuel consumption and carbon emissions, companies can minimize their environmental impact and play a part in combatting climate change. In addition, by demonstrating a commitment to sustainability, companies can improve their brand image and attract environmentally conscious customers.

- **System integration** – The integration between Supply Chain Management and Microsoft Sustainability Manager uses REST APIs. Therefore, data can flow seamlessly between the two systems, and organizations can track sustainability metrics alongside their other business processes.
- **Carbon emission calculation** – Microsoft Sustainability Manager uses the route data from Supply Chain Management to offer a variety of data models and services that can help organizations calculate and analyze transportation-related carbon emissions. The route data can be used to calculate emissions from different modes of transportation, including cars, trucks, planes, and ships.
- **Route planning with carbon dioxide equivalent (CO2e) results** – After Microsoft Sustainability Manager returns the calculated emissions for each mode of transportation, you can compare them to determine which mode emits the least carbon dioxide. You can select the most eco-friendly route, based on the emissions calculation, or select the mode of transportation that has the lowest carbon emissions in the transportation management rate and route workbench.

Learn more in [Integrate with Microsoft Sustainability Manager](sustainability-manager-integration-setup.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
