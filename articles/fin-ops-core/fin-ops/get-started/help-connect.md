---
# required metadata

title: Connect the Help system
description: Learn about the components of the Help system for certain Dynamics 365 apps. Get an overview of how to connect them and a summary of how to create custom help. 
author: margoc
manager: AnnBe
ms.date: 03/17/2020
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

# Configure the Help experience for Finance and Operations apps

[!include [banner](../includes/banner.md)]

In this article, you find an overview of the components of the Help system for Finance and Operations apps, such as Dynamics 365 Finance, Supply Chain Management, Commerce, and Human Resources. You can also learn how to connect these components and a summary of how to create custom help.  

## Help architecture

The Finance and Operations apps come with conceptual overviews and other articles that publish to the [https://docs.microsoft.com/dynamics365/](/dynamics365/) site. This content is then accessible from the in-product Help pane. The following illustration shows the parts of the Help system.  

[![Help architecture](./media/help-architecture.png)](./media/help-architecture.png)

The in-product Help system pulls articles from https://docs.microsoft.com and other connected websites, as well as task guides stored in Business Process Modeler in Lifecycle Services (LCS).

## Adding Task guides

> [!NOTE]
> The **Task guides** tab is currently not available in Dynamics 365 Human Resources or Commerce. <!--We are currently working to enable this functionality in a future release.--> The Task guides in the Getting Started experience in Human Resources remain available to cover basic functionality. For both Human Resources and Commerce. procedural help is also available on the [https://docs.microsoft.com/dynamics365/](/dynamics365/) site.

Using the **System Parameters** page, system administrators can configure access to the relevant task guide libraries for an implementation.

> [!NOTE]
> - In order to configure help, you must be signed in with an account in the same tenant as the tenant in which the app is deployed.
> - It is not possible to connect to an LCS library from an instance of the app running in a local virtual hard drive (VHD).

[![System Parameters form with Help settings](./media/system-parameters_ops-1024x437.png)](./media/system-parameters_ops.png)

To configure task guides for a solution, on the **System parameters** page, follow these steps:

> [!IMPORTANT]
> The first time that you open the **Help** tab, you must connect to Lifecycle Services. Be sure to click the link in the middle of the form, wait for the connection, close the dialog box, and then click **OK** to get to the **System Parameters** page.
>
> [![Connect to LCS](./media/connect-to-lcs-crop-1024x365.png "Connect to LCS")](./media/connect-to-lcs-crop.png)

1. Select the Lifecycle Services project to connect to.
2. Select the BPM libraries (within the selected project) to retrieve task recordings from.
3. Set the display order of the BPM libraries to define the order in which task recordings from the libraries will appear in the **Help** pane.

After you complete these steps, you can open the **Help** pane and click the **Task guides** tab. You'll now see the task guides that apply to the page that you're currently on in Finance and Operations apps. If no task guides are found, you can enter keywords to refine your search.

### Showing translated task guides

Translated Task guides were first shipped in the May 2016 APQC Unified Library, and the Getting Started library. To see localized Task guide help, make sure that your Dynamics 365 solution is connected to the May library. Users can change the language that a Task guide appears in by changing the Language settings under **Options** &gt; **Preferences**.

> [!NOTE]
> Even though many Task guides have been translated, right now the client is not showing the translated Task guide names. Also, only the task guides that were released in February 2016 are available in translation in the May library. We will release an updated library with additional translations.
>
> - If a task guide has been translated, when you open that task guide all the text of the task guide will appear in your selected language.
> - If a task guide has not yet been translated, when you open it, only some of the text (the text of the controls) will appear in your selected language.

## Adding custom help

You can use task guides to create custom help, or connect a custom help website to the Help pane.

### Create custom help with task guides

You can create custom help for the supported apps by creating task recordings that reflect your implementation, and saving them to an LCS Business Process Library. You cannot create custom task guides for Human Resources.

As a partner, if you promote a library to be a corporate library, and include it in a solution, it will be available to your customers. You can also make a copy of the APQC Unified global library, and then open the task recordings in the copy, modify them, and save the recordings with your changes. For more information, see [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).

### Connect a custom help site

Finance and Operations apps are rarely used out-of-the-box. Rather, the solution is customized and extended to fit the organization's needs. Similarly, you can customize and extend the Help experience, including adding custom help to the in-product Help pane.  

Microsoft has provided a toolkit to help you deploy and connect custom Help to the Help pane. In [Custom Help Overview](../../dev-itpro/help/custom-help-overview.md), you can read about how you can set up a custom Help solution that is connected to the Help pane.  

If you want to collaborate with Microsoft on tools and processes for customizing help, fill in the form at [https://aka.ms/customhelpfeedback](https://aka.ms/customhelpfeedback).  

## See also

[Help overview](help-overview.md)  
[Custom Help Overview](../../dev-itpro/help/custom-help-overview.md)  
[Task recorder overview](../../dev-itpro/user-interface/task-recorder.md)  
[How to create a task recording to use as documentation or training](../../dev-itpro/user-interface/task-recorder-training-docs.md)  
[Custom Help GitHub repository](https://github.com/microsoft/dynamics356f-o-custom-help)  
