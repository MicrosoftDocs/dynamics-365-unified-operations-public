---
title: Display vacation balance in the production floor execution interface
description: This topic provides an example scenario that shows how to set up Supply Chain Management to use payroll statistics to provide workers an overview of their vacation balance for the current year.
author: johanhoffmann
ms.date: 04/22/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-04-22
ms.dyn365.ops.version: 10.0.XX
---

# Display vacation balance in the production floor execution interface

[!include [banner](../includes/banner.md)]

This topic provides an example scenario that shows how to set up Supply Chain Management to use payroll statistics to provide workers an overview of their vacation balance for the current year. Workers will be able to see their vacation balance on the **My day** page of the production floor execution interface.

This scenario uses the Danish holiday law as an example, where the vacation year goes from September 1 to August 31. In this scenario, your company has hired a new worker and will grant that worker a balance of 10 vacation days for the rest of the current vacation year.

## Turn on the required features

To run this scenario, the *"My day" view for the production floor execution interface* feature must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). For instructions on how to enable this and other features for the production floor execution interface, see [Configure the production floor execution interface](production-floor-execution-configure.md).

## Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard \[demo data\](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

## Create a new pay type

Start by creating a new *pay type*, which will keep track of workers earned vacation days (also called their *vacation balance*). Normally, pay types are used to calculate workers' pay, but the one created here will be used to calculate a balance.

1.  Go to **Time and attendance &gt; Setup &gt; Payroll &gt; Pay types.**

2.  On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Pay type****:** *5151-1*

    - **Description:** *Counter for workers vacation days*

    - **Include in export:** *No*

## Update the pay agreement

In this section, you will edit an existing pay agreement by adding a new pay type, which will be used to set the rules for how each worker's vacation balance is adjusted when vacation days are registered.

1.  Go to **Time and attendance &gt; Setup &gt; Payroll &gt; Pay agreements.**

2.  Select the pay agreement where you want to set up the vacation policy (if you are working with standard USMF sample data, there is just one, *Man*.).

3.  On the Action Pane, select **Agreement lines** on the Action Pane.

4.  The **Pay agreement lines** page opens. On the **Overview** FastTab toolbar, make the following settings:

    -   From the first drop-down list, select **Monday**.

    -   From the second drop-down list, select **Absence**.

5.  On the Action Pane, select **New** to add a new row to the grid. For the new row, set **Pay type** to the pay type you created for this scenario (*5151-1*). Leave all other fields at their default settings.

6.  With the new row still selected, expand the **General** FastTab and make the following settings:

    - **Absence code:** *Vacation*

    - **Use fixed quantity:** *Yes*

    - **Constant:** *-1*

7.  On the Action Pane, select **Copy day**.

8.  The Copy day dialog opens. Make the following settings:

    - **Tuesday**, **Wednesday**, **Thursday,** and **Friday**: *Yes*

    - **Overwrite**: *Yes*

    - **Absence**: *Yes*

9.  Select **OK.**

## Create a payroll statistic group

Payroll statistic groups are used to set up statistics for worker registrations during a period. In this scenario, you will use a payroll statistic group to calculate the number of vacation days earned during a vacation period. In Denmark, the vacation period is one year that runs from September 1 to August 31 the next year.

1.  Go to **Time and attendance &gt; Setup &gt; Payroll &gt; Payroll statistics groups.**

2.  On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Payroll statistics group:** *VAC*

    - **Description:** *Vacation balance*

    - **Transfer***: No*

3.  With the new row still selected, select **Setup** in the Action Pane.

4.  The **Setup** page opens. On the Action Pane, select **New** to add a new row to the grid.

5.  For the new row, set **Pay type** to 5151-1.

6.  Right-click in the **Period code** field and select **View details.** This will let you set up the period code that you will later assign for this field.

7.  The **Period types** page opens. On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Period types:** *VacYear*

    - **Description:** *Vacation year*

    - **Frequency:** *Years*

8.  With the new row still selected, select **Generate periods** from the Action Pane.

9.  The **Generate periods** dialog opens. Make the following settings:

    - **Specify start date of the period:** *September 1, 2021*

    - **Length of period:** *5*

10. Select **OK.**

11. Return to the **Payroll statistics groups page** by closing the **Period types** page.

12. Set **Period code** to the period type you just created (*VacYear*).

## Create a statistical balance setup

In this section, you will create a statistical balance setup that links to the payroll statistics group you created in the previous section. Later, you will link this statistics balance setup to the **My day** view in the production floor execution interface, which will then be able to show the vacation balances for the pay type assigned to the associated payroll statistics group.

1.  Go to **Time and attendance &gt; Setup &gt; Payroll &gt; Statistical balance setup.**

2.  On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Payroll statistics group:** *VAC*

    - **External name:** *Vacation balance*

    - **Flex:** *No*

## Create a manual premium

Manual premiums are normally used to grant workers extra pay for extra work. In this case, you will create a manual premium that you can use to set the initial vacation balance for each worker.

1.  Go to **Time and attendance &gt; Setup &gt; Payroll &gt; Manual premiums.**

2.  On the Action Pane, select **New** to add a new record. Then make the following settings for it:

    - **Premiums:** *VAC*

    - **Description:** *Adjustments to workers vacation balance.*

    - **Pay type***: 5151-1*

## Set a worker's initial vacation balance and adjust it by one day

Payroll administrators use the **Approve** page to approve and review workers daily registrations. In this scenario, you will take on the role of an admin so you can set the initial vacation balance for a worker and register vacation days taken by that worker.

1.  Go to **Time and attendance &gt; Review and approve &gt; Approve**.

2.  The **Approve** dialog opens. Make the following settings:

    - **Approval group** – Select the approval group you belong to. (If you are working with standard USMF sample data, there is just one, *AdmMan*.)

    - **View entire group, 1 day** – Select this radio button and set it to today's date.

3.  Select **OK.**

4.  The **Approve** page opens, listing records that match your criteria. Select a worker with absence time that you want to approve. (If you are working with standard USMF sample data, you should be able to select worker *000496*, *Christina Portra*.)

5.  In the lower section of the page, open the **Overview** tab. Then select **New** from the toolbar to add a new row and make the following settings for it:

    - **Journal registration type:** *Absence*

    - **Reference:** *Vacation*

6.  Select **Premium lines** in the Action pane.

7.  On the Action Pane, select **New** to add a row to the grid. Then make the following settings for it:

    - **Premiums:** *VAC*

    - **Quantity:** *10*

8.  Close the **Premium lines** page.

9.  Back on the **Approve** page, select **Transfer** from the toolbar in the upper section.

## Configure the production floor execution interface to include the My day page

In this section, you will enable the **My day** page for the production floor execution interface. This will add a **My day** button to the interface, which workers will be able to use to open the page.

1.  Go to **Production control &gt; Setup &gt; Manufacturing execution &gt; Configure production floor execution.**

2.  Select a configuration such as **Default.**

3.  On the Action Pane, select **Design tabs**.

4.  The **Design tabs** page opens. Set **Main view** to *All jobs*.

5.  On the **Secondary tool bar** FastTab, select **My day** in **Available actions** column and then select the right-arrow to move it into the **Selected actions** column.

## Check your balance in the production floor execution interface

In this section, you will sign in to the production floor execution interface as the worker whose vacation time you set up previously and open the **My day** page to check your vacation balance.

1.  Go to **Production control &gt; Setup &gt; Manufacturing execution &gt; Production floor execution.**

2.  Sign in with 123 (Christina Portra).

3.  Select the **My day** button in the left toolbar.

4.  Inspect the **Balances** section of page, which should now show that you have a balance of 9 vacation days.
