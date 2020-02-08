---
# required metadata

title: Help system
description: This topic provides an overview of the Help system.
author: margoc
manager: AnnBe
ms.date: 10/02/2019
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
ms.custom: 16381
ms.assetid: 018c148c-9cbd-41e0-8186-d75dbf66288f
ms.search.region: Global
# ms.search.industry: 
ms.author: margoc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Help system

[!include [banner](../includes/banner.md)]

This topic provides an overview of the components of the Help system. The Help system is shared by the following products:

- Dynamics 365 Finance 
- Dynamics 365 Commerce
- Dynamics 365 Supply Chain Management
- Dynamics 365 Human Resources

You can access help from the Help pane in whichever product you are using. 

![Help pane](./media/help-pane-ops-task-guides.png)

## Help on docs.microsoft.com

The docs.microsoft.com site ([docs.microsoft.com/dynamics365/](https://docs.microsoft.com/dynamics365/)) is the primary source of product documentation for the applications listed above. The site offers the following features:

- **Access to the most up-to-date content** – The site gives us a faster and more flexible way to create, deliver, and update product documentation. Therefore, it helps to ensure that you have access to the latest technical information.
- **Content that is written by experts** – The site provides a richer set of product documentation that can be enhanced by community members both inside and outside Microsoft.

You can also find our content with any search engine. We recommend that for best results, you use a site search, such as site:docs.microsoft.com dynamics 365 "search term".

### Use an RSS feed

To subscribe to an RSS feed of all updates to the content, use the following link from a browser that supports RSS feeds, such as Internet Explorer, or an RSS feed manager:

[RSS feed](https://docs.microsoft.com/api/search/rss?locale=en-us&$filter=scopes%2Fany(t%3A%20t%20eq%20%27Unified%20Operations%27))

### Leave us feedback

If you have feedback or questions about a topic, leave us a comment at the bottom of the page.

1. Click **Feedback** to get to the comments at the bottom of the page, and then click either **Product feedback**, or **Sign in to give documentation feedback**.

2. Start typing your comments, and then click **Submit feedback**.

    ![Post comment](./media/feedback.png)

### Contribute to the documentation

You can contribute and make edits to the documentation. To get started, click the **Edit** (pencil) button on a topic. The following video shows how you can contribute to our documentation.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE36liB]

The [How to contribute to the Microsoft Dynamics 365 documentation](https://youtu.be/m5djioozRbg) video (shown above) is included in the Microsoft Dynamics 365 channel on YouTube.

For more information, refer to our [contributor's guide](https://docs.microsoft.com/contribute).

> [!NOTE]
> We only accept contributions to our English content at this time.

## Task guides

A Task guide is a controlled, guided, interactive experience that leads you through the steps of a task, or business process. You can open (play) a Task guide from the Help pane. When you first click a Task guide, the Help pane will show the step-by-step instructions for the task. Localized Task guides are available.

Microsoft shipped Task guide libraries for releases through December 2017 for Dynamics 365 for Finance and Operations. The section [Help system](help-overview.md#accessing-task-guides-from-the-help-pane) describes how to find the correct Task guides for your product.

![Task guide reading view](./media/task-guide-ops.png)

To begin the guided, interactive experience, click **Start task guide** at the bottom of the Help pane. A black pointer opens and indicates the action that you must perform. Follow the directions that appear in the UI, and enter data as directed.

![Task guide step instruction](./media/task-guide-step-1-ops.png)

> [!IMPORTANT]
> The data that you enter when you play a Task guide is real. If you're in a production environment, the data will be entered in the company that you're currently using.

You can use Task recorder to create your own custom Task guides. For more information, see [Create documentation or training with Task Recorder](../../dev-itpro/user-interface/task-recorder-training-docs.md).

## In-product Help

To access Help content, either click the **Help** (**?**) icon and then choose Help or press Ctrl+Shift+?. In both cases, the Help pane opens. From the Help pane, you can access articles or Task guides.

![Help pane](./media/help-pane-wiki.png)

### Accessing help topics from the Help pane

From the Help pane, you can access articles that apply to the client. When you first open the Help pane and click the **Help** tab, you'll see the articles that apply to the page that you're currently on. If no articles are found, you can enter keywords to refine your search. When you click an article in the Help pane, a new tab opens in your browser and displays the article.

> [!IMPORTANT]
> This section does not apply to Dynamics 365 Human Resources. The Help system for Human Resources is automatically connected to Task guides for the product. Also, you cannot create custom Task guides for Human Resources.


### Accessing Task guides from the Help pane

Before you can access Task guides from the Help pane, a System administrator has to go to the **System parameters** page in Finance, Supply Chain Managment, and Commerce and configure some settings.

> [!NOTE]
> - In order to configure help, you must be signed in with an account in the same tenant as the tenant in which the app is deployed.
> - It is not possible to connect to an LCS library from an instance of the app running in a local virtual hard drive (VHD).

![System Parameters form with Help settings](./media/system-parameters_ops-1024x437.png)

On the **System parameters** page, follow these steps:

1. **Important:** The first time that you open the Help tab, you must connect to Lifecycle Services. Be sure to click the link in the middle of the form, wait for the connection, close the dialog box, and then click **OK** to get to the parameters form.

    ![Connect to LCS](./media/connect-to-lcs-crop-1024x365.png)

2. Select the Lifecycle Services project to connect to.
3. Select BPM libraries (within the selected project) to retrieve task recordings from.
4. Set the display order of the BPM libraries. This determines the order in which task recordings from the libraries will appear in the Help pane.

After a System administrator has completed these steps, you can open the Help pane and click the **Task guides** tab. You'll now see the Task guides that apply to the page that you're currently on. If no Task guides are found, you can enter keywords to refine your search. After you click a Task guide in the Help pane, the Help pane shows the step-by-step instructions, and you can play the task guide.

![Task guide reading view](./media/task-guide-ops.png)

### Where are the translated Task guides for Microsoft libraries?

Translated Task guides are released in libraries with "All languages" in the title. To see localized Task guide help, make sure that you are connected to an appropriate library. The language that a Task guide appears in is controlled for each user by the Language settings under **Options** &gt; **Preferences**.

- If a Task guide has been translated, when you open that Task guide all the text of the Task guide will appear in your selected language.
- If a Task guide has not yet been translated, when you open it, only some of the text (the text of the controls) will appear in your selected language.

## Creating custom help

You can create help for your users by creating custom Task guides, or connect your own website to the Help pane. For details, see:

- [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).
- [Create Custom Help (white paper)](https://go.microsoft.com/fwlink/?linkid=2041185)

## Additional resources

- [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md)

The following table lists our websites. Sites that have an asterisk (\*) next to the name require that you sign in by using an account that is associated with a service plan.

| Site                                                                                           | Description |
|------------------------------------------------------------------------------------------------|-------------|
| [Docs.microsoft.com](/dynamics365/)                                                            | Hosts or links to all product documentation for Dynamics 365. |
| [Microsoft Learn](https://docs.microsoft.com/learn/)                                           | Microsoft's free eLearning site. |
| [Lifecycle Services](https://lcs.dynamics.com/)\*                                              | Provides a cloud-based collaborative workspace that customers and partners can use to manage projects from pre-sales to implementation and operations. This site is useful in all phases of an implementation. |
| [Support blog](https://aka.ms/AXSupportBlog)                                                    | Provides tips and tricks that are posted by the Support team. |
| [Docs.microsoft.com/previous versions](https://docs.microsoft.com/previous-versions/dynamics/) | Hosts content from previous releases. |
| [Dynamics Community](https://community.dynamics.com/)                                          | Hosts blogs, forums, and videos. |
| [Microsoft.com/dynamics365/](https://www.microsoft.com/dynamics365/home)                       | Provides evaluation and sales information. |
| [CustomerSource](https://mbs.microsoft.com/customersource/)\*                                  | Hosts training resources, downloadable reports and white papers, and is the primary support site for service plan holders. May require a service plan to access some resources on the site. |
