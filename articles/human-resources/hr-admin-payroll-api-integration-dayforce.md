---
# required metadata

title: API-based payroll integration with Ceridian Dayforce
description: This article describes the API-based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce.
author: TulsiJhaveri 
ms.author: tulsijhaveri
ms.date: 09/15/2023
ms.topic: how-to
ms.custom: 

---

# API-based payroll integration with Ceridian Dayforce

This article describes the configuration steps that are required for API-based payroll integration between Microsoft Dynamics 365 Human Resources and Ceridian Dayforce. You must configure the integration in both Human Resources and Dayforce before you can process a pay run.

## Environment settings

Before you use the Human Resources payroll integration, set up the following parameters:

- On the **Human Resources shared parameters** page:

    - On the **Positions** tab, select **Require departments on positions**.
    - On the **Payroll integration** tab, select **Use payroll address purposes**.
    - On the **Financial dimensions** tab, select **Default financial dimensions**.

- On the **Human Resources parameters** page:

    - On the **Payroll integration** tab, select **Use identification types in payroll processing**.
    - On the **Payroll integration** tab, in the **Identification type** field, select the appropriate identification type for the legal entity.

- In **System administration**, go to **Financial dimension configuration for integrating applications** \> **Data entities**, and define financial dimension formats for data entities.

> [!NOTE]
> Human Resources parameters are unique to each legal entity. If you use multiple legal entities, you must configure Human Resources parameters for each one.
>
> Ensure that the financial dimension items in the selected list are in the correct order. The connector looks at the financial dimension position that has been provided from the selected list in the MyIntegration portal.
>
> Work with Ceridian to determine which financial dimensions should be enabled for alignment with the Dayforce site (location).

For more information, see [Configure Human resources parameters](hr-setup-parameters.md).

## API setup

