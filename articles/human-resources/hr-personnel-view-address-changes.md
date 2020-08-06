---
# required metadata

title: View and manage address changes
description: This article explains how you can view and manage address changes that are made in the employee self-service **Edit personal details** page or in the **Worker** details page.
author: andreabichsel
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: HCMChangedPostalAddress, HCMPersonnelManagementWorkspace, HRMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Human Resources
# ms.tgt_pltfrm: 
ms.custom: 269074
ms.assetid: 426c6127-42ee-4163-8dd0-b2867f95581d
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# View and manage address changes

This article explains how you can view and manage address changes that are made in the employee self-service **Edit personal details** page or in the **Worker** details page.

Many organazitions want to enable employees to manage thier own personal details through a self-service experience. You can allow users to make updates to thier address for through the **Employee self-service** workspace and moniitor those changes in the **Personnel management** workspace. In order to use this feature you must specify the number of days you want to view changes in the **Human resources parameters** page.

## Configure address change parameters
To configure the address change parameters, follow these steps.
1. On the Navigation pane, click **Personnel management**.
2. Click **Links**
3. Click **Human resources parameters**.
4. In the **Number of days** field under **ADDRESS CHANGE**, enter the number of days that you want address changes to appear in the **Personnel management** workspace.
5. Close the page.

## Create or change an address in Employee self-service
Employees can update thier own address in the **Employee self service** workspace by following these steps.

1. Click the **Employee self-service** tile on your home page.
2. Click the **Edit personel details** link.
3. To add an address click **Add**, to update and existing address, select the address from the list and then click **Edit**
4. Enter or update the **Name or description** field.
5. Click the **Purpose** drop-down box to select a type of address you are creating or updating.
6. Enter or update the **Country/region** field.
7. Enter or update the **ZIP/postal code** field.
8. Enter or update the **Street** field.
9. Enter or update the **City**field. This field typically autopopulates based on the **ZIP/postal code** field.
10. Enter or update the **State** field. This field typically autopopulates based on the **ZIP/postal code** field.
11. Enter or update the **County** field. This field typically autopopulates based on the **ZIP/postal code** field.
12. Optionally, select the **Primary** field to indicate a primary address. Only one address can be marked as the primary. If another address is already marked as the primary address, you will be prompted to confirm if you want this address to be the primary.
13. Optionally, select the **Private** field to indicate that the address is private and can only be viewed by users with explicit permission to view private address information.
14. Click **OK**.

## Create or change an address on Workers


## Create a future change for an address
In some cases you may want to update an address to change in the future. For example, an employee is moving on the 14th of next month. To make future changes for an address you must use the **Advanced** option to open the **Manage addresses** page. You can open the **Advanced** option by clicking **More options** and selecting **Advanced** from the **Addresses** grid on the **Personal details** page, the **Workers** page, or any page that has the **Address** grid. To make a future change follow these steps.

1. Open the **Manage addresses** page by clicking **More options > Advanced** from any address grid.
2. Click **New** to create a new address.
3. Enter the details of the address.
4. Cilck the **General** FastTab.
5. In the **Effective date** field, select the date the new address will be effective.
6. In the **Expiration date** field, optionally select when the address will no longer be effective.
7. Close the pages.

## View and monitor address changes
HR personnel can view and monitor address changes from the **Personnel management** workspace. To view the address changes, open the **Personnel management** tile from the **Home** page. The address changes are displayed on a tile in the upper right corner. The number above **Address changes** indicates how many address changes have occured in the last number of days that you specify in the **Human resources parameters** page. 

By clicking on the **Address changes** tile, a new page will open where you can view the details of the address changes that have occured. You can optionally select the **Include future address changes** slider in the upper right corner to display not only the current and past address changes, but the address changes with a future date as well.

> [!NOTE]
> If you want to receive an alert rule or email about these address changes, you can create a new alert rule from the **Options** tab in the Action Pane. For more information about alert rules, refer to [Create alert rules](/fin-ops-core/fin-ops/get-started/create-alert-rules.md).

> [!NOTE]
> If you want to configure a workflow for the address changes, you can select the **Send externally** option on your alert rule, and then use Power Automate to trigger the business event and configure a workflow. For more information refer to [Alerts as business events](/fin-ops-core/dev-itpro/business-events/alerts-business-events.md).
