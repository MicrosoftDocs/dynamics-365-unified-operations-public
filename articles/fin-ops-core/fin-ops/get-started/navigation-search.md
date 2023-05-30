---
title: Navigation search
description: This article explains how to use the search functionality to navigate to pages.
author: jasongre
ms.date: 08/11/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: eef0676f-c4b1-490e-a032-e9c8580f3fea
---

# Navigation search

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article explains how to use the search functionality to navigate to pages.

The application includes a number of areas and pages to help you perform various tasks. To quickly find the pages that you need to complete your tasks, use the navigation search feature.

To use this feature, click the **Search** icon to display the **Search** box. You can then type one or more words in the box. The system instantly searches for relevant pages in the application that match the words that you entered. For example, you could type "vendor invoice" as the input, and then the system displays results that match that input.

> [!NOTE]
> The **Search** box helps you find and navigate to pages. It will not help you find specific data or actions.

![search-box.](media/navigation-search.png "Search box")

## Quickly navigate to a particular page

The navigation search feature also serves as a great way for you to quickly navigate to a particular page. For example, if you are an accounts payable clerk who frequently uses the **Payment journal** page, you could enter "payment journal" in the **Search** box. Because the input is an exact match for the page title, the page is listed at the top of the search results, and you can quickly navigate to it.

The search results list displays the page title as well as the navigation path. This shows the location of the page in the application. It also helps you differentiate between two or more similar pages in the results.

When you search for a page, your input is matched against the page title, as well as its navigation path. For example, if you enter "receivable" in the **Search** box, you will see results for the pages available to you in the Accounts receivable area – even though the page titles do not include the word "receivable."

## Quickly navigate to a page based on the technical form name

The navigation search functionality also includes a much-requested feature for power users: the ability to quickly navigate to a page based on the technical form name. Many users are so familiar with the system that they know the exact form names they work with. If you are one of these users, you can enter **form:** followed by the name of the form you are looking for. For example, if you enter **form: vendinvoice**, the search results will show all pages where the form name starts with **vendinvoice**.

## Administration and security

From an administration and security perspective, the navigation search functionality only surfaces two types of results:

- Pages that are enabled in the current configuration (via configuration keys).
- Pages that the user has access to based on the user's role.

The list of search results is limited to 10 items. If you do not find what you're looking for in the results, you should try refining or updating the input.

## Development

From a development perspective, the navigation search functionality is easy to leverage because there is virtually no delay between the deployment of menu items and their ability to show up in search results. As long as the menu items are linked to from either the navigation pane or the dashboard, they will automatically become searchable.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