Before you can use the API, the virtual tables must be generated. For more information, see [Virtual tables for Human Resources in Dataverse](hr-admin-integration-payroll-api-introduction.md#virtual-tables-for-human-resources-in-dataverse).

>[!NOTE]
>For the payroll integration to work for customers using the mshr entities, the row version change tracking must be disabled. To disable row version change tracking, reach out to Microsoft support to enable the DMFDisableSqlRowVersionCtForCDSVirtualEntity flight. Enabling this flight will disable row version change tracking.


## Enable features

You must enable features in Feature management to enable Microsoft APIs to be exposed to the integration and the data to be passed to Dayforce.

1. Go to **System administration** \> **Feature management** \> **All**.
2. Enable the following features:

    - (Preview) Payroll integration
    - Virtual table support for HR in Dataverse
    - Streamline employee entity
    - Benefits management

> [!NOTE]
> Features in Feature management might be enabled by default.

## Virtual tables

Human Resources is a virtual data source in Dataverse. It provides full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform. For more information about Dataverse virtual tables, see [Configure Dataverse virtual tables](hr-admin-integration-common-data-service-virtual-entities.md).

For more information about how to install virtual tables, see [Install the Dynamics 365 HR Virtual Table app](hr-admin-integration-common-data-service-virtual-entities.md#install-the-dynamics-365-hr-virtual-table-app) and 
[Generate virtual tables](hr-admin-integration-common-data-service-virtual-entities.md#generate-virtual-tables).

After the virtual tables are installed, generate the virtual tables for the data to pass to Dayforce. The Dayforce people connector pulls data from the following tables at **Dataverse integration** \> **Virtual tables** to ensure that Dayforce can process payroll. For more information, see [Enable Microsoft Dataverse virtual entities](../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

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
- HcmJobFamilyEntity
- HcmJobFunctionEntity
- HcmJobTypeEntity
- HcmLaborUnionAgreementEntity
- HcmLaborUnionEntity
- HcmPayRateConversionEntity
- HcmPersonIdentificationNumberEntity
- HcmPersonLaborUnionEntity
- HcmPositionDefaultDimensionEntity
- HcmPositionDetailEntity
- HcmPositionEntity
- HcmPositionHierarchyEntity
- HcmPositionTypeEntity
- HcmPositionUnionAgreementEntity
- HcmPositionV2Entity
- HcmPositionWorkerAssignmentV2Entity
- HcmReasonCodeEntity
- HcmUnionsEntity
- HcmWorkerBankAccountEntity
- HcmWorkerBaseEntity
- HcmWorkerContactEntity
- HcmWorkerEntity
- HcmWorkerPayrollInfoEntity
- Hcmworkerpostaladdressv2entity
- HcmWorkerSummaryEntity
- OMCostCenterEntity
- OMDepartmentV2Entity
- OMLegalEntity
- OmLegalEntityContactEntity
- PayrollBankAccountDisbursementEntity
- PayrollEmployeeEntity
- PayrollEmployeeV2Entity
- PayrollFixedCompensationPlanEntity
- PayrollPositionDetailsEntity
- PayrollPositionEntity
- PayrollPositionJobEntity
- PayrollPositionWorkerDefaultTaxRgnEntity
- PayrollWorkerAddressCurrentEntity
- PayrollVariableCompensationAwardEntity
- HcmVariableCompensationAwardEntity

### Track changes

The change tracking feature in Dataverse detects data that has changed since the data was originally extracted or last synced. For more information, see [Use change tracking to synchronize data with external systems](/power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems).

To enable change tracking, follow these steps.

1. Go to **System administration** \> **Data management** \> **Data entities**.
2. Search for the **target** entity.
3. Turn on **Track changes**.


Turn on **Track changes** as appropriate, for the following:

| **Target entity**|**Change tracking** |
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
| HcmEmploymentV2Entity | Al ltables |
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
| PayrollBankAccountDisbursementEntity | Primar ytable |
| PayrollEmployeeEntity | Primary table |
| PayrollFixedCompensationPlanEntity | All tables |
| PayrollPositionDetailsEntity | All tables |
| PayrollPositionEntity | All tables |
| PayrollPositionJobEntity | All tables |
| PayrollWorkerAddressCurrentEntity | All tables |

Turn on Tracking Changes, as appropriate, for the following:

| **Target**** Entity **|** Change ****Tracking** |
| --- | --- |
| DirPersonNameHistoricalEntity | Alltables |
| HcmCompFixedEmplEntity | Alltables |
| HcmCompFixedPlanTableEntity | Alltables |
| HcmCompVarPlanTableEntity | Alltables |
| HcmEmployeeEntity | Alltables |
| HcmEmployeeV2Entity | Alltables |
| HcmEmploymentDetailEntity | Alltables |
| HcmEmploymentEmployeeEntity | Alltables |
| HcmEmploymentEntity | Alltables |
| HcmEmploymentTypeEntity | Alltables |
| HcmEmploymentV2Entity | Alltables |
| HcmIdentificationTypeEntity | Alltables |
| HcmJobBaseEntity | Alltables |
| HcmJobCompensationEntity | Alltables |
| HcmJobDetailEntity | Alltables |
| HcmJobEntity | Primarytable |
| HcmJobFamilyEntity | Alltables |
| HcmJobFunctionEntity | Alltables |
| HcmJobTaskEntity | Alltables |
| HcmJobTypeEntity | Alltables |
| HcmLaborUnionEntity | Alltables |
| HcmPersonDetailsEntity | Alltables |
| HcmPersonIdentificationNumberEntity | Alltables |
| HcmPositionBaseEntity | Alltables |
| HcmPositionDefaultDimensionEntity | Alltables |
| HcmPositionDetailEntity | Alltables |
| HcmPositionEntity | Primarytable |
| HcmPositionHierarchyEntity | Alltables |
| HcmPositionHierarchyTypeEntity | Alltables |
| HcmPositionTypeEntity | Alltables |
| hcmPositionUnionAgreementEntity | Alltables |
| HcmPositionV2Entity | Alltables |
| HcmPositionWorkerAssignmentEntity | Primarytable |
| HcmPositionWorkerAssignmentV2Entity | Primarytable |
| HcmUnionsEntity | Alltables |
| HcmVariableCompensationTypeEntity | Alltables |
| HcmWorkerBankAccountEntity | Alltables |
| HcmWorkerBaseEntity | Custom |
| HcmWorkerEntity | Custom |
| HcmWorkerPayrollInfoEntity | Alltables |
| PayrollBankAccountDisbursementEntity | Primarytable |
| PayrollEmployeeEntity | Primarytable |
| PayrollFixedCompensationPlanEntity | Alltables |
| PayrollPositionDetailsEntity | Alltables |
| PayrollPositionEntity | Alltables |
| PayrollPositionJobEntity | Alltables |
| PayrollWorkerAddressCurrentEntity | Alltables |
## Add a Dayforce Connector user in the Human Resources environment

1. Go to **System administration** \> **Manager user**, and select **New user**.
2. Enter values in the **User ID**, **User name**, **User email**, and **Role** fields. (Use the previously created API Dayforce Connector role).

> [!NOTE]
> The user name and password are required for the setup of the MyIntegration portal in Dayforce.

## Enable the connection

> [!IMPORTANT]
> This section requires a user who has full administrative security access to the Dataverse and Azure tenant. The user must also have the right to give consent on behalf of the company (tenant) to allow access to the Human Resources APIs.

To connect the Human Resources environment to Dayforce payroll, follow these steps.

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
