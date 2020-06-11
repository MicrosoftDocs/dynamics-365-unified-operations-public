---
# required metadata

title: Engineering change management
description: Engineering change management gives you the possibility to have a structured process to manage changes to engineering products. There are structured processes for proposing, requesting, and making changes. This are also processes for reviewing and approving changes, assessing the impact on existing transactions, and following up.
author: XXXX
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---


# Engineering change management

Engineering change management gives you the possibility to have a *structured process to manage changes to engineering products*. There is a structured process for proposing and requesting changes in the *engineering change request* and there is a structured process for making changes in the *engineering change order*. This will allow you to create the engineering change request and engineering change order, have a process for reviewing and approving them, assessing the impact on existing transactions and following up on them.

## Engineering change request

The engineering change request allows you to capture requests for change from all involved departments within the organization. It does not matter if you are an engineer, work in manufacturing, sourcing, warehouse or on a sales department, with the engineering change request anybody can make a request for change. This can be **an idea for a new product, an issue which you discovered while working with the product, a suggestion for improving the product** etcetera. After documenting the request for change, the **review and approval process** will be handled by a workflow in which you can use as an example the **product owner** asan approver. For more information about the workflow see [Workflow system overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/overview-workflow-system?toc=/dynamics365/supply-chain/toc.json) and for more information on the product owner, see ….

As part of the review of the request for change, you can use the **dependencies** option to assess the impact of the requested change on open transaction like sales orders, production order and inventory on-hand. With the **search** option the system scans all open transactions and you can view them with the **view** option. If the issue that requires a change is found critical, you can already block the open transactions or notify the responsible user via processing the actions.

## Engineering change order

The engineering change order allows you to make changes to engineering products in a structured process. You will **propose changes** on a **copy of the engineering relevant data** without affecting the real master data yet. For more information on engineering relevant data, see … (engineering versions &amp; engineering product type). The engineering change order can be created based on approved engineering change requests, but it is also possible as an engineer to create them from scratch. You can include multiple products in a single engineering change order:

- Manually select products
- Use the bill of material to include products lower in the product structure (children)
- Use a where-used search to include products higher in the product structure (parents)

When the proposal for changes is finished, the **review and approval process** will be handled by a workflow. You can setup different workflows based on the priority and severity. For more information about the workflow see [Workflow system overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/overview-workflow-system?toc=/dynamics365/supply-chain/toc.json).

Typical stakeholders for approving the engineering change order can be:

- Product owners, for more information, see … (product owners)
- Responsible team lead: the engineering who created the engineering change order is stored in the **Engineer** field at the header of the engineering change order. In case he is a part of a **team** in the system, the **team leader** of the team will be added in the **responsible** field at the header of the engineering change order
- Finance department in case the change involves high costs

It can be chosen if the **processing** the engineering change order is done directly after approval of the engineering change order in the workflow or as a manual step. Processing the engineering change order, will update the engineering data actual product master data.

As part of the review of the request for change, you can use the **dependencies** option to assess the impact of the proposed change on open transaction like sales orders, production order and inventory on-hand. With the **search** option the system scans all open transactions and you can view them with the **view** option. You can block the open transactions or notify the responsible user via processing the actions.

### Engineering change order in engineering organization or operational organization

As described in the … (engineering organization &amp; data ownership rules), there is a difference in which data you can change in a legal entity, based on the engineering organization for the product. These rules are also applied in the engineering change order, so based on the legal entity where you create the engineering change order, different types of changes can be made:

- **Engineering change order in engineering organization:** you can make basic changes to the engineering data. As examples this includes creating new versions of the products, changing the products structure via the bill of materials, changing engineering attribute values. You can edit the field **impact** and choose between the following options:
  - **None** : an update to the existing version (in-version update)
  - **New**** version**: a new version will be created based on the selected version
  - **New product** : a completely new product or a new product variant will be created based on the selected product version
- **Engineering change order in operational organization:** you can make changes to the logistical data of the product. This can be just enriching the existing bill of materials with settings for sourcing. It can be adding local routes or even local bill of materials. But it can also be enriching the bill of material by adding new bill of material lines for local packaging materials, lubrication fluids or instructions in the local language. Whenever these enrichments have been done in the operational organization, they will be preserved when new updates are sent over from the engineering organization again. For more info see … (Engineering organization &amp; data ownership rules).

When the engineering change order is processed in the engineering organization, the products are created and/ or updated in the engineering organization only, so you will need to release the products to operational organizations to have the product master data updated there as well:

- You can release directly from the engineering change order manually with the **Release products** option. This is the same option as when doing it from a released product. For more information see … (Release management)
- You can release automatically from the engineering change order, based on:
  - re-releasing to companies where the product previously is released to. With the **search** option the system scans all previous releases and you can view them with the **view** option. With the **process** option, you will re-release them.
  - auto release settings in the release control of the engineering product type. You can do this as part of the workflow. With the block **collect release proposal** , the release proposal will be populated with **re-releasing proposals** (see previous bullet) and products to companies based on the **auto release** checkmark in the release control of the engineering product type. The result can be viewed also via the **view** option as described in the previous bullet. With the block **process release proposal** , the products will be released as well. If you choose to only collect the release proposal as part of the workflow, you can manually start the release via the **process** option as described in the previous bullet.

## Following up an engineering change request by an engineering change order

As soon as an engineering change request is approved, you can follow it up by an engineering change order. It is possible to combine multiple engineering change requests into a single engineering change order, where it can even involve different products. Normally this could be applicable in case the same change needs to be applied on multiple products. However, it is not possible to create multiple engineering change orders from a single engineering change request.

You can start the process as well from the engineering change request with the option **Add to ECO**. From the engineering change order, you can start the process when adding a new impacted product with the option **New/ Products from change requests**.

## Engineering change order report

You can use the engineering change order report to review what changes are made in the engineering change order. This can be very helpful during the review and approval process, but also afterwards to review what is the change made on a certain engineering change order.

## Fields on the engineering change order

Almost all fields on the engineering change order are the same as on the released products, engineering versions, documents, bill of material (lines) and route (operations). The following fields on the fast tab change information are an exception:

| **Fields** | **Description** |
| --- | --- |
| Engineering change reasons | You can choose the reason for change for the impacted product |
| Change description | You can provide a description of what the change is about |
| Required special tooling | You can specify if special tooling is required for applying the change |
| Engineering material disposition | You can choose a material disposition code for the waste when applying the change |
| Customer approval required | You can indicate if a customer approval is required before applying the change |
| Received customer approval | You can choose what the status is on the customer approval |
| Environmental Health and Safety | You can first indicate if environmental, health and safety rules are applicable. If so, you can select the rules that are applicable for the change |

With the **maintain/ copy change information** button, you can copy the change information between impacted products.