---
# required metadata

title: Work order project setup
description: This topic explains work order project setup in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
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

# Work order project setup

In the **Asset management** module, a project relation on a work order job is mandatory. The project associated with the work order job allows you to track costs on different projects related to Asset Management, for example, internal maintenance projects, service management projects, and investment projects. Refer to [Integration to project management and accounting](../integration-to-project-management-and-accounting/forecasts-work-orders-and-projects.md) for more information about project relations to work orders and assets.

## Project setup for a work order job

When you create a new work order job on a work order, the project setup in the **Project management and accounting** module, and the work order project setup in **Asset management** determine how projects can be used for cost control on the asset selected on the work order job. This section describes different parts of the project setup used on a work order: Parent project (Project ID) - Project type - Project activities - Financial dimensions:

- When you create a new work order job on a work order, a unique Project ID and a related project activity are automatically created for the work order job. However, if several work order jobs on a work order include the same asset, the same Project ID is used on those work order jobs, meaning one Project ID is created for each asset on a work order.  
  - The parent project (Project ID) for a work order job is found in the parent project setup, explained in the procedure below. You can associate, for example, a customer or a functional location to a specific parent project. In that case, that parent project will be used each time you create work orders for that specific customer or that specific functional location. If you have not related a specific Project ID to, for example, a functional location, the next relevant parent project in the work order project setup will be used.  
  - A project type is required for a Project ID. The project type is found in the project group setup, explained in the section and procedure below, or, if no match is found in the project group setup, the project group setup on the parent project is used.  
  - The setup for requiring project activities on forecasts and journals is copied from the parent project to the work order project. If "Yes" is selected in the **Hour**, **Expense**, and **Item** toggle buttons in **Project management and accounting** > **Projects** > **All Projects** > select the project used as a parent project > **Setup** FastTab > **Require activity on journals** section, a project activity is mandatory on forecasts and journals.  
- Financial dimensions are copied from the asset and merged with the parent project.

The section below explains how to set up parent projects and project groups, which are used for controlling and reporting regarding work orders.

## Set up work order projects

Before you start creating work orders, you must set up work order projects. **Work order project setup** contains two links, **Parent project** and **Project group**. In the **Parent project** section, you can set up project relations to be used in case no project is set up on the asset selected on the work order job. Parent project setup is not required if your company uses asset projects. It is only relevant if you want to use work order projects instead of asset projects - in that case you must set up at least one parent project.

In the **Project group** section, you can set up project groups to be associated with work order types, asset types, and assets.

Project groups can be used to create specific categories (groups) used for cost control. *Example:* Creating project groups for specific asset types or work order types allow you to track maintenance costs by type on a detailed level.

Project groups are not mandatory. If you do not set up project groups, the parent project is used to determine the project group, and a child project is created from the parent project's project group.

The setup allows complete integration with the **Project management and accounting** module, allowing you to track costs related to work orders in the related projects. Read more about the relation between work order projects, project stages and work order lifecycle states in [Forecasts, work orders, and projects](../integration-to-project-management-and-accounting/forecasts-work-orders-and-projects.md). The following procedure describes the work order project setup.

1. Click **Asset management** > **Setup** > **Work orders** > **Project setup**. Make sure the **Parent project** link is selected.
2. Click the **Add** button.
3. Select a **Work order type**, **Functional location**, **Asset type**, **Asset**, as required, in the related fields. It is possible to fill out only one field, two fields, or all fields for each line. The number of fields you fill out determine the combination used when selection of a project ID is done in Asset Management. Read more about the combinations and the selection process in [Forecasts, work orders, and projects](../integration-to-project-management-and-accounting/forecasts-work-orders-and-projects.md).

- If you select a functional location, the related child locations are automatically included. If you select an asset, it is possible to create more work order project setup lines for the same asset, but select different projects for the same asset.   

4. In the **Project ID** field, select the project to be related to the setup you created in step 3.
5. In the **End date** field, you can select a date if the project setup is to be valid for only a limited period. If no limitation is relevant, make sure the "None" option is selected.

- Select **View** > **All** to see the **Valid from** field. The standard setup regarding start date is the date you add the work order project to the form. If required, you can set up a limited period for the work order project in the **Valid from** and **End date** fields.


![Figure 1](media/17-setup-for-work-orders.png)

6. Click the **Project group** link, and click the **Add** button.
7. In the **Work order type** field, select a work order type.
8. If you want the project group association to be more specific, select **Asset type** or **Asset** in the related fields.
9. In the **Project group** field, select the project group to be related to the work order type. Examples: A work order type called "Preventive maintenance" may be associated with a project group called "Prev Maint" or "Internal". A work order type called "Investment", to be used for work orders related to investments and fixed assets, may be associated with a project group called "Invest" or "Investment".
10. Click **Save**.

![Figure 2](media/18-setup-for-work-orders.png)


>[!NOTE]
>Each time a new work order line is created, Asset management searches for a project group to be related to the work order job project, based on the setup described in this section. All project groups have a related project type. Project groups that use the project type "Time and material" or "Fixed-price" are only valid for assets that are related to a customer account.  


>[!NOTE]
>Regarding Parent project and Project group, when the system selects the available work order project or project group, the selection is based on the records you created in the procedure above. Asset Management goes through records related to the work order project to check for a possible match, always checking the most specific combination first. For the work order parent project, this means that, first, a possible match regarding Asset is checked. If no match is found, Asset type is checked. If no match is found, Functional location is checked, and so on. As you can see in the layout of the form, this means that Asset Management checks each record from right to left for a match (Asset, then Asset type, Functional location, and Work order type) to find the most specific combination. If no match is found, the "default" record is used in which only a Project ID is selected. Finding the related project group is a similar process. First, a possible match regarding Asset is checked, then Asset type, and Work order type. Also in this case, if no match is found, the "default" record is used in which only a Project group is selected.

