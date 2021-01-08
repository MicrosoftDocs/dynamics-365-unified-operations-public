---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (October 31, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/31/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (October 31, 2018)

**Build 8.1.2031**

This topic describes features that are either new or changed in Core HR.

## Create links from Talent to Finance
This new navigation functionality allows you to link from Talent to Finance, giving you direct navigation into Finance pages. When links are configured, you can specify the name and group of the link, where the link should surface in Talent, and the target page to be opened within Finance.

#### Coming soon
Field context will be added in the future to allow for direct navigation to corresponding records in Finance. For example, you can use **Link to field** to provide the context to navigate directly to a specific employee or position in Finance.

### Configure target systems

In Talent, system administrators can define links that will be surfaced through the System Administration workspace. Part of the configuration is the Finance environments that you would like to navigate to as the "target" of the link. You do this by giving the target system a name and providing the URL of the Finance environment. Here is an example of a Finance URL that you would provide: https://devax00124aos.cloud.test.dynamics.com/. After you have configured your target systems,  you can define your links.

### Configure links

Each link that is created will have the following information defined.

- Link - Name of the link, used for identification only.

- Enable this Link - Set to **Yes** if you want to display the link to users of Talent.

- Display name - Define the name that will appear as a link to Finance. This data is currently is not translated.

- Surface link on form - Choose which page you would like to display the link on.

- Group - Groups are not required, but if you want to organize your links using groups, select an existing group or create a new one using the **Group** field.

- Target system - Select the target system that was created using the **Configure target system** option. This will be the Finance environment that will be used when navigating by using the link.

- Use user's current Company - Select **Yes** if you would like to use the User's current company context when navigating to Finance. If **No** is selected, then you can select the company that should be used.

- Target menu item - Enter the menu item from Finance that the link should use when navigating. Menu items that you can directly navigate to are available. To find the menu item required, open Finance and open the page that is the target of the navigation. Copy the menu item from the URL. For example, if you want the link to take you to the employee list in Finance and Operations, enter the value that appears after the "&mi" in the URL. https://devax00124aos.cloud.test.dynamics.com/?p=USMF&mi=HcmWorkerListPage_Employees. The menu item to navigate to the employee list page in this example is: HcmWorkerListPage_Employees.

- Link to data source - Select the source of data that the link is referencing. The most common sources like **Worker** and **Position** are available.

- Link to field - (Coming soon) This field selection will allow for direct navigation from a single record in Talent to a single record in Finance.

### Access to links

System administrators will see the newly created links on the defined pages even if the **Enable this link** option is set to **No**. This can be used for testing links prior to surfacing them to other employees. All other roles will only see the configured links after the **Enable this link** option is set to **Yes**. Employees who have access to the pages in which the links are surfaced will have access to the links.

Users can also have security rights within Finance defined to access the pages in Finance and Operations. If they don't, a security dialog box will be displayed when using the link.


## Other changes/fixes

### Positions with a future start date cannot be assigned to a new employee

Changes have been made to allow employee assignments to future-dated positions. Positions that have start dates in the future can be selected and the employee assignment will be made upon save or completion of the workflow (if the workflow is enabled).

### New employee cannot be assigned existing position

Changes have been made so new employee assignment can now be assigned to existing positions.

### Seniority date/Office location disappears when the employment start date is in the past and the record is saved

Changes have been made to correct the visibilty of the **Senority date** and **Office location** when saving changes for past employees.

### Can't enter data for future-dated employments on the worker page

Employment data for future-dated employments has been disabled on the main worker page. Employment data can be entered through the **Date Manager** pages. Additional changes will be made in future releases to enable entering employment data directly during the workflow process.

### Add ValidFrom and ValidTo to HcmPersonalContactPersonEntity

The Data Management Framework (DMF) entity HcmPersonalContactPersonEntity has been updated to include "valid from" and "valid to" dates to enable certain benefit integration scenarios. 

## Known issue
- **Issue**: When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. 
- **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
