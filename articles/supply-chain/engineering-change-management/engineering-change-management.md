---
title: Manage changes to engineering products
description: Learn about engineering change management, which provides structured processes for managing changes to engineering products.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 09/28/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  EngChgEcmRequestSelection,EngChgEcmRequestProducts,EngChgEcmRequestPriorityChart,EngChgEcmRequestListPage,EngChgEcmRequestFilteredPart,EngChgEcmRequestDetails,EngChgEcmReason,EngChgEcmProjTableInformation,EngChgEcmProductRoute,EngChgEcmProductRelease,EngChgEcmProductPreview, EngChgEcmWhereUsed, EngChgEcmInventTrans,EngChgEcmHeaderSelection,EngChgEcmHeaderPreviewPart,EngChgEcmHeaderFilteredPart,EngChgEcmHeaderDetails, EngChgCaseWhereUsedAnalysis, EngChgCaseValidatorMessage
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
| Priority | Select a value to indicate how high the priority of the change is. You can customize the available values for your company, as required. (Learn more in [Establish common values for engineering change management](engineering-change-management-setup.md).) |
| Category | Select a value to describe the type of change that you're requesting. You can customize the available values for your company, as required. (Learn more in [Establish common values for engineering change management](engineering-change-management-setup.md).) |
| Severity | Select a value to indicate the severity of the issue that should be fixed by implementing the request. You can customize the available values for your company, as required. (Learn more in [Establish common values for engineering change management](engineering-change-management-setup.md).) |
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

### Evaluate the business impact of a change request and send notifications

When you review a request for change, you can search for dependencies. In this way, you can assess the impact of the requested change on open transactions, such as sales orders, production orders, and on-hand inventory. As you review change requests, you can send notifications to the people who are responsible for fulfilling the various types of related orders.

#### Review affected transactions, block selected transactions, and send notifications

To review affected transactions, block selected transactions, and send related notifications, follow these steps.

