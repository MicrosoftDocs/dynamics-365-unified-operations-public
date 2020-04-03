--- 
# required metadata 
 
title: Set up quality orders
description: This procedure shows you how to enable a quality management process where incoming inventory must be inspected immediately after arrival registration. 
author: perlynne
manager: tfehr 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventParameters, InventTestReportSetup, InventTestTable, DefaultDashboard, InventTestVariable, InventTestVariableOutcome, InventItemSampling, InventTestQualityGroup, InventTestItemQualityGroupAdd, SysQueryForm, InventTestItemQualityGroup, InventTestGroup, InventTestAssociationTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up quality orders

[!include [banner](../../includes/banner.md)]

This procedure shows you how to enable a quality management process where incoming inventory must be inspected immediately after arrival registration. The procedure will typically be carried out by a quality manager. The process includes the creation of a quality group, to define the items that are going to be sampled, and a test group to group the tests that are to be performed on items in the quality group. You can run this guide in the USMF demo data company.


## Enable quality management
1. Go to **Navigation pane > Modules > Inventory management > Setup > Inventory and warehouse management parameters**.
2. Click the **Quality management** tab.
3. Set the **Use quality management option** to 'Yes'.
4. Click **Report setup**. In USMF, the report setup for quality management is already defined. If this wasn't done, you'd add new lines here for the different report types, and select the type of document to be used for each report.  
5. Close the page.
6. Close the page.

## Create a test
1. Go to **Inventory management > Setup > Quality control > Tests**.
2. Click **New**.
3. In the **Test** field, type a value.
4. In the **Description** field, type a value.
5. In the **Type** field, select 'Option'. In this example, we'll select "Option" which will make it possible to assign the test results based on pre-defined values.  
6. Click **Save**.
7. Close the page.

## Create Test variables to define the way test results are recorded
1. Go to **Inventory management > Setup > Quality control > Test variables**.
2. Click **New**.
3. In the **Variable** field, type a value.
4. In the **Description** field, type a value.
5. Click **Save**.
6. Click **Outcomes**.
7. Click **New**.
8. In the **Outcome** field, type a value.
9. In the **Description** field, type a value.
10. In the **Outcome status** field, select 'Pass'.
11. Click **Save**.
12. Click **New**.
13. In the **Outcome** field, type a value.
14. In the **Description** field, type a value.
15. Click **Save**.
16. Close the page.
17. Close the page.

## Set up item sampling
1. Go to **Inventory management > Setup > Quality control > Item sampling**.
2. Click **New**.
3. In the **Item sampling** field, type a value.
4. In the **Description** field, type a value.
5. In the **Value** field, enter a number. This value relates to the Quantity specification that's selected in the adjacent field.  
6. Expand or collapse the **Process** section.
7. Select or clear the **Full blocking** check box. If you select this option, the whole lot or order line quantity is blocked if a test is failed. If you don't select it, only the items in the quality order are blocked.  
8. Click **Save**.
9. Close the page.

## Create a quality group
1. Go to **Inventory management > Setup > Quality control > Quality groups**.
2. Click **New**.
3. In the **Quality group** field, type a value. Use a descriptive name to help you identify which kind of items the group will contain (your sampling criteria).  
4. In the **Description** field, type a value.
5. Click **Save**.
6. Click **Add items**.
7. Select the **Item number** row. In this example the filtering will be run based on  the item number.  
8. In the **Criteria** field, type a value. For example, type T* to filter on the item numbers that start with T.  
9. Click **OK**.
10. Click **OK**.
11. Click **Item quality groups**.
12. Close the page.
13. Close the page.

## Create a test group
1. Go to **Inventory management > Setup > Quality control > Test groups**.
2. Click **New**.
3. In the **Test group** field, type a value. Give the **Test group** a name that will help you remember what kind of tests are being run, and which quality group it should be associated with. For example, it it's to be used with a quality group that selects items starting with "T", you could call it "T-item tests".  
4. In the **Description** field, type a value.
5. In the **Item sampling** field, select the item sampling line that you created before.
6. In the list, find and select the desired record.
7. Click **Add**.
8. In the **Sequence number** field, enter a number.
9. In the **Test** field, select the test that you created earlier.
10. In the list, find and select the desired record.
11. Click the **Test** tab.
12. In the **Variable** field, select the test variable that you created before
13. In the list, find and select the desired record.
14. In the **Default outcome** field, click the drop-down button to open the lookup.
15. In the list, click the link in the selected row.
16. Click **Save**.
17. Close the page.

## Define when quality orders will be created
1. Go to **Inventory management > Setup > Quality control > Quality associations**.
2. Click **New**.
3. In the **Reference type** field, select an option.
4. In the **Item code** field, select 'Group'. In this example, we'll select "Group" and use the quality group we created before. You could also set this to "Table" to specify the items manually, or select "All" to add all items to the quality order.  
5. In the **Item** field, select the quality group that you created before. The options available in the Item field depend on what you set in the Item code field.  
6. In the list, find and select the desired record.
7. Expand or collapse the Process section.
8. In the **Event type** field, select an option. This is the event that triggers the test. The options available here depend on which process you selected in the Reference type field.  
9. In the **Execution** field, select an option.
10. Expand or collapse the **Quality order process** section.
11. In the **Event blocking** field, click the drop-down button to open the lookup. This field shows the list of processes that it's possible to block if the quality order is still open. The options depend on what you selected in the Event type field.  
12. In the list, click the link in the selected row. This will be depending on the previous selected values. Select if the following processes must be blocked while having open quality orders linked to a source document line.  
13. Expand or collapse the **Specifications** section.
14. In the **Test group** field, select the test group that you created before.
15. In the list, find and select the desired record.
16. Click **Save**.
17. Close the page.

