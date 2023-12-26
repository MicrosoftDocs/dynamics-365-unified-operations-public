---
title: EUR-00002 Generate an EU Intrastat declaration
description: This article explains how to export the Intrastat declaration in the electronic file format and preview the declaration data in an Excel format.
author: AdamTrukawka
ms.date: 08/01/2023
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport, IntrastatParameters, IntrastatCommodityLookup, IntrastatCompressParameters, Intrastat, SysQueryForm
---
# EUR-00002 Generate an EU Intrastat declaration

[!include [banner](../../includes/banner.md)]

This article explains how to export the Intrastat declaration in the electronic file format and preview the declaration data in a a Microsoft Excel format. 

## Prerequisites
Before you complete the steps in this article, transfer transactions to the Intrastat. 

## Import configurations with settings
1. Go to **Workspaces** > **Electronic reporting** and select **Set active**.
2. Select **Repositories** > **Open**.
3. Open the **Configuration name** column filter.
4. Apply a filter on the **Configuration name** field, with a value of **"Intrastat (DE)"**, using the **"begins with"** filter operator. Select the configuration name that's applicable for the country/region of your legal entity.
5. Select **Import** and then select **Yes**.
6. Open the **Configuration name** column filter.
7. Apply a filter on the **Configuration name** field, with a value of **"intrastat report"**, using the **"begins with"** filter operator.
8. Select **Import** and then select **Yes**.  

## Set up Foreign trade parameters
1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. In the **Electronic reporting** section, in the **File format mapping** field, enter or select a value.
4. In the **Report format mapping** field, enter or select a value .
5. In the **Rounding rules** section, in the **Rounding rule** field, enter a number.  
7. In the **Number of decimals for amount** field, enter a number.
8. In the **Rounding below 1 kg** field, select an option.
9. In the **Rounding rule** field, enter a number.
10. In the **Minimum limit** section, in the **Weight** field, enter a number. 
12. In the **Amount** field, enter a number.
13. In the **Commodity** field, enter or select a value.

## Set up Compression of Intrastat
1. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**.
2. In the list, find and select the desired record. 
3. Select **Add**.

## Generate Intrastat declaration
1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. Select **Validate**. The validation is completed according to the **Check setup** field on the **Foreign trade parameters** page.  
3. Select **OK**.
4. Select **Update** > **Minimum limit**.
5. In the **Start date** field, enter a date.
6. In the **Compress** field, select **Yes**.
7. In the **End date** field, enter a date and then select **OK**
8. Click **Update** > **Compress**. The compression happens according to the **Compression of intrastate** settings.  
9. In the **Start date** field, enter a date.
10. In the **End date** field, enter a date and then select **OK**
11. Select **Update** > **Regenerate sequence numbers**.
12. Select **OK**.
13. Select **Output** > **Report**.
14. In the **From date** field, enter the first date of the reporting period.
15. In the **To date** field, enter a date. 
16. In the **Generate file** field select **Yes**.
17. In the **File name** field, enter a value.
18. In the **Generate report** field, select **Yes**.
19. In the **Report file** name field, enter a value.
20. In the **Direction** field, select an option and then select **OK**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
