--- 
# required metadata 
 
title: Enable license plate label printing
description: This article shows how to enable the automatic printing of a Serial shipping container code (SSCC) label after the last item is picked from inventory in a sales picking work process. 
author: perlynne
ms.date: 07/19/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysCorpNetPrinterList, WHSParameters, NumberSequenceTableListPage, NumberSequenceDetails, WHSDocumentRoutingLayout, WHSDocumentRouting, WHSRFMenuItem, WHSRFMenu, WHSWorkTemplateTable, WHSLicensePlateLabelBuildConfig, WHSLicensePlateLabel
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enable license plate label printing

[!include [banner](../../includes/banner.md)]

This article shows how to enable the automatic printing of a Serial shipping container code (SSCC) label after the last item is picked from inventory in a sales picking work process. You can run this procedure in demo data company USMF. If you're run it using your own data, you need to have a number sequence set up for license plates. You need to set up a label printer before you begin this task. Go to Organization administration > Setup > Network printers. On the Action Pane, click Options, and then click the Download document routing agent installer button. Run the installer and make sure that you have a working network printer set to Active before you continue with the procedure.


## Set up the GS1 company prefix
1. Go to **Warehouse management > Setup > Warehouse management parameters**.
2. In the **GS1 company prefix** field, enter the 7 numbers for your GS1 company number.
3. Select **Save**.
4. Close the page.

## Setup the SSCC license plate number sequence
1. Go to **Organization administration > Number sequences > Number sequences**.
2. In the **Area** field, select an option.
3. In the **Reference** field, select an option.
4. In the **Company** field, type a value.
5. Expand the **Segments** section.
6. Select **Edit**.
7. In the **Segments** table, select the first row
8. Select **Remove**.
9. Select **Remove**.
10. Select **Save**.
11. Close the page.

## Create the document route layout
1. Go to **Warehouse management > Setup > Document routing > Document routing layouts**. Enable the SSCC layout.  
2. Select **New**.
3. In the **Layout ID** field, type a value.
4. In the **Description** field, type a value.
5. Select **Insert at end of text**.
6. Select **Save**.
7. Close the page.

## Set up the document routing
1. Go to **Warehouse management > Setup > Document routing > Document routing**.
2. In the **Work order type** field, select an option.
3. Select **New**.
4. In the **Warehouse** field, type a value.
5. In the **Name** field, type a value.
6. Select **New**.
7. In the **Layout ID** field, enter or select a value.
8. In the **Name** field, enter the printer name that you want to use.
9. Select **Save**.
10. Close the page.

## Create mobile device menu
1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
2. Select **New**.
3. In the **Menu item name** field, type a value.
4. In the **Title** field, type a value.
5. In the **Mode** field, select an option.
6. Select **Yes** in the **Use existing work** field.
7. Select **Yes** in the **Generate license plate** field.
8. Expand the **Work classes** section.
9. Select **New**.
10. In the **Work class ID** field, type a value.
11. Select **Save**.
12. Close the page.
13. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
14. In the tree, select the menu item that you created before.
15. Select **Edit**.
16. Select the arrow to add the menu item to the menu.
17. Select **Save**.
18. Close the page.

## Update a work template
1. Go to **Warehouse management > Setup > Work > Work templates**.
2. Select **Edit**.
3. Select **New**.
4. In the **Work type** field, select **Print**.
5. In the **Work class ID** field, enter or select a value.
6. Select **Move up**.
7. Select **Save**.
8. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]