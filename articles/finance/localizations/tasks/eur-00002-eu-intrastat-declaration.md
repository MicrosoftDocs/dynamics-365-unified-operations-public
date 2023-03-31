---
title: EUR-00002 Generate an EU Intrastat declaration
description: This procedure walks you through the steps required to export the Intrastat declaration in the electronic file format and preview the declaration data in an Excel format.
author: AdamTrukawka
ms.date: 08/29/2018
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

This procedure walks you through the steps required to export the Intrastat declaration in the electronic file format and preview the declaration data in an Excel format. 

Before you can complete this procedure, you must transfer transactions to the Intrastat. 

This procedure was created using the demo data company DEMF.


## Import configurations with settings
1. Go to Workspaces > Electronic reporting
2. Click Set active.
3. Click Repositories.
4. Click Open.
5. Open Configuration name column filter.
6. Apply a filter on the "Configuration name" field, with a value of "Intrastat (DE)", using the "begins with" filter operator.
    * You should select the configuration name applicable for the country of your legal entity. This procedure uses the German legal entity (DEMF) as an example, therefore "Intrastat (DE)" should be chosen.  
    * Click Import and then click Yes.  
7. Open Configuration name column filter.
8. Apply a filter on the "Configuration name" field, with a value of "intrastat report", using the "begins with" filter operator.
    * Click Import and then click Yes.  

## Set up Foreign trade parameters
1. Go to Tax > Setup > Foreign trade > Foreign trade parameters
2. Expand the Electronic reporting section.
3. In the File format mapping field, enter or select a value Intrastat (DE)
4. In the Report format mapping field, enter or select a value Intrastat report
5. Expand the Rounding rules section.
    * You should set up rounding rules that are applicable in your country/region for Intrastat reporting.  
6. In the Rounding rule field, enter a number.
    * Enter rounding precision, for example, enter '0.01'.  
7. In the Number of decimals for amount field, enter a number.
    * For example, enter '2'.  
8. In the Rounding below 1 kg field, select an option.
    * For example, select 'Rounding up to 1 kg'.  
9. In the Rounding rule field, enter a number.
    * For example, enter '1' for rounding weight to the integer.  
10. Expand the Minimum limit section.
11. In the Weight field, enter a number.
    * For example, enter '10' as the minimum weight.  
12. In the Amount field, enter a number.
    * For example, enter '200' as the minimum amount.  
13. In the Commodity field, enter or select a value.

## Set up Compression of Intrastat
1. Go to Tax > Setup > Foreign trade > Compression of Intrastat.
2. Click Remove.
3. In the list, find and select the desired record.
    * For example, select Commodity in the Available section.  
4. Click Add.

## Generate Intrastat declaration
1. Go to Tax > Declarations > Foreign trade > Intrastat
2. Click Validate.
    * The validation is done according to the Check setup field on the Foreign trade parameters page.  
3. Click OK.
4. Click Update.
5. Click Minimum limit.
6. In the Start date field, enter a date.
    * For example, enter January 1, 2015.  
7. Select Yes in the Compress field.
8. In the End date field, enter a date.
    * For example, enter January 31, 2015.  
9. Click OK.
10. Click Update.
11. Click Compress.
    * This compression happens according to how you set the Compression of intrastate settings.  
12. In the Start date field, enter a date.
    * For example, enter January 1, 2015.  
13. In the End date field, enter a date.
    * For example, enter 31st January 2015.  
14. Click OK.
15. Click Update.
16. Click Regenerate sequence numbers.
17. Click OK.
18. Click Output.
19. Click Report.
20. In the From date field, enter the first date of the reporting period.
    * For example, set the date to January 1, 2015.  
21. In the To date field, enter a date.
    * For example, enter January 31, 2015.  
22. Select Yes in the Generate file field.
23. In the File name field, type a value.
24. Select Yes in the Generate report field.
25. In the Report file name field, type a value.
26. In the Direction field, select an option.
    * For example, select 'Dispatches'.  
27. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
