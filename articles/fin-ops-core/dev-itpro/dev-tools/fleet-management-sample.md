---
title: End-to-end scenario for the Fleet Management sample application
description: Learn about an end-to-end scenario that the Fleet Management sample application is designed to support, including prerequisites and how to install demo data.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e289504e-a1d9-44b7-8f84-f99f330321d6
ms.custom: sfi-image-nochange
---

# End-to-end scenario for the Fleet Management sample application

[!include [banner](../includes/banner.md)]

This tutorial walks you through an end-to-end scenario that the Fleet Management sample application is designed to support.

In this tutorial, you take a tour of the Fleet Management sample. The overviews in this tutorial provide some background knowledge and contextual info. You walk through an end-to-end scenario that this sample application is designed to support. This information helps you before proceeding to other tutorials.

## Prerequisites

- You must be provisioned as an end user before you start this tutorial.
- This tutorial mainly explores the FleetManagement Migrated project and the application that it builds.

## Installing the demo data

To work with the sample, you must install the provided demo data.

1. In the virtual machine (VM), open Microsoft Edge and go to the application's base URL.
1. Sign in.
1. On the dashboard, open the navigation pane and go to **Fleet Management \> Setup\> Fleet setup**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_setup_data.png" alt-text="Screenshot of the Fleet setup page.":::

1. On the **Data setup** tab, select **Create**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_data_setup_create.png" alt-text="Screenshot of the Load Demo Data button on the Data setup tab.":::

1. If you're prompted to reload the demo data, select **Yes**.
1. When the data finishes loading, select **Close**.

## Use the Fleet Management application to rent a vehicle

In this section, you're working with the migrated app. The forms you see are directly ported from the Microsoft Dynamics AX 2012 version of the sample. Although they're modified and restyled, they're not reimagined.

1. Open Microsoft Edge, and sign in to the finance and operations application.
1. To return to the **Dashboard**, select the product name in the upper-left corner of the page.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_logo.png" alt-text="Screenshot of the product name link used to return to the dashboard.":::

    The dashboard is the main working hub. You can see the various tiles, organized into sections, which lead to parts of the application. The dashboard is designed for horizontal scrolling, which is an optimization for working well on modern devices. The button to the right of the dashboard shows the navigation bar.
1. From the Dashboard, open the navigation bar and go to **Fleet Management \> Customers \> Customer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_customers_customer.png" alt-text="Screenshot of the navigation path to the customer list.":::

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_new_customer.png" alt-text="Screenshot of the new customer form.":::

1. To switch to the **Details** view, select a value in the **First Name** column. This view shows detailed information for a single customer.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_details_view.png" alt-text="Screenshot of the customer details view after selecting a first name.":::

1. Select **Show list** to show the navigation list.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_show_list.png" alt-text="Screenshot of the navigation list in the side pane.":::

1. Select the various customer names in the navigation list in the side pane, and watch as the detailed information about each customer changes.
1. Select the customer **Eduardo Cobo**. You see the charts update to indicate Eduardo's previous rental preferences.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_another_customer.png" alt-text="Screenshot of the customer details view showing Eduardo Cobo's rental preferences.":::

1. Hover over the pie slices to see the details. You notice that, in the past, Eduardo often rented red SUVs. This insight might give the sales clerk a cue to look for available red SUVs the next time Eduardo makes a reservation. This insight is a simple example of proactively providing insights.
1. Add yourself as a customer.
    - On the Action Pane, select **New**.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="media/fmt_add_new.png" alt-text="Screenshot of the New button on the Action Pane to add a customer.":::

    - Fill in the form to add yourself as a customer. Make sure that you provide your name, a 16-digit number in the credit card field, and address information, at a minimum. **Note**: You don't have to take any action to save a new record.

1. Create a new rental.
    1. On the navigation bar, go to **Fleet management** \> **Rentals** \> **Rental**.
    1. In the **Rental** form, on the Action Pane, select **New.**
    1. In the **Vehicle** field, select a vehicle.
    1. In the **Customer** field, select your name.
    1. In the **To** field, pick an end date.
    1. In the **Start** field, enter **35,000**.
    1. In the **Pickup** field, enter **Full**.
    1. When you finish, select **Save**.

1. Start the rental period.
    1. On the Action Pane, select **Start rental**.
    1. In the dialog box, verify the values in the fields and select **OK**.

## Use Fleet Management to run a workflow

1. Select the **Home** icon to return to the dashboard.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_home_icon.png" alt-text="Screenshot of the Home icon used to return to the dashboard.":::

1. Find the **Reservation Management** tile and select it to open the Reservation Management workspace.
1. Select **Current rentals**.
1. On the **Rentals** form, select the ID of your rental.
1. On the Details view of the **Rentals** form, on the Action Pane, select **Complete rental**.
1. In the **New mileage** field, enter **40,000**, and then select **OK**.
1. Select the **Home** icon to return to the dashboard.
1. On the navigation bar, go to **Fleet management** &gt; **Vehicles** &gt; **Vehicle Maintenance**. In the **Vehicle Maintenance** form, the **Status** field shows that your rental is awaiting examination by the service department.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_vehicle_examination.png" alt-text="Screenshot of the Vehicle Maintenance form showing a rental awaiting examination.":::

    > [!NOTE]
    > You might need to wait up to two minutes for the batch framework to change the status of the vehicle. On the Action Pane, select **Refresh** periodically to update the view, until you see the status change. Keep in mind that a different person usually handles each step in a workflow. The brief delay introduced by the batch framework isn't an issue in a real-world application.

