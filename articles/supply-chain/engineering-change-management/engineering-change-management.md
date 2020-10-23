---
# required metadata

title: Manage changes to engineering products
description: This topic provides information about engineering change management. Engineering change management provides structured processes for managing changes to engineering products, from proposing, requesting, and making changes, to reviewing and approving changes, assessing their impact on existing transactions, and following up on them.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  EngChgEcmRequestSelection,EngChgEcmRequestProducts,EngChgEcmRequestPriorityChart,EngChgEcmRequestListPage,EngChgEcmRequestFilteredPart,EngChgEcmRequestDetails,EngChgEcmReason,EngChgEcmProjTableInformation,EngChgEcmProductRoute,EngChgEcmProductRelease,EngChgEcmProductPreview, EngChgEcmWhereUsed, EngChgEcmInventTrans,EngChgEcmHeaderSelection,EngChgEcmHeaderPreviewPart,EngChgEcmHeaderFilteredPart,EngChgEcmHeaderDetails, EngChgCaseWhereUsedAnalysis, EngChgCaseValidatorMessage
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
---

# Manage changes to engineering products

[!include [banner](../includes/banner.md)]

Engineering change management provides structured processes for managing changes to engineering products. You can use the *engineering change request* process to propose and request changes, and then use the *engineering change order* process to actually make those changes. Users can create engineering change requests or engineering change orders, and there is then a process for reviewing and approving them, assessing their impact on existing transactions, and following up on them.

## Engineering change requests

The engineering change request process lets you capture requests for changes from all the relevant departments in your company. It doesn't matter whether you work as an engineer, or in the Manufacturing, Sourcing, Warehouse, or Sales department: anybody can use an engineering change request to request a change. This change might be an idea for a new product, an issue that you discovered while you were working with an existing product, a suggestion for improving an existing product, or something else.

After someone submits a request for change, the *review and approval* process is managed by a workflow that identifies who must approve the change (for example, the product owner).

To set up a workflow for engineering change orders or engineering change requests, go to **Engineering change management \> Engineering workflows**. Select **New**, select whether the workflow will be used to review engineering change orders or engineering change requests, and then configure the workflow.

For more information about workflows see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md). For more information about product owners, see [Product owners](product-owner.md).

### Create a new engineering change request

To create an engineering change request, follow one of these steps.

- Go to **Engineering change management \> Common \> Engineering change management \> Engineering change requests**, and then select **New** on the Action Pane.
- Open the **Product details** page for an existing engineering product. Then, on the Action Pane, on the **Engineer** tab, in the **Engineering change management** group, select **Engineering change request \> New engineering change request**.

A new change request is created. You can now set the fields on each FastTab, as described in the following subsections.

#### General FastTab

The **General** FastTab lets you provide a basic description of the change request. The following table describes the fields on this FastTab.

| Field | Description |
|---|---|
| Change request | Enter a name for the engineering change request. |
| Title | Enter text that briefly describes or identifies the changes in the request. |
| Priority | Select a value to indicate how high the priority of the change is. You can customize the available values for your company, as required. (For more information, see [Establish common values for engineering change management](engineering-change-management-setup.md).) |
| Category | Select a value to describe the type of change that you're requesting. You can customize the available values for your company, as required. (For more information, see [Establish common values for engineering change management](engineering-change-management-setup.md).) |
| Severity | Select a value to indicate the severity of the issue that should be fixed by implementing the request. You can customize the available values for your company, as required. (For more information, see [Establish common values for engineering change management](engineering-change-management-setup.md).) |
| Requested by | The name of the user who created the request. |
| On | The date when the request was created. |
| Status | The status of the request. When a request is first created, the status is *Created*. When the request is approved, the status changes to *Approved*. If a related change order has been created for the request, the status changes to *Followed up*. |
| Change order | The change order number, if the change request was followed up on via a change order. |

#### Information FastTab

The **Information** FastTab lets you add more information about the request.

To add a row to the grid, select **New** on the toolbar above the grid, and then select one of the following options:

