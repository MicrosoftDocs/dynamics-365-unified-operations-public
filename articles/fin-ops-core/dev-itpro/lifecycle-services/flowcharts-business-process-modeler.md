---
title: Flowcharts in Business process modeler (BPM)
description: Learn about how to modify connected flowcharts, create and upload flowcharts from Task recorder, and import a business process model flowchart.
author: AngelMarshall
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 7.0
ms.assetid: c1735f54-e020-45c6-97d1-d6da2382881b
---

# Flowcharts in Business process modeler (BPM)

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> Flowchart diagrams in Business process modeler are deprecated. For more information, see [Flowchart diagrams in Business process modeler](/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#flowchart-diagrams-in-business-process-modeler).

You can use Business process modeler in Microsoft Dynamics Lifecycle Services to define and store business process flowcharts for an organization. This article explains how you can view the default connected flowcharts, export a connected flowchart as a Visio file, and upload and view unconnected flowcharts.

- Connected flowcharts are the automatically generated flowcharts based on data recorded in Task recorder and uploaded to Business process modeler. This flowchart also includes the process steps from the task recording.
- Unconnected flowcharts are uploaded directly from Visio.

<!---
## Connected flowcharts
This section explains how to view a connected flowchart, how to modify it, how to export the flowchart to Visio, how to generate a gap analysis, and how to export the gap analysis to a comma-separated file that you can manually import into Microsoft Visual Studio Team Foundation Server as work items. For information about how to upload recordings of custom business processes, see [Upload custom business processes to Business process modeler (BPM)](upload-business-processes-bpm-task-recorder.md). 

The following table describes the activities that can appear in flowcharts.

| Activity                  | Description                                                                                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Script                    | Action that a script performs.                                                                                                                                    |
| Loop                      | Action that the process performs repetitively.                                                                                                                                   |
| Service                   | Action that a service performs.                                                                                                                                   |
| Manual                    | Step that a user performs outside of a finance and operations app.                                                                                                                               |
| Receive                   | Information that the process receives from outside of a finance and operations app without using a service or script.                                                                                  |
| Send                      | Information that the process sends outside of a finance and operations app without using a service or script.                                                                                           |
| User                      | Action that a user performs.                                                                                                                                      |
| Collapsed                 | A sub-process that the diagram doesn't show. Collapsed processes can't be expanded.                                                                          |
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

1. Sign in to Lifecycle Services, open a project, and then select **Business process modeler**.
1. In the **Project libraries** section, select a library to display it.
1. Expand the business process library and then select a library node that has a flowchart icon associated with it: :::image type="content" source="./media/flowchart-bpm-topic1.jpg" alt-text="Screenshot of the flowchart icon in Business process modeler.":::

    The flowchart is displayed. Each activity in the process is represented by a shape in the diagram. Process steps are displayed in the right pane.

<!---
### Modify a connected flowchart

You can modify an existing connected flowchart to match your company's business process.

> [!NOTE]
> Any time you modify a flowchart, a gap is automatically created.

To modify a connected flowchart, follow these steps:
1.  Sign in to Lifecycle Services, open a project, and then select **Business process modeler**.
1.  In the **My libraries** section, select a library to display it.
1.  Open a library node with a flowchart icon.
1.  Make changes to the flowchart.
    -   To change an existing flowchart activity, right-click the activity to display the app bar, and then select **Edit**. Make changes, and then select **Save**.
    -   To add a flowchart activity, drag an activity from the **Activities** list to the flowchart. Right-click the new activity and then select **Edit** to change the name and other information for the activity. Make changes and then select **Save**.
    -   To delete a flowchart activity, right-click the activity, and then select **Delete**.

### Import a business process model flowchart from another library

You can import a business process model flowchart from an existing business process library into a bottom-level task.
1.  Select an existing task that doesn't have an associated flowchart, right-click it to display the app bar, and then select **Import**.
1.  On the **Import business process model** page, select a library to import from, and then select the appropriate business process. Only business processes with existing model flowcharts appear in the list.
1.  When the **Do you want to copy** message appears, select **Yes**. When the import finishes, the flowchart is associated with the original task. Gap information and the version history are also copied.
--->

### Export a flowchart as a Visio file

You can export a business process model flowchart to a Visio file.

1. Sign in to Lifecycle Services, open a project, and then select **Business process modeler**.
1. In the **Project libraries** section, select a library to display it.
1. Expand the library and then select any library node that has a flowchart icon associated with it.
1. From the **Overview** pane, select **Diagram** to view the flowchart.
1. From the flowchart tab, select **Export** to save as a Visio file.

<!--
### Mark a change to not be a gap
The gap functionality is deprecated in Lifecycle Services. For more information about how to use Azure DevOps Synchronization, see [Synchronize BPM libraries with Azure DevOps](synchronize-bpm-vsts.md).

Any time you modify a flowchart, a gap is automatically created. You can modify any change to no longer be considered a gap. 

To modify a change, follow these steps:

1.  Select the object that you added, and then right-click it.
1.  On the app bar, select **Not a gap**.

### Generate a gap analysis and export it to use with Azure DevOps

You can generate a gap analysis list for the project that you are working with. You can export the gap analysis list to a comma-separated file. You can then import that file to Visual Studio Team Foundation Server to create work items. 

To generate a gap analysis and export it, follow these steps:

1.  Sign in to Lifecycle Services, open a project, and then select **Business process modeler**.
1.  In the **My libraries** section, select a library to display it.
3.  Expand the library and then click any library node that has a flowchart icon associated with it. The flowchart is displayed.
4.  Right-click the flowchart to display the app bar, and then click **Gap list**. The **Gap analysis** page is displayed. The page includes all modifications for the project that you are working with. It includes changes to the standard library and to all default flowcharts for the project.
5.  Optional: To export the gap analysis to a comma-separated file, right-click to display the app bar, and then click **Export**. A .csv file is created. You can import the file into Visual Studio Team Foundation Server to create work items that represent the work that is required to fill in the gaps.
-->

## Unconnected flowcharts

Unconnected flowcharts, such as a Visio diagram, can be helpful for describing high-level business processes that are performed outside of the finance and operations apps.

### Upload an unconnected flowchart

1. In the **Project libraries** section, select a library to display it.
1. Expand the library and then select any library node that has a flowchart icon associated with it.
1. From the **Overview** pane, select **Diagram**.
1. From the **Visio** tab, select **Upload** to upload a Visio file.

> [!NOTE]
> If you have uploaded the wrong file, you can delete the existing one, and upload a new one to replace it.

<!--
### View an unconnected flowchart

A business process with an unconnected Visio flowchart associated with it shows a document icon on its title bar: [![Flowchart BPM topic2.](./media/flowchart-bpm-topic2.jpg)](./media/flowchart-bpm-topic2.jpg)
-   Select the document icon to view the flowchart.
-   Select **Download** on the Visio page to download the flowchart.
--->

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
