---
title: Task recorder and help for Store Commerce
description: This article describes how to use the task recorder in Microsoft Dynamics 365 Commerce Store Commerce.
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 1205393
ms.assetid: 2f13e9cf-55b5-458b-8c32-3f8cd98c9ecf
ms.search.industry: Retail
ms.search.form: RetailTerminalTable, SystemParameters
---

# Task recorder and help for Store Commerce

[!include [banner](includes/banner.md)]

This article describes how to use the task recorder in Microsoft Dynamics 365 Commerce Store Commerce.

Task recorder in Store Commerce is a new solution that was built with a focus on high responsiveness. It provides a flexible application programming interface (API) for extensibility and seamless integration with consumers of business process recordings. Additionally, task recorder integration with the Business process modeler (BPM) tool on Microsoft Dynamics Lifecycle Services ([https://bpm.lcs.dynamics.com](https://bpm.lcs.dynamics.com/)) has been brought forward. Therefore, users can continue to produce rich business process diagrams from recordings to analyze and design their applications.

## Architecture

Task recorder can record user actions in the client with exact fidelity. Each control is instrumented to notify task recorder about the execution of a user action. The control notifies Task recorder that an event occurred and passes along all pertinent information about the corresponding user action in real time. From this information, Task recorder can capture the type of user action (such as a button click, value entry, or navigation) and any data that is related to the user action (such as the input data value and type, form context, or record context). Task recorder persists the information with enough detail to help guarantee that a playback of the recording can perform the recorded actions exactly as the user performed them. (The playback feature isn't yet implemented in Store Commerce.)

## Basic configuration

To enable task recording in POS, follow these steps.

1. Select **Retail and Commerce \> Channel Setup \> POS Setup \> Registers**.
2. Select the register to enable task recording on.
3. On the **Register** tab, on the **General** FastTab, set the **Enable task recording** option to **Yes**.
4. Select **Save**.
5. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
6. Select the **Registers (1090)** job, and then select **Run now**.

## Create a recording

Follow these steps to create a new recording using task recorder.

1. Start Store Commerce, and sign in.
2. On the **Settings** page, in the **Task Recorder** section, select **Open task recorder**. The **Task recorder** pane appears. You can select the close symbol (**X**) in the upper-right corner to close the **Task recorder** pane before you begin a new recording. To reopen the pane, repeat step 2.

    [![Task recorder pane.](./media/newrecording-1024x450.jpg)](./media/newrecording.jpg)

3. Enter a name and description for the recording, and then select **Start**. The recording session begins as soon as you select **Start**.

    > [!NOTE]
    > If you select the close symbol (**X**) in the upper-right corner while recording is in progress, the **Task recorder** pane is closed, but the recording session isn't ended. To reopen the **Task recorder** pane, select help symbol (**?**) at the top of the screen.
    >
    > [![Question mark.](./media/help.jpg)](./media/help.jpg)

4. After you select **Start**, task recorder enters recording mode. The **Task recorder** pane shows information and controls that are related to the recording process.
5. Perform the actions that you want to perform in the Store Commerce user interface (UI).
6. To end the recording session, select **Stop**.

## Download options

After you end the recording session, several options are shown, so that you can download your recording.

[![Download options.](./media/downlaod-options.jpg)](./media/downlaod-options.jpg)

### Save to this PC

You can use the recording package to play a Task guide, maintain the recording, or edit the annotations in the recording. (This feature isn't yet implemented in Store Commerce.)

### Export as Word document

You can save the recording as a Microsoft Word document. The document will contain the recorded steps and the screenshots that were captured.

### Save as developer recording

The raw recording file will be useful for developer scenarios such as test code generation. (This feature isn't yet implemented.)

## Recording controls

[![Recording controls.](./media/controls.jpg)](./media/controls.jpg)

### Stop the recording session

Select **Stop** to end the recording session. Note that you can't restart a session after you end it. Therefore, make sure that the recording is completed before you end it.

### Pause the recording session

Select **Pause** to temporarily stop (pause) the recording session and continue with the operation. Steps that you perform after you select **Pause** aren't recorded.

### Continue the recording session

To resume the recording session after you've paused it, select **Continue**.

### Capture screenshots

Task recorder can capture screenshots of the Store Commerce UI as you record a business process. To turn on the screenshot capture feature, set the **Capture screenshot** option to **Yes** and then make the recording. Once the recording is completed, select **Stop** and download the Word document. The document will contain the steps with relevant screenshots.

> [!NOTE]
> Capture screenshot functionality is not supported in Store Commerce.

### Start task and End task

You can specify the beginning and end of a set of grouped steps by using the **Start task** and **End task** buttons. Select **Start task** to add a "Start Task" step, and then perform the steps that should be included in the group. After you've finished performing the steps for the group, select **End task**. Tasks help you organize your procedures. Tasks can be nested within other tasks. In this way, you can better organize very long and complex business processes.

## Adding annotations

An annotation is additional text that you add to a step in a recording. For example, you can use annotations to give the user more context or instructions. You can add annotations before or after a step. You can add an annotation to any step by selecting the edit (pencil) symbol  to the right of the step.

[![Edit button for a step.](./media/annotate.jpg)](./media/annotate.jpg)

### Texts and notes

You can use the **Texts** and **Notes** fields to add text that should be associated with a step in a Task guide.

[![Text and Notes fields.](./media/annotatesteps.jpg)](./media/annotatesteps.jpg)

#### Text

Text that you enter in the **Text** field appears *above* the step text in the Task guide. This location is appropriate for text that you want the user to read before the user completes the step.

#### Notes

Text that you enter in the **Notes** field appears *below* the step text in the Task guide. To read the note text, the user must expand the step text in the pop-up window. This location is appropriate for optional reading material or other information that might be useful to the user, but that the user doesn't require in order to complete the action.

## Help in Store Commerce

To show your own custom task recordings in the **Help** pane of Store Commerce so that they can be viewed as text, you must save your task recordings to your own BPM library, and then update your help system parameters to point to your BPM library. For more information, see [Connecting the Help system](../fin-ops-core/fin-ops/get-started/help-connect.md). Store Commerce help searches LCS in real time. It searches across all the BPM libraries that are selected in the Commerce help system parameters and shows the relevant results. To access the help menu, select the help symbol (**?**) at the top of the screen, and then in the search box enter your process name and select the search symbol.

[![Help button.](./media/help.jpg)](./media/help.jpg)

When you select a task guide in the search results, you can either view the steps as a help article or export the steps to a Word document.

> [!NOTE]
> Help in Store Commerce will not bring up task guides according to what form you're on or operation you're doing. You have to type the process name in the search box and then select **Search**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