- **File** – Upload a file.
- **Image** – Upload an image file.
- **Note** – Enter a note directly in the grid.
- **URL** – Enter a URL directly in the grid.

The following table describes the fields on each row.

| Field | Description |
|---|---|
| Created date and time | The date and time when the row was created. |
| Type | The type of information that the row was created for (file, image, note, or URL). |
| Description | Enter a description for the row. |
| Restriction | A value that indicates whether the information that has been added came from an internal or external source. |
| Attached | A selected check box indicates that the row includes an attachment (file or image). To download the attachment, select the row, and then select **Open** on the toolbar above the grid. |

#### Products FastTab

The **Products** FastTab lets you list each product that is affected by the change request. You can use the buttons on the toolbar to add products to the grid, or to remove products.

This list is for informational purposes only. Therefore, you can add as many related products as you consider relevant. If you create a change request from the **Product details** page for an existing product, that product should be listed on the **Products** FastTab after you save the request record.

#### Source FastTab

The **Source** FastTab lets you track the starting point of the change request. It's useful if, for example, you want to see whether the change request was created from a sales order, who created it, and which company it was created in.

### Evaluate the business impact of a change request

When you review a request for change, you can search for dependencies. In this way, you can assess the impact of the requested change on open transactions, such as sales orders, production orders, and on-hand inventory.

1. Go to **Engineering change management \> Common \> Engineering change management \> Engineering change requests**.
1. Either open an existing change request, or select **New** on the Action Pane to create a new change request.
1. On the Action Pane, on the **Change request** tab, in the **Business impact** group, select one of the following buttons:

    - **Search** – Scans all open transactions, and then open the **Business impact to open transactions** dialog box, which lists all transactions that will be affected by the change.
    - **View previous search** – Open the **Business impact to open transactions** dialog box, which lists the results of the previous search. (A new search isn't done.)

1. If the issue that requires a change is found to be critical, you can block the open transactions or notify the responsible user by using the buttons on the toolbar in the **Business impact to open transactions** dialog box.

### Create a change order from a change request

An engineer who is reviewing an engineering change request can create an engineering change order directly from the change request page. On the Action Pane, on the **Change request** tab, in the **Engineering change order** group, select **Copy link and products**.

## Engineering change orders

Engineering change orders provide a structured process for making changes to engineering products. You propose changes by using a copy of the engineering-relevant data. The real master data isn't affected. For more information about engineering-relevant data, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

You can create an engineering change order that is based on an approved engineering change request. Engineers can also create engineering change orders from scratch. You can include multiple products on a single engineering change order by following any of these steps:

- Manually select products.
- Use the bill of materials (BOM) to include products that are lower in the product structure (that is, children).
- Use a where-used search to include products that are higher in the product structure (that is, parents).

After the proposal for changes is completed, the review and approval process will be handled by a workflow. You can set up different workflows, based on priority and severity.

To set up a workflow for engineering change orders or engineering change requests, go to **Engineering change management \> Engineering workflows**. Select **New**, select whether the workflow will be used to review engineering change orders or engineering change requests, and then configure the workflow.

For more information about workflows, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).

Here are some typical stakeholders who might have to approve an engineering change order:

- **Product owners** – For more information about product owners, see [Product owners](product-owner.md).
- **Responsible team lead** – The **Engineer** field in the **Header** view of the engineering change order shows the engineer who created the engineering change order. If the engineer belongs to a team that is defined in the system, the **Responsible** field shows the leader of that team.
- **Finance department** – The Finance department might have to review cases where the change involves high costs.

You can choose whether the engineering change order should be processed directly after it's approved, as part of the workflow, or whether the processing should be done later, as a manual step. During processing of an engineering change order, engineering data on the actual product is updated.

While you're reviewing a request for change, you can use the **Dependencies** button on the Action Pane to assess the impact of the proposed change on open transactions, such as sales orders, production orders, and inventory on-hand. You can select **Search** to scan all open transactions, and then select **View** to view the results. You can then block the open transactions or notify the responsible user via processing the actions.

