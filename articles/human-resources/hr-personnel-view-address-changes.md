---

# required metadata

title: View and manage address changes
description: This article explains how you can view and manage address changes in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/08/2024
ms.topic: article
# optional metadata

# ms.search.form: HCMChangedPostalAddress, HCMPersonnelManagementWorkspace, HRMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 426c6127-42ee-4163-8dd0-b2867f95581d
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: Version 1611

---

# View and manage address changes

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how you can view and manage address changes on the **Edit personal details** page (which you open from the **Employee self service** workspace) or the **Worker** details page in Dynamics 365 Human Resources.

Many organizations want employees to manage their own personal details through a self-service experience. You can allow users to update their address in the **Employee self service** workspace. You can then monitor these changes in the **Personnel management** workspace. To use this feature, you must specify the number of days that you want to view changes in the **Human resources parameters** page.

## Configure address change parameters

To configure the number of days that you want address changes to appear in the **Personnel management** workspace, follow these steps:

1. On the navigation pane, select **Personnel management**.
2. Select **Links**.
3. Select **Human resources parameters**.
4. In the **Number of days** field under **Address change**, enter the number of days that you want address changes to appear in the **Personnel management** workspace.
5. Close the page.

## Create or change an employee address

Employees can update their own address in the **Employee self service** workspace. Follow these steps to create or change an address:

1. Select the **Employee self service** tile on the **Home** page.
2. Select **Edit personal details**.
3. To add an address, select **Add**. To update an existing address, select the address from the list and then select **Edit**.
4. Enter the **Name or description**.
5. Select the **Purpose** drop-down box and then select the type of address.
6. Enter the **Country/region**.
7. Enter the **ZIP/postal code**.
8. Enter the **Street**.
9. Enter the **City**, **State**, and **County**. Typically, these fields are automatically set based on the **ZIP/postal code** field.
10. Optionally, select the **Primary** field to indicate a primary address. Only one address can be marked as the primary. If another address is already marked as the primary address, you'll need to confirm that you want to use this address as the primary.
11. Optionally, select the **Private** field to indicate that the address is private. Only users with explicit permission to view private address information can view this address.
12. Select **OK**.

## Create or change a worker address

You can update an address in the **Personnel management** workspace. Follow these steps to create or change an address:

1. In the **Personnel management** workspace, select **Links**, and then select **Workers**.
2. Select the worker, and then select **Addresses**.
3. To add an address, select **Add**. To update an existing address, select the address from the list and then select **Edit**.
4. Enter the **Name or description**.
5. Select the **Purpose** drop-down box and then select the type of address.
6. Enter the **Country/region**.
7. Enter the **ZIP/postal code**.
8. Enter the **Street**.
9. Enter the **City**, **State**, and **County**. Typically, these fields are automatically set based on the **ZIP/postal code** field.
10. Optionally, select the **Primary** field to indicate a primary address. Only one address can be marked as the primary. If another address is already marked as the primary address, you'll need to confirm that you want to use this address as the primary.
11. Optionally, select the **Private** field to indicate that the address is private. Only users with explicit permission to view private address information can view this address.
12. Select **OK**.
 
## Create a future change for an address

In some cases, you might want to update an address to change in the future. For example, this would be useful if an employee is moving on the 15th of the following month.

1. Open the **Manage addresses** page by selecting **More options > Advanced** from any address grid.
2. Select **New** to create a new address.
3. Enter the details of the address.
4. Select the **General** FastTab.
5. In the **Effective date** field, select the date the new address will be effective.
6. In the **Expiration date** field, optionally select when the address will no longer be effective.
7. Close the pages.

## View and monitor address changes

HR personnel can view and monitor address changes from the **Personnel management** workspace. To view the address changes, select the **Personnel management** tile on the **Home** page. The address changes appear on a tile in the upper-right corner. The number above **Address changes** shows how many address changes occurred during the number of days that is specified on the **Human resources parameters** page. 

When you select the **Address changes** tile, a new page displays the details of any address changes. You can optionally select **Include future address changes** in the upper-right corner to display address changes with a future date.

> [!NOTE]
> If you want to receive an alert or email about these address changes, you can create a new alert rule on the **Options** tab in the Action Pane. For more information about alert rules, see [Create alert rules](../fin-ops-core/fin-ops/get-started/create-alerts.md).
>
> If you want to configure a workflow for the address changes, you can select the **Send externally** option on your alert rule, and then use Power Automate to trigger the business event and configure a workflow. For more information, see [Alerts as business events](../fin-ops-core/fin-ops/get-started/create-alerts.md#alerts-as-business-events).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
