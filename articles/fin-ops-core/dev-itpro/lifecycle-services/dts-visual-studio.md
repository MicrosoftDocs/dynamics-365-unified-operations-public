---
title: Dynamics 365 Translation Service Visual Studio extension
description: Learn about how to integrate the Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio into your Visual Studio workflow.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-12-13
ms.custom: sfi-image-nochange
---

# Dynamics 365 Translation Service Visual Studio extension

[!include[banner](../includes/banner.md)]
[!INCLUDE[dts-deprecation](../../fin-ops/includes/dts-deprecation.md)]

The Microsoft Dynamics 365 Translation Service (DTS) extension for Visual Studio enables finance and operations developers to perform DTS actions directly from their Visual Studio integrated development environment (IDE). For example, you can translate user interface (UI) files and regenerate the translations. For more information about the supported functionality, see [Dynamics 365 Translation Service overview](translation-service-overview.md).

To use the DTS Visual Studio extension, you must have access to Microsoft Dynamics Lifecycle Services. Additionally, the extension primarily supports the development workflow for finance and operations apps in Visual Studio. For more information, see [Development and administration for finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/). 

## Installing the extension

You can download the Visual Studio extension from [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

Download and install the extension to your Visual Studio development environment. After you install the extension, the **Tools** menu includes new commands that DTS adds. This extension only supports finance and operations app localization.

## Using the extension

### Sign in to DTS

Before you can start to use the DTS Visual Studio extension, you must authenticate with Lifecycle Services. You're automatically prompted to sign in after running any command while you're in a signed-out state.

### Access the DTS commands

You can access the DTS commands in two ways:

- Select **Tools** on the main toolbar, select **Dynamics 365 Translation Service**, then select a DTS command from the menu. Five DTS commands are available: **Translate**, **Regenerate**, **Download translation result**, **Align**, and **Log out**.

    :::image type="content" source="media/dts-vs-tools-menu.png" alt-text="Screenshot of Tools menu in the Visual Studio IDE.":::

- Select and hold (or right-click) a file in your solution, then select a DTS command on the shortcut menu.

## Features

### Translation workflow

Before you translate any resource files, you should have the resource files for both the source language and the target language. If you already have the resource files for the source language, you can create the files for the target language by selecting and holding (or right-clicking) a source resource node and then selecting **Add new languages**.

:::image type="content" source="media/dts-vs-new-language.png" alt-text="Screenshot of Add new languages command.":::

The **Label File Wizard** appears. Complete this wizard to create new label files for your desired languages. For guidance on using the label file wizard, see [How to: Create a Label File](/dynamicsax-2012/developer/how-to-create-a-label-file).

:::image type="content" source="media/dts-vs-label-wizard.png" alt-text="Screenshot of Label file wizard.":::

You're now ready to create a new translation request. On the **Tools** menu, select **Dynamics 365 Translation Services**, then select **Translate**. A dialog box appears, where you can configure the new translation request.

The following table describes the fields in the **Translate with Dynamics 365 Translation Service** dialog box.

| Field              | Required | Description |
|--------------------|----------|-------------|
| Region             | Yes | Leave the default value, unless you need to change it. |
| Request name       | Yes | Enter a name for the request. |
| Product            | Yes | Select the product type. |
| Project            | Yes | Select the project that contains the resource files. |
| Source language    | Yes | Select the language of the source files. |
| Source files       | Yes | Select one or more resource files for translation. This field lists all resource files that are referenced in the selected project. |
| Target language    | Yes | <p>Select a language to translate the source files into.</p><p><strong>Note:</strong> You can translate only into a target language that a resource file already exists for. Language names that are shown in bold are General Availability (GA) languages for Microsoft Dynamics products. Therefore, product-specific translation memories (TM) and machine translation (MT) models are available in those languages. The MT models are trained on the terminology for Microsoft Dynamics. For non-GA languages, the general domain MT models are used.</p> |
| Translation memory | No | Add the translation memory files for a specific target language. (The value is the zip file that contains translation memories for recycling.) |
| Create custom MT?  | No | Select whether you want to use the uploaded translation memory to create a custom MT model. |

:::image type="content" source="media/dts-vs-translate.png" alt-text="Screenshot of Translate with DTS dialog box.":::

When you finish configuring the translation request, select **Submit** to send it to DTS. You receive a confirmation window stating the next steps.

:::image type="content" source="media/dts-vs-confirmation.png" alt-text="Screenshot of Confirmation window for the DTS extension.":::

After a short time, the Output window shows the status of the request (unless you select the **Create custom MT?** option). 

:::image type="content" source="media/dts-vs-outputwindow.png" alt-text="Screenshot of Output window for the DTS extension.":::

When the request is completed, you see a Download Translation window stating that the output files (translation memory files and translated resource files) are downloaded. These output files are put in the appropriate language subfolder for the module.

:::image type="content" source="media/dts-vs-downloadtranslations.png" alt-text="Screenshot of Download Translations window for the DTS extension.":::

If you close Visual Studio before the output files are downloaded, you can manually download the files by selecting **Download translation results** on the **Tools** menu.

### Regeneration workflow

We recommend that you review and edit the translations that DTS provides. The XML Localization Interchange File Format (XLIFF) files are in the same directory as their corresponding translated resource files. For more information about how to edit XLIFF files, see [Translation memory files](use-translation-service-tm.md).

When you finish reviewing and editing the XLIFF translation files, you can regenerate the translated native format files. On the **Tools** menu, select **Dynamics 365 Translation Services**, then select **Regenerate**. A dialog box appears, where you can configure the regeneration request.

The following table describes the fields in the **Regenerate** dialog box.

| Input             | Required | Description |
|-------------------|----------|-------------|
| Project           | Yes | Select the project that is associated with the revised translation memories. |
| Translation files | Yes | <p>Select one or more revised translation memory files. The files in the list are automatically identified and are the result of previous DTS translation requests.</p><p>Each revised translation memory file (.xlf file) that you select is used to regenerate the corresponding target native file. For example, **ExampleLabel.es.label.txt.xlf** regenerates **ExampleLabel.es.label.txt**.</p> |

:::image type="content" source="media/dts-vs-regenerate.png" alt-text="Screenshot of Regenerate with DTS dialog box.":::

When you finish configuring the regeneration request, select **Submit** to send it to DTS. The **Output** window shows the status of the request. When the request completes, you see a Download Translation window stating that output files (translation memory files and target translated files) are downloaded by overwriting the previous outputs.

:::image type="content" source="media/dts-vs-downloadtranslations.png" alt-text="Screenshot of Download Translations window for the DTS extension.":::

### Creating a translation memory (alignment)

If you have label resource files that were previously translated, you can reuse the translation for a newer version of the source files by creating a translation memory (TM) that uses XLIFF.

On the **Tools** menu, select **Dynamics 365 Translation Services**, then select **Align**. A dialog box appears, where you can configure the alignment request.

| Field              | Required | Description |
|--------------------|----------|-------------|
| Region             | Yes | Leave the default value, unless you need to change it. |
| Source Language    | Yes | Select the language of the source files. Select a label file or folder containing the label files. |
| Target Language    | Yes | Select the language of the target files and upload the file or folder. |
| Output Path        | Yes | Select the output path. |

:::image type="content" source="media/dts-vs-alignment.png" alt-text="Screenshot of Dialog box where you can configure the alignment request.":::

When you finish configuring the alignment request, select **Submit** to send it to DTS. You're notified that the process has started.

:::image type="content" source="media/dts-vs-alignmentinprocess.png" alt-text="Screenshot of You're notified that the process has started.":::

The **Output** window shows the status of the request. When the request is completed, you see a window stating that output files are available.

:::image type="content" source="media/dts-vs-alignedfiles.png" alt-text="Screenshot of Output files are available.":::
