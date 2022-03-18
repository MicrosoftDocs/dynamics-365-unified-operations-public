---
# required metadata

title: Create links from Human Resources to another environment
description: This topic explains how to create a link from Microsoft Dynamics 365 Human Resources to another Dynamics 365 environment.
author: twheeloc
ms.date: 03/18/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-29-11
ms.dyn365.ops.version: Human Resources

---

# Create links from Human Resources to another Finance environment

A customer may have two Dynamics 365 environments that they're working in. This was a common scenario when a customer was using Dynamics 365 Human Resources 
standalone and also using a Dynamics 365 Finance environment. With the infrastructure merge into Dynamics 365 Finance, this situation may still occur. 

As an example, a customer may have a Dynamics 365 Human Resources environment on the Finance infrastructure, and also need to connect to another Dynamics 365 Finance environment. This new navigation functionality allows you to link from a Human Resources page to another Finance environment, giving you direct navigation into specific pages. When links are configured, you can specify the name and group of the link, where the link should surface in Human Resources, and the target page to be opened within the other environment.

> [!Note] 
> You must turn on **Human resource user experience enhancements** in **Feature management** to get this feature.

## Configure target systems

In Human Resources, system administrators can define links that will surface in Human Resources pages. Part of the configuration are Finance environments that you would like to navigate to as the target of the link. 

To configure the target system:
1. On the **Configure links** page, select **Configure target system** button.  
2. Enter the target system name and provide the URL of the Finance environment. After you have configured your target systems, you can define your links.

## Configure links

Each link that is created will have the following information defined.
**Link** - Name of the link and is used for identification only.
**Enable this link** - Set to **Yes** if you want to display the link to users of Human Resources.
**Display name** - Enter the name that will appear as a link to the secondary environment. 
**Surface link on form** - Choose which page you would like to display the link on.  Links can only be surfaced on the **Employee self service** workspace, **Job**, **Position**, **Worker**, and **Streamlined Worker** pages.
**Group** - Groups are not required, but if you want to organize your links using groups, select an existing group or create a new one using the **Group** column.
**Target system** - Select the target system that was created using the **Configure target system** option. This will be the secondary environment that will be used when navigating using the link.
**Use user's current Company** - Select **Yes** if you would like to use the User's current company context when navigating to Finance. If **No** is selected, then you can select the company that should be used.
**Target** menu item - Enter the menu item from Finance that the link should use when navigating. Menu items that you can directly navigate to are available. 

To find the menu item required, 
1. Open Finance and open the page that is the target of the navigation. 
2. Copy the menu item from the URL. For example, if you want the link to take you to the employee list in Finance and Operations, enter the value that appears after the "&mi" in the URL. 
3. The menu item to navigate to the employee list page in this example is: HcmWorkerListPage_Employees.

**Link to data source** - Select the source of data that the link is referencing. The most common sources like **Worker** and **Position** are available.

### Access to links

System administrators will see the newly created links on the defined pages even if the **Enable this link** option is set to **No**. This can be used for testing links prior to surfacing them to other employees. All other roles will only see the configured links after the **Enable this link** option is set to **Yes**. Employees who have access to the pages in which the links are surfaced will have access to the links.

Users must also have security rights within the secondary environment defined to access the pages in that environment. If they don't, a security dialog box will be displayed when using the link.