### Engineering change orders in engineering or operational companies

As is described in [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md), the product data that you can edit varies, depending on the type of legal entity that you're working in (an engineering company versus an operational company). Data ownership rules are also applied to engineering change orders. Therefore, depending on the legal entity where you create an engineering change order, different types of changes can be made. Here are some examples:

- For engineering change orders in an **engineering company**, you can make basic changes to the engineering data. For example, you can create new versions of a product, change a product's structure via the BOM, and change engineering attribute values. For each affected product, select one of the following values in the **Impact** field:

    - **None** – Update the existing product version (in-version update).
    - **New version** – Create a new version that is based on the selected product version.
    - **New product** – Create a completely new product or product variant that is based on the selected product version.

- For engineering change orders in an **operational company**, you can change the logistical data of the product. For example, you can enrich the existing BOM with settings for sourcing, add local routes or local BOMs, and even enrich a BOM by adding new BOM lines for local packaging materials, lubrication fluids, or instructions in the local language. Enrichments that users make in the operational company will be preserved when new updates are sent from the engineering company. For more information, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).

    When engineering change orders are processed in the engineering company, the products are created and/or updated only in the engineering company. Therefore, if the product master data should also be updated, you must also release the products to operational companies.

- You can release products directly from engineering change orders. Open the change order, and then, on the Action Pane, on the **Change order** tab, in the **Product releases** group, select **Release product structure**. The process works just as it works when you release products from a released products page. For more information, see [Release product structures](release-product-structure.md).
- You can have products automatically released from engineering change orders, based on the following factors:

    - Re-releases to companies where products were previously released. Select **Search** to scan all previous releases, and then select **View** to view the results. The **View** page shows the previous product releases, and you can select which products you want to re-release. Then close the **View** page, and select **Process** to re-release the selected products.
    - Automatic release settings in the release control of the engineering product category. You can do this release as part of the workflow. When the **collect release proposal** block is used, the release proposal will be filled with re-releasing proposals (see the previous list item), and products will be released to companies if the **Auto release** check box is selected in the release control of the engineering product category. You can select **View** to view the results, as described in the previous list item. The products will also be released when the **process release proposal** block is used. If you choose only to collect the release proposal as part of the workflow, you can manually start the release by selecting **Process**, as described in the previous list item.

## Follow up on an engineering change request via an engineering change order

As soon as an engineering change request is approved, you can follow up on it via an engineering change order. You can combine multiple engineering change requests into a single engineering change order. A single engineering change order can even include multiple products. (Typically, you use this approach when the same change must be applied to multiple products.) However, you can't create multiple engineering change orders from a single engineering change request.

To follow up on a change request via a change order, open the change request, and then, on the Action Pane, on the **Change order** tab, in the **Engineering change order** group, select **Copy link and products**. You can then select an existing engineering change order to connect the change request to, or you can create a new engineering change order for that specific request.

## Engineering change order report

Engineering change order reports describe the changes that were made in an engineering change order. They are useful both during and after the review and approval process.

To view an engineering change order report, open the relevant change order, and then, on the Action Pane, on the **Change order** tab, in the **View** group, select **Engineering change order report**.

## Fields on an engineering change order

Most of the fields on engineering change orders are the same as the fields for released products, engineering versions, documents, BOMs (lines) and routes (operations). However, the fields in the following table are unique to change orders.

| Field | Description |
|---|---|
| Engineering change reasons | Select the reason for changing the affected product. |
| Change description | Enter a description of the change. |
| Required special tooling | Specify whether special tooling is required to apply the change. |
| Engineering material disposition | Select a material disposition code for the waste when the change is applied. |
| Customer approval required | Specify whether customer approval is required before the change can be applied. |
| Received customer approval | Specify the status of the customer approval. |
| Environmental health and safety | Specify whether environmental health and safety rules are applicable to the change. If they are, you can then select the applicable rules. |

You can use the **Maintain/copy change information** button to copy change information between affected products.
