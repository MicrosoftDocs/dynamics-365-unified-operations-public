---
# required metadata

title: Create links from Human Resources to another environment
description: This article explains how to create a link from Microsoft Dynamics 365 Human Resources to another Dynamics 365 environment.
author: twheeloc
ms.date: 05/13/2026
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-29-11
ms.dyn365.ops.version: Human Resources

---


# Create links from Human Resources to another Finance environment

You might work in two Dynamics 365 environments. For example, you might have a Dynamics 365 Human Resources environment and need to connect to another Dynamics 365 Finance environment.

This feature enables you to create links from a Human Resources page to a specific page in another Finance environment. When you configure the links, you can specify where the link is available in Human Resources and the target page that opens in the other environment.

> [!NOTE]
> Turn on the **Human resource user experience enhancements** feature in **Feature management** to get this functionality.

## Configure target systems

In Human Resources, system administrators can define links that appear on **Human Resources** pages. Parts of the configuration are Finance environments that you want to navigate to as the target of the link.

To configure the target system:

1. On the **Configure links** page, select **Configure target system**.  
1. Enter the target system name and provide the URL of the Finance environment. After you configure your target systems, you can define your links.

## Configure links

Each link you create has the following information defined:

- **Link**: Name of the link. Used for identification only.
- **Enable this link**: Set to **Yes** if you want to display the link to Human Resources users.
- **Display name**: Enter the name that appears as a link to the secondary environment.
- **Surface link on form**: Choose which page you want to display the link on. You can surface links only on the **Employee self service** workspace and the **Job**, **Position**, **Worker**, and **Streamlined Worker** pages.
- **Group**: Organize your links by using groups. Select an existing group or create a new one by using the **Group** column.
- **Target system**: Select the target system that you created by using the **Configure target system** option. This system is the secondary environment that you use when navigating by using the link.
- **Use user's current company**: Select **Yes** to use the user's current company when navigating to Finance. Select **No** to select the company that should be used.
- **Target** menu item: Enter the menu item from the Finance environment that the link should use when navigating. Menu items that you can directly navigate to are available.

   To find the menu item required:
   1. Go to the Finance environment and open the page that is the target of the navigation.
   1. Copy the menu item from the URL. For example, if you want the link to take you to the employee list in finance and operations, enter the value that appears after the "&mi" in the URL.
   1. The menu item to navigate to the employee list page in this example is: HcmWorkerListPage_Employees.

- **Link to data source**: Select the source of data that the link is referencing. The most common sources like **Worker** and **Position** are available.

### Access to links

System administrators see the newly created links on the defined pages even if the **Enable this link** option is set to **No**. This can be used for testing links prior to surfacing them to other employees. All other roles will see only the configured links after the **Enable this link** option is set to **Yes**. Employees who have access to the pages in which the links are surfaced will have access to the links.

Users must also have security rights within the secondary environment defined to access the pages in that environment. If they don't, a security dialog box is displayed when using the link.
