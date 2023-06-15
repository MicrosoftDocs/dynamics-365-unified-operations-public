---
# required metadata

title: Flowcharts in Business process modeler (BPM)
description: This article describes how to modify connected flowcharts, create and upload flowcharts from Task recorder, and import a business process model flowchart.
author: AngelMarshall 
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: c1735f54-e020-45c6-97d1-d6da2382881b
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 
ms.dyn365.ops.version: 7.0

---

# Flowcharts in Business process modeler (BPM)

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> Flowchart diagrams in Business process modeler have been deprecated. To learn more about the deprecation, see [Flowchart diagrams in Business process modeler](/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#flowchart-diagrams-in-business-process-modeler).

You can use Business process modeler in Microsoft Dynamics Lifecycle Services (LCS) to define and store business process flowcharts for an organization. This article explains how you can view the default connected flowcharts, export a connected flowchart as a Visio file, and upload and view unconnected flowcharts.

-   Connected flowcharts are the automatically generated flowcharts based on data recorded in Task recorder and uploaded to Business process modeler, this also includes the process steps from the task recording. 
-   Unconnected flowcharts are uploaded directly from Visio.

<!---
## Connected flowcharts
This section explains how to view a connected flowchart, how to modify it, how to export the flowchart to Visio, how to generate a gap analysis, and how to export the gap analysis to a comma-separated file that you can manually import into Microsoft Visual Studio Team Foundation Server as work items. For information about how to upload recordings of custom business processes, see [Upload custom business processes to Business process modeler (BPM)](upload-business-processes-bpm-task-recorder.md). 

Activities that can appear in flowcharts are described in the following table.

| Activity                  | Description                                                                                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Script                    | Action performed by a script.                                                                                                                                    |
| Loop                      | Action performed repetitively.                                                                                                                                   |
| Service                   | Action performed by a service.                                                                                                                                   |
| Manual                    | Step performed outside of a finance and operations app.                                                                                                                               |
| Receive                   | Information received from outside of a finance and operations app without using a service or script.                                                                                  |
| Send                      | Information sent outside of a finance and operations app without using a service or script.                                                                                           |
| User                      | Action performed by a user.                                                                                                                                      |
| Collapsed                 | A sub-process that is not shown in the diagram. Collapsed processes cannot be expanded.                                                                          |
| Arrow                     | Indicates direction of flow between process steps.                                                                                                               |
| Validation                | Decision point at which a process either proceeds or loops.                                                                                                      |
| Process start (circle)    | The beginning of the process.                                                                                                                                    |
| Process end (bold circle) | The end of the process.                                                                                                                                          |
| Roles                     | Role swimlane. Add roles when a process requires actions by multiple roles to complete. Swimlanes list the default roles that can perform the action. |

### 
--->

### View a connected flowchart

Default connected flowcharts are available for many nodes in the industry-standard libraries. You can view a connected flowchart to determine whether it meets your needs. 

To view a connected flowchart, follow these steps:

1.  Sign in to Lifecycle Services, open a project, and then click **Business process modeler**.
2.  In the **Project libraries** section, select a library to display it. 
3.  Expand the business process library and then click a library node that has a flowchart icon associated with it: [![Flowchart BPM topic1.](./media/flowchart-bpm-topic1.jpg)](./media/flowchart-bpm-topic1.jpg)

    The flowchart is displayed. Each activity in the process is represented by a shape in the diagram. Process steps are displayed in the right pane. 

<!---
### Modify a connected flowchart

You can modify an existing connected flowchart to match your company's business process.

> [!NOTE]
> Any time you modify a flowchart, a gap is automatically created.

To modify a connected flowchart, follow these steps:
1.  Sign in to Lifecycle Services, open a project, and then click **Business process modeler**.
2.  In the **My libraries** section, select a library to display it.
3.  Open a library node with a flowchart icon.
4.  Make changes to the flowchart.
    -   To change an existing flowchart activity, right-click the activity to display the app bar, and then click **Edit**. Make changes, and then click **Save**.
    -   To add a flowchart activity, drag an activity from the **Activities** list to the flowchart. Right-click the new activity and then click **Edit** to change the name and other information for the activity. Make changes and then click **Save**.
    -   To delete a flowchart activity, right-click the activity, and then click **Delete**.

### Import a business process model flowchart from another library

You can import a business process model flowchart from an existing business process library into a bottom level task.
1.  Select an existing task that does not have an associated flowchart, right-click it to display the app bar, and then click **Import**.
2.  On the **Import business process model** page, select a library to import from, and then select the appropriate business process. Only business processes with existing model flowcharts appear in the list.
3.  When the **Do you want to copy** message appears, click **Yes**. When the import is complete, the flowchart will be associated with the original task. Gap information and the version history are also copied.
--->

### Export a flowchart as a Visio file

You can export a business process model flowchart to a Visio file.
1.  Sign in to Lifecycle Services, open a project, and then click **Business process modeler**.
2.  In the **Project libraries** section, select a library to display it.
3.  Expand the library and then select any library node that has a flowchart icon associated with it.
4.  From the **Overview** pane, select **Diagram** to view the flowchart.   
5.  From the flowchart tab, click **Export** to save as a Visio file. 

<!--
### Mark a change to not be a gap
Please note that gap functionality has been deprecated in LCS. To learn more about how to use Azure DevOps Synchronization, see [Synchronize BPM libraries with Azure DevOps](synchronize-bpm-vsts.md).

Any time you modify a flowchart, a gap is automatically created. You can modify any change to no longer be considered a gap. 

To modify a change, follow these steps:

1.  Select the object that you added, and then right-click it.
2.  On the app bar, click **Not a gap**.

### Generate a gap analysis and export it to use with Azure DevOps

You can generate a gap analysis list for the project that you are working with. You can export the gap analysis list to a comma-separated file. You can then import that file to Visual Studio Team Foundation Server to create work items. 

To generate a gap analysis and export it, follow these steps:

1.  Sign in to Lifecycle Services, open a project, and then click **Business process modeler**.
2.  In the **My libraries** section, select a library to display it.
3.  Expand the library and then click any library node that has a flowchart icon associated with it. The flowchart is displayed.
4.  Right-click the flowchart to display the app bar, and then click **Gap list**. The **Gap analysis** page is displayed. The page includes all modifications for the project that you are working with. It includes changes to the standard library and to all default flowcharts for the project.
5.  Optional: To export the gap analysis to a comma-separated file, right-click to display the app bar, and then click **Export**. A .csv file is created. You can import the file into Visual Studio Team Foundation Server to create work items that represent the work that is required to fill in the gaps.
-->

## Unconnected flowcharts
Unconnected flowcharts, such as a Visio diagram, can be very helpful for describing high-level business processes that are performed outside of the finance and operations apps.

### Upload an unconnected flowchart

1.  In the **Project libraries** section, select a library to display it.
2.  Expand the library and then click any library node that has a flowchart icon associated with it.
3.  From the **Overview** pane, select **Diagram**.   
5.  From the **Visio** tab, click **Upload** to upload a Visio file.

> [!Note] 
> If you have uploaded the wrong file, you can delete the existing one, and upload a new one to replace it.

<!--
### View an unconnected flowchart

A business process with an unconnected Visio flowchart associated with it will have a document icon on its title bar: [![Flowchart BPM topic2.](./media/flowchart-bpm-topic2.jpg)](./media/flowchart-bpm-topic2.jpg)
-   Click the document icon to view the flowchart.
-   Click **Download** on the Visio page to download the flowchart.
--->


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
