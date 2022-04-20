---
title: Display vacation balances in the production floor execution interface
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

# Display vacation balances in the production floor execution interface

[!include [banner](../includes/banner.md)]

This topic provides an example scenario that shows how to set up payroll statistics to provide each worker with an overview of their vacation balance for the current year. Workers will be able to see their vacation balance on the **My day** dialog of the production floor execution interface.

This scenario uses the Danish holiday law as an example, where the vacation year goes from September 1 to August 31. In this scenario, your company has hired a new worker and will grant that worker a balance of 10 vacation days for the rest of the current vacation year.

## Turn on the required features

To run this scenario, the *"My day" view for the production floor execution interface* feature must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). For instructions on how to enable this and other features for the production floor execution interface, see [Configure the production floor execution interface](production-floor-execution-configure.md).

## Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

## Create a new pay type

Start by creating a new *pay type*, which will keep track of workers earned vacation days (also called their *vacation balance*). Normally, pay types are used to calculate workers' pay, but the one created here will be used to calculate a balance.

1. Go to **Time and attendance \> Setup \> Payroll \> Pay types**.
1. On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Pay type:** *5151-1*
    - **Description:** *Counter for worker vacation days*
    - **Include in export:** *No*

## Update the pay agreement

In this section, you will edit an existing *pay agreement* by adding the new pay type and setting the rules for how each worker's vacation balance is adjusted when vacation days are registered.

1. Go to **Time and attendance \> Setup \> Payroll \> Pay agreements**.
1. Select the pay agreement where you want to set up the vacation policy (if you are working with standard USMF sample data, there is just one, *Man*.).
1. On the Action Pane, select **Agreement lines** on the Action Pane.
1. The **Pay agreement lines** page opens. On the **Overview** FastTab toolbar, make the following settings:

    - From the first drop-down list, select **Monday**.
    - From the second drop-down list, select **Absence**.

1. On the Action Pane, select **New** to add a new row to the grid. For the new row, set **Pay type** to the pay type you created for this scenario (*5151-1*). Leave all other fields at their default settings.

1. With the new row still selected, expand the **General** FastTab and make the following settings:
    - **Absence code:** *Vacation*
    - **Use fixed quantity:** *Yes*
    - **Constant:** *-1*

1. On the Action Pane, select **Copy day**.
1. The **Copy day** dialog opens. Make the following settings:
    - **Tuesday**, **Wednesday**, **Thursday,** and **Friday:** *Yes*
    - **Overwrite:** *Yes*
    - **Absence:** *Yes*

1. Select **OK**.

## Create a payroll statistic group

*Payroll statistic groups* are used to set up statistics for worker registrations during a period. In this scenario, you will use a payroll statistic group to calculate the number of vacation days earned during a vacation period. In Denmark, the vacation period runs from September 1 to August 31 the next year.

1. Go to **Time and attendance \> Setup \> Payroll \> Payroll statistics groups**.
1. On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:
    - **Payroll statistics group:** *VAC*
    - **Description:** *Vacation balance*
    - **Transfer:** *No*

1. With the new row still selected, select **Setup** in the Action Pane.
1. The **Setup** page opens. On the Action Pane, select **New** to add a new row to the grid.
1. For the new row, set **Pay type** to *5151-1*.
1. Right-click in the **Period code** field and select **View details**. This will let you set up the period code that you will later assign to this field.
1. The **Period types** page opens. On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:
    - **Period types:** *VacYear*
    - **Description:** *Vacation year*
    - **Frequency:** *Years*

1. With the new row still selected, select **Generate periods** from the Action Pane.
1. The **Generate periods** dialog opens. Make the following settings:
    - **Specify start date of the period:** *September 1, 2021*
    - **Length of period:** *5*

1. Select **OK**.
1. Return to the **Payroll statistics groups page** by closing the **Period types** page.
1. Set **Period code** to the period type you just created (*VacYear*).

## Create a statistical balance setup

In this section, you will create a *statistical balance setup* that links to the payroll statistics group you created in the previous section. Later, you will link this statistics balance setup to the **My day** view in the production floor execution interface, which will then be able to show the vacation balances for the pay type assigned to the associated payroll statistics group.

1. Go to **Time and attendance \> Setup \> Payroll \> Statistical balance setup**.

1. On the Action Pane, select **New** to add a new row to the grid. Then make the following settings for the new row:

    - **Payroll statistics group:** *VAC*
    - **External name:** *Vacation balance*
    - **Flex:** *No*

## Create a manual premium

*Manual premiums* are normally used to grant workers extra pay for extra work. In this case, you will create a manual premium that you can use to set the initial vacation balance for each worker.

1. Go to **Time and attendance \> Setup \> Payroll \> Manual premiums**.
1. On the Action Pane, select **New** to add a new record. Then make the following settings for it:
    - **Premiums:** *VAC*
    - **Description:** *Adjustments to workers' vacation balance*.
    - **Pay type:** *5151-1*

## Set a worker's initial vacation balance and adjust it by one day

Payroll administrators use the **Approve** page to approve and review workers daily registrations. In this scenario, you will take on the role of an admin so you can set the initial vacation balance for a worker and register vacation days taken by that worker.

1. Go to **Time and attendance \> Review and approve \> Approve**.
1. The **Approve** dialog opens. Make the following settings:
    - **Approval group** – Select the approval group you belong to. (If you are working with standard USMF sample data, there is just one, *AdmMan*.)
    - **View entire group, 1 day** – Select this radio button and set it to today's date.

1. Select **OK**.
1. The **Approve** page opens, listing records that match your criteria. Select a worker that you want to approve. (If you are working with standard USMF sample data, select worker *000496*, *Christina Portra*.)
1. In the lower section of the page, open the **Overview** tab. Then select **New** from the toolbar to add a new row and make the following settings for it:
    - **Journal registration type:** *Absence*
    - **Reference:** *Vacation*

1. Select **Premium lines** in the Action pane.
1. On the Action Pane, select **New** to add a row to the grid. Then make the following settings for it:
    - **Premiums:** *VAC*
    - **Quantity:** *10*

1. Close the **Premium lines** page.
1. Back on the **Approve** page, select **Transfer** from the toolbar in the upper section.

## Configure the production floor execution interface to include the My day dialog

In this section, you will add a **My day** button to the interface, which workers can use to open the **My day** dialog.

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. Select a configuration such as **Default**.
1. On the Action Pane, select **Design tabs**.
1. The **Design tabs** page opens. Select *All jobs* from the list pane to view the settings for that tab. (**Main view** should now show a value of *All jobs*.)
1. On the Action Pane, select **Edit**.
1. On the **Secondary tool bar** FastTab, select **My day** in **Available actions** column and then select the right-arrow to move it into the **Selected actions** column.

## Check your balance in the production floor execution interface

In this section, you will sign in to the production floor execution interface as the worker whose vacation time you set up previously and open the **My day** dialog to check your vacation balance.

1. Go to **Production control \> Setup \> Manufacturing execution \> Production floor execution**.
1. If you are asked to select a configuration, select the configuration you set up previously in this scenario (*Default*).
1. Sign in as the user you set up previously in this scenario. (If you are using demo data, then you should be able to sign in with **Badge ID** *123* which is Christina Portra.)
1. Select the **My day** button in the left toolbar.
1. Inspect the **Balances** section of dialog, which should now show that you have a balance of 9 vacation days.
