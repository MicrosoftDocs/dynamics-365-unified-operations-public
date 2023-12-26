---
title: Show vacation balances in the production floor execution interface
description: This article provides an example scenario that shows how to set up Microsoft Dynamics 365 Supply Chain Management so that it uses payroll statistics to provide workers an overview of their vacation balance for the current year.
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

# Show vacation balances in the production floor execution interface

[!include [banner](../includes/banner.md)]

This article provides an example scenario that shows how to set up Microsoft Dynamics 365 Supply Chain Management so that it uses payroll statistics to provide each worker with an overview of their vacation balance for the current year. Workers will be able to see their vacation balance in the **My day** dialog box in the production floor execution interface.

This scenario uses the Danish holiday law, where the vacation year goes from September 1 through August 31. In this scenario, your company has hired a new worker and will grant that worker a balance of 10 vacation days for the rest of the current vacation year.

## Turn on the required features

To run this scenario, the *"My day" view for the production floor execution interface* feature must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). For information about how to enable this and other features for the production floor execution interface, see [Configure the production floor execution interface](production-floor-execution-configure.md).

## Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

## Create a new pay type

Start by creating a new *pay type* that will track workers' earned vacation days (also referred to as their *vacation balance*). Typically, pay types are used to calculate workers' pay. However, the pay type that you create here will be used to calculate a balance.

1. Go to **Time and attendance \> Setup \> Payroll \> Pay types**.
1. On the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the following values:

    - **Pay type:** *5151-1*
    - **Description:** *Counter for worker vacation days*
    - **Include in export:** *No*

## Update the pay agreement

In this section, you will edit an existing *pay agreement* by adding the new pay type and setting the rules that define how each worker's vacation balance is adjusted when vacation days are registered.

