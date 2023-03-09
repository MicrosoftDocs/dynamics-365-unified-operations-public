# Manage work orders using the Asset Management mobile app

Maintenance workers can use the Asset Management mobile app to manage and process maintenance work orders. The app supports maintenance workers with the following main capabilities:

-   Lists maintenance jobs and work orders assigned to the worker, including all information the worker needs to process each job.

-   Enables workers to register the time and spare parts consumed for each job.

-   Let workers view and update the maintenance checklist associated with a job.

For more information about maintenance work orders in Supply Chain Management, see [Introduction to work orders](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/work-orders/introduction-to-work-orders).

## User requirements

To be able to view and process work orders using the Asset Management mobile app, you must meet the following requirements:

-   Your user account in Supply Chain Management must be assigned the *Maintenance worker* security role.

-   Your user account in Supply Chain Management must be associated with a human resources *Worker* record that is also set up as an Asset Management worker.

-   You must sign in to Power Apps using a domain account that matches a user account in Supply Chain Management with the same Azure Active Directory ID.

For more information about how to set up roles and security in Supply Chain Management, see [Security roles](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/role-based-security#security-roles).

## View the jobs and work orders assigned to you

When you launch the Asset Maintenance mobile app and sign in as a user with the Maintenance worker security role, the app opens to the jobs and work orders list.

![Diagram Description automatically generated](media/image1.png)

The jobs and work orders list have the following elements. The numbers correspond to the numbers in the previous illustration.

1. **Jobs** – Select this tab to see the jobs list. It only shows maintenance jobs that are both assigned to you and belong to a maintenance work order that is *Active*.

2. **Work orders** – Select this tab to see the work orders list. It only shows active work orders that have jobs assigned to you.

3. **User icon** – Select this icon to get information about the app, such as terms and conditions and the current version of the app.

4. **Legal entity –** Shows the legal entity (company) that you are currently working in. The lists only show jobs and work orders associated with this legal entity. If your Supply Chain Management user account is set up as an Asset Management worker in more than one legal entity, then you can select this label to switch between legal entities.

5. **Request** – If your Supply Chain Management user account is assigned the *Maintenance requester* security role, then you can use this button to create a maintenance request. For more information about this functionality, see [Maintenance requests - Supply Chain Management \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/manage-maintenance-requests/maintenance-request-overview).

6. **Search –** When you select this button, a search field appears where you can enter text to search for ID of the work order, asset, or functional location you are looking for.

7. **Filter** – Select this button to filter the jobs or work orders in the list based on the following criteria:

    - **Today** – Only show jobs that are scheduled for today.

    - **This week** – Only show jobs that are scheduled to start during the current week.

    - **All time** – Show all jobs.

8. **Sort order –** Select this button to choose how to sort the list. You can choose to sort by work order service level, scheduled start date, or work order ID.

9. **Job or work order cards** – Each listed job or work order is presented as a *card*, which summarizes the item. Tap a card to open its details page, which provides more information about the selected job or work order.

For more information about work order life cycle states, see [Work order lifecycle states](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/setup-for-work-orders/work-order-lifecycle-states).

## The job details page

In the job lists, each job is presented as a *card*, which shows summary information. Tap a card to open its details page, which provides more information about the selected job. The job details page provides access both to job information and to the maintenance checklist.

### Job information

To see the job information, select the **Jobs** tab at the top of the page. The following illustration highlights the various elements shown on the **Jobs** tab.

![Graphical user interface  application Description automatically generated](media/image2.png)

The job detail page has the following elements. The numbers correspond to the numbers in the previous illustration.

1. **Job and Checklist tabs** – Select a tab to switch between the **Jobs** and the **Checklist**. The numbers in parentheses on the **Checklist** tab indicate the number of completed items and the total number of tasks in the checklist.

2. **Work order identification –** This heading shows the ID of the work order that the current job belongs to. The number in square brackets indicates the total number of jobs in the work order.

3. **Job information** – This section shows the job description and lets you view and edit a **Worker's remark** and **Internal note**.

4. **Attachments, time spent, and materials consumed** – This section lets you view, and open documents attached to the job. You can also adjust time spent and material consumed while working on the job. In Supply Chain Management, the hours spent on a maintenance job are accounted for in a project journal. For more information about how materials and time are accounted for in journals, see [Register consumption](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/consumption/register-consumption).

    -   To adjust the number of hours spent working on the job, select the **Adjust** button next to the **My time spent** heading.

    -   To adjust material consumed while working on the job, select the **Adjust** button next to the **Items consumed** heading. You can both adjust quantities in the list of items expected to be consumed for the job and add new items. When adding new items, you can choose from lists of released products, items in the asset BOM, and spare parts for the current asset. When selecting a product to be consumed, you can specify storage dimensions (site, warehouse, and location) and tracking dimensions (batch and serial number) as needed. Items with product variants (such as configuration, color, and size) aren't listed.

<!-- -->

5. **Scheduled start and end date and times** **–** Shows the days and times when the current job was expected to be done.

6. **Work order state** – Shows the current state of the work order.

7. **Change work order state** – Select this button to change the state of the parent work order for the current job. You'll typically use this to mark the work order as complete or to note a problem that prevents it from being completed.

8. **Go to work order** – Select this button to open the work order that this job belongs to.

9. **See jobs for this asset** – Select this button to see a list of all open maintenance jobs associated with the same asset as the current job. This includes jobs assigned to other workers.

10. **See jobs for this location** – Select this button to see a list of all open maintenance jobs associated with the same location as the current job. This includes jobs assigned to other workers.

### The maintenance checklist

A maintenance checklist is a set of tasks that the maintenance worker needs to complete to close the maintenance job. For more information about how to define a checklist for a job, including how to use item types and how to create groups, see [Maintenance checklists](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/work-orders/maintenance-checklists). For more information about how to set up default checklists that can be assigned to various maintenance jobs or asset types see [Maintenance job types, categories, variants, trades, and checklists](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists).

To see the maintenance checklist, select the **Checklist** tab at the top of the page. The following illustration highlights the various elements shown on the **Checklist** tab.

![Text Description automatically generated](media/image3.png)

The checklist has the following elements. The numbers correspond to the numbers in the previous illustration.

1. **Job and Checklist tabs** – Select a tab to switch between the **Jobs** and the **Checklist**. The numbers in parentheses on the **Checklist** tab indicate the number of completed items and the total number of items in the checklist.

2. **Checklist line number** – Each checklist item has a system generated line number. You can use this to refer to the checklist item when communicating with other workers. The text color changes to green when the item is marked as completed by the worker.

3. **Group name** – Checklist items can be grouped under a header text. (Group names are set up in Supply Chain Management by creating a checklist item of type *Header*.)

4. **Checklist item title** – Shows the title of the checklist item.

5. **Checklist item type** – Shows the type of checklist item it is (*Variable*, *Text*, or*Measurement*).

6. **Value** – Showing the value entered for checklist items of type *Measurement* or*Variable*. To enter these values, select the checklist item card.

## The work order details page

The work order details page shows more information about a selected work order. To open it, select a card from the work order list. The following illustration highlights the various elements shown on the **Checklist** tab.

![Graphical user interface  text  application  chat or text message Description automatically generated](media/image4.png)

The work order detail page has the following elements. The numbers correspond to the numbers in the previous illustration.

1. **Work order and jobs tabs** – Select a tab to switch between the **Work order** details and the list of **Jobs** that belong to this work order. The Jobs list shows a list of job cards; select a card to open the jobs details page for that job.

2. **Work order information** – Information about the work order is shown here in various cards.

3. **Change state** – Select this button to change the life cycle state of the work order. For more information about work order states, see [Work order lifecycle states](https://learn.microsoft.com/en-us/dynamics365/supply-chain/asset-management/setup-for-work-orders/work-order-lifecycle-states).
