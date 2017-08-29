--- 
# required metadata 
 
title: Enable license plate label printing
description: This procedure enables the automatic printing of a Serial shipping container code (SSCC) label after the last item is picked from inventory in a sales picking work process. 
author: perlynne
manager: AnnBe 
ms.date: 11/03/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enable license plate label printing

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure enables the automatic printing of a Serial shipping container code (SSCC) label after the last item is picked from inventory in a sales picking work process. You can run this procedure in demo data company USMF. If you’re run it using your own data, you need to have a number sequence set up for license plates. You need to set up a label printer before you begin this task. Go to Organization administration > Setup > Network printers. On the Action pane, click Options, and then click the Download document routing agent installer button. Run the installer and make sure that you have a working network printer set to Active before you continue with the procedure.


## Set up the GS1 company prefix
1. Go to Warehouse management > Setup > Warehouse management parameters.
2. In the GS1 company prefix field, enter the 7 numbers for your GS1 company number.
3. Click Save.
4. Close the page.

## Setup the SSCC license plate number sequence
1. Go to Organization administration > Number sequences > Number sequences.
2. In the Area field, select an option.
3. In the Reference field, select an option.
4. In the Company field, type a value.
5. In the list, mark the selected row.
6. In the list, click the link in the selected row.
7. Expand the Segments section.
8. Click Edit.
9. In the Segments table, select the first row
10. Click Remove.
11. Click Remove.
12. Click Save.
13. Close the page.

## Create the document route layout
1. Go to Warehouse management > Setup > Document routing > Document routing layouts.
    * Enable the SSCC layout.  
2. Click New.
3. In the Layout ID field, type a value.
4. In the Description field, type a value.
5. In the list, find and select the desired record.
6. Click Insert at end of text.
7. Click Save.
8. Close the page.

## Set up the document routing
1. Go to Warehouse management > Setup > Document routing > Document routing.
2. In the Work order type field, select an option.
3. Click New.
4. In the Warehouse field, type a value.
5. In the Name field, type a value.
6. Click New.
7. In the Layout ID field, enter or select a value.
8. In the Name field, enter the printer name that you want to use..
9. Click Save.
10. Close the page.

## Create mobile device menu
1. Go to Warehouse management > Setup > Mobile device > Mobile device menu items.
2. Click New.
3. In the Menu item name field, type a value.
4. In the Title field, type a value.
5. In the Mode field, select an option.
6. Select Yes in the Use existing work field.
7. Select Yes in the Generate license plate field.
8. Expand the Work classes section.
9. Click New.
10. In the Work class ID field, type a value.
11. Click Save.
12. Close the page.
13. Go to Warehouse management > Setup > Mobile device > Mobile device menu.
14. In the list, find and select the desired record.
15. In the tree, select 'In the tree, select the menu item that you created before.'.
16. Click Edit.
17. Click on the arrow to add the menu item to the menu.
18. Click Save.
19. Close the page.

## Update a work template
1. Go to Warehouse management > Setup > Work > Work templates.
2. In the list, find and select the desired record.
3. Click Edit.
4. Click New.
5. In the list, mark the selected row.
6. In the Work type field, select 'Print'.
7. In the Work class ID field, enter or select a value.
8. In the list, click the link in the selected row.
9. Click Move up.
10. Click Save.
11. Close the page.

