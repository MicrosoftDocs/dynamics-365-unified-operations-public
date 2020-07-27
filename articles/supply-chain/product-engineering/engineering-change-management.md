---
# required metadata

title: Engineering change management
description: Engineering change management gives you the possibility to have a structured process to manage changes to engineering products. There are structured processes for proposing, requesting, and making changes. This are also processes for reviewing and approving changes, assessing the impact on existing transactions, and following up.
author: t-benebo
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

[!include [banner](../includes/banner.md)]

Engineering change management provides a structured processes for managing changes to engineering products. Use the *engineering change request* process to propose and request changes; use the *engineering change order* process to actually make the changes. This lets users create an engineering change request or engineering change order, and then have a process for reviewing and approving them, assessing their impact on existing transactions, and following up on them.

## Engineering change requests

The engineering change request allows you to capture requests for change from all the relevant departments within your organization. It doesn't matter whether you work as an engineer, or in the manufacturing, sourcing, warehouse, or sales department&mdash;with the engineering change request, anybody can request a change. This can be an idea for a new product, an issue that you discovered while working with an existing product, a suggestion for improving the product, or something else.

After someone submits a request for change, the *review and approval process* is managed by a workflow that establishes who needs to approve it (for example, the product owner). For more information about workflows see the [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md). For more information about product owners, see [Product owner](product-owner.md). <!-- KFM: How do we add a workflow here? -->

### Create a new engineering change request

To create an engineering change request, do one of the following:
- Go to **Project Oaktree \> Common \> Engineering change management > Engineering change requests** and then select **New** from the Action Pane.
- Open the **Product details** page for an existing engineering product. Then, on the Action Pane, open the **Engineer** tab and, from the **Project Oaktree** group, select **Engineering change request > New engineering change request**.

A new change request is created. Then make the settings on each FastTab, as described in the following subsections.

#### The General FastTab

Use the **General** FastTab to provide a basic description of the change request. Make the settings described in the following table.

| **Setting** | Description |
| --- | --- |
| **Change request** | <!-- KFM: Describe this setting. How is this different from the title?  --> |
| **Title** | <!-- KFM: Describe this setting.  --> |
| **Priority** | Select a value to describe how highly to prioritize this change. You can customize the values available here as required for your organization (see also [Establish common values for engineering change management](engineering-change-management-setup.md)). |
| **Category** | Select a value to describe the type of change you are requesting. You can customize the values available here as required for your organization (see also [Establish common values for engineering change management](engineering-change-management-setup.md)). |
| **Severity** | Select a value to describe how severe the problem is that should be resolved by implementing this request. You can customize the values available here as required for your organization (see also [Establish common values for engineering change management](engineering-change-management-setup.md)). |
| **Requested by** | Shows the name of the user who created the request |
| **On** | Shows the date the request was created. |
| **Status** | Shows the status of the request. When first created, the status is *Created*. When approved, the status changes to *Approved*. <!-- KFM: Other values? --> |
| **Change order** | <!-- KFM: Describe this setting.  --> |

#### The Information FastTab

Use the **Information** FastTab to add more information about your request.

To add a new row here, open the New menu from the **Information** toolbar and select one of the following:

- **File** - To upload a file.
- **Image** - To upload an image file.
- **Note** - To enter a note directly into the grid.
- **URL** - To enter a URL directly into the grid. <!-- KFM: Do we do anything special with URLs? Seems exactly like the Note option.  -->

Each row provides the settings and information described in the following table.

| **Setting** | Description |
| --- | --- |
| **Created date and time** | Shows the date and time that the row was created. |
| **Type** | Shows the type that was selected when the row was created (file, image, note, or URL). |
| **Description** | Enter a description for the row. |
| **Restriction** | <!-- KFM: Describe this setting.  --> |
| **Attached** | If the row includes an attachment (file or image), then a check mark is shown here. To download the attachment, select the row and then select **Open** from the **Information** toolbar |

#### The Products FastTab

The **Products** FastTab can list each product affected by the change request. Use buttons in the toolbar to add or remove products in the grid.

<!-- KFM: What are some features and effects of this list? Affects business impact search? Should a product already be here if I create a request from the product details page (didn't do that when I tried it)? -->

#### The Source FastTab

<!-- KFM: Describe this FastTab and its settings/information.  -->

### Evaluate the business impact of a change request

As part of the review of the request for change, you can use the **dependencies** option to assess the impact of the requested change on open transaction like sales orders, production order and inventory on-hand. With the **search** option the system scans all open transactions and you can view them with the **view** option. If the issue that requires a change is found critical, you can already block the open transactions or notify the responsible user via processing the actions. <!-- KFM: I think this belongs here, but the labels have changed. Now the tab is called "Business impact". Is that right? Please update with the correct labels if this is the case.-->

### Review and approve change requests

### Create a change order from a change request

<!-- KFM: We should describe how to create a change order from a change request.  -->

## Engineering change orders

Engineering change orders let you make changes to engineering products using a structured process. You propose changes using a copy of the engineering relevant data without affecting the real master data. For more information on engineering relevant data, see [Engineering versions and engineering product category](engineering-versions-product-category.md). You can create an engineering change order based on an approved engineering change requests, but engineers can also create them from scratch. You can include multiple products in a single engineering change order by doing any of the following:

- Manually select products
- Use the bill of material to include products lower in the product structure (children)
- Use a where-used search to include products higher in the product structure (parents)

<!-- KFM: We should have a procedure here about how to create an engineering change order, and describe all of the options that are available. -->

When the proposal for changes is finished, the review and approval process will be handled by a workflow. You can set up different workflows based on the priority and severity. For more information about workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md). <!-- KFM: How do we attach a workflow to a change order? -->

