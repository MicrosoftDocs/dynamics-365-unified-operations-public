---
title: End-to-end scenario for the Fleet Management sample application
description: This tutorial walks you through an end-to-end scenario that the Fleet Management sample application is designed to support.
author: gianugo
ms.date: 07/08/2019
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e289504e-a1d9-44b7-8f84-f99f330321d6
---

# End-to-end scenario for the Fleet Management sample application

[!include [banner](../includes/banner.md)]

This tutorial walks you through an end-to-end scenario that the Fleet Management sample application is designed to support.

In this tutorial, you’ll take a tour of the Fleet Management sample. The overviews in this tutorial provide some background knowledge and contextual info. You’ll walk through an end-to-end scenario that this sample application is designed to support. This is information that you should have before proceeding to other tutorials.

## Prerequisite

-   You must first be provisioned as an end user before you start this tutorial.
-   This tutorial mainly explores the FleetManagement Migrated project and the application that it builds.

## Installing the demo data
To work with the sample, you must install the provided demo data.

1.  In the virtual machine (VM), open Internet Explorer and navigate to the application's base URL.
2.  Sign in.
3.  On the dashboard, open the navigation pane and go to **Fleet Management \> Setup\> Fleet setup**. 

    > [!div class="mx-imgBorder"]
    > ![Fleet setup.](media/fmt_setup_data.png)
    
4.  On the **Data setup** tab, select **Create**. 
    
    > [!div class="mx-imgBorder"]
    > ![Load Demo Data.](media/fmt_data_setup_create.png)

5.  If you're prompted to reload the demo data, click **Yes**.
6.  When the data is finished loading, select **Close**.

## Use the Fleet Management application to rent a vehicle
Remember that you’re working with the migrated app in this section. The forms that you see are directly ported from the Microsoft Dynamics AX 2012 version of the sample. Although they have been modified and restyled, they have not been reimagined.

1.  Open Internet Explorer, and sign into the finance and operations application.
2.  To return to the **Dashboard**, select the product name in the top-left corner of the page.

    > [!div class="mx-imgBorder"]
    > ![Return to dashboard.](media/fmt_logo.png)
    
    The dashboard is the main working hub. You can see the various tiles, organized into sections, which lead to parts of the application. The dashboard is designed for horizontal scrolling, which is an optimization for working well on modern devices. The button to the right of the dashboard shows the navigation bar.
3.  From the Dashboard, open the navigation bar and go to **Fleet Management \> Customers \> Customer**. 

    > [!div class="mx-imgBorder"]
    > ![Navigate to customer list.](media/fmt_customers_customer.png)
    
    > [!div class="mx-imgBorder"]
    > ![New customer.](media/fmt_new_customer.png)

4.  To switch to the **Details** view, select a value in the **First Name** column. This view shows detailed information for a single customer.

    > [!div class="mx-imgBorder"]
    > ![First name to details view.](media/fmt_details_view.png)

5.  Click **Show list** to show the navigation list. 

    > [!div class="mx-imgBorder"]
    > ![Navigation list.](media/fmt_show_list.png)

6.  Click the various customer names in the navigation list in the side pane, and watch as the detailed information about each customer changes.
7. Select the customer **Eduardo Cobo**. You'll notice the charts update to indicate Eduardo's previous rental preferences.

    > [!div class="mx-imgBorder"]
    > ![Details view.](media/fmt_another_customer.png)

8. Hover over the pie slices to see the details. You'll notice that, in the past, Eduardo has often rented red SUVs. This might give the sales clerk a cue to look for available red SUVs the next time Eduardo makes a reservation. This is a simple example of proactively providing insights.
9. Add yourself as a customer.
    -   On the Action Pane, click **New**. 
        
        > [!div class="mx-imgBorder"]
        > ![Add yourself.](media/fmt_add_new.png)

    -   Fill in the form to add yourself as a customer. Make sure that you provide your name, a 16-digit number in the credit card field, and address information, at a minimum. **Note**: You don't have to take any action to save a new record.

