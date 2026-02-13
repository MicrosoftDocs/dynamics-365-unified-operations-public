---
title: EUR-00002 Generate an EU Intrastat declaration
description: Learn how to export the Intrastat declaration in the electronic file format and preview the declaration data in a Microsoft Excel format.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport, IntrastatParameters, IntrastatCommodityLookup, IntrastatCompressParameters, Intrastat, SysQueryForm
ms.dyn365.ops.version: Version 7.0.0
---

# EUR-00002 Generate an EU Intrastat declaration

[!include [banner](../../includes/banner.md)]

This article explains how to export the Intrastat declaration in the electronic file format and preview the declaration data in a Microsoft Excel format. 

## Prerequisites

Before you complete the steps in this article, you must transfer transactions to the Intrastat. 

## Import configurations with settings

To import configurations with settings, follow these steps:

1. In Dynamics 365 Finance, go to **Workspaces \> Electronic reporting** and select **Set active**.
1. Select **Repositories \> Open**.
1. Open the **Configuration name** column filter.
1. Apply a filter on the **Configuration name** field using the **begins with** filter operator with a value of "Intrastat (DE)". Select the configuration name that's applicable for the country/region of your legal entity.
1. Select **Import**, and then select **Yes**.
1. Open the **Configuration name** column filter.
1. Apply a filter on the **Configuration name** field, with a value of "intrastat report", using the **begins with** filter operator.
1. Select **Import**, and then select **Yes**.  

## Set up Foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> Foreign trade parameters**.
1. In the **Electronic reporting** section, in the **File format mapping** field, enter or select a value.
1. In the **Report format mapping** field, enter or select a value.
1. In the **Rounding rules** section, in the **Rounding rule** field, enter a number.  
1. In the **Number of decimals for amount** field, enter a number.
1. In the **Rounding below 1 kg** field, select an option.
1. In the **Rounding rule** field, enter a number.
1. In the **Minimum limit** section, in the **Weight** field, enter a number. 
1. In the **Amount** field, enter a number.
1. In the **Commodity** field, enter or select a value.

## Set up compression of Intrastat

To set up compression of Intrastat, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> Compression of Intrastat**.
1. In the list, find and select the desired record. 
1. Select **Add**.

## Generate Intrastat declaration

To generate an Intrastat declaration, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Foreign trade \> Intrastat**.
1. Select **Validate**. The validation is completed according to the **Check setup** field on the **Foreign trade parameters** page.  
1. Select **OK**.
1. Select **Update \> Minimum limit**.
1. In the **Start date** field, enter a date.
1. In the **Compress** field, select **Yes**.
1. In the **End date** field, enter a date and then select **OK**
1. Select **Update \> Compress**. The compression begins according to the **Compression of intrastate** settings.  
1. In the **Start date** field, enter a date.
1. In the **End date** field, enter a date, and then select **OK**
1. Select **Update \> Regenerate sequence numbers**.
1. Select **OK**.
1. Select **Output \> Report**.
1. In the **From date** field, enter the first date of the reporting period.
1. In the **To date** field, enter a date. 
1. In the **Generate file** field, select **Yes**.
1. In the **File name** field, enter a value.
1. In the **Generate report** field, select **Yes**.
1. In the **Report file** name field, enter a value.
1. In the **Direction** field, select an option, and then select **OK**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
