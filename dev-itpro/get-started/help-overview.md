---
# required metadata

title: Help overview
description: This article provides an overview of the components of the Microsoft Dynamics 365 for Operations Help system. It also explains how you can provide custom documentation and training to your organization. 
author: margoc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 16381
ms.assetid: 018c148c-9cbd-41e0-8186-d75dbf66288f
ms.search.region: Global
# ms.search.industry: 
ms.author: margoc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Help overview

[!include[banner](../includes/banner.md)]


This article provides an overview of the components of the Microsoft Dynamics 365 for Operations Help system. It also explains how you can provide custom documentation and training to your organization. 

Dynamics 365 for Operations includes a Help system that is based on two main components:

-   A documentation site
-   Task guides

You can access both articles and task guides from the Help pane in Dynamics 365 for Operations as shown in the following screen shot. 
[![Help pane](./media/help-pane-ops-task-guides-1024x741.png)]
This article describes the Help system, and explains how you can create custom documentation and training resources for your organization.

## Help on docs.microsoft.com
The docs.microsoft.com site ([docs.microsoft.com/dynamics365/operations](/dynamics365/#pivot=solutions&panel=solutions_operations)) is the primary source of product documentation for Dynamics 365 for Operations. The site offers the following features:

-   **Access to the most up-to-date content** – The site gives us a faster and more flexible way to create, deliver, and update product documentation. Therefore, it helps guarantee that you have access to the latest technical information.
-   **Content that is written by experts** – The site provides a richer set of product documentation that can be enhanced by community members both inside and outside Microsoft.
-   **Access to different types of content** – The site lets you quickly access different types of content about Dynamics 365 for Operations, such as Microsoft Office Mix presentations, task guides, videos, and topics.
-   **Content that supports your business processes** – The site includes business process–focused content that takes advantage of the Business Process Modeler (BPM) in Microsoft Dynamics Lifecycle Services (LCS).

We've migrated all of the content from our previous help wiki to docs. We’re very excited about our new site and hope that you will be too.

### How can I contribute? 

Leave us a comment! Click **Comments** to get to the comments at the bottom of the page.
[!Comments](./media/comments.png)]

Start typing your comments, and then click **Post comment**.
[!Post comment](./media/before-signin.png)]

Click an icon on the left to sign in with any of the following types of accounts, or, on the right, enter an email address, and a new password to create a new account for this site: 

[!Sign in options](./media/signin-options.png)]


## Task guides
A Task guide is a controlled, guided, interactive experience that leads you through the steps of a task, or business process. You can open (play) a Task guide from the Help pane. When you first click a Task guide, the Help pane will show the step-by-step instructions for the task. Localized Task guides are now available. [![Task guide reading view](./media/task-guide-ops-1024x742.png)](./media/task-guide-ops.png) To begin the guided, interactive experience, click **Start task guide** at the bottom of the Help pane. A black pointer opens and indicates the action that you have to perform. Follow the directions that appear in the UI, and enter data as directed. [![Task guide step instruction](./media/task-guide-step-1-ops.png)](./media/task-guide-step-1-ops.png) **Important:** The data that you enter when you play a Task guide is real. If you're in a production environment, the data will be entered in the company that you’re currently using.

### It all begins with Task Recorder

Task guides are created by using Task Recorder. When you use Task Recorder, all the actions that you perform in the Dynamics 365 for Operations UI (such as clicking menus, changing settings, and entering data) are recorded. The steps that you record are collectively called a task recording. As we explained in the previous section, task recordings can be displayed in the Help pane and played as task guides. However, there are other ways that you can use task recordings:

-   **Save task recordings to BPM** – You can save a task recording to a line of a hierarchy in a BPM library in LCS. When you save a task recording to BPM, a flowchart diagram is generated and displayed, together with the steps of the recording. **Note:** To display a task recording in the Dynamics 365 for Operations Help pane and play it as a task guide, you'll have to save the recording to a BPM library.
-   **Save task recordings as Word documents** – By saving a task recording as a Microsoft Word document, you can easily produce printable training guides for your organization.

For more information about Task Recorder, see [Task recorder in Dynamics 365 for Operations](../user-interface/task-recorder.md).

### Creating customized task recordings

You can create your own task recordings, or you can download and customize task recording that Microsoft provides. Therefore, you can create customized Help for your organization that reflects your specific Dynamics 365 for Operations implementation. To display a task recording in the Dynamics 365 for Operations Help pane and play it as a Task guide, you'll have to save the recording to a BPM library in LCS. If you're a partner, and you promote a library to a corporate library and include it in a solution, it will be available to your customers. For complete instructions, see [Using task recordings to create documentation or training](../user-interface/task-recorder.md).

## In-product Help
To access Help content within Dynamics 365 for Operations , either click the **Help** (**?**) icon and then choose Help or press Ctrl+Shift+?. In both cases, the Help pane opens. From the Help pane, you can access articles or task guides. [![Help pane](./media/help-pane-wiki-1024x684.png)](./media/help-pane-wiki.png)