10. Create a new rental.
    1.  On the navigation bar, go to **Fleet management** \> **Rentals** \> **Rental**.
    2.  In the **Rental** form, on the Action Pane, click **New.**
    3.  In the **Vehicle** field, select a vehicle.
    4.  In the **Customer** field, select your name.
    5.  In the **To** field, pick an end date.
    6.  In the **Start** field, enter **35,000**.
    7.  In the **Pickup** field, enter **Full**.
    8.  When you are done, click **Save**.

11. Start the rental period.
    1.  On the Action Pane, click **Start rental**.
    2.  In the dialog box, verify the values in the fields and click **OK**.

## Use Fleet Management to run a workflow
1. Click the **Home** icon to return to the dashboard.

    > [!div class="mx-imgBorder"]
    > ![Home icon.](media/fmt_home_icon.png)

2. Find the **Reservation Management** tile and select it to open the Reservation Management workspace.
3. Click **Current rentals**.
4. On the **Rentals** form, click the ID of your rental.
5. On the Details view of the **Rentals** form, on the Action Pane, click **Complete rental**.
6. In the **New mileage** field, enter **40,000**, and then click **OK**.
7. Click the **Home** icon to return to the dashboard.
8. On the navigation bar, navigate to **Fleet management** &gt; **Vehicles** &gt; **Vehicle Maintenance**. In the **Vehicle Maintenance** form, the **Status** field shows that your rental is awaiting examination by the service department.

    > [!div class="mx-imgBorder"]
    > ![Vehicle mainenance.](media/fmt_vehicle_examination.png)
        
    > [!NOTE]
    > You might need to wait up to two minutes for the batch framework to change the status of the vehicle. On the Action Pane, click **Refresh** periodically to update the view, until you see the status change. Keep in mind that a different person usually handles each step in a workflow; the brief delay introduced by the batch framework is not an issue in a real-world application.

9.  Select the row that contains your rental. On the Action Pane, click **Workflow**, and then click **Examination complete**. You may need to refresh the page to get the full set of options under Workflow.
10. Enter a comment, and then click **Examination complete**.
11. You might again need to wait up to two minutes for the batch framework to process the change. On the Action Pane, click **Refresh** periodically, until you see the **Status** field change. Notice that the vehicle now has a status of **Awaiting Service**.
12. Optionally, you can continue to repeat these workflow steps to take the vehicle through the service and cleaning phases. After cleaning is completed, the final status is **Done**.
13. Click **Workflow**, and then click **View history**. The **Workflow history** form provides information about the vehicle workflow.
14. Click **Tracking details** to see the activities. 

    > [!div class="mx-imgBorder"]
    > ![Tracking details.](media/fmt_workflow_history.png)

### To view the setup behind the workflow

1.  On the dashboard, navigate to **Fleet Management** \> **Setup** \> **Workflow setup**. The **Workflow Setup** page shows the list of workflows. 

    > [!div class="mx-imgBorder"]
    > ![Workflow setup.](media/fmt_workflow_setup.png)
    
2.  In the **Workflow ID** column, click the ID of your vehicle maintenance workflow.
3.  Accept any prompts that ask you for permission to run code. After a short wait, the workflow editor opens. This step works on the one-box environment, but not in the cloud. You can view the workflow diagram in the workflow editor. The following illustration shows the workflow.
    
    > [!div class="mx-imgBorder"]
    > ![Workflow editor.](media/fmt_workflow_editor.png)

4.  When you are done, close the **Workflow** window.

## Create a new KPI definition
The web client enables users who have appropriate permissions to modify KPI definitions that have been modeled and deployed by developers. Users also have the ability to create new KPI definitions in the client. In this walkthrough, you create a new KPI definition in the client.

