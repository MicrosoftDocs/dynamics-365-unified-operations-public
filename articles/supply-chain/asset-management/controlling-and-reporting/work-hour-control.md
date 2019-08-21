---
# required metadata

title: Work hour control
description: This topic explains work hour control in Asset Management.
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

# Work hour control

In Asset Management, you can calculate hours to get an overview of actual hours compared to budget hours on assets, functional locations, or work orders. Actual hours are based on posted transactions.

## Work hour control for assets, functional locations, and work orders

The calculations made for assets, functional locations, and work orders are almost identical. Only difference is that for assets and functional locations, you can also include sub assets and sub locations in your calculation. The date is the transaction date when the registration was recorded.

1. Click **Asset management** > **Inquiries** > **Assets** > **Asset hour control** or **Functional location hour control**, or **Asset management** > **Inquiries** > **Work orders** > **Work order hour control**.

2. Click **Hour control** > **Calculate hours**.

3. In the **Object hour control** form / **Functional location hour control** form / **Work order hour control** drop-down, select a period to be calculated.

4. If you want to limit the search, you can select specific objects / functional locations / work orders.

5. If required, select a financial dimension set to be included in the calculation.

6. Select the **Skip zero** check box if you do not want to show results containing zero hours.

7. You can use the **Level** field to indicate how detailed you want the hour control lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location hierarchy, all hour control lines for a functional location will be shown on the top level, and therefore the hours on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you will see a detailed result showing all hour control lines on all the functional location levels to which they are related.

8. Click **OK** to start the calculation.

9. In the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane group buttons are highlighted. Click on a button to activate or deactivate it.

The figures below show screenshots of the interface.

![Figure 1](media/06-controlling-and-reporting.png)

![Figure 2](media/07-controlling-and-reporting.png)

![Figure 3](media/08-controlling-and-reporting.png)

Another way of making a cost calculation is to multi-select objects in **All objects** or **Active objects** grid view. Then, you click the **Hour control** button > **Hour control** > **Calculate hours**, and you will see that the selected objects are automatically inserted in the **Object** field on the **Records to include** FastTab. Click **OK** in the **Object hour control** drop-down, and an hour calculation for the selected objects is shown. The same procedure can be done for functional locations in **All functional locations** or **Active functional locations**, and for work orders in the **All work orders** or **Active work orders**.

>[!NOTE]
>The **Original budget** field shows budget hours from the work order forecast. The **Actual hours** field shows posted hours on work orders. The **Committed hours** field shows total amount of hours that your company is committed to in relation to work orders.
