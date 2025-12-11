---
title: Output unfolding for Folder component of ER format
description: Learn about the output unfolding for Folder component of ER format in Electronic reporting destinations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/01/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
---

# Output unfolding for Folder component of ER format

[!include [banner](../includes/banner.md)]

When you configure a destination for the **Folder** component of your ER format, you specify how the output of that component is delivered to the configured destination.

## Applicability

You can configure the output unfolding option only for the format components of the **Folder** type. When you start to configure a **Folder** component, the **General** FastTab is available on the **Electronic reporting destination** page. 

## Use the output unfolding option

On the **General** FastTab, in the **Send folder as** field, select one of the following values:

- **ZIP archive** – Deliver a generated file as a zip file.
- **Separate files** – Deliver every file of a generated zip file as an individual file.

    > [!NOTE]
    > When you select **Separate files**, the generated output is collected in memory in a zipped state. Therefore, the maximum [file size limit](er-compress-outbound-files.md) is applied for zipped output when the real file size can exceed this limit. Select this value when you expect the size of the generated output to be large.

:::image type="content" source="./media/er_destinations-set-unfolding-option.png" alt-text="Screenshot of configuring a destination for a Folder format component.":::

## Limitations

If you set the **Send folder as** field to **Separate files** for a **Folder** component that contains other nested **Folder** components, the setting doesn't apply recursively to the nested **Folder** components.
