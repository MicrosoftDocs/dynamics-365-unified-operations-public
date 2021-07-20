--- 
# required metadata 
 
title: EUR-00011 Set up EU sales list reporting
description: This task walks you through an overview of the prerequisites required for EU sales list reporting. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport, SysQueryForm, SysQueryFieldLookUp,  TaxTable, TaxGroup, TaxItemGroup, TaxCountryRegionParameters, TaxVATNumTable, IntrastatParameters, CustTable, DirPartyQuickCreateForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# EUR-00011 Set up EU sales list reporting

[!include [banner](../../includes/banner.md)]

This task walks you through an overview of the prerequisites required for EU sales list reporting. For more information about EU Sales list reporting, including required prerequisites, refer to Help.

This task applies to all European countries/regions. The guide was created using the demo data company DEMF and consequently Germany as an exemplar domestic country/region. The guide also uses Portugal as an exemplar EU country/region.

These tasks are intended for system administrators.


## Import electronic reporting configurations for EU sales list reporting
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Set active.
3. Click Repositories.
4. Click Open.
5. On the Action Pane, click Options.
6. Click Advanced Filter/Sort.
7. Click Add.
8. In the Field field, select 'Configuration name'.
9. In the Criteria field, type 'EU Sales list (DE)'.
10. Click OK.
11. Click Import.
12. Click Yes.
13. On the Action Pane, click Options.
14. Click Advanced Filter/Sort.
15. Click Reset.
16. Click Add.
17. In the Field field, select 'Configuration name'.
18. In the Criteria field, type 'EU Sales list by rows report'.
19. Click OK.
20. Click Import.
21. Click Yes.

## Set up sales tax codes for EU sales list reporting
1. Go to Tax > Indirect taxes > Sales tax > Sales tax codes.
2. Use the Quick Filter to filter on the Sales tax code field with a value of 'VAT19'.
3. Expand the Report setup section.
    * Verify that the Excluded selection is set to No.  
    * You may need to unlock the task guide to change this setting.  

## Set up sales tax groups for EU sales list reporting
1. Go to Tax > Indirect taxes > Sales tax > Sales tax groups.
2. Use the Quick Filter to filter on the Sales tax group field with a value of 'AR-DOM'.
3. Click Edit.
4. Expand the Setup section.
5. In the list, select the first row.
6. Select the Exempt check box.
7. In the list, select the second row.
8. Select the Exempt check box.
9. In the list, select the third row.
10. Select the Exempt check box.

## Set up item sales tax groups for EU sales list reporting
1. Go to Tax > Indirect taxes > Sales tax > Item sales tax groups.
2. Use the Quick Filter to filter on the Item sales tax group field with a value of 'FULL '.
    * Verify that the Reporting type selection is set to 'Item'.  
    * You may need to unlock the task guide to change the value in this field.  
3. Use the Quick Filter to filter on the Item sales tax group field with a value of 'RED '.
    * Verify that the Reporting type selection is set to 'Service'.  
    * You may need to unlock the task guide to change the value in this field.  

## Set up country/region parameters for EU sales list reporting
1. Go to Tax > Setup > Sales tax > Country/region parameters.
2. Click New.
3. In the Country/region field, type 'PRT'.
4. In the Sales tax field, type 'PT'.

## Create tax exempt numbers
1. Go to Tax > Setup > Sales tax > Tax exempt numbers.
2. Click New.
3. In the Country/region field, type 'PRT'.
4. In the Tax exempt number field, type 'PT12345'.

## Set up EU sales list reporting parameters
1. Go to Tax > Setup > Foreign trade > Foreign trade parameters.
2. Click the EU sales list tab.
3. Select Yes in the Transfer purchases field.
4. Expand the Rounding rules section.
5. Set Rounding rule to '0.1'.
6. Select Yes in the Use minimum value field.
7. In the Number of decimals field, enter '2'.
8. Expand the Electronic reporting section.
9. In the File format mapping field, select 'EU Sales list (DE)'.
10. In the Report format mapping field, select 'EU Sales list by rows report'.
11. Click the Country/region properties tab.
    * Verify that the Country/region type field is set to 'Domestic' for Country/region DEU.  
    * You may need to unlock the task guide to change the value in this field.  
12. Click New.
13. In the Country/region field, type 'PRT'.
14. In the Intrastat code field, type 'PT'.
15. In the Country/region type field, select 'EU'.
16. Click the Number sequences tab.
    * Verify that a Number sequence code is specified for the Reference 'EU sales list'.  

## Create a customer for EU sales list reporting demo purposes
1. Go to Accounts receivable > Customers > All customers.
2. Click New.
3. In the Customer account field, type 'PRT-001'.
4. In the Name field, type 'A customer from Portugal'.
5. In the Customer group field, select '10'.
6. In the Sales tax group field, select 'AR-DOM'.
7. In the Tax exempt number field, select 'PT12345'.
8. In the Country/region field, type 'PRT'.
9. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]