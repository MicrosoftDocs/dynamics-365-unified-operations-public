---
# required metadata

title: Microsoft Power Platform integration with Finance and Operations
description: This topic provides an overview for Power Platform Integration via Lifecycle Services for Finance and Operations and Microsoft Dataverse.
author: Sunil-Garg
ms.date: 05/10/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.0
---

# Microsoft Power Platform integration with Finance and Operations

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Microsoft Power Platform provides a suite of capabilities for Dynamics 365 applications via the Power Platform Admin Center. Today, Finance and Operations apps are not managed by the Power Platform Admin Center, however, over time more and more management capabilities will be migrated from Lifecycle Services (LCS) over to the admin center. In the interim, customers will be able to unlock features, such as dual-write functionality, virtual entities, add-ins, and more via Power Platform integration functionality in LCS.

## Prerequisite reading

To understand the architecture of Power Platform, Microsoft Dataverse, dual-write, and virtual entities for Finance and Operations apps, you must understand how they work. Therefore, the following documentation is a prerequisite:

- [Administer Power Platform](/power-platform/admin/admin-documentation)
- [What is Dataverse?](/powerapps/maker/common-data-service/data-platform-intro)
- [Entity overview](/powerapps/maker/common-data-service/entity-overview)
- [Entity relationships overview](/powerapps/maker/common-data-service/relationships-overview)
- [Create and edit virtual entities that contain data from an external data source](/powerapps/maker/common-data-service/create-edit-virtual-entities)
- [What is Power Apps portals?](/powerapps/maker/portals/overview)
- [Overview of creating apps in Power Apps](/powerapps/maker/)

## Tools and services unlocked with Power Platform integration
Virtual entities, dual-write, and business events together make up the shared data layer of the converged of Finance and Operations apps and Dataverse platform. They are complementary technologies intended to work together. 

For scenarios which desire to access the Finance and Operations data from the Power Platform or native Dataverse applications, **virtual entities** allow you to do this. You can query, as well as bind forms to that data, and generally use the full power of the Power Platform against the full breadth of Finance and Operations applications. Data is not copied between systems, but rather directly accessed through the standard Virtual Entity infrastructure which Power Platform technologies can already bind to. For more details, visit <virtual entities overview page>. 

If you want to respond to events happening in Finance and Operations applications with Power Platform, **business events** allow you to do this. Business Events can be raised from any application, including Finance and Operations applications, and handled by Power Platform business logic. This will often include querying or interacting with additional data through either Native or Virtual Entities. 

For a subset of scenarios, data must be physically copied between Finance and Operations applications and native Dataverse entities. These are for overlapping entities which already have a large amount of bound logic in both native Dataverse and Finance and Operations applications, requiring the data be resident in the local database of each. While this is a relatively small number of entities, it includes some of the most important entities such as Account/Customer, Company, Product, and Sales order. For these scenarios, **dual-write** enables near-real-time synchronous copying of data. This allows existing applications to continue to operate against local data as designed, while also ensuring the corresponding overlapping entity is kept in sync. For more details, visit the [Dual-write home page](../data-entities/dual-write/dual-write-home-page.md). 

Together Virtual Entity, Dual Write, and Business Events allow building applications and business processes which span the boundaries between Finance and Operations applications and native Dataverse applications. Most applications and business processes will use a combination or all three of these parts of the shared data layer. As always, extension and customization should reduce the amount of data copied between databases as much as possible, while optimizing for the best possible user experience using these tools. 

### Add-ins functionality
Add-ins provide a way to extend the functionality of Finance and Operations apps. All add-ins are installed and managed via Lifecycle Services on the environment details page for sandbox and production-type environments. The metadata regarding which add-ins are installed and the configuration options for each add-in are stored in the Microsoft Dataverse database that is provisioned as part of the Power Platform integration. Some add-ins also store business data in the Dataverse database. To learn more about available add-ins, see [Add-ins overview](add-ins-overview.md).

## Typical scenarios and patterns that use dual-write

Here are some typical scenarios that use dual-write.

### Enable customer service representative to facilitate change of address for Finance and Operations customers 
A customer relocates and wishes to change their billing and shipping address information. This customer contacts the customer support representative and requests a change of address. The customer support representative takes the call and changes the billing and shipping address information of the customer.

|Decision |  Information| 
|--------|-------------|
| Is real-time data required? | Yes |
| Peak data volume  | - |
| Frequency | Ad hoc |

#### Recommended solution
This scenario of near-real time data synchronization is best implemented by dual-write.
- The customer's information is sourced in a Finance and Operations app.
- A customer calls customer support and asks to change their billing and shipping address information.
- A customer support representative retrieves the customer’s record in Dynamics 365 Customer Service.
- The customer support representative updates the billing and shipping address and saves the data.
- The new billing and shipping address syncs back to the Finance and Operations app in real-time.

