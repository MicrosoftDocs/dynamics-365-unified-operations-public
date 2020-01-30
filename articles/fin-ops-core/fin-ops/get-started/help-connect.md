---
# required metadata

title: Connect the Help system
description: This topic describes the components of the Help system for certain Dynamics 365 apps, and provides an overview of how to connect them and a summary of how to create custom help. 
author: margoc
manager: AnnBe
ms.date: 01/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SystemParameters
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 16141
ms.assetid: 0b9c8630-9474-4473-80fd-7db5d54b2275
ms.search.region: Global
# ms.search.industry: 
ms.author: margoc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Connect the Help system

[!include [banner](../includes/banner.md)]

This topic describes the components of the Help system for Dynamics 365 Finance, Supply Chain Management, Retail, and Talent. It provides an overview of how to connect these components and a summary of how to create custom help.

## Help architecture

The following illustration shows the parts of the Help system. The in-product Help system pulls articles from https://docs.microsoft.com, as well as task guides stored in Business Process Modeler in Lifecycle Services (LCS).

> [!NOTE]
> The features listed in the diagram with an asterisk (\*) are planned, but are not available yet.

[![Help architecture](./media/help-architecture.png)](./media/help-architecture.png)

## Adding Task guides

> [!NOTE]
> The **Task guides** tab is currently available for Dynamics 365 Finance and Dynamics 365 Supply Chain Management. The Task guides in the Getting Started experience in Talent remain available to cover basic functionality. Procedural help is also available on the docs.microsoft.com site for both [Retail](/dynamics365/retail/) and [Talent](/dynamics365/talent/).

Using the **System Parameters** page, system administrators connect the pieces of the Help system for an implementation.

[![System Parameters form with Help settings](./media/system-parameters_ops-1024x437.png)](./media/system-parameters_ops.png)

On the **System parameters** page, follow these steps:

> [!IMPORTANT]
> The first time that you open the **Help** tab, you must connect to Lifecycle Services. Be sure to click the link in the middle of the form, wait for the connection, close the dialog box, and then click **OK** to get to the **System Parameters** page.
>
> [![Connect to LCS](./media/connect-to-lcs-crop-1024x365.png "Connect to LCS")](./media/connect-to-lcs-crop.png)

1. Select the Lifecycle Services project to connect to.
2. Select the BPM libraries (within the selected project) to retrieve task recordings from.
3. Set the display order of the BPM libraries. This determines the order in which task recordings from the libraries will appear in the **Help** pane.

After you complete these steps, you can open the **Help** pane and click the **Task guides** tab. You'll now see the task guides that apply to the page that you're currently on in Finance and Operations apps. If no task guides are found, you can enter keywords to refine your search.

### Showing translated task guides

Translated Task guides were first shipped in the May 2016 APQC Unified Library, and the Getting Started library. In the relevant Dynamics 365 app, to see localized Task guide help, make sure that you are connected to the May library. The language that a Task guide appears in is controlled for each user by the Language settings under **Options** &gt; **Preferences**.

> [!NOTE]
> Even though many Task guides have been translated, right now the client is not showing the translated Task guide names. Also, only the task guides that were released in February 2016 are available in translation in the May library. We will release an updated library with additional translations.
>
> - If a task guide has been translated, when you open that task guide all the text of the task guide will appear in your selected language.
> - If a task guide has not yet been translated, when you open it, only some of the text (the text of the controls) will appear in your selected language.

## Adding custom help

You can use task guides to create custom help, or connect a website to the Help pane.

### Create custom help with task guides

You can create custom help for Finance and Supply Chain Management by creating task recordings that reflect your implementation, and saving them to an LCS Business Process Library. You cannot create custom task guides for Retail and Talent.

For partners, if you promote a library to be a corporate library, and include it in a solution, it will be available to your customers. You can also make a copy of the APQC Unified global library, and then open your copy, open task recordings from it, modify them, and save the recordings with your changes. For more information, see [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).

### Connect a custom help site

Finance and Operations apps are rarely used out-of-the-box. Rather, the solution is customized and extended to fit the organization's needs. Similarly, you can customize and extend the Help experience, including adding custom help to the in-product help pane.  

Microsoft has provided a toolkit with sample code to help you deploy and connect custom Help to the Help pane. In [Deploying custom Help](../../dev-itpro/help/deploy.md), you can read about how you can set up a custom Help solution by publishing content as HTML to a website, make the content searchable, and extending the Help pane to connect to the website.  

If you want to collaborate with Microsoft on tools and processes for customizing help, please fill in the form at [https://aka.ms/customhelpfeedback](https://aka.ms/customhelpfeedback).  

## See also

[Help overview](help-overview.md)  
[Deploying custom help](../../dev-itpro/help/deploy.md)  
[Task recorder overview](../../dev-itpro/user-interface/task-recorder.md)  
[How to create a task recording to use as documentation or training](../../dev-itpro/user-interface/task-recorder-training-docs.md)  
[Custom Help GitHub repository](https://github.com/microsoft/dynamics356f-o-custom-help)  
