---
title: Business performance planning Excel add-in FAQ
description: Access answers to frequently asked questions about the Microsoft Excel add-in for business performance planning, including questions about installation.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 05/31/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Business performance planning Excel add-in FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Excel add-in for business performance planning.

## After I install the Business performance add-in from the business performance planning app, I don't see it in my downloaded Excel workbook. What should I do?

To make the tab for the add-in visible in your Excel workbook, follow this step.

- When you open the downloaded Excel workbook, select **Enable content**.

If that approach doesn't work, follow these steps.

1. Confirm that other add-ins are disabled, and then restart Excel.
2. Select **File** \> **Options** to open Excel options.
3. Select **Add-ins**.
4. In the **Manage** field, select **COM Add-ins**. Then select **Go**.
5. The available Component Object Model (COM) add-ins are shown. Clear the checkbox for each of the other add-ins, and then select **OK**.
6. Close all open Excel workbooks.
7. Reopen your downloaded Excel workbook.
8. Select **Enable content**.

## When I connect to data, I can't select the cube/dimension tables because the selection window is inconsistently empty. What should I do?

This issue occurs when you work with multiple monitors or more than just your laptop display. It's a known bug that we're actively working to fix.

To work around this issue, follow one of these steps.

- Go to **File** > **Options**. On the **General** tab, > **User interface options**, select **Optimize for compatibility (application restart required)**.
- Drag the table selection window to your main monitor (laptop display). The user interface should appear.
- Duplicate your screen, and begin to interact with table selections and authentication prompts.

## After I connect to data, I see only my cube data connected. How do I see my dimension data connected?

After you connect to your database server, confirm that all the cube and dimension tables that you want to bring into your data model in Excel are selected. You can also follow these steps.

1. To select multiple items, select the checkbox.
2. Select your cube.
3. Select **Select related tables**.
4. Wait until Excel selects everything. Then select **Load**.

## After I create my PivotTable, I can't modify values in it. An error message states that the source table name is incorrect. What should I do?

The relationship between your cube and dimension tables isn't set up correctly. For more information, see [Configure and use the Excel add-in for business performance planning](use-excel-addin.md).
