---
title: Regression suite automation tool best practices
description: Learn about how to use the Regression suite automation tool (RSAT)/Task recorder to record client functions, including best practices.
author: FrankDahl
ms.author: johnmichalak
ms.topic: best-practice
ms.date: 01/20/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Regression suite automation tool best practices

[!include [banner](../../includes/banner.md)]

This article describes best practices and common use cases for the Regression suite automation tool (RSAT) and Task recorder.

## Author test cases by using the Task recorder

When you author task recordings for RSAT, follow these practices:

1. Make sure all your recordings start on the main dashboard.
1. Keep individual recordings short and focus on a business task performed by one user, like creating a sales order. This approach simplifies maintainability and reusability of test cases.
1. Chart controls aren't supported. RSAT ignores any task recording actions related to charts during test case playback.
1. When creating a recording, make sure to select a tab header even if the tab is already open. For example, you can switch to another tab and then select the needed tab again to activate it before using a control on it. This practice makes your recording more reliable during test case playback.
1. RSAT can't play back any test step that the task recorder doesn't recognize. For example, you can't upload a file from the local disk during playback of a test case.
1. RSAT can't play back a **page refresh** step. Avoid refreshing a page while recording your test.

## Best practices when using the Regression suite automation tool

1. When you open the tool for the first time, select **Settings** and make sure that you have all the needed settings.
1. Before you install a new version of the tool, close and uninstall the previous version.
1. When you install a new version of the tool, regenerate **all** test execution files.

    :::image type="content" source="media/generate-execution-files.png" alt-text="Screenshot of the Generate execution files menu item.":::

    You don't need to regenerate Microsoft Excel parameter files unless you want to take advantage of new features available in a newer format of parameter files.

1. For test parameters that need a unique value, such as the product receipt number in the **Product Receipt** form or the invoice number in the **Vendor Invoice** form, use the **RandBetween(a,b)** Excel function to generate a unique number every time the test case runs.
1. The default values in Excel come from the task recording. For **Reference Group** controls such as storage dimensions or tracking dimensions, the recording stores the key of the lookup instead of the value, such as **2** instead of **SiteWH**. Update these fields with the actual value in Excel so that the test is more robust and resilient to changes.
1. Set the same locale for **Language** and **Date, time, and number format** settings of your environment before running RSAT. If these values are inconsistent, validation errors can occur.

    :::image type="content" source="media/locale.png" alt-text="Screenshot of setting locale, date, time, and number format.":::

## Manage local recording files

RSAT relies on Azure DevOps to store and manage test recording files (also known as task recordings). When RSAT loads a test plan from Azure DevOps, it downloads associated files to the current **working directory** on your local computer. You define this working directory in RSAT settings.

In version 1.200.42264.6 and later, it's easier to manage local recording files. You can make changes in Task recorder and then use RSAT to test them, without having to go through the Business process modeler (BPM) or Azure DevOps. When you use Task recorder, after you finish authoring or modifying a recording, you can save it directly to your local disk as a developer recording.

:::image type="content" source="media/rsat-save-as-developer-recording.png" alt-text="Screenshot of saving a task recording as a developer recording.":::

Put the recording file under the working directory that is associated with the test case. For example, if your configured working directory is `C:\Users\<username>\Documents\RSAT`, put the recording file for test case 1234 under `C:\Users\<username>\Documents\RSAT\1234\attachments`. You must name the developer recording file **Recording.xml**. Alternatively, you can name the recording file **-Test Case Title-.xml**, where **-Test Case Title-** is the title of the test case in Azure DevOps.

The following illustration shows an example of a working directory folder structure. You can open the directory directly from RSAT by selecting the folder symbol.

:::image type="content" source="media/rsat-working-directory-example.png" alt-text="Screenshot of a working directory example.":::

Each test case has its own folder, which is named after the ID of the test case. The **attachments** folder stores test case attachments, including recording files, automation files, and Excel parameter files. Here's an example.

:::image type="content" source="media/rsat-test-case-attachments.png" alt-text="Screenshot of test case attachments.":::

The **generatorLogs** directory contains log files. It doesn't contain any files that users can modify. You can ignore this directory unless RSAT support explicitly asks you to provide log files from it.

### Commit a recording file to Azure DevOps

After you test and finalize a recording, use RSAT to upload and commit it to Azure DevOps. The upload button has two options: **Upload automation files** and **Upload recording file**. The second option uploads only your recording file to Azure DevOps.

> [!NOTE]
> If you're using a version of RSAT that is earlier than 1.200.37255.0, and you upgrade to the latest version, you must reload your test cases from Azure DevOps to download them into the correct directory. Otherwise, RSAT fails and you receive a "File not found" error.
>
> If you're working across several DevOps projects, use a different working directory for each project. Otherwise, attachment files from multiple projects can become commingled in the same directory structure.

## Modify (edit) a task recording

To modify an existing task recording, follow these best practices.

In the web client, open the Task recorder pane and start editing the recording by using the **Edit Recording** option.

:::image type="content" source="media/edit-recording.png" alt-text="Screenshot of the Edit recording option.":::

When you finish editing the recording, play it back in the client, and verify that all the steps work correctly. Playback is required.

:::image type="content" source="media/playback-recording.png" alt-text="Screenshot of the Playback recording option.":::

After you finish playing back an edited recording, save it. RSAT can then use the recording.

## Copy test cases in Azure DevOps

As you build your test suites in Azure DevOps, it's handy and common to duplicate test cases along with their
attachments. If a copied test case contains an existing Excel parameter file attached, RSAT can't execute it without
manual edits to the Excel file. The **Test Case ID** in the Excel parameter file must match the Azure DevOps test case ID.
You need to edit all copied Excel parameter files. In the following image, the Excel file is associated with
Test Case number 53 in Azure DevOps.

:::image type="content" source="media/copy-test-cases.png" alt-text="Screenshot of editing copied test cases.":::

As of RSAT version 1.210, this process is easier. To automatically fix all occurrences of a mismatch, select the
desired test cases in the grid, and then select **Resolve test case ID mismatch** in the **Generate** menu.

:::image type="content" source="media/resolve-test-case-id-mismatch.png" alt-text="Screenshot of resolving a mismatch.":::


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
