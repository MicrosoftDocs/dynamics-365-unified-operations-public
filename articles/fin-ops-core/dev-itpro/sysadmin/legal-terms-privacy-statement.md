---
# required metadata

title: Add links to your organization's legal terms and privacy statement
description: This topic explains how administrators can add links to their organization's legal terms and privacy statement in the About pane.
author: aneesmsft
ms.date: 10/02/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SystemParameters, SysAbout
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 267894
ms.assetid: b74f8d8b-e20b-4ffd-8fd6-c64c2fe31c8a
ms.search.region: Global
# ms.search.industry: 
ms.author: aneesa
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Application update 4

---

# Add links to your organization's legal terms and privacy statement

[!include [banner](../includes/banner.md)]

This topic explains how administrators can add links to their organization's legal terms and privacy statement in the <strong>About</strong> pane of Microsoft Dynamics 365 Finance, Supply Chain Management, and Commerce.

Organizations often need to ensure that the links to their legal terms and privacy statement are readily available and visible to users in order to meet legal and compliance requirements. Administrators of an organization can follow these steps to have the links to their legal terms and privacy statement be available in the **About** pane (**Settings** &gt; **About**).

## Add links
1.  Go to the **System parameters** page and click **Legal and Privacy.** On this page:

    1.  Enter the link to a page that outlines the legal terms for your organization.

    2.  Enter the link to a page that outlines the privacy statement for your organization.

        > [!NOTE]
        > Make sure that you enter the full URL, starting with either *https* or *http*.

2.  Click **Save**.

3.  If you are using Commerce, go to the **Distribution schedules** page. On this page:

    1.  Select the **1110 – Global configuration** job.

    2.  Click **Run now**.

        > [!NOTE]
        > To verify that the job completed, go to the **Download sessions** page.

## Validate links

### Validate the links in Finance, Supply Chain Management, and Commerce

To validate that the links have been added, on the toolbar at the top of the page, click the **Settings** icon, and then click **About**. In the **Links** section of the pane, you should see two new links:

-   **Your organization’s Legal terms**
-   **Your organization’s Privacy and Cookies**

Click these links to validate that the appropriate pages open. 

> [!NOTE]
> The links open in a new window, so if you have a pop-up blocker enabled, you will need to add an exception to your pop-up blocker settings to launch a new window.

### Validate the links in Modern Point of Sale (MPOS) and Cloud Point of Sale (CPOS)
To validate that the links have been added, go to the **Settings** page. In the **About** section, click the links to validate that the appropriate pages open.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]