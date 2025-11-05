---
title: Change page layout properties of a template in ER destinations
description: Learn how to change page layout properties of a template in ER destinations.
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

# Change page layout properties of a template in ER destinations

[!include [banner](../includes/banner.md)]

You can configure an ER destination for an ER format component that's designed to use a template in a Microsoft Office (Excel or Word) format for report generation. 
If you aren't the owner of this format and you need to change page layout properties of the format's template, you can change the page layout properties of the template at runtime to avoid creating and maintaining the derived format configuration. To do this, set up the desired properties as part of the settings of the configured ER destination. When you run an ER format and execute an ER destination that's configured to use certain page layout properties, the values of page layout properties of the executed destination are applied to the template you use, replacing the original template's properties. You can configure different destinations for the same format's component configuring different page layout properties for the template in use.

The following properties can be configured in an ER destination for a format component that's designed to use a template in Excel or Word format:

- Page orientation
    - Portrait
    - Landscape
- Paper size
    - A3
    - A4
    - A5
    - B4
    - B5
    - Executive
    - Legal
    - Letter
    - Statement
    - Tabloid
- Page margins
    - Top
        - Header
    - Bottom
        - Footer
    - Left
    - Right

> [!NOTE]
> The page orientation of the template that's configured in this way must be aligned with the page orientation for PDF conversion if the PDF conversion is configured.

You must select the length unit for setting page margins:

- Inches
- Centimeters
- Millimeters

:::image type="content" source="./media/er_destinations-set-page-layout-properties.png" alt-text="Screenshot of the Electronic reporting destination page showing page layout property settings.":::

> [!TIP]
> When you specify a margin value in centimeters with multiple decimals, the value is rounded at runtime to the nearest value with one decimal point.
>
> When you specify a margin value in millimeters with decimals for Excel, the value is rounded at runtime to the nearest integer value with no decimal point.
>
> When you specify a margin value in millimeters with multiple decimals for Word, the value is rounded at runtime to the nearest value with one decimal point.
