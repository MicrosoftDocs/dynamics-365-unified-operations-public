---
# required metadata

title: Run, store, and export compare item prices reports
description: Learn how to run a compare item prices report and make the output available digitally
author: AndersGirke
manager: AnnBe
ms.date: 12/12/2019
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace  
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: aevengir
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.0

---

# Run, store, and export compare item prices reports

[!include [banner](../includes/banner.md)]

Read this topic to learn how to run a compare item prices report and make the output available digitally, either as a browsable form in Supply Chain Management, or as an exported document in any of several formats.

In the form, columns and aggregate balances are dynamically adjusted, depending on your configured layout. You can sort the form, filter it, drill down into the data, and more. Report results are stored in the *compare item prices* data entity, which lets you export the results to a format such as Microsoft Excel or Adobe PDF.

This method of running the compare item prices report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have more than 40,000 items holding a pending item price in the costing version.

To run a compare item prices report and then store or export it:

1. Go to **Cost management** > **Inquiries and reports** > **Predetermined cost reports** > **Compare item prices storage**.

1. Select **New** to open the **Compare item prices** flyout. Make the following settings here:

    - In the **Parameters** FastTab, give the report a unique **Name** and use the fields in the **Pending prices to compare** and **Prices used for comparison** to define which prices and dates to compare.
    - In the **Records to include** FastTab, set up filters and constraints to define which data to include in the report.
    - In the **Run in the background** FastTab, set up how, when, and how often you want to run the report.
    <!-- editor comment: I wasn't able to generate a report because it needed a "version" but there aren't any in my system; there are multiple tables called "costing versions", so I don't know which to use. Many of these settings aren't obvious--do we have any existing documentation to link to from here? -->
    > [!NOTE]
    > This report is always executed as part of a batch job.

1. Select **OK** to apply your settings and close the flyout.

1. After the batch job is completed, the output is shown on the **Compare item prices storage** page.

1. To view the output as a form that has a traditional grid layout, select **View details**.

The *compare item prices* data entity lets you export the output of a compare item prices report by applying a filter for the **Process Identifier – Name** and **Execution time** fields to any format that data management supports.

<!-- editor comment: I don't understand this last paragraph. Can we give a procedure for how to do the export? -->