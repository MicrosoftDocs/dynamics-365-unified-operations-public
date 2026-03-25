---
# required metadata

title: API-based payroll integration with Ceridian Dayforce
description: This article describes the API-based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce.
author: twheeloc
ms.date: 03/25/2026
ms.topic: concept-article
# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-02-03
ms.dyn365.ops.version: Human Resources
---


# API-based payroll integration with Ceridian Dayforce

This article describes the configuration steps required for API-based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce. Configuration is required in both systems before a pay run can be processed.


## Environment settings

Before using the Human Resources payroll integration, configure the following parameters:

   - On the **Human Resources shared parameters** page:
      - On the **Positions** tab, select **Require departments on positions**.
      - On the **Payroll integration** tab, select **Use payroll address purposes**.

   - On the **Human Resources parameters** page:
      - On the **Payroll integration** tab, select **Use identification types in payroll processing**.
      - In the **Identification type** field, select the appropriate identification type for the legal entity.

   - In General Ledger, navigate to **Chart of accounts** > **Dimensions** > **Financial dimension configuration for integrating applications** > **Data entities**. Define financial dimension formats for data entities.
 
> [!NOTE]
> Human Resources parameters are unique per legal entity and must be configured for each entity.
> Coordinate with Ceridian to determine which financial dimensions align with the Dayforce site (location).

> [!IMPORTANT]  
> For customers using **mshr entities**, row version change tracking must be disabled. Contact Microsoft support to enable the `DMFDisableSqlRowVersionCtForCDSVirtualEntity` flight.


## Enable features

You must enable features in Feature management to expose Microsoft APIs to the integration and the data to be passed to Dayforce. Some features may already be enabled by default.

To enable features, follow these steps:
   1. Go to **System administration** > **Feature management** > **All**.
   2. Enable the following features:
      - **Streamline employee entity**
      - **Benefits management**

### Virtual tables

Human Resources is a virtual data source in Dataverse. It provides full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform. 

To set up mshr Virtual tables, follow these steps.

### Register the app in Microsoft Azure

You must register your Human Resources instance in the Azure portal so the Microsoft identity platform can provide authentication and authorization services for the app and users. For more information about registering apps in Azure, see [Register an application with the Microsoft identity platform](../../entra/identity-platform/quickstart-register-app).