### Accessing articles from the Help pane

From the Help pane, you can access articles that apply to the Dynamics 365 for Operations client. When you first open the Help pane and click the **Wiki** tab, you’ll see the articles that apply to the page that you’re currently on in Dynamics 365 for Operations. If no articles are found, you can enter keywords to refine your search. When you click an article in the Help pane, a new tab opens in your browser and displays the article. 

### Accessing Task guides from the Help pane

Before you can access Task guides from the Help pane, a System administrator has to go to the **System parameters** page in Dynamics 365 for Operations and configure some settings. **Notes:**

-   In order to configure help, you must be signed in with an account in the same tenant as the tenant in which Dynamics 365 for Operations is deployed.
-   It is not possible to connect to an LCS library from an instance of Dynamics 365 for Operations running in a local virtual hard drive (VHD).

[![System Parameters form with Help settings](./media/system-parameters_ops-1024x437.png)](./media/system-parameters_ops.png) On the **System parameters** page, follow these steps:

1.  **Important:** The first time you open the Help tab, you must connect to Lifecycle Services. Be sure to click the link in the middle of the form, wait for the connection, close the dialog box, and then click OK to get to the parameters form.[![Connect to LCS](./media/connect-to-lcs-crop-1024x365.png)](./media/connect-to-lcs-crop.png)
2.  Select the Lifecycle Services project to connect to.
3.  Select the BPM libraries (within the selected project) to retrieve task recordings from.
4.  Set the display order of the BPM libraries. This determines the order in which task recordings from the libraries will appear in the Help pane.

After a System administrator has completed these steps, you can open the Help pane and click the **Task guides** tab. You'll now see the Task guides that apply to the page that you’re currently on in Dynamics 365 for Operations. If no Task guides are found, you can enter keywords to refine your search. After you click a Task guide in the Help pane, the Help pane shows the step-by-step instructions, and you can play the task guide. [![Task guide reading view](./media/task-guide-ops-1024x742.png)](./media/task-guide-ops.png)

### Where are the translated Task guides?

Translated Task guides are released in libraries with "All languages" in the title. In Dynamics 365 for Operations, to see localized Task guide help, make sure that you are connected to an apppropriate library. The language that a Task guide appears in is controlled for each user by the Language settings under **Options** &gt; **Preferences**. 
-   If a Task guide has been translated, when you open that Task guide all the text of the Task guide will appear in your selected language.
-   If a Task guide has not yet been translated, when you open it, only some of the text (the text of the controls) will appear in your selected language.

## Additional resources
The following table lists websites that provide Dynamics 365 for Operations content. Our content websites are organized to support the customer life cycle. Each phase is supported by a different set of sites. Sites that have an asterisk (\*) next to the name require that you sign in by using an account that is associated with a service plan.

| Site                                                                     | Description                                                                                                                                                                                                                                |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Docs.microsoft.com](/dynamics365/#pivot=solutions&panel=solutions_operations) | Hosts or links to all product documentation for Dynamics 365 for Operations.                                                                                                                                                               |
| [Lifecycle Services](http://lcs.dynamics.com/en/)\*                      | Provides a cloud-based collaborative workspace that customers and partners can use to manage Dynamics 365 for Operations projects from pre-sales to implementation and operations. This site is useful in all phases of an implementation. |
| [CustomerSource](http://www.customersource.com/)\*                       | Hosts extensive training resources and is the primary support site for Dynamics 365 for Operations. Sign in may be required to access specific resources on the site.                                                                      |
| [Support blog](http://aka.ms/AXSupportBlog)                              | Provides tips and tricks that are posted by the Dynamics 365 for Operations Support team.                                                                                                                                                  |
| [MSDN](http://aka.ms/AXMSDN)                                             | Hosts content from previous releases that is written for developers.                                                                                                                                                                       |
| [TechNet](http://aka.ms/TechNet)                                         | Hosts content from previous releases that is written for IT professionals and application users.                                                                                                                                           |
| [Dynamics Community](http://community.dynamics.com/)                  | Hosts blogs, forums, and videos.                                                                                                                                                                                                           |
| [Microsoft.com/Dynamics/](http://www.microsoft.com/dynamics/)                 | Provides evaluation and sales information.                                                                                                                                                                                                 |



See also
--------

[Dynamics 365 for Operations help system (downloadable fact sheet)](https://mbs.microsoft.com/files/public/CS/AX2012R3/DynamicsAXHelpSystemFactSheet.pdf)

[Task Recorder in Microsoft Dynamics 365 for Operations](../user-interface/task-recorder.md)

[Create documentation or training using Task recordings](../user-interface/task-recorder.md)

[New or updated Task guides (November 2016)](new-task-guides-november-2016.md)
[New or updated task guides (August 2016)](new-updated-task-guides-available-august-2016.md)
[New or updated task guides (May 2016)](new-updated-task-guides-available-may-2016.md)
[New task guides (February 2016)](new-task-guides-available-february-2016.md)







