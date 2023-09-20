---

# required metadata

title: API based Payroll integration with Ceridian Dayforce
description: This article describes the API based Payroll integration API
Author: Tulsi
ms.author: tulsijhaveri
ms.date: 09/15/2023
ms.topic: how-to
ms.custom: 
---

# API based Payroll integration with Ceridian Dayforce

The API based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce relies on several configuration steps that are described in this article. You must configure the integration in both Human Resources and Dayforce before you can process a pay run. 

## Environment Settings

Before using the Dynamics 365 Human Resources Payroll integration, you must set up the parameters described in this article. 

- Human Resources shared parameters:
    - **Positions** > enable **Require departments on positions**
    - **Payroll integration** > enable **Use payroll address purposes**
    - **Financial dimensions** > enable **Default financial dimensions**

-	Human Resources parameters
    - **Payroll Integration** > enable **Use identification Types in payroll processing**
    - **Payroll Integration** > Select appropriate **Identification type** for legal entity
    

-	In System administration, define financial dimension formats for data entities using **Financial dimension configuration for integrating applications** > **Data entities**

> [!NOTE]
> Human Resources parameters are unique to each legal entity. When using multiple legal entities, To expose the identification type ID in the payroll employee entity, you must configure human resources parameters for each company.
> Ensure that the financial dimension item(s) in the Selected list are in the correct order. The Connector will look at the financial dimension position that has been provided from the selected list in the Myintegration Portal.
> Collaborate with Ceridian to determine which Financial dimensions should be enabled to align with the Dayforce Site (location).

For more information, see [Configure Human Resources Parameters](https://dynamics.microsoft.com/human-resources/overview/).
![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/8fe8abab-0c24-4dfd-8110-ae2abd5dfae2)



## API Setup

To use the API, the [Virtual tables](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-payroll-api-introduction#virtual-tables-for-human-resources-in-dataverse) for the Human Resources entities must be generated for the environment.

## Enable features
Enable appropriate features in Feature Management to allow Microsoft APIs to be exposed to the integration and the data to pass to Dayforce:
- Navigate to: System Admin > Feature Management > All
- Enable:
    - (Preview) Payroll integration
    - Virtual table support for HR in Dataverse
    - Streamline Employee Entity
    - Benefits management
> [!NOTE]
> Features in feature management may run through its feature cycle and may be enanbled by default in due course.

## Virtual tables

Dynamics 365 Human Resources is a virtual data source in Microsoft Dataverse. It provides full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform. For more information on Dataverse Vitual tables, see [Configure Dataverse virtual tables](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

### [Install virtual tables](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities#install-the-dynamics-365-hr-virtual-table-app)
### [Generate virtual tables](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities#generate-virtual-tables)

Once the virtual tables are installed, you must generate the virtual tables for the data to pass to Dayforce. The Dayforce People Connector pulls data from the tables listed below, to ensure that Dayforce can execute a proper payroll. 
For additional information, please see [Enable Microsoft Dataverse virtual entities](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-virtual-entities).

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

The [change tracking](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems) feature in Microsoft Dataverse provides a way to keep the data synchronized in an efficient manner by detecting what data has changed since the data was initially extracted or last synchronized. This article discusses how to enable and retrieve changes for a table.

Navigate to: **System Admin** > **Data management** > **Data entities**. Search for the **target** entity. Turn on Tracking Changes as appropriate

## Add Dayforce Connector user in HR Environment

- Go to: System Administration > Manager User > New User
- Input appropriate info:
    - User ID
    - User Name
    - User Email
    - Role (Use the previously created API Dayforce Connector Role)

> [!NOTE]
> Please take note of the username and password. This information will be required for the setup of the MyIntegration portal in Ceridian Dayforce.

## Enable the Connection

> [!IMPORTANT] 
> Following section requires a user with full administrative security access to the Microsoft Dataverse and Azure Tenant. This also requires the user to have rights to consent on behalf of the company (Tenant) to allow this application access to the Microsoft Dynamics 365 HR APIs. 

To connect the Microsoft Dynamics 365 Human Resources environment to Ceridian's Dayforce Payroll, the following three steps will need to be completed:

1.	Add the Dayforce Payroll Connector application to the Tenant.
2.	Configure an API role for the Dataverse environment.

### Enable the Dayforce People Connector application on the Customer Tenant

Customer Microsoft tenant controls all activity in the customer’s Microsoft environment including, controlling security and access to all the Microsoft applications. Enabling the Dayforce People Connector on the tenant enables the connector to communicate with the necessary Microsoft applications used in this integration.

- Go to:  https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=6817703f-e5b3-4eec-b11f-ba6367f1b156&response_type=id_token&redirect_uri=https://developersdev.dayforce.com/Dev/Microsoft-to-Dayforce-Connector.aspx&scope=openid&response_mode=fragment&state=12345&nonce=678910
- Enable the URL for the company
  ![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/520495b3-fcab-41d0-a3bb-1e3032d3ae1c)

- Consent on behalf of your organization

### Connector in Dataverse

The Dayforce People Connector will need to be added to your specific Dataverse.

Go to:  Admin.powerplatform.microsoft.com > environment > Settings > Application Users > New User

- Add the Dayforce People Connector Application
- App ID: 6817703f-e5b3-4eec-b11f-ba6367f1b156
- Give the application the following security roles:
    - Basic User
    - Finance and Operations Basic User

For more information, see: 

[Authentication and authorization](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/authentication-and-authorization#security-roles-in-microsoft-power-platform)<br>
[Security roles and privileges](https://learn.microsoft.com/en-us/power-platform/admin/security-roles-privileges)<br>
[Configure user security](https://learn.microsoft.com/en-us/power-platform/admin/database-security#predefined-security-%20roles)<br>

### Add the Dayforce People Connector to the HR environment

In Human Resources go to: **Azure Active Directory Application** > **New**

- Add the following:
    - The CeridianDayforce Payroll Connector
    - Client ID: 6817703f-e5b3-4eec-b11f-ba6367f1b156
    - User ID: DFAPIConnector (Created previously)

![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/5fe3d568-c993-4447-b7ab-960fb082e236)

      
## Ready to Pay

> [!IMPORTANT]
> In order for employees to be integrated to Dayforce, they need to be enabled for Ready to pay. Employees not marked as ready to pay will not be picked up.

Ceridian’s Dayforce People Connector integration uses Microsoft’s [Ready to pay](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-compensation-payroll) feature to ensure that a complete, valid employee profile has been created prior to being picked up and processed.

