---
# required metadata

title: Client FAQ
description: This article provides answers to frequently asked questions about the finance and operations client.
author: jasongre
ms.date: 09/11/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: a9a57f0e-a67c-46b1-83c9-5d6350fb3b86
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Client FAQ

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article provides answers to frequently asked questions about the finance and operations client.

## Why aren't symbols loaded?

The security settings on your browser might prevent the symbols from being loaded correctly. To resolve this issue, try the following steps:

- If you're experiencing this issue in Internet Explorer, click **Tools**, and then click **Internet Options**. In the Internet Options dialog box, on the **Privacy** tab, click **Custom level**, and make sure the **Font download** option is selected.
- Otherwise, you might have to add the app site to the list of trusted sites.

## I miss the ribbon from Dynamics AX 2012. Can I keep Action Pane tabs open all the time?

We are planning to implement this feature soon. Users will then be able to choose to keep the tabs on Action Panes open all the time. Otherwise, the tabs will be collapsed when they aren't being used, to gain more screen space for the page.

## Why do I sometimes see different shortcut menus when I right click?

If you right-click in an editable field (or if text is selected), the browser's shortcut menu is displayed. This menu gives you access to the **Cut**, **Copy**, and **Paste** commands. We can't embed these commands into the shortcut menus because, for security reasons, browsers don't allow us to programmatically access the system clipboard.

If you right-click a field label or the value of a read-only control, you'll see the shortcut menu.

To make keyboard access easier, we plan to implement a keyboard shortcut in the future that will open the shortcut menu.

## Where is the View details functionality?

The **View details** option is available in a couple of ways:

- If a control has **View details** capabilities, and if the control has a value, that value is displayed as a hyperlink. You can click the hyperlink to open a page that contains additional details.
- **View details** is also an option on shortcut menus. For more information about when shortcut menus are displayed when you right-click, see the previous section.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