1.	Open the [Microsoft Azure portal](https://portal.azure.com/).
2.	In the Azure services list, select **App registrations**.
3.	Select **New registration**.
4.	In the **Name** field, enter a descriptive name for the app. For example, **Dynamics 365 Human Resources Virtual Tables**.
5.	In the **Redirect URI** field, select Web and enter the namespace URL of your FinOps application like `https://<hostname>.operations.dynamics.com`
6.	Select **Register**.
7.	When registration completes, the Azure portal displays the app registration's Overview pane, which includes its **Application (client) ID**. Note the Application (client) ID. 
8.	In the left navigation pane, select **Certificates and secrets**.
9.	In the **Client secrets** section, select **New client secret**.
10. Provide a description, select a duration, and select **Add**.
11. Record the secret's value from the **Value** property of the table.


> [!IMPORTANT]  
> Be sure to take note of the secret's value as the secret isn't displayed again after you leave this page.


### Install the Dynamics 365 Human Resources virtual table app
Install the Dynamics 365 Human Resources virtual table app in your Power Apps environment to deploy the virtual table solution package to Dataverse.

1.	Navigate to [Power platform admin center](https://admin.powerplatform.microsoft.com/) and select your environment.
2.	Select Dynamics 365 apps under **Resources** tile.
3.	Select **Install app**.
4.	Select **Dynamics 365 HR Virtual Tables app**.

### Configure the virtual table data source
To configure the virtual table data source in the Power Apps environment, follow these steps:
1.	Open the [Maker portal](https://make.powerapps.com/) and select your environment.
2.	Go to tables and search for **Finance and Operations Virtual Data source configuration table**.
3.	Select **Microsoft HR Data Source** record and enter the following information.
4.	Enter the required information for the data source configuration:
      - **Target URL**: The URL of your Finops namespace. The format of the target URL is: `https://<hostname>.operations.dynamics.com/`

      > [!NOTE]
      > Be sure to include the "/" character at the end of the URL to avoid receiving an error.

      - **Tenant ID**: The Microsoft Entra tenant ID.
      - **Microsoft Entra Application ID (AAD ApplicationId)**: The application (client) ID created for the application registered in the Microsoft Azure portal. You received this information during the [Register the app in Microsoft Azure](#register-the-app-in-microsoft-azure) step.
      - **Microsoft Entra Application Secret**: The client secret created for the application registered in the Microsoft Azure portal. You received this information earlier during the [Register the app in Microsoft Azure](#register-the-app-in-microsoft-azure) step.
      - **AAD Resource**: Put this value 00000015-0000-0000-c000-000000000000.

5.	Select **Save** and **Close**.

### Grant app permissions in Dynamics 365 finance and operations 

Grant permissions for the two Microsoft Entra applications in the Dynamics 365 finance and operations application:
1.	In Dynamics 365 finance and operations, navigate to **System administration -> Setup -> Microsoft Entra ID applications** page.
2.	Select **New** to create a new application record:
      - In the **Client ID** field, enter the client ID of the app you registered in the Microsoft Azure portal.
      - In the **Name** field, enter the name of the app you registered in the Microsoft Azure portal.
      - In the **User ID** field, select the user ID of a user with admin permissions in Dynamics 365 finance and operations and the Power Apps environment.
3.	Select **New** to create a second application record:
      - **Client Id**: f9be0c49-aa22-4ec6-911a-c5da515226ff
      - **Name**: Dynamics 365 HR Virtual Table
      - In the **User ID** field, select the user ID of a user with admin permissions in Finops and the Power Apps environment.


### Generate virtual tables
When setup completes, you can select the virtual tables you want to generate and enable in your Dataverse instance.
1.	Open the [Maker portal ](https://make.powerapps.com/)and select your environment.
2.	Select **Available HR Entities** table.
3.	Select the table or tables you want to generate in Dataverse.
4.	Select **Has Been Generated/refresh**.

To see the entities that are present for dayforce integration, see [Mshr payroll entities](./hr-admin-integration-payroll-api-payroll-employee.md).


## Change tracking

The change tracking feature in Dataverse detects data that has changed since the data was originally extracted or last synced. For more information, see [Use change tracking to synchronize data with external systems](../../power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems).  

To enable change tracking, follow these steps.
1.	Go to **System administration > Data management > Data entities**.
2.	Search for the target entity.
3.	Turn on **Track changes**.

| Target entity|Change tracking |
| --- | --- |
| DirPersonNameHistoricalEntity | All tables |
| HcmCompFixedEmplEntity | All tables |
| HcmCompFixedPlanTableEntity | All tables |
| HcmCompVarPlanTableEntity | All tables |
| HcmEmployeeEntity | All tables |
| HcmEmployeeV2Entity | All tables |
| HcmEmploymentDetailEntity | All tables |
| HcmEmploymentEmployeeEntity | All tables |
| HcmEmploymentEntity | All tables |
| HcmEmploymentTypeEntity | All tables |
| HcmEmploymentV2Entity | All ltables |
| HcmIdentificationTypeEntity | All tables |
| HcmJobBaseEntity | All tables |
| HcmJobCompensationEntity | All tables |
| HcmJobDetailEntity | All tables |
| HcmJobEntity | Primary table |
| HcmJobFamilyEntity | All tables |
| HcmJobFunctionEntity | All tables |
| HcmJobTaskEntity | All tables |
| HcmJobTypeEntity | All tables |
| HcmLaborUnionEntity | All tables |
| HcmPersonDetailsEntity | All tables |
| HcmPersonIdentificationNumberEntity | All tables |
| HcmPositionBaseEntity | All tables |
| HcmPositionDefaultDimensionEntity | All tables |
| HcmPositionDetailEntity | All tables |
| HcmPositionEntity | Primary table |
| HcmPositionHierarchyEntity | All tables |
| HcmPositionHierarchyTypeEntity | All tables |
| HcmPositionTypeEntity | All tables |
| hcmPositionUnionAgreementEntity | All tables |
| HcmPositionV2Entity | All tables |
| HcmPositionWorkerAssignmentEntity | Primary table |
| HcmPositionWorkerAssignmentV2Entity | Primary table |
| HcmUnionsEntity | All tables |
| HcmVariableCompensationTypeEntity | All tables |
| HcmWorkerBankAccountEntity | All tables |
| HcmWorkerBaseEntity | Custom |
| HcmWorkerEntity | Custom |
| HcmWorkerPayrollInfoEntity | All tables |
| PayrollBankAccountDisbursementEntity | Primary table |
| PayrollEmployeeEntity | Primary table |
| PayrollFixedCompensationPlanEntity | All tables |
| PayrollPositionDetailsEntity | All tables |
| PayrollPositionEntity | All tables |
| PayrollPositionJobEntity | All tables |
| PayrollWorkerAddressCurrentEntity | All tables |


## Add Dayforce Connector user in Dynamics 365 finance and operations

1. Go to **System administration** > **Manager user**, and select **New user**.
2.	Enter values in the **User ID**, **User name**, **User email**, and **Role** fields.
3.	Use the previously created API Dayforce Connector role.

> [!NOTE]  
> The user name and password are required for the setup of the MyIntegration portal in Dayforce.

### Enable the connection

> [!IMPORTANT]
> This section requires a user who has full administrative security access to the Dataverse and Azure tenant. The user must also have the right to give consent on behalf of the company (tenant) to allow access to the Human Resources APIs.

To connect the Human Resources environment to Dayforce payroll, follow these steps:

1. Add the Dayforce payroll connector application to the tenant.
2. Configure an API role for the Dataverse environment.

### Enable the Dayforce people connector application on the customer tenant

The customer's Microsoft tenant controls all activity in the customer's Microsoft environment. This activity includes security and access to all Microsoft applications. By enabling the Dayforce people connector on the tenant, you enable it to communicate with the necessary Microsoft applications that are used in this integration.

1. Go to <https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=6817703f-e5b3-4eec-b11f-ba6367f1b156&response_type=id_token&redirect_uri=https://developersdev.dayforce.com/Dev/Microsoft-to-Dayforce-Connector.aspx&scope=openid&response_mode=fragment&state=12345&nonce=678910>.
2. Enable the URL for the company.
3. Select **Consent** on behalf of your organization.

### Add the Dayforce people connector in Dataverse

You must add the Dayforce people connector to your specific Dataverse instance.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/), go to **Environment** \> **Settings** \> **Application users**, and select **New user**.
2. Add the Dayforce people connector application. The app ID is **6817703f-e5b3-4eec-b11f-ba6367f1b156**.
3. Give the application the following security roles:

    - Basic user
    - Finance and operations basic user

For more information, see the following resources:

- [Security roles in Microsoft Power Platform](../fin-ops-core/dev-itpro/power-platform/authentication-and-authorization.md#security-roles-in-microsoft-power-platform)
- [Security roles and privileges](/power-platform/admin/security-roles-privileges)
- [Predefined security roles](/power-platform/admin/database-security#predefined-security-roles)

### Add the Dayforce people connector to the Human Resources environment

1. In Human Resources, go to **Microsoft Entra Application**, and select **New**.
2. Add the Dayforce payroll connector that has the client ID **6817703f-e5b3-4eec-b11f-ba6367f1b156** and the user ID **DFAPIConnector**.

## Ready to pay

> [!IMPORTANT]
> Before employees can be integrated into Dayforce, they must be marked **Ready to pay**. Employees that aren't marked **Ready to pay** won't be picked up.

The Dayforce people connector integration uses Microsoft's ready to pay feature to ensure that a complete, valid employee profile has been created before payroll is processed. For more information, see [Ready to pay](hr-compensation-payroll.md).
