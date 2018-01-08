---
# required metadata

title: Microsoft Project client integration
description: Planning and maintaining a project schedule can be complex, so project managers need to use tools that help them manage this task. Integration with Microsoft Project Client provides support to open and manage a project work breakdown structure. 
author: KimANelson
manager: AnnBe
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: ProjWbsTemplate
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2017-12-04
ms.dyn365.ops.version: AX 7.3.0

---

# Microsoft Project client integration

[!include[banner](../includes/banner.md)]

Planning and maintaining a project schedule can be complex, so project managers need to use tools that help them manage this task. 
Integration with Microsoft Project Client provides support to open and manage a project work breakdown structure. The project manager 
can publish any changes back to the Finance and Operations project work breakdown structure.

> [!NOTE]
> If you are using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, July update, you must install KB 4054797 and 4055884.

## Configure the Microsoft Project Client add-in
To enable the integration with Microsoft Project Client, a Microsoft Dynamics 365 add-in is required to be installed in the user’s 
client Microsoft Project application. This is done by opening the **Project management workspace**.

•	Click **Configure project client add-in** from the **Links** > **Setup** section of the workspace.

•	Click **Open**, then click **Run** when prompted.

## Open and edit an existing draft work breakdown structure in Microsoft Project Client
If a project in Finance and Operations already has a work breakdown structure created, the work breakdown structure can be opened in the
Microsoft Project Client application if the work breakdown structure is in a draft status. To open from the **Project** page, click 
**Open in Microsoft Project** link from the **Plan** tab. This page can also be opened from within the Microsoft Project Client 
application by clicking **Open** in the **Microsoft Dynamics 365** tab. Select the **Legal entity** and **Project** from the list.

> [!NOTE]
> If you're using Internet Explorer as your browser, you will need to click **Save** to manually open from the location that the file is downloaded to. Or, click **Save and open** to open the file in Microsoft Project Client. Do not rename the file name when saving.

Before making any edits to the file using Microsoft Project Client, you need to check it out. Click **Check out** in the **Microsoft 
Dynamics 365** tab. This will prevent other users from editing the work breakdown structure from within Finance and Operations at the 
same time. To publish the work breakdown structure after completing any edits, click **Check in** on the **Microsoft Dynamics 365** tab.

If a project team has already been added to the project in Finance and Operations, the resource list will be populated with the team 
members. If a project team has not yet been added to the project, you can select resources and build the team within Microsoft Project 
Client by clicking the **Resources** button on the **Microsoft Dynamics 365** tab. 

The following data will be synced back to Finance and Operations as part of the check in process:

•	Task name

•	Start date

•	Finish date

•	Predecessors

•	Resource names

•	Category

•	Resource category

•	Work hours

•	Notes

•	Priority

> [!NOTE]
> If you add any other columns to your Microsoft Project Client file, they will not be saved to the file and will not be displayed when 
the file is opened again.

## Create the work breakdown structure for an existing project using Microsoft Project Client
To create a new work breakdown structure using Microsoft Project Client, follow these steps:


1.	Open Microsoft Project Client.

2.	On the **Microsoft Dynamics 365** tab, click **Open**.

3.	Select the **Legal entity** for the project.

4.	Select the **Project**.

5.	Click **Check out** on the **Microsoft Dynamics 365** tab.

6.	When ready to publish to Finance and Operations, click **Check in** on the **Microsoft Dynamics 365** tab.

## Replace the existing work breakdown structure for an existing project using Microsoft Project Client
To create a new work breakdown structure using Microsoft Project Client and replace an existing work breakdown structure for an existing
project, follow these steps:

1.	Open the Microsoft Project Client.

2.	Create the schedule in Microsoft Project Client.

3.	On the **Microsoft Dynamics 365** tab, click **Save changes** > **Replace existing project**.

4.	Select the **Legal entity** for the project.

5.	Select the **Project**.

6.	Click **OK**.

## Create a new project from within Microsoft Project Client


1.	Open the Microsoft Project Client.

2.	Create the schedule in Microsoft Project Client.

3.	On the **Microsoft Dynamics 365** tab, click **Save changes** > **Save to new Project**.

4.	Select the **Legal entity** for the project.

5.	Enter the **Project ID**, if necessary.

6.	Enter the **Project name**.

7.	Select the **Project type**, **Project group** and the **Project contract ID**. Alternatively, you can create a new project contract
by clicking **New**.

8.	Select the **Calendar** to be used for resourcing.

11.	Click **OK**.
