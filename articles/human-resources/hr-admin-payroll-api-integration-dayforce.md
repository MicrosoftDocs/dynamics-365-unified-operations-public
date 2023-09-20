---
# required metadata

title: API based Payroll integration with Ceridian Dayforce
description: This article describes the API based Payroll integration API
author: TulsiJhaveri 
ms.author: tulsijhaveri
ms.date: 09/15/2023
ms.topic: how-to
ms.custom: 

---

# API based Payroll integration with Ceridian Dayforce

The API based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce relies on several configuration steps that are described in this article. You must configure the integration in both Human Resources and Dayforce before you can process a pay run. 

## Environment settings

Before using the Dynamics 365 Human Resources payroll integration, set up the following parameters: 

- Human Resources shared parameters:
    - **Positions** > select **Require departments on positions**.
    - **Payroll integration** > select **Use payroll address purposes**.
    - **Financial dimensions** > select **Default financial dimensions**.

-	Human Resources parameters
    - **Payroll Integration** > select **Use identification Types in payroll processing**.
    - **Payroll Integration** > select the appropriate **Identification type** for legal entity.
    

-	In System administration, define financial dimension formats for data entities using **Financial dimension configuration for integrating applications** > **Data entities**

> [!NOTE]
> Human Resources parameters are unique to each legal entity. When using multiple legal entities, you must configure human resources parameters for each company.
> Ensure that the financial dimension item(s) in the selected list are in the correct order. The connector looks at the financial dimension position that has been provided from the selected list in the Myintegration Portal.
> Collaborate with Ceridian to determine which Financial dimensions should be enabled to align with the Dayforce site (location).

For more information, see [Configure Human resources parameters](hr-setup-parameters.md).

![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/8fe8abab-0c24-4dfd-8110-ae2abd5dfae2)

## API Setup

