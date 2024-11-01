---
title: Create consumption reports
description: Learn how to create consumption reports in Asset Management, including an outline on asset consumption reports and a step-by-step process.
author: jodahl
ms.author: jodahl
ms.topic: article
ms.date: 08/21/2019
ms.custom:
ms.reviewer: kamaybac
ms.search.form: 
---

# Create consumption reports

[!include [banner](../../includes/banner.md)]

 

When you've created and posted consumption registrations on work orders in Asset Management, two reports are available to display consumption details.


## Asset consumption report

When you have posted consumption on work orders, you can print an asset consumption report. The report displays hours, hour costs, item costs, and expenses posted on assets.

1. Click **Asset management** > **Reports** > **Assets** > **Asset consumption**.

2. In the **Asset consumption** dialog, select the parameters and detail level you want to see by selecting **Yes** on the relevant toggle buttons, and inserting a functional location level in the **Show** section.
    - You can use the **Levels** field to indicate how detailed you want the asset lines to be regarding functional locations. 
    
        For example, if you enter the number "1" in the field, and you have a multi-level functional location structure, all assets for a functional location will be shown on the top level, and therefore a line may be added up from functional locations located at a lower level. 
        
        If you enter the number "0" in the **Levels** field, you will see a detailed result showing all assets on all the functional location levels to which they are related. 
        
    - Select **Yes** on the **Sum on all sub assets** toggle button to see sums for each sub asset in the report.

3. Select a date interval in the **Dates** section.

4. On the **Destination** FastTab, select if you want to display the report on screen, print it, or save it as a file or email.

5. If required, you can select specific assets to be displayed in the report. On the **Records to include** FastTab, click **Filter**, and add the assets you want to include in the report.

6. Click **OK** to generate the report.


## Work order consumption report

When you have posted consumption on work orders, you can print a work order consumption report. The report displays hours, hour costs, item costs, and expenses posted on work orders.

1. Click **Asset management** > **Reports** > **Work orders** > **Work order consumption**.

2. In the **Work order consumption** dialog, select the parameters you want to include in the report by selecting **Yes** on the relevant toggle buttons in the **Show** section.

3. Select a date interval in the **Dates** section.

4. On the **Destination** FastTab, select if you want to display the report on screen, print it, or save it as a file or email.

5. If required, you can select specific work orders to be displayed in the report. On the **Records to include** FastTab, click **Filter**, and add the work orders you want to include in the report.

6. Click **OK** to generate the report.


>[!NOTE]
>You can also generate a [work order report](../work-orders/work-order-report.md), which contains more work order details.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]