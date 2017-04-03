---
# required metadata

title: Set up Business process modeler libraries for an LCS solution
description: This topic explains how to create and work with Business process modeler (BPM) libraries.
author: kfend
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: Lifecycle Services
# ms.tgt_pltfrm: 
ms.custom: 196953
ms.assetid: 6e6d6896-edef-4739-98ad-c4ea19180972
ms.search.region: Global
# ms.search.industry: 
ms.author: omarc
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Set up Business process modeler libraries for an LCS solution

This topic explains how to create and work with Business process modeler (BPM) libraries.

Create a business process library
---------------------------------

There are two ways to create a Business process modeler (BPM) library. You can create a new library that has no lines or task recordings, or you can copy an existing library.

1.  In Microsoft Dynamics Lifecycle Services (LCS), open a project, scroll to the right until you see the **More tools** section, and then click the **Business process modeler** tile. The **Business process libraries** page that appears has three sections, one for each type of library:
    -   **My libraries** – Business processes that users have created or added.
    -   **Corporate libraries** – Custom business processes that someone in your organization has uploaded.
    -   **Global libraries** – Cross-industry standard business processes. [![Three types of libraries on the Business process libraries page](./media/bpm_02.png)](./media/bpm_02.png)

2.  To create a new library, right-click any library, and then, in the lower-left corner of the window, click **Create**. To copy an existing library, right-click that library, and then, in the lower-left corner of the window, click **Copy**. [![Location of the Copy button](./media/bpm_03.png)](./media/bpm_03.png)
3.  Enter a name for the library.

The library that you created now appears under **My libraries**.

## Update, publish, or delete a business process library
You can change the name or description of a library, publish a library so that other people in your organization can view it, or delete a library.

-   On the **Business process libraries** page, right-click the library to update, publish, or delete. Then, in the lower-left corner of the window, click **Edit**, **Publish**, or **Delete**.
    -   **Edit** lets you change the name and description of the library.
    -   **Publish** creates a copy of the library under **Corporate libraries**. This library will be available to everyone in your organization.
    -   **Delete** deletes the library and any information that is stored in it.

## Modify a business process library
Follow these steps to change or update the business process lines or hierarchy in your business process library.

1.  Select and open the library to update.
2.  In the left pane, under **Core views**, click **Author and edit**.
3.  Follow one or more of these steps to make the required changes:
    -   To rearrange the hierarchy of the business process lines, drag the processes in the hierarchy.
    -   To delete a node, click a business process in the center pane, and then click **Delete** in the right pane.
    -   To create a new node, drag the **New Business Process** flag at the top of the center pane to the place in the hierarchy where the new node should appear. [![BPM\_06](./media/bpm_06.png)](./media/bpm_06.png)
    -   To import business processes from existing business process libraries, follow these steps:
        1.  Click **Import** in the center pane.
        2.  On the right side of the page that appears, select the library to import business processes from.
        3.  Drag the required business processes into the hierarchy on the left side of the page.

## View and modify task recordings in a business process library
1.  Open the library that you want to work in.
2.  Navigate to the business process line that has a task recording associated with it, and click the link.
3.  Drag the tiles under **Activities** to manually modify the flow chart. [![BPM\_09](./media/bpm_09.png)](./media/bpm_09.png)
4.  To upload a Microsoft Visio diagram of the modified flow chart, click the **Visio** tab.

## Structure a business process library
There are two sections in business process libraries: **Core Business Processes** and **Support Processes**. The **Core Business Processes** section should include all custom business processes for your solution. All customizations and functionality should be covered in end-to-end scenarios. Task recordings should be created for all processes in this section. Import American Productivity & Quality Center (APQC) processes that are relevant to your solution into the **Support Processes** section. This section should not include any custom business processes. You don't have to create task recordings for processes in this section. Your business process library should be aligned with the descriptions and summaries in your methodology and your marketing material.

## Create a task recording and associate it with a business process
Task recordings should be created in a Microsoft Dynamics 365 for Operations environment that has your custom data and customizations. For reference information about Task recorder, see [Task Recorder in Microsoft Dynamics 365 for Operations](../user-interface/task-recorder.md).

### Create a task recording

1.  In Dynamics 365 for Operations, click the **Settings** button in the upper-right corner, and then click **Task recorder**.
2.  Click **Create recording**.
3.  Enter a name and description for the recording.
4.  Perform the task that you want to record.
5.  When you've completed the task, click **Stop**.
6.  If you want to upload your new task recording to LCS, continue to the next section. To save your recording to your local computer or convert the recording to a Microsoft Word document, select the appropriate option.

### Associate a task recording with a business process

1.  Click **Save to LCS**.
2.  Select a business process library.
3.  Select the business process line to associate with the recording.
4.  Click **OK**.

You can now view the task recording in the business process library in LCS.

## Set up and use task guides
Task recordings can be played as task guides. Task guides are used to guide users through the steps for completing business processes. Before you set up and use task guides, create task recordings and save them to a business process library in LCS.

### Set up task guides

1.  In Dynamics 365 for Operations, click **System administration** &gt; **Setup** &gt; **System parameters**, and then click the **Help** tab.
2.  Select the LCS project where the business process library that you want to work with is stored.
3.  Select the business process libraries that have the task recordings that you want to play as task guides.
4.  Adjust the order of the business process libraries as required. The order of the business process libraries determines the order that the task guides appear in. Therefore, the task guides for the first business process library appear first when a user uses the task guide functionality.

### Use task guides

1.  In Dynamics 365 for Operations, open the page where you want to run the task guide.
2.  In the upper-right corner, click the **Settings** button, and then click **Task recorder**.
3.  Select a task guide.
4.  Click **Start Task guide**.
5.  Follow the steps in the task guide. If you click **Unlock**, you can work without following the task guide.
6.  When you've finished, click **Stop Task guide**.


See also
--------

[LCS Solutions for AppSource home page](lcs-solutions-app-source.md)