1. Go to **Time and attendance \> Setup \> Payroll \> Pay agreements**.
1. Select the pay agreement where you want to set up the vacation policy. (If you're working with standard USMF sample data, there is only one pay agreement, *Man*.)
1. Make sure that the selected pay agreement is valid for the current date. If you're working with standard USMF sample data, the **To date** field of the *Man* pay agreement might be set to a date that is in the past. Change the value so that it's a year or two in the future, as required.
1. On the Action Pane, select **Agreement lines**.
1. On the **Pay agreement lines** page, on the **Overview** FastTab, set the following values on the toolbar:

    - In the first drop-down list, select **Monday**.
    - In the second drop-down list, select **Absence**.

1. On the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the **Pay type** field to the pay type that you created for this scenario (*5151-1*). Leave all other fields set to their default values.
1. While the new row is still selected, on the **General** FastTab, set the following values:

    - **Absence code:** *Vacation*
    - **Use fixed quantity:** *Yes*
    - **Constant:** *-1*

1. On the Action Pane, select **Copy day**.
1. In the **Copy day** dialog box, set the following values:

    - **Tuesday**, **Wednesday**, **Thursday**, and **Friday:** *Yes*
    - **Overwrite:** *Yes*
    - **Absence:** *Yes*

1. Select **OK**.

## Create a payroll statistic group

*Payroll statistic groups* are used to set up statistics for worker registrations during a period. In this scenario, you will use a payroll statistic group to calculate the number of vacation days that workers earn during a vacation period. In Denmark, the vacation period runs from September 1 through August 31.

1. Go to **Time and attendance \> Setup \> Payroll \> Payroll statistics groups**.
1. On the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the following values:

    - **Payroll statistics group:** *VAC*
    - **Description:** *Vacation balance*
    - **Transfer:** *No*

1. While the new row is still selected, select **Setup** on the Action Pane.
1. On the **Setup** page, on the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the **Pay type** field to *5151-1*.
1. Select and hold (or right-click) the **Period code** field, and then select **View details**. You can now set up the period code that you will assign to this field later.
1. On the **Period types** page, on the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the following values:

    - **Period types:** *VacYear*
    - **Description:** *Vacation year*
    - **Frequency:** *Years*

1. While the new row is still selected, select **Generate periods** on the Action Pane.
1. In the **Generate periods** dialog box, set the following values:

    - **Specify start date of the period:** *September 1, 2021*
    - **Length of period:** *5*

1. Select **OK**.
1. Close the **Period types** page to return to the **Payroll statistics groups** page.
1. Set the **Period code** field to the period type that you just created (*VacYear*).

## Create a statistical balance setup

In this section, you will create a *statistical balance setup* that is linked to the payroll statistic group that you created in the previous section. Later, you will link this statistical balance setup to the **My day** view in the production floor execution interface. The **My day** view will then be able to show the vacation balances for the pay type that is assigned to the associated payroll statistic group.

1. Go to **Time and attendance \> Setup \> Payroll \> Statistical balance setup**.
1. On the Action Pane, select **New** to add a row to the grid.
1. On the new row, set the following values:

    - **Payroll statistics group:** *VAC*
    - **External name:** *Vacation balance*
    - **Flex:** *No*

## Create a manual premium

*Manual premiums* are typically used to grant workers extra pay for extra work. In this scenario, you will create a manual premium that you can use to set the initial vacation balance for each worker.

1. Go to **Time and attendance \> Setup \> Payroll \> Manual premiums**.
1. On the Action Pane, select **New** to add a record.
1. In the new record, set the following values:

    - **Premiums:** *VAC*
    - **Description:** *Adjustments to workers' vacation balance*
    - **Pay type:** *5151-1*

## Set a worker's initial vacation balance and adjust it by one day

Payroll administrators use the **Approve** page to review and approve workers' daily registrations. In this scenario, you will take on the role of an admin so that you can set the initial vacation balance for a worker and register vacation days that the worker takes.

1. Go to **Time and attendance \> Review and approve \> Approve**.
1. In the **Approve** dialog box, set the following fields:

    - **Approval group** – Select the approval group that you belong to. (If you're working with standard USMF sample data, there is only one approval group, *AdmMan*.)
    - **View entire group, 1 day** – Select the option, and then set the field to the current date.

1. Select **OK**.
1. The **Approve** page shows a list of records that match your criteria. Select the worker that you want to approve. If you're working with standard USMF sample data, select worker *000496* (*Christina Portra*).
1. Grant the selected worker 10 days of vacation:

    1. While the worker is still selected, select **Premium lines** on the Action Pane.
    1. On the **Premium lines** page, on the Action Pane, select **New** to add a row to the grid.
    1. On the new row, set the following values:

        - **Premiums:** *VAC*
        - **Quantity:** *10*

    1. Close the **Premium lines** page.

1. On the **Approve** page, register the fact that the worker used one of their vacation days on the current date:

    1. While the worker is still selected, in the lower part of the page, on the **Overview** tab, select **New** on the toolbar to add a row to the grid.
    1. On the new row, set the following values:

        - **Journal registration type:** *Absence*
        - **Reference:** *Vacation*

    1. In the upper part of the page, select **Transfer** on the toolbar to apply the vacation balance and calculate the deduction.

## Configure the production floor execution interface so that it includes the My day dialog box

In this section, you will add a **My day** button to the production floor execution interface. Workers can then use this button to open the **My day** dialog box.

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. Select a configuration, such as *Default*.
1. On the Action Pane, select **Design tabs**.
1. On the **Design tabs** page, in the list pane, select *All jobs* to view the settings for that tab. The **Main view** field should now show a value of *All jobs*.
1. On the Action Pane, select **Edit**.
1. On the **Secondary tool bar** FastTab, in the **Available actions** column, select **My day**. Then select the right arrow button to move it to the **Selected actions** column.

## Check your balance in the production floor execution interface

In this section, you will sign in to the production floor execution interface as the worker whose vacation time you set up earlier. You will then open the **My day** dialog box to view your vacation balance.

1. Go to **Production control \> Setup \> Manufacturing execution \> Production floor execution**.
1. If you're prompted to select a configuration, select the configuration that you set up earlier in this scenario (*Default*).
1. Sign in as the user that you set up earlier in this scenario. If you're working with standard USMF sample data, you should be able to sign in by entering *123* in the **Badge ID** field. This badge ID corresponds to Christina Portra.
1. Select **My day** on the left toolbar.
1. Inspect the **Balances** section of the dialog box. This section should now show that you have a balance of nine vacation days.
