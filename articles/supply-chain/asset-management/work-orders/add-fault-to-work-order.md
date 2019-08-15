---
# required metadata

title: Add fault to work order
description: This topic describes how to add fault registrations to work orders in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 08/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---


# Add fault to work order

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]


You can add faults set up in the fault designer to a work order. The asset selected in the work order must contain asset types that have one or more fault records connected to it. Read more about setup in the [Fault management](../setup-for-work-orders/fault-management.md) section.

1. Click **Asset management** > **Common** > **Work orders** > **All Work orders** or **Active work orders**.

2. In the list, select the work order on which you want to make a fault registration and click **Asset fault**.

3. On the **Symptoms** FastTab, click **Add line**. A sequential fault number is automatically inserted in the **Fault** field.

4. Select the relevant symptom in the **Fault symptom** field.

5. Select **Fault area** and **Fault type**.

6. In the **Fault date** field, the current date is automatically inserted. You can select another date, if necessary.

7. On the **Causes for selected symptom** FastTab, add a line describing the cause of the problem.

8. On the **Remedies for selected symptom** FastTab, add a line describing a possible solution to the problem.

9. Click **Save**.

![Figure 1](media/19-work-orders.png)


## View asset faults

In the **Asset faults** list, you can get an overview of all faults registered on assets.

Click **Asset management** > **Inquiries** > **Asset fault** > **Asset faults** to open the list.


## Print asset fault report

From the **All assets** list page, you can print an asset fault report displaying all fault registrations as well as a graphic overview of fault statistics.

1. Click **Asset management** > **Common** > **Assets** > **All assets**.

2. In the **Assets** list, select the asset for which you want to print a fault report.

3. On the **General** tab > **Reports section**, click **Asset fault**.

4. Insert a specific period, or select a fault type.

5. Click **OK** to print the report.

>[!NOTE]
>You can also print a fault report for several assets or asset types by clicking **Asset management** > **Reports** > **Assets** > **Asset fault**.