Typical stakeholders for approving an engineering change order include:

- **Product owners**: For more about product owners, see [Product owner](product-owner.md).
- **Responsible team lead**: the engineering who created the engineering change order is stored in the **Engineer** field, on the **Header** tab of the engineering change order. If this engineer is a part of a team in the system, the team leader of that team will be added in the **Responsible** field on the **Header** tab of the engineering change order.
- **Finance department**: in cases where the change involves high costs.

You can choose whether the engineering change order should be processed directly after approval as part of the workflow, or as a manual step afterwards. <!-- KFM: How do we choose this? --> Processing an engineering change order will update engineering data on the actual product master.

While you are reviewing a request for change, use the **dependencies** option <!-- KFM: where is this option? --> to assess the impact of the proposed change on open transaction like sales orders, production orders, and inventory on-hand. With the **search** option, the system scans all open transactions and you can view them with the **view** option. You can block the open transactions or notify the responsible user via processing the actions. <!-- KFM: where is these options? "Where used", or "Impacted products" maybe? We should have a procedure for how to review a request for change, including steps for how to use each of these options. -->

### Engineering change orders in engineering or operational organizations

As described in [Engineering organization and data ownership rules](engineering-org-data-ownership-rules.md), there is a difference in which data you can change in a legal entity, based on the engineering organization for the product. These rules are also applied in the engineering change order, so based on the legal entity where you create the engineering change order, different types of changes can be made, including: <!-- KFM: I don't understand what we are talking about here. Does this have something to do with the type of legal entity a user belongs to? -->

- **Engineering change orders in an engineering organization:** you can make basic changes to the engineering data. This includes creating new versions of a product, changing a product's structure via the bill of materials, and changing engineering attribute values. Select one of the following options from the **Impact** field: <!-- KFM: where is this field? What is the context here? Why is this the only field we are talking about? -->
  - **None**: To update the existing product version (in-version update).
  - **New version**: To create a new version based on the selected version.
  - **New product** : To create a completely new product or product variant based on the selected product version.
- **Engineering change orders in an operational organization:** you can make changes to the logistical data of the product. For example, you could enrich the existing bill of materials with settings for sourcing; add local routes or local bills of materials; or even enrich a bill of material by adding new bill of material lines for local packaging materials, lubrication fluids, or instructions in the local language. Whenever a user makes these enrichments in the operational organization, they will be preserved when new updates are sent over from the engineering organization again. See also [Engineering organization and data ownership rules](engineering-org-data-ownership-rules.md).

    When the engineering change order is processed in the engineering organization, the products are created and/or updated in the engineering organization only, so you must also release the products to operational organizations to have the product master data updated too.

- You can release directly from the engineering change order manually with the **Release products** option<!-- KFM: where is this option? -->. This is the same option as when doing it from a released product. For more information see [Release product structure](release-product-structure.md).
- You can release automatically from the engineering change order based on:
  - Re-releasing to companies where the product was previously released. Use the **search** option to scan all previous releases, which you can view with the **view** option. Use the **process** option to re-release them.<!-- KFM: where are these options? How do we use them? -->
  - Auto-release settings in the release control of the engineering product category. You can do this as part of the workflow. With the block **collect release proposal** , the release proposal will be populated with **re-releasing proposals** (see previous bullet) and products to companies based on the **auto release** check mark in the release control of the engineering product category. The result can be viewed also via the **view** option as described in the previous bullet. With the block **process release proposal** , the products will be released as well. If you choose to only collect the release proposal as part of the workflow, you can manually start the release via the **process** option as described in the previous bullet.

## Follow up an engineering change request with an engineering change order

As soon as an engineering change request is approved, you can follow it up with an engineering change order. You can combine multiple engineering change requests into a single engineering change order, which can even include different products. You'd typically do this when applying the same change needs to multiple products. However, you can't create multiple engineering change orders from a single engineering change request.

<!-- KFM: We should provide the procedure for how to do this here. -->

You can start the process as well from the engineering change request with the option **Add to ECO**. From the engineering change order, you can start the process when adding a new impacted product with the option **New/ Products from change requests**.

<!-- KFM: We should provide the procedure for how to do this here. -->

## Engineering change order report

Engineering change order reports describe the changes made in an engineering change order. They are useful both during the review and approval process and afterwards, so you can review the changes made by a selected engineering change order.

<!-- KFM: We should provide the procedure for how to create and use this type of report here. -->

## Fields on the engineering change order

Almost all fields on the engineering change order are the same as on the released products, engineering versions, documents, bill of material (lines) and route (operations). However, the fields listed in the following table are unique to the change order:

| Field | Description |
| --- | --- |
| **Engineering change reasons** | Choose the reason for change for the impacted product. |
| **Change description** | Provide a description of what the change is about |
| **Required special tooling** | Specify whether special tooling is required for applying the change |
| **Engineering material disposition** | Choose a material disposition code for the waste when applying the change |
| **Customer approval required** | Indicate if a customer approval is required before applying the change. |
| **Received customer approval** | Specify the status of the customer approval |
| **Environmental health and safety** | You can first indicate if environmental, health and safety rules are applicable. If so, you can select the rules that are applicable for the change |

Use the **maintain / copy change information** button to copy change information between impacted products.