To use the API, the virtual tables must be generated. For more information, see [Virtual tables](hr-admin-integration-payroll-api-introduction.md#virtual-tables-for-human-resources-in-dataverse).

## Enable features
Enable the following features in **Feature management** to allow Microsoft APIs to be exposed to the integration and the data to pass to Dayforce:
1. Go to **System administration** > **Feature management** > **All**.
2. Enable these features:
    - (Preview) Payroll integration
    - Virtual table support for HR in Dataverse
    - Streamline employee entity

    - Benefits management
> [!NOTE]
> Features in feature management may be enabled by default.

## Virtual tables

Dynamics 365 Human Resources is a virtual data source in Microsoft Dataverse. It provides full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform. For more information on Dataverse vitual tables, see [Configure Dataverse virtual tables](hr-admin-integration-common-data-service-virtual-entities.md).

For more information about installing virtual tables, see [Install virtual tables](hr-admin-integration-common-data-service-virtual-entities.md#install-the-dynamics-365-hr-virtual-table-app) and 
[Generate virtual tables](hr-admin-integration-common-data-service-virtual-entities.md#generate-virtual-tables)

After the virtual tables are installed, generate the virtual tables for the data to pass to Dayforce. The Dayforce people connector pulls data from the tables listed below, to ensure that Dayforce can execute a proper payroll. For additional information, see [Enable Microsoft Dataverse virtual entities](../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

Go to: **Dataverse integration** > **Virtual tables**

- DimAttributeHcmPositionEntity
- DirPersonNameHistoricalEntity
- FinancialDimensionValueEntity
- HcmCompFixedPlanTableEntity
- HcmEmployeeV2Entity
- HcmEmploymentDetailEntity
- HcmEmploymentEmployeeEntity
- HcmEmploymentV2Entity
- HcmJobDetailEntity
- HcmJobEntity
•	HcmJobFamilyEntity
•	HcmJobFunctionEntity
•	HcmJobTypeEntity
•	HcmLaborUnionAgreementEntity
•	HcmLaborUnionEntity
•	HcmPayRateConversionEntity
•	HcmPersonIdentificationNumberEntity
•	HcmPersonLaborUnionEntity
•	HcmPositionDefaultDimensionEntity
•	HcmPositionDetailEntity
•	HcmPositionEntity
•	HcmPositionHierarchyEntity
•	HcmPositionTypeEntity
•	HcmPositionUnionAgreementEntity
•	HcmPositionV2Entity
•	HcmPositionWorkerAssignmentV2Entity
•	HcmReasonCodeEntity
•	HcmUnionsEntity
•	HcmWorkerBankAccountEntity
•	HcmWorkerBaseEntity
•	HcmWorkerContactEntity
•	HcmWorkerEntity
•	HcmWorkerPayrollInfoEntity
•	Hcmworkerpostaladdressv2entity
•	HcmWorkerSummaryEntity
•	OMCostCenterEntity
•	OMDepartmentV2Entity
•	OMLegalEntity
•	OmLegalEntityContactEntity
•	PayrollBankAccountDisbursementEntity
•	PayrollEmployeeEntity
•	PayrollEmployeeV2Entity
•	PayrollFixedCompensationPlanEntity
•	PayrollPositionDetailsEntity
•	PayrollPositionEntity
•	PayrollPositionJobEntity
•	PayrollPositionWorkerDefaultTaxRgnEntity
•	PayrollWorkerAddressCurrentEntity
- PayrollVariableCompensationAwardEntity
- HcmVariableCompensationAwardEntity


### Track changes

The **Change tracking** feature feature in Microsoft Dataverse provides a way to keep the data synchronized in an efficient manner by detecting what data has changed since the data was initially extracted or last synchronized. For more information, see [change tracking](/power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems).

To enable change tracking:
1. Go to **System administration** > **Data management** > **Data entities**.
2. Search for the **target** entity.
3. Turn on Tracking changes.

## Add Dayforce Connector user in Human Resources environment

1. Go to **System administration** > **Manager user** > **New user**.
2. Enter the **User ID**, **User name**, **User email** and **Role** (Use the previously created API Dayforce Connector Role).

> [!NOTE]
> Note the username and password as this information is required for the set up of the MyIntegration portal in Ceridian Dayforce.

## Enable the connection

> [!IMPORTANT] 
> Following section requires a user with full administrative security access to the Microsoft dataverse and Azure tenant and the rights to consent on behalf of the company (Tenant) to allow this application access to the Microsoft Dynamics 365 HR APIs. 

To connect the Microsoft Dynamics 365 Human Resources environment to Ceridian's Dayforce Payroll, the complete the following steps:

1.	Add the Dayforce payroll connector application to the Tenant.
2.	Configure an API role for the Dataverse environment.

### Enable the Dayforce people connector application on the customer tenant

The customer Microsoft tenant controls all activity in the customer’s Microsoft environment including controlling security and access to all the Microsoft applications. Enabling the Dayforce People Connector on the tenant enables the connector to communicate with the necessary Microsoft applications used in this integration.

- Go to (https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=6817703f-e5b3-4eec-b11f-ba6367f1b156&response_type=id_token&redirect_uri=https://developersdev.dayforce.com/Dev/Microsoft-to-Dayforce-Connector.aspx&scope=openid&response_mode=fragment&state=12345&nonce=678910)
- Enable the URL for the company
  ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/520495b3-fcab-41d0-a3bb-1e3032d3ae1c)

- Consent on behalf of your organization

### Connector in Dataverse

The Dayforce People Connector will need to be added to your specific Dataverse.

1. Go to **Admin.powerplatform.microsoft.com** > **Environment** > **Settings** > **Application users** > **New user**.
2. Add the Dayforce people connector application: App ID: 6817703f-e5b3-4eec-b11f-ba6367f1b156
3. Give the application the following security roles:
    - Basic user
    - Finance and operations basic user

For more information, see: 

[Authentication and authorization](../fin-ops-core/dev-itpro/power-platform/authentication-and-authorization.md#security-roles-in-microsoft-power-platform)
[Security roles and privileges](/power-platform/admin/security-roles-privileges)
[Configure user security](/power-platform/admin/database-security#predefined-security-%20roles)

### Add the Dayforce People Connector to the Human Rresources environment

1. In Human Resources, go to: **Azure Active Directory Application** > **New**.
2. Add the Ceridian Dayforce payroll connector with Client ID: 6817703f-e5b3-4eec-b11f-ba6367f1b156 and User ID: DFAPIConnector. 

![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/5fe3d568-c993-4447-b7ab-960fb082e236)

      
## Ready to Pay

> [!IMPORTANT]
> In order for employees to be integrated to Dayforce, they need to be enabled for ready to pay. Employees not marked as ready to pay will not be picked up.

Ceridian’s Dayforce people connector integration uses Microsoft’s ready to pay feature that ensures a complete, valid employee profile has been created prior to being picked up and processed.
For more information, see [Ready to pay](hr-compensation-payroll.md).

