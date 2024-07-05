---
title: Manage approvals using the Approvals Management mobile app
description: This article describes how to use the Approvals Management mobile app to approve, reject, or delegate approval requests.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Manage approvals using the Approvals Management mobile app

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes how to use the Approvals Management mobile app to approve, reject, or delegate approval requests.

## User requirements

To manage purchasing requests from the Approvals Management mobile app, you must meet the following requirements:

- You must sign in to Power Apps by using a domain account that matches a user account in Supply Chain Management with the same Microsoft Entra ID username.
- Your user account in Supply Chain Management must be assigned one of the following security roles, depending on which types purchases you want to manage.
    - *Buying agent* - This role allows you to use the app to manage purchase orders.
    - *Purchasing agent* – This role allows you to use the app to manage purchase requisitions.
    - *Purchasing manager* – This role allows you to use the app to manage both purchase orders and purchase requisitions.

For more information about how to set up roles and security in Supply Chain Management, see
[Security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

## Home page

When you open the Asset Maintenance mobile app and sign in, it shows the home page, which provides an overview of requests awaiting your approval.

The following illustration highlights user interface (UI) elements on the home page.

:::image type="content" source="media/approval-app-home.png" alt-text="User interface elements on the home page" lightbox="media/approval-app-home.png":::

The home page includes the UI following elements, many of which are common to all pages in the app. The numbers correspond to the numbers in the previous illustration.

1. **About button** – View information about the app, such as terms and conditions and the current version of the app.
1. **Navigator** – Navigate between the main pages of the app (*Home*, *Purchase orders*, and *Purchase requisitions*).
1. **Search** – Search for specific purchase orders or purchase requisitions. You can search, for example, for a specific purchase order number, vendor account, vendor name, legal entity, or item number.
1. **Alerts** – Read your notifications. A red dot indicates that you have new notifications.
1. **Purchase orders** – If you are able to manage purchase orders, this section shows the number of purchase orders that are awaiting your approval. Select this row to view the list of purchase orders.
1. **Purchase requisitions** – If you are able to manage purchase requisitions, this section shows the number of purchase requisitions that are awaiting your approval. Select this row to view the list of purchase requisitions.
1. **Refresh** – Refresh the list (the list refreshes automatically every 30 seconds).
1. **Sort** – Choose how items are sorted in the list.
1. **Filter** – Filter the list by specifying specific values to look for. This is useful on pages that show longer lists.

## List pages

List pages show a list of orders, requisitions, or line items that are awaiting your approval. The type of item being shown depends on how you navigated to the list page. From here, you can select any listed item to see more detail or, if you enable multiselect, select one or more items to approve, reject, delegate, or request changed right from here.

### List pages without multiselect

List pages without multiselect enabled show a list of items that you can navigate and select to see more details. The following illustration highlights the UI elements on a list page without multiselect.

:::image type="content" source="media/approval-app-list-single.png" alt-text="User interface elements on list pages without multiselect" lightbox="media/approval-app-list-single.png":::

List pages without multiselect include the UI following elements. The numbers correspond to the numbers in the previous illustration.

1. **List item** – Represents an individual purchase order/requisition header or line. A summary of the item is shown. Select the item to view details about it.
1. **View comments** – View comments about the related item. These are usually comments written by the requester for the reviewer.
1. **Multiselect** – Turn multiselect on or off. This illustration shows a list with multiselect turned off.
1. **Header/Lines selector** – Choose whether to view a list of purchase order/requisition headers or individual lines.

### List pages with multiselect

List pages with multiselect enabled show a list where you can select one or more items to approve, reject, delegate, or request changed right from here. The following illustration highlights the UI elements on a list page with multiselect.

:::image type="content" source="media/approval-app-list-multi.png" alt-text="User interface elements on list pages with multiselect" lightbox="media/approval-app-list-multi.png":::

List pages with multiselect include the UI following elements. The numbers correspond to the numbers in the previous illustration.

1. **Select all** – Select or deselect all items in the list.
1. **Checkbox** – Select or deselect the related item.
1. **Action buttons** – Approve, reject, delegate, or request changes for the selected items.
1. **Multiselect** – Turn multiselect on or off. This illustration shows a list with multiselect turned on.

## Detail pages

Detail pages show detailed information about a specific purchase order, requisition, or line item. The details provided vary slightly based on whether you are viewing header details or line details.

### Header details

Header details show information about a select purchase order or requisition as a whole. The following illustration highlights the UI elements on a header detail page.

:::image type="content" source="media/approval-app-detail-header.png" alt-text="User interface elements for header details" lightbox="media/approval-app-detail-header.png":::

Header details pages include the UI following elements. The numbers correspond to the numbers in the previous illustration.

1. **Back** – Go back to the page you came from.
1. **Details tab** – View general information about the purchase order or requisition, as shown in the previous illustration.
1. **Attachments tab** – View and open any attachments that are associated with the purchase order or requisition.
1. **Timeline tab** – View a timeline of events related to the purchase order or requisition.
1. **Accounting distribution details** – View accounting distribution details linked to the purchase order or requisition.
1. **View workflow instructions** – View instructions for the workflow.
1. **Header details** – View detailed information about the purchase order or requisition.
1. **Lines** – Lines are listed under the header details. Each line shows a summary of the line item. Select a line to view more details about it.
1. **Action buttons** – Approve, reject, delegate, or request changes for the current purchase order or requisition.

### Line details

Line details show information about a specific line item on a purchase order or requisition. The following illustration highlights the UI elements on a line detail page.

:::image type="content" source="media/approval-app-detail-line.png" alt-text="User interface elements for line details" lightbox="media/approval-app-detail-line.png":::

Line details pages include the UI following elements. The numbers correspond to the numbers in the previous illustration.

1. **Back** – Go back to the page you came from.
1. **View workflow instructions** – View instructions for the workflow.
1. **Standard details** – Shows general information about the line item.
1. **Extra details** – Expand or collapse additional information about the line item.
1. **Action buttons** – Not all list details pages include these buttons. If they are shown, you can use them to approve, reject, delegate, or request changes for the current line.