1.  Open the **Reservation Management** workspace. On the navigation bar, go to **Fleet Management &gt; Workspaces &gt; Reservation Management**.
2.  Notice the Total revenue KPI tile shown on the bottom left of the workspace. Click the **Total Revenue KPI** tile. Details of the total revenue KPI tile along with charts indicating top and bottom contributors to revenue will be shown on screen.
3.  Next, you will define a new KPI to monitor the number of rentals.
4.  On the Action Pane, click **New**. The **New KPI** dialog will open.
5.  Enter following values for the new KPI definition.

    | Field         | Value               |
    |---------------|-------------------------|
    | Name          | Number of Rentals       |
    | Measurement   | FMAggregateMeasurements |
    | Measure group | FmRentalCharges         |
    | Measure       | NoRentals               |
    | KPI Goal Type | Fixed Value             |
    | Goal value    | 30                      |
    
    > [!div class="mx-imgBorder"]
    > ![New KPI.](media/fmt_new_kpi.png)

6.  Click **Save**. 

    > [!NOTE]
    > If the **Save** button isn’t visible in the **New KPI** dialog box, use a higher screen resolution so that you can see the entire dialog. You can see the KPI details page that contains details about the KPI that you created. You can make changes in the **Details** section. You will modify the default threshold values so that if the value is less than 90% of the goal, the KPI will show red and if the value is over 110% of the goal, the KPI will show green.

7.  Click **Edit**.

8.  Scroll to the right of the screen, and modify the values in the thresholds fields as follows.

    | Property           | Value     |
    |--------------------|-----------|
    | Bad if less than   | 90        |
    | Good if more than  | 110       |

9.  In the application bar, click **Save**. 
    
    > [!div class="mx-imgBorder"]
    > ![KPI graph.](media/fmt_kpi_value.png)

10. Click the form caption to return to the grid view.
11. Click the **Name** column header, change the filter operator to **contains**, and update the filter field value to **Number**. You will see the new KPI is available in the list.
    
    > [!div class="mx-imgBorder"]
    > ![KPI list.](media/fmt_kpi_list.png)

## Launch an operational report
In this tutorial, you’ll launch an operational report that contains a list of customers who are currently renting vehicles.

1.  Use the dashboard to open the **Reservation management** workspace.
2.  On the right side of the page, under **Reports** click **Customer list**. Do not enter anything in the parameter for **Customer group**. 
    
    > [!div class="mx-imgBorder"]
    > ![Customer list.](media/fmt_customer_list_report.png)

3.  Click **OK** to close the dialog box. The report will be rendered and show the list of customers. The report may take a minute to render.

## Secure access using the role-based security system
In this tutorial, you’ll access the system as a user that has been assigned a different security role. This tutorial requires that you have created at least one additional end user.

1.  On the dashboard, in the **System administration** section, click **Users** and then **Users**.
2.  On the Action Pane, click **New**.
3.  Enter the following field information.

    | Property        | Value                                                                                 |
    |-----------------|-------------------------------------------------------------------------------------------|
    | User ID         | Eight character unique ID                                                                 |
    | User name       | The first name of the user                                                                |
    | Provider        | `urn:Federation:MicrosoftOnline`                                                          |
    | Email           | Use an email alias that you can login with for testing.                                   |
    | Company         | `DAT`                                                                                     |
    | Enabled         | Verify that this slider is set to **Yes**.                                                |

    > [!div class="mx-imgBorder"]
    > ![New user record.](media/fmt_new_user_record.png)

4.  Click **Assign Roles**. 

    > [!div class="mx-imgBorder"]
    > ![Assign branch manager.](media/fmt_branch_manager.png)

5.  Select **Fleet management branch manager**, and then click **OK**.
6.  Click the user name on the top right, and then click **Sign Out**. You’ll be redirected back to the sign-n page
7.  Sign in using the credentials for the user who you assigned the security role to in the steps above.
8.  Notice that in the dashboard, this user can see only items that are related to the branch manager security role. Items that system administrators can see are now hidden.
9.  Click **Sign out** to sign out of the session.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
