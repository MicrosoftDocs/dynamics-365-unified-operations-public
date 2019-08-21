---
# required metadata

title: Cost and date control
description: This topic explains cost and date control in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cost and date control

In Asset Management, you can calculate costs to get an overview of actual costs compared to budget costs on assets, functional locations, and work orders. Actual costs are based on posted transactions. You can also make a date calculation if you want to compare scheduled start and end dates to actual start and end dates on work orders.

## Cost control for assets, functional locations, and work orders

The calculations made for assets, functional locations, and work orders are almost identical. Only difference is that for assets and functional locations, you can also include sub assets and sub locations in your calculation. The date is the transaction date when the registration was recorded.

1. Click **Asset management** > **Inquiries** > **Assets** > **Asset cost control** or **Functional location cost control**, or **Asset management** > **Inquiries** > **Work orders** > **Work order cost control**.

2. In the **Asset cost control** / **Functional location cost control** / **Work order cost control** dialog, select a period to be calculated.

3. If required, select a financial dimension set to be included in the calculation.

4. Select "Yes" on the **Skip zero** toggle button if you don't want to show results with a cost of zero.

5. You can use the **Level** field to indicate how detailed you want the cost control lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location hierarchy, all cost control lines for a functional location will be shown on the top level, and therefore the hours on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you will see a detailed result showing all cost control lines on all the functional location level to which they are related.

6. Select "Yes" on the **Show open committed cost** toggle button if you want to include that column in the calculation.

7. Select "Yes" on the **Include sub assets** toggle button to show costs related to sub assets as separate lines.

8. If you want to limit the search, you can select specific assets / functional locations / work orders on the **Records to include** FastTab.

9. Click **OK** to start the calculation.

The figure below shows an example of the **asset cost control** dialog.

![Figure 1](media/01-controlling-and-reporting.png)

10. In the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane group buttons are highlighted. Click on a button to activate or deactivate it.

The figure below shows an example of calculation results in **Asset cost control**.

![Figure 2](media/02-controlling-and-reporting.png)

Another way of making a cost calculation is to multi-select assets in **All assets** or **Active assets**. Then, you click the **Cost control** button on the **General** tab. In the **Asset cost control** dialog, the selected assets are automatically inserted in the **Asset** field on the **Records to include** FastTab. Click **OK**, and a cost calculation for the selected assets is shown. The same procedure can be done for functional locations in **All functional locations** or **Active functional locations**, and for work orders in the **All work orders** or **Active work orders**.

>[!NOTE]
>The **Original budget** field shows budget costs from the work order forecast. The **Committed cost** field shows the total amount of expenses that a legal entity has committed itself to pay. The **Open committed cost** field shows commitments to pay for items, hours, and services you have ordered or received but not yet paid for. When all consumption registrations have been posted, the related costs are included in the **Actual cost** field.

## Work order date control

Use this form to get an overview of expected start and end dates compared to actual start and end dates on work orders. Select a period for the calculation, then select the information you want to display by selecting the check boxes in the **Group by** section, and click **Calculate**.

1. Click **Enterprise asset management** > **Inquiries** > **Work orders** > **Work order date control**.

2. Click **Edit**.

3. Select a functional location in the **Functional location** field.

4. Insert the period for which you want to make the calculation in the **From date** and **To date** fields. All work orders with expected start within the period will be included.

5. In the **Group by** section, select which information you want to include in the calculation by selecting the relevant check boxes.

6. Click **Calculate**.

7. After you have made the calculation, if you select or clear check boxes in the **Group by** section, click the **Calculate** button again to update the calculation.

The figure below shows a screenshot of the interface.

![Figure 5](media/05-controlling-and-reporting.png)

- The **Avg. start delay** field shows the difference in days between scheduled start date for a work order compared to actual start date. If, for example, the actual start date was two days before the scheduled start date, "-2" will be displayed in this field.  
- The **Avg. end delay** field shows the difference in days between scheduled end date for a work order compared to actual end date. If, for example, the actual end date was three days after the scheduled end date, "3" will be displayed in this field.  
- The **Occurrences** fields show the number of times deviations occur in relation to scheduled and actual start date, and scheduled and actual end date on the work order.