1. Go to **Engineering change management \> Common \> Engineering change management \> Engineering change requests**.
1. Either open an existing change request, or select **New** on the Action Pane to create a new change request.
1. On the Action Pane, on the **Change request** tab, in the **Business impact** group, select one of the following buttons:

    - **Search** – Scans all open transactions, and then open the **Business impact to open transactions** dialog box, which lists all transactions that will be affected by the change.
    - **View previous search** – Open the **Business impact to open transactions** dialog box, which lists the results of the previous search. (A new search isn't done.)

1. The **Business impact to open transactions** dialog box provides a set of tabs, each of which shows a list of affected transactions of a specific type (**Sales orders**, **Purchase orders**, **Production orders**, **Inventory**, and so on). Each tab also shows a number that indicates the number of affected transactions of that type. Select a tab to view the relevant list.
1. To work with a transaction in the list, select it, and then select one of the following buttons on the toolbar:

    - **View transaction** – Open the selected transaction record.
    - **Block order** – This button is available only on the **Sales orders** tab. Select it to block the selected sales order.
    - **Block line** – This button is available only on the **Purchase orders** tab. Select it to block the selected purchase order line.
    - **Notify responsible** – This button is available only on the **Sales orders** tab. Select it to send a change notification to the user who is set as responsible for the selected sales order. For more information about who can see the notifications and how, see [Review and process change notifications for transactions](#review-notifications).
    - **Notify orderer** – This button is available only on the **Purchase orders** tab. Select it to send a change notification to the user who is set as the orderer for the selected purchase order. For more information about who can see the notifications and how, see [Review and process change notifications for transactions](#review-notifications).
    - **Notify production** – This button is available only on the **Production orders** tab. Unlike sales orders and purchase orders, production orders don't have a single user who is set as responsible for them from end to end. Instead, various supervisors or planners usually take ownership for a specific site or for a specific part of the production (for example, for specific resources or resource groups). Therefore, when you select this button, all users who are responsible for any resource that is related to the selected production order receive a change notification. For more information about who can see the notifications and how, see [Review and process change notifications for transactions](#review-notifications).
    - **Notify preparer** – This button is available only on the **Purchase requisition** tab. Select it to send a change notification to the user who is set as the preparer of the selected purchase requisition. For more information about who can see the notifications and how, see [Review and process change notifications for transactions](#review-notifications).
    - **Notify sales responsible** – This button is available only on the **Quotations** tab. Select it to send a change notification to the user who is set as responsible for the selected quotation. For more information about who can see the notifications and how, see [Review and process change notifications for transactions](#review-notifications).
    - **Scrap** – This button is available only on the **Inventory** tab. Select it to scrap the selected inventory.
    - **View history** – Open a history of actions that have been taken on the selected transaction by using the **Business impact to open transactions** dialog box. (For example, the history shows whether notifications have been sent or transactions have been blocked.) 
    - **View all transactions** – Open the full list of all transactions, not just the open transactions.

> [!IMPORTANT]
> The **Notify production** button is available only if the *Engineering notifications for production* feature is turned on for your system. For instructions on how to turn this feature and its prerequisites on or off, see [Engineering change management overview](product-engineering-overview.md).

#### <a name="review-notifications"></a>Review and process change notifications for transactions

You can read and process the change notifications that you receive in the following ways:

- Except in the case of production orders, change notifications for the transactions that you're responsible for appear in the Action center. The **Show messages** button (bell symbol) on the right side of the navigation bar indicates when a message is available for you in the Action center. Select the **Show messages** button to open the Action center and review the messages.
- To view all production orders that an engineering notification has been sent for, go to **Production orders \> Production orders \> All production orders**. Then, on the Action Pane, on the **Production order** tab, in the **Engineering change request** group, select **Engineering notifications** to open the **Engineering notifications** page.
- For production orders, you can choose to review only the change notifications that apply to the production resources that you manage. In the **Production floor management** workspace, on the Action Pane, select **Configure my workspace** to filter the page so it shows only information about the production units, groups, and/or resources that you manage. In the **Summary** section, a tile that is named **Production orders with changed products** shows a count of notifications that match your filter settings. Select this tile to open the **Engineering notifications** page, which shows the full list of transactions that meet the criteria of your filter.

As you're reviewing production order notifications on the **Engineering notifications** page, you can follow links to related change orders or production orders by selecting column values or using the related commands on the Action Pane. After you've finished evaluating a change, and after you've canceled or modified production orders as required, you can mark a notification as resolved. Select the notification, and then, on the Action Pane, select **Resolve**. The notification is removed from all users' views.

> [!IMPORTANT]
> The ability to send notifications for production orders requires that the *Engineering notifications for production* feature be turned on for your system. For instructions on how to turn this feature and its prerequisites on or off, see [Engineering change management overview](product-engineering-overview.md).

### Create a change order from a change request

An engineer who is reviewing an engineering change request can create an engineering change order directly from the **Engineering change requests** page. On the Action Pane, on the **Change request** tab, in the **Engineering change order** group, select **Copy link and products**.

Be sure to select the correct company for the new engineering change order. If the change order will result in the engineering product itself being changed (new version, new product, or new variant), then the change order must be assigned to the engineering company. If only a local change is needed (**Impact** is set to *None*), then the change order can be assigned to a local company and the changes will apply to the current product.

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

While you're reviewing a request for change, on the Action Pane, on the **Change request** tab, in the **Business impact** group, select **Search** to assess the impact of the proposed change on open transactions, such as sales orders, production orders, and inventory on-hand. The results are shown in the **Business impact to open transactions** dialog box, where you can select impacted transactions and then use commands in the toolbar to view more information, notify the responsible user, or block the transaction.

### Engineering change orders in engineering or operational companies

As is described in [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md), the product data that you can edit varies, depending on the type of legal entity that you're working in (an engineering company versus an operational company). Data ownership rules are also applied to engineering change orders. Therefore, depending on the legal entity where you create an engineering change order, different types of changes can be made. Here are some examples:

- For engineering change orders in an *engineering company*, you can make basic changes to the engineering data. For example, you can create new versions of a product, change a product's structure via the BOM, and change engineering attribute values. For each affected product, select one of the following values in the **Impact** field:

    - **None** – Update the existing product version (in-version update).
    - **New version** – Create a new version that is based on the selected product version.
    - **New product** – Create a completely new product that is based on the selected product version.
    - **New variant** – Create a new variant based on the selected product version. Its BOM and route information will be copied.

- For engineering change orders in an *operational company*, you can change the logistical data of the product. For example, you can enrich the existing BOM with settings for sourcing, add local routes or local BOMs, and even enrich a BOM by adding new BOM lines for local packaging materials, lubrication fluids, or instructions in the local language. Enrichments that users make in the operational company will be preserved when new updates are sent from the engineering company. Learn more in [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).

    When engineering change orders are processed in the engineering company, the products are created and/or updated only in the engineering company. Therefore, if the product master data should also be updated, you must also release the products to operational companies.

- You can release products directly from engineering change orders. Open the change order, and then, on the Action Pane, on the **Change order** tab, in the **Product releases** group, select **Release product structure**. The process works just as it works when you release products from the **Released products** page. Learn more in [Release product structures](release-product-structure.md).
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
| Engineering material disposition | Select a material disposition code for any waste that is produced when the change is applied. |
| Customer approval required | Specify whether customer approval is required before the change can be applied. |
| Received customer approval | Specify the status of the customer approval. |
| Environmental health and safety | Specify whether environmental health and safety rules are applicable to the change. If they are, you can then select the applicable rules. |

You can use the **Maintain/copy change information** button to copy change information between affected products.

## Use electronic signatures to approve and active BOMs and routes

To use electronic signatures to approve and/or activate bills of material (BOM) and/or route changes, go to **Organization administration \> Setup \> Electronic signature \> Electronic signature requirements**. Then make sure each of the following items has **Signature required** set to *Yes*:

- Activate engineering change order product bill of materials
- Activate engineering change order product route
- Approve engineering change order product bill of materials
- Approve engineering change order product route
- Approve engineering version BOM and BOM versions
- Approve engineering version and route version

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