1. Select the row that contains your rental. On the Action Pane, select **Workflow**, and then select **Examination complete**. You might need to refresh the page to get the full set of options under **Workflow**.
1. Enter a comment, and then select **Examination complete**.
1. You might again need to wait up to two minutes for the batch framework to process the change. On the Action Pane, select **Refresh** periodically, until you see the **Status** field change. Notice that the vehicle now has a status of **Awaiting Service**.
1. Optionally, you can continue to repeat these workflow steps to take the vehicle through the service and cleaning phases. After cleaning is completed, the final status is **Done**.
1. Select **Workflow**, and then select **View history**. The **Workflow history** form provides information about the vehicle workflow.
1. Select **Tracking details** to see the activities.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_workflow_history.png" alt-text="Screenshot of the Workflow history form showing tracking details.":::

### To view the setup behind the workflow

1. On the dashboard, go to **Fleet Management** > **Setup** > **Workflow setup**. The **Workflow Setup** page shows the list of workflows.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_workflow_setup.png" alt-text="Screenshot of the Workflow Setup page showing the list of workflows.":::

1. In the **Workflow ID** column, select the ID for your vehicle maintenance workflow.
1. Accept any prompts that ask you for permission to run code. After a short wait, the workflow editor opens. This step works on the one-box environment, but not in the cloud. You can view the workflow diagram in the workflow editor. The following illustration shows the workflow.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_workflow_editor.png" alt-text="Screenshot of the workflow editor showing the workflow diagram.":::

1. When you're done, close the **Workflow** window.

## Create a new KPI definition

The web client enables users with the right permissions to modify KPI definitions that developers model and deploy. Users can also create new KPI definitions in the client. In this walkthrough, you create a new KPI definition in the client.

1. Open the **Reservation Management** workspace. On the navigation bar, go to **Fleet Management &gt; Workspaces &gt; Reservation Management**.
1. Notice the Total revenue KPI tile shown on the bottom left of the workspace. Select the **Total Revenue KPI** tile. The details of the total revenue KPI tile appear, along with charts that show the top and bottom contributors to revenue.
1. Next, you define a new KPI to monitor the number of rentals.
1. On the Action Pane, select **New**. The **New KPI** dialog opens.
1. Enter the following values for the new KPI definition.

    | Field         | Value               |
    |---------------|-------------------------|
    | Name          | Number of Rentals       |
    | Measurement   | FMAggregateMeasurements |
    | Measure group | FmRentalCharges         |
    | Measure       | NoRentals               |
    | KPI Goal Type | Fixed Value             |
    | Goal value    | 30                      |

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_new_kpi.png" alt-text="Screenshot of the New KPI dialog with fields filled in.":::

1. Select **Save**.

    > [!NOTE]
    > If you don't see the **Save** button in the **New KPI** dialog box, use a higher screen resolution so that you can see the entire dialog. You see the KPI details page that contains details about the KPI that you created. You can make changes in the **Details** section. You modify the default threshold values so that if the value is less than 90% of the goal, the KPI shows red and if the value is over 110% of the goal, the KPI shows green.

1. Select **Edit**.

1. Scroll to the right of the screen, and modify the values in the thresholds fields as follows.

    | Property           | Value     |
    |--------------------|-----------|
    | Bad if less than   | 90        |
    | Good if more than  | 110       |

1. In the application bar, select **Save**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_kpi_value.png" alt-text="Screenshot of the KPI graph showing the KPI value.":::

1. Select the form caption to return to the grid view.
1. Select the **Name** column header, change the filter operator to **contains**, and update the filter field value to **Number**. You see the new KPI in the list.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_kpi_list.png" alt-text="Screenshot of the KPI list with the new KPI available.":::

## Launch an operational report

In this tutorial, you launch an operational report that contains a list of customers who are currently renting vehicles.

1. Use the dashboard to open the **Reservation management** workspace.
1. On the right side of the page, under **Reports**, select **Customer list**. Don't enter anything in the parameter for **Customer group**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_customer_list_report.png" alt-text="Screenshot of the Customer list report.":::

1. Select **OK** to close the dialog box. The report renders and shows the list of customers. The report might take a minute to render.

## Secure access by using the role-based security system

In this tutorial, you access the system as a user assigned a different security role. This tutorial requires that you create at least one additional end user.

1. On the dashboard, in the **System administration** section, select **Users** and then **Users**.
1. On the Action Pane, select **New**.
1. Enter the following field information.

    | Property        | Value                                                                                 |
    |-----------------|-------------------------------------------------------------------------------------------|
    | User ID         | Eight character unique ID                                                                 |
    | User name       | The first name of the user                                                                |
    | Provider        | `urn:Federation:MicrosoftOnline`                                                          |
    | Email           | Use an email alias that you can sign in with for testing.                                   |
    | Company         | `DAT`                                                                                     |
    | Enabled         | Verify that this slider is set to **Yes**.                                                |

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_new_user_record.png" alt-text="Screenshot of the new user record form with fields filled in.":::

1. Select **Assign Roles**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/fmt_branch_manager.png" alt-text="Screenshot of the Assign Roles dialog for assigning the branch manager role.":::

1. Select **Fleet management branch manager**, and then select **OK**.
1. Select the user name on the top right, and then select **Sign Out**. You're redirected back to the sign-in page.
1. Sign in by using the credentials for the user who you assigned the security role to in the preceding steps.
1. Notice that in the dashboard, this user can see only items that are related to the branch manager security role. Items that system administrators can see are now hidden.
1. Select **Sign out** to sign out of the session.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
