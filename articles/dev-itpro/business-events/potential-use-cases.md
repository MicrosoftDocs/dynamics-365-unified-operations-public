---
# required metadata

title: Use cases for business events
description: This topic lists use cases for business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 03/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Use cases for business events

[!include[banner](../includes/banner.md)]
[!include[preview-banner](../includes/preview-banner.md)]

The following are potential uses cases for business events. This is by no means an exhaustive list of the potential use cases. It should also be noted that some of these use cases may not have been implemented yet either by Microsoft or other organizations. These are meant to provide ideas and help with understanding certain business events.

| **Use case**                         | **Value**  |
|----------------------------------------|----------|
| The procurement process frequently relies on manual intervention, so automating this process should increase procurement manager productivity.             | You can make the procurement process more efficient by alerting procurement managers when quotation requests are sent, allowing for prompt follow up and faster engagement. The goal is to have procurement managers follow up within three days and possibly create a Flow that automates this follow up. |
| Managers are not informed about newly created financial reports. As a result, managers might analyze and make decisions based on outdated data.          | You can make the reporting process more efficient by alerting managers when financial reports are sent, allowing for prompt follow up and faster engagement. The goal is to have managers follow up within three days and possibly create a Flow that automates this follow-up.                            |
| When a new customer is created, a credit limit check is needed. If something could automatically trigger an API that subscribes to a credit limit, and then check the website and import specific credit limit check fields, such as limit amount and rating. At the same time, an approval Flow needs to start so that the customer account can be used after approval from management. | This is required by many companies, especially in the retail area. This would be beneficial because partners develop customizations for this purpose.   |
| The month-end closing schedule is a simple list that does not allow automatic actions. If functionality could be created to inform a group of people about tasks that have been completed and verified as complete, then a different group of people could start working.    | Use real-life scenarios to enhance the currently static and difficult to use month-end closing workspace.  |
| If functionality could be created to trigger a flow when the status of a period is changed – either opened or closed.  | Users are not automatically informed when new periods are opened after the month-end close is completed and they are allowed to start recording transactions in the new period.                             |
| When using the supplier (Vendor) collaboration workspace functionality, there is no automated way to inform the supplier that new record has been created, or existing records have been updated (With new attachments etc.) This issue is evident for both RFQ and PO functionality and means the supplier would need to constantly review the D365FO supplier collaboration workspace, on the off chance something changes.     | If business events were added, the supplier portal functionality will provide improved productivity and efficiency by removing the need for additional correspondence between the supplier and the D365FO company. This leads to true collaboration and will lead to supply chain efficiency. Without the functionality being implemented, the D365FO company must follow up any new requests / change information with phone calls / emails to the suppliers. This is the improvement the supplier collaboration workspace was aiming to achieve. |
| In D365CE a quotation is placed for a bespoke product, when the quotation is won the bespoke product needs to become a real product. From CE requests are sent to a Data team (PowerApp, Office) to create the item in D365FO. Once the item has been manually created in FO, the item on the CE line is updated and the CE Quote can be triggered to make a sales order in FO. Currently once the item is created in FO, the approach is to wait for the data integrator to copy it to CDS. CE monitors new entries on CDS and compares the unique CE references to its own open numbers. Ideal – an Item created business event exists, we extend it so it has the CE unique identifier. This event is then subscribed to (flow/logicapp) and immediately updates the CE quote line. | If business events were added, the business would be able to update the won quote with the new product at the creation of the new product. This will remove delays, manual changes and errors.          |
| Shipment for Sales orders can be undertaken in a different system to enable logistics balancing of third-party haulers, production of customs and delivery documentation. Pushing the data to a major transport company like DHL, FedEx, UPS, Blue Dart, Royal Mail. On the picking OR shipment of a sales order the line details are the event to tell the external system to analyze and decide upon utilized shipment. The decision on the pushing event depends upon the ability for a business action to update D365FO, it could be the order is picked and then the shipment information pushed into D365FO or it is marked as shipped in D365FO as it is pushed externally.   | This allows businesses with third party transport companies to send the shipping information to the vendors. This approach is putting the weight of dispatch utilization onto the external vendors and simplifies the setup in D365FO.    |
| Picking for Sales orders can be undertaken in a different system, whether this is a separate warehousing system internally or a third-party location that is not on the D365FO system. On the confirmation OR picking of a sales order the line details are the event to tell the external system to analyze and decide upon utilized picking.   | This allows businesses with third party warehouses to send the picking information to the system. This can also be used where the warehouse has automated picking machines and needs to understand what is required when. This approach is putting the weight of picking priority and utilization onto the external system and simplifies the setup in D365FO.     |
