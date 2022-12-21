
# Customer Managed Keys (CMK)

[This article is pre-release documentation and is subject to change.]

CMK policy enforcement can be enabled for Finance and Operations environments where Power Platform Integration is enabled ([Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md)), for all environment specific resources (SQL DBs and Storage Account). Finance & Operations environments without Power Platform integration will continue to use the Microsoft Managed key to encrypt its data.

Please note Lockbox policy enforcement for Dynamics Lifecycle Management Service (LCS) metadata will be announced separately in future. All the data you store in LCS (File Assets, Methodologies, Task Recorder, and any other project metadata etc.), will not be part of this CMK policy enforcement. CMK support for LCS will be managed via LCS and will be announced separately in future.

## How to enable CMK for Finance and Operations environments:

1. Go to environment details page in LCS
1. If you have not setup Power Platform Integration then first please setup that using the instructions: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md). Please note, if you setup integration with existing power platform environment, it should not have CMK enabled on it before integration. (Support for this scenario will be enabled in future).
1. Once you have Power Platform integration setup, in the Power Platform Environment Information on the LCS environment details page, you will see Environment Name. This is the name of your Dataverse Organization. (Please note that name of your Finance and Operations environment might be different than your power platform integration environment, you will need the later for enabling CMK).
1. Go to Power platform admin portal and lookup your Power platform integration environment name.

> [!IMPORTANT]
>
> Follow the instructions from Private Preview July 2022 document to enable CMK on your power platform environment.

### CMK support in Finance and Operation Environment Add-Ins

A number of Add-Ins may be available in LCS for each Finance and Operations environment once the Power Platform integration has been enabled. Add-Ins that have some limitations for CMK are mentioned in the following table (if an Add-In is not in this list, then it supports the CMK policies).

|Add In  |Status  |
|--------|--------|
|Tax Calculation|Tax Calculation uses RCS which doesn’t support CMK policy enforcement as of now, support for this will be enabled in late 2023.|
|Electronic Invoicing|Electronic Invoicing uses RCS which doesn’t support CMK policy enforcement as of now, support for this will be enabled in late 2023.|
|||

### CMK support across Finance and Operations Offers / Applications

Not all applications among Finance and Operations support CMK policies in the preview to the full extent yet. Find more details for individual applications below:

|Offer|Application Status|
|-----|------------------|
|Dynamics 365 Supply Chain Management|Finance and Operations environment provisioned under Dynamics 365 Supply Chain Management offering supports CMK policy enforcement for all environment specific resources.|
|Dynamics 365 Human Resources|Dynamics 365 Human Resources provisioned via Finance and Operations environment will support CMK policy enforcement for all environment specific resources.<br/><br/>Dynamics 365 Human Resources Standalone offering is not CMK compliant; these customers will have to use migration tooling to migrate their environments to Finance and Operations environment and then they can use the CMK policy enforcement.|
|Dynamics 365 Finance|Finance and Operations environment provisioned under Dynamics 365 Finance offering supports CMK policy enforcement for all environment specific resources.<br/><br/>If you use [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) to compliment your Dynamics 365 Finance environment then please note that data managed under RCS environment, currently doesn’t support CMK policy enforcement. CMK support for RCS will be enabled in late 2023.|
|||
