--- 
# required metadata 
 
title: EUR-00011 Generate the EU sales list report
description: This procedure walks you through generating the EU sales list report. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines,  EUSalesList, EUSalesListSelection, SysQueryForm, SysLookup   
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
# EUR-00011 Generate the EU sales list report

[!include [banner](../../includes/banner.md)]

This procedure walks you through generating the EU sales list report. This includes transferring intra-community trade transactions to the EU sales list and running the report. This procedure also includes creating an intra-community trade transaction for demo purposes. For more information about EU Sales list reporting, including required prerequisites, refer to Help.

This procedure applies to all European countries/regions. The procedure was created using the demo data company DEMF and consequently Germany as an exemplar domestic country/region. The procedure also uses Portugal as an exemplar EU country/region. Before you can complete this procedure, you must configure EU sales list reporting.

This procedure is intended for accountants.


## Create an intra-community sales transaction for demo purposes
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, type 'PRT-001'.
4. Click OK.
5. In the Item number field, type 'D0001'.
6. Expand the Line details section.
7. Click the Setup tab.
8. In the Item sales tax group field, type 'FULL'.
9. Click Add line.
10. In the Item number field, type 'D0003'.
11. In the Item sales tax group field, type 'RED'.
12. Click Save.
13. On the Action Pane, click Invoice.
14. Click Invoice.
15. Expand the Parameters section.
16. In the Quantity field, select 'All'.
17. Expand the Setup section.
18. In the Invoice date field, set the date to '01/11/2016'.
19. Click OK.
20. Click OK.

## Transfer intra-community trade transactions to the EU sales list
1. Go to Tax > Declarations > Foreign trade > EU sales list.
2. Click Transfer.
3. Select Yes in the Item field to transfer item transactions.
4. Select Yes in the Service field to transfer service transactions.
    * You can also specify additional filters on intra-community trade transactions to transfer.  
5. Click Transfer.
    * Verify that the intra-community sales transaction is successfully transferred to the EU sales list.  

## Generate the EU sales list report
1. Click Reporting.
2. In the Reporting period field, select 'Monthly'.
3. In the From date field, set the date to '01/01/2016'.
4. Select Yes in the Generate file field.
5. Select Yes in the Generate report field.
6. In the File name field, type 'EUSalesList'.
7. In the Report file name field, type 'EUSalesList'.
8. In the EU Sales List Registration ID field, type '123'.
    * This field is only available for Germany.  
    * You can also specify additional filters on intra-community trade transactions to include in the report.  
9. Click OK.
    * Verify that pop-up windows appear to confirm that the file and the control report are being downloaded.  

## Mark EU sales list lines as Reported
1. Click Mark.
2. Click Mark as reported.
3. In the list, select the row for the Invoice date field.
4. In the Criteria field, type '01/01/2016..01/31/2016'.
5. In the list, select the row for the Reporting status field.
6. In the Criteria field, select 'Included'.
    * You can also specify additional filters on intra-community trade transactions to mark as Reported.  
7. Click OK.
8. In the Selection field, select 'Reported'.

## Mark EU sales list lines as Closed
1. Click Mark.
2. Click Mark as closed.
3. In the list, mark the row for the Invoice date field.
4. In the Criteria field, type '01/01/2016..01/31/2016'.
5. In the list, mark the row for the Reporting status field.
6. In the Criteria field, select 'Reported'.
    * You can also specify additional filters on intra-community trade transactions to mark as Closed.  
7. Click OK.
8. In the Selection field, select 'Closed'.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]