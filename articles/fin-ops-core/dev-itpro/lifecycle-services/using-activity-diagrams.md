---
title: Work with activity diagrams in Business process modeler libraries
description: Learn about how you can use activity diagrams in a BPM library, including an overview on browsing activity diagrams.
author: AngelMarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: johnmichalak 
audience: Developer, IT Pro
ms.assetid: 
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 2012
ms.custom: sfi-image-nochange
---

# Work with activity diagrams in Business process modeler libraries

[!include [banner](../includes/banner.md)]
[!include [Lifecycle Services deprecation](../includes/lcs-deprecation.md)]

You can associate an activity diagram with a business process. Use activity diagrams to describe how a business process or task is completed in a proposed software solution.

There are two types of activity diagrams:

- **Task recordings** – Business processes that you associate with task recordings for finance and operations include activity diagrams and process steps that are automatically generated.
- **Microsoft Visio** – You can associate a business process with a Visio diagram by manually uploading a Visio file.

## Browse activity diagrams

The **Diagrams** column in your BPM library indicates whether a particular business process is associated with an activity diagram. The number in the column indicates the number of child processes that include diagrams. The symbol next to the number indicates whether the current node or process is associated with a diagram. These indicators don't apply to Visio diagrams.

:::image type="content" source="./media/browse_activity_diagrams.JPG" alt-text="Screenshot of the Diagrams column in a BPM library.":::

To view an activity diagram, select the business process. In the right pane, on the **Overview** tab, select **Diagrams**. The **Flowchart** page appears.

## Upload Task Recording

To upload a task recording, open the business process library that you want to upload to. Select the process step that you want to upload the task recording to, and then select **Upload**.

:::image type="content" source="./media/activity_diagrams_01.jpg" alt-text="Screenshot of selecting a process step to upload a task recording.":::

In the right pane, select **Browse** to choose a file, and then select **Upload**.

:::image type="content" source="./media/activity_diagrams_02.jpg" alt-text="Screenshot of browsing and uploading a task recording file.":::

## Activity diagrams that are created from task recordings

> [!IMPORTANT]
> Flowchart diagrams in Business process modeler are deprecated. For more information, see [Flowchart diagrams in Business process modeler](/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#flowchart-diagrams-in-business-process-modeler).

You can create a task recording in your environment and save it directly to Microsoft Dynamics Lifecycle Services. By using this method, you can associate the task recording with a business process in a BPM library. For more information, see [Connecting the help system](../../fin-ops/get-started/help-connect.md) and [Create documentation or training with Task Recorder](../user-interface/task-recorder-training-docs.md).

The Task recorder tool lets you create a distributable recording file. Recording files use the.axtr file name extension. You can associate a business process in BPM with a task recording by manually uploading the recording file.

To upload a recording file, select the business process. In the right pane, on the **Overview** tab, select **Upload**.

BPM automatically generates an activity diagram and detailed process steps for all task recordings that you create. The following illustration shows an example.

:::image type="content" source="./media/NEWBPM_BlogPost17-1024x483.png" alt-text="Screenshot of an example of an activity diagram and process steps for a task recording.":::

## Visio files

You can associate a business process with a Visio diagram. Typically, use this functionality for high-level processes that can't be represented by a task recording.

> [!NOTE]
> BPM supports .vsd and .vsdx files. However, it doesn't support .vsdm files (macro-enabled Visio drawing files). If a .vsd file contains macros, BPM disables the execution of the macros.

To view or upload a Visio file, follow these steps:

1. Select the business process. In the right pane, on the **Overview** tab, select **Diagrams**.
1. On the **Flowchart** page, select the **Visio** tab. For more information, see the "Unconnected flowcharts" section in [Flowcharts in Business process modeler (BPM)](flowcharts-business-process-modeler.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
