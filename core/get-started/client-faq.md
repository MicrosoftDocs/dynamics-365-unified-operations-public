---
# required metadata

title: Dynamics 365 for Operations client FAQ
description: This article provides answers to frequently asked questions about the Microsoft Dynamics 365 for Operations client.
author: jasongre
manager: AnnBe
ms.date: 2015-11-04 19 - 47 - 08
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 12334
ms.assetid: 2b7f8ba3-aaaa-4d76-af5d-eea94754436e
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Dynamics 365 for Operations client FAQ

This article provides answers to frequently asked questions about the Microsoft Dynamics 365 for Operations client.

Why aren't symbols loaded when I use Dynamics 365 for Operations?
-----------------------------------------------------------------

The security settings on your browser might prevent the symbols from being loaded correctly. To resolve this issue, try the following steps:

-   If you're experiencing this issue in Internet Explorer, click **Tools**, and then click **Internet Options**.  In the Internet Options dialog box, on the **Privacy** tab, click **Custom level**, and make sure the **Font download** option is selected.
-   Otherwise, you might have to add the Dynamics 365 for Operations site to the list of trusted sites.

## I miss the ribbon from Dynamics AX 2012. Can I keep Action Pane tabs open all the time?
We are planning to implement this feature soon. Users will then be able to choose to keep the tabs on Action Panes open all the time. Otherwise, the tabs will be collapsed when they aren't being used, to gain more screen space for the page.

## Why do I sometimes see different shortcut menus when I rightclick?
If you right-click in an editable field (or if text is selected), the browser's shortcut menu is displayed. This menu gives you access to the **Cut**, **Copy**, and **Paste** commands. We can't embed these commands into the Dynamics 365 for Operations shortcut menus because, for security reasons, browsers don’t allow us to programmatically access the system clipboard.

If you right-click a field label or the value of a read-only control, you'll see the Dynamics 365 for Operations shortcut menu.

To make keyboard access easier, we plan to implement a keyboard shortcut in the future that will open the Dynamics 365 for Operations shortcut menu.

## Where is the View details functionality in Dynamics 365 for Operations?
The **View details** option is available in a couple of ways:

-   If a control has **View details **capabilities, and if the control has a value, that value is displayed as a hyperlink. You can click the hyperlink to open a page that contains additional details.
-   **View details** is also an option on Dynamics 365 for Operations shortcut menus. For more information about when Dynamics 365 for Operations shortcut menus are displayed when you right-click, see the previous section.