### Sales representatives can change customer credit limits without logging into a Finance and Operations app
A customer has a credit limit of $2,000 and wants to increase it to $5,000. This customer calls the customer support and requests the increase. The ticket is assigned to the sales department. The head of sales reviews the request, checks the customer's payment history, and determines that the customer is eligible for an increased credit limit. The head of sales approves the request and responds to the ticket. The customer receives an email informing the approval of $5,000 credit limit.

|Decision |  Information| 
|--------|-------------|
| Is real-time data required? | Yes |
| Peak data volume  | - |
| Frequency | Ad hoc |

#### Recommended solution
This scenario is best implemented by dual-write.
- A customer calls customer support and wants to increase their credit limit from $2,000 to $5,000.
- A customer support representative creates a ticket in Dynamics 365 Customer Service.
- This ticket is assigned to the sales unit.
- A sales representative from the sales unit reviews and approves the request.
- This result is the increase of credit limit of the customer to $5,000 in Dynamics 365 Sales.
- The credit limit in the Finance and operations app is updated to $5,000.
- The sales representative responds to the ticket and resolves it.
- The customer receives an email about the increased credit limit.

## Prerequisites for setting up the Power Platform integration
The following list provides details about the prerequisites for setting up the Power Platform integration:

- Make sure that at least one gigabyte (GB) of Power Platform database storage capacity space is available for your tenant. Otherwise, setup will fail. You can view your capacity in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 
- Identify your Finance and Operations environment administrator. You can find that information in the **Environment details** section.

    ![Environment details tab](media/EnvironmentDetails.png)
    
- Validate your Power Platform environment governance policy. To validate, you must be a **Global administrator** or **Power Platform administrator**.
    
    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. Select the gear icon in the upper-right corner of the Power Platform site.
    
        ![Power Platform settings](media/PowerPlatformSettings.png)
    
- For organizations that do not allow **Everyone** to create Power Platform production environments, the Finance and Operations environment administrator account for your environment must be added to one of the following Power Platform admin roles.
    
    The Finance and Operations environment administrator must be added to one of the following roles. You will need a Global Administrator to perform this action.
    - Global admins
    - Dynamics 365 admins
    - Power Platform admins
    
    For more information, see [Use service admin roles to manage your tenant](/power-platform/admin/use-service-admin-role-manage-tenant).

- All users who create Power Platform environments must be licensed. The Finance and Operations environment administrator account should have the **Dynamics 365 Unified Operations Plan** license applied using the Microsoft 365 admin center.

## Enabling the Power Platform integration
Currently, the Power Platform integration can only be set up after the Finance and Operations environment is deployed.  In the future, this will also be possible during deployment of the Finance and Operations environment itself, as well for new sandbox and production environments.

### Set up after environment deployment
To set up after the Finance and Operations environment has been deployed, follow these steps:

1. After the Finance and Operations environment has been deployed through LCS, open the **Environment details** page in LCS.
2. In the **Power Platform integration** section, select **Setup**.
3. In the **Power Platform environment setup** dialog box, agree to the terms and conditions, and then select **Setup** at the bottom of the dialog box.

    > [!NOTE]
    > This will provision a Microsoft Dataverse-based environment in the Power Platform admin center, and typically requires 1GB of database storage capacity.  It will have the same name as your Finance and Operations environment.  Dual-write platform-level components will be installed, but dual-write application components will not be set up or enabled.  That is a separate action.  

4. When you receive a message that states that the Microsoft Power Platform environment is being provisioned, select **OK**.

    The **Power Platform integration** section of the **Environment details** page now shows a message that states that the Microsoft Power Platform environment is being provisioned.

5. After a few minutes, refresh the **Environment details** page.
6. In the **Power Platform integration** section, notice that the value of the **Status** field is **Environment setup is in progress**.

    Typically, the setup takes between 60 and 90 minutes.

    After the Dataverse environment is provisioned, the **Install a new add-in** and the **Dual-write application** buttons become available in the **Power Platform integration** section.

    ![Install a new add-in button](media/InstallANewAddIn.png)
    <br/>
    ![Dual-write application button](media/powerplat_integration_dwApp_button.png)

### Troubleshooting the setup
Setup can fail at various stages of the deployment of the Dataverse-based environment.   

![Dual-write setup failure](media/Error.png)

- Anytime the setup fails, an error message will be displayed.  Based on the error message, you may need to address licensing or capacity issues.  After these have been resolved, you can then use the **Resume** button in the **Power Platform integration** section of the **Environment details** page in LCS to finish the setup.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
