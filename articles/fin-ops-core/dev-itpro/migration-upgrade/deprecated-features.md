---
# required metadata

title: Removed or deprecated features in previous releases
description: This article describes features that have been removed, or that were planned for removal from Dynamics 365 for Finance and Operations and previous releases.
author: sericks007
ms.date: 02/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 31019808-4cbf-47d7-b1ba-d791db4281ae
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28 
ms.dyn365.ops.version: AX 7.0.0 

---

# Removed or deprecated features in previous releases

[!include [banner](../includes/banner.md)]



> [!IMPORTANT]
> This article is no longer updated. To see a current list of features that have been removed or deprecated from Finance and Operations apps, search for **"Removed or deprecated features"** content that relates to the app you're using.

This article describes features that have been removed or deprecated from Dynamics 365 for Finance and Operations and previous releases of that product.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Finance 10.0.7 with Platform update 31

### Chinese voucher types without Account groups selection
|&nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Changed to the feature with account groups selection. |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2020, we plan to no longer support Chinese voucher types setup without Account groups selection. Find more details about new feature design in What's new in 10.0.7 |

## Finance and Operations 10.0.6 with Platform update 30


### DimensionHash.getHash(str _message)

|&nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Windows is deprecating the use of SHA1, as documented in [Windows Enforcement of SHA1 Certificates](https://social.technet.microsoft.com/wiki/contents/articles/32288.windows-enforcement-of-sha1-certificates.aspx).  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By April 1, 2020, developers must use the platform APIs found in the class **HasFunction**. |

### Hash.ComputeSHA1Hash(string message)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Windows is deprecating the use of SHA1, as documented in [Windows Enforcement of SHA1 Certificates](https://social.technet.microsoft.com/wiki/contents/articles/32288.windows-enforcement-of-sha1-certificates.aspx).  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Platform |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By April 1, 2020, developers  must use the platform APIs found in the class **HasFunction**. |


### FormDateTimeControl.setUtcString()

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We are retiring the **setUtcString()** method, because a better replacement method is available. |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Platform |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, we plan to no longer support the **setUtcString()** method. Developers should be using the **setUtcDateTime()** method instead. |

### Blocklist report (IT) – Feature reference IT-00001

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Not legally required. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Italian localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, we plan to no longer support this report. |

### Domestic tax report – Feature reference IT-00003

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Not legally required. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Italian localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, we plan to no longer support the **Domestic tax report – Feature reference IT-00003**. |

## October 2019 deprecation announcement

### Flowchart diagrams in Business process modeler

<table>
<tbody>
<tr>
<td><strong>Reason for deprecation/removal</strong></td>
<td>We are deprecating the flowchart diagrams component in Business process modeler (BPM), because the legacy design caused low usage.</td>
</tr>
<tr>
<td><strong>Replaced by another feature?</strong></td>
<td>No</td>
</tr>
<tr>
<td><strong>Areas affected</strong></td>
<td>Business process modeler</td>
</tr>
<tr>
<td><strong>Status</strong></td>
<td>Deprecated: The flowchart diagrams component in BPM is expected to be removed in 2020. The following functionality will be unavailable:
<ul>
<li>All flowcharts will be read-only and unavailable for editing. The shape properties that are associated with flowchart activities will also be unavailable. These flowcharts include both the default flowcharts that are automatically generated and customized flowcharts that are modified based on those default flowcharts.</li>
<li>The process steps will be read-only and unavailable for editing.</li>     
<li>The legacy fit/gap analysis feature will be unavailable. Therefore, no gap list will be automatically created or available for export.
<p><strong>Note:</strong> This feature had previously been deprecated and replaced by Microsoft Azure DevOps integrations.</p>
</li>
<li>The version history of the flowchart will be unavailable.</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Finance and Operations 10.0.5 with Platform update 29

### US Payroll tax updates

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We are retiring tax updates for the US Payroll functionality due to low usage and enhanced functionality that is now offered via strategic integrations.  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Payroll |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By July 31, 2024, we plan to no longer provide tax updates to US Payroll customers. The functionality will remain in the product, but enhancements will no longer keep the functionality up to date, and any product defects will be evaluated on a case-by-case basis. |

>[!NOTE]
> This represents a change from the original discontinuation date of October 1, 2021. For more information, see [Tax updates being retired for US Payroll feature in Microsoft Dynamics 365 for Finance and Operations](https://aka.ms/financepayrollfaq).


### Data management staging clean up
|&nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Does not meet the core requirements that are needed for scheduling periodic cleanup. |
| **Replaced by another feature?**   | Yes, the Job history cleanup feature is being added to meet the scenarios holistically. |
| **Product areas affected**         | Data management |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is December 2020. |

## Finance and Operations 10.0.4 with Platform update 28

### France: FEC Accounting data export in XML

|  &nbsp; |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by TXT format, **French FEC audit file** is available through **General ledger** \> **Periodic tasks** \> **Data export**.
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | General ledger |
| **Deployment option**              | All |
| **Status**                         | Deprecated. Target timeframe for the functionality to be removed is July 2020. |


### Legacy navigation bar

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Header alignment with other Dynamics and Office products. For more details, see [Updated navigation bar that aligns with the Office header](/business-applications-release-notes/April19/dynamics365-finance-operations/updatednavbar).
| **Replaced by another feature?**   | Starting in Platform update 24, a restyled navigation bar that features search was introduced. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, the legacy navigation bar will no longer be available. Until that point, customers can revert to the legacy navigation bar through the **Client performance options** page. |


## Finance and Operations 10.0.2 with Platform update 26


### Legacy default action behavior

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The legacy behavior for default actions in grids results in an unexpected column having the default action link after grid columns have been reordered via personalization. The new sticky default action feature corrects this. For more details, see [Sticky default actions in grids](/business-applications-release-notes/October18/dynamics365-finance-operations/sticky-default-action). |
| **Replaced by another feature?**   | Starting in Platform update 21, a feature for "sticky default actions" was introduced. This feature can be enabled on the **Client performance options** page. |
| **Product areas affected**         | Grids in the web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, sticky default actions will be the default behavior, without a mechanism to revert to the legacy behavior. |

### Legacy "is one of" filtering experience

|&nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The "is one of" filtering experience went through a redesign in Platform update 22,with the plan for this to eventually be the only "is one of" filtering experience. |
| **Replaced by another feature?**   | Starting in Platform update 22, an improved "is one of" filtering experience became available on the **Client performance options** page. For more information, see [Optimized is one of filtering experience](/business-applications-release-notes/October18/dynamics365-finance-operations/improved-isoneof-filtering). |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, the improved "is one of" experience will be the default behavior, without a mechanism to revert to the legacy behavior. |

### Parameter to enable sales orders with multiple project contract funding sources
Support for creating project-based sales orders where the project contract has multiple funding sources is enabled with the **Project management parameters** setting **Allow sales orders for project with multiple funding sources**. By default, this parameter is not enabled. 

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The functionality will always be enabled after the parameter is removed. |
| **Replaced by another feature?**   | No. The functionality to support project-based sales orders with multiple funding sources will always be enabled.   |
| **Product areas affected**         |The **Allow sales orders for projects with multiple funding sources** parameter will be removed. The following methods will be modified when the parameter is removed: **ctrlSalesOrderTable** method in **ProjStatusType** class, **validate** method for **ProjId** field, and **run** method in **SalescreateOrder** form. The following methods will be deprecated when the parameter is removed: **IsSalesOrderAllowedForMultipleFundingSources** in **ProjTable** table file, **IsAllowSalesOrdersForMultipleFundingSourcesParamEnabled** method in **ProjTable** table file, **AllowSalesOrdersForMultipleFundingSources** data field in **ProjParameters** form and **ProjParameterEntity** files, **IsAssociatedToMultipleFundingSourcesContract** private method in **ProjTable** table file. |
| **Deployment option**              | All  |
| **Status**                         | Deprecation is planned for the April 2020 release wave. |

### Legacy workflow reports for tracking and instance status

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The legacy workflow reports for tracking and instance status are being deprecated because they are no longer referenced from the navigation. The report names are WorkflowWorkflowInstanceByStatusReport and WorkflowWorkflowTrackingReport. |
| **Replaced by another feature?**   | The workflow history form can be used instead. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is April 2020. |

## Finance and Operations 10.0.1 with Platform update 25

### Deprecated APIs and potential breaking changes


#### Deriving from internal classes is deprecated

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Before Platform update 25, it was possible to create a class or table that derives from an internal class/table that is defined in another package/module. This is not a safe coding practice. As of Platform update 25, the compiler will display a warning. |
| **Replaced by another feature?**   | The compiler warning will be replaced by an error in Platform update 26. This change is backward compatible at runtime, which means that Platform update 25 or newer can be deployed on any sandbox or production environment without the need to modify custom code. This change only affects development and compile time.|
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning will become a compilation error in Platform update 26. |

#### Overriding internal methods is deprecated

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Before Platform update 25, it was possible to override an internal method in a derived class that is defined in another package/module. This is not a safe coding practice. As of Platform update 25, the compiler will display a warning. |
| **Replaced by another feature?**   | This warning will be replaced by a compile error in Platform update 26. This change is backward compatible at runtime, which means that Platform update 25 or newer can be deployed on any sandbox or production environment without the need to modify custom code. This change only affects development and compile time. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning will become a compilation error in Platform update 26. |

## Finance and Operations 10.0.0 with Platform update 24

### Renaming released products 
| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | When you use the **Rename primary key** function to change the ItemId of a released product, only direct foreign key references are updated. Any other references to the released product, such as from production orders, will retain the old ItemId. As a result, there could be inconsistent data that will eventually block business processes. |
| **Replaced by another feature?**   | No. |
| **Product areas affected**         | Product information management |
| **Deployment option**              | All  |
| **Status**                         | Removed as of Finance and Operations 10.0.0 with Platform update 24.|


## Finance and Operations 8.1.3 with Platform update 23

### SQL Server Reporting Services ReportViewer Control
Customers can use the **Export** action provided by the embedded SQL Server Reporting Services (SSRS) ReportViewer control to download documents produced by Finance and Operations applications. This HTML-based presentation of the report offers users a non-paginated preview of the document.

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The non-paginated nature of the HTML-based preview experience does **not** deliver fidelity with the physical documents ultimately produced by Finance and Operations. By fully embracing PDF as the standard format for business documents, users are able to take advantage of a modern viewing experience with improved performance when producing application reports. |
| **Replaced by another feature?**   | Going forward, PDF documents will be the default format for reports rendered by Finance and Operations.   |
| **Product areas affected**         | This change does **not** impact customer scenarios where reports are distributed electronically or sent directly to printers.    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: A removal date has not been set for this feature. The functionality to automatically preview application reports using an embedded PDF viewer is planned for the May 2019 Platform update. |

### Client KPI controls
Embedded key performance indicators (KPIs) could be modeled in Visual Studio by a developer and further customized by the end user.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The native client controls used to define KPIs have low customer uptake and rely on a developer to add trackable metrics. |
| **Replaced by another feature?**   | PowerBI.com service delivers world-class tooling for defining and managing KPIs based on data from external sources.  In an upcoming release, we plan to enable you to embed solutions hosted on PowerBI.com in application workspaces.   |
| **Product areas affected**         | This update will prevent developers from introducing new KPI controls in Visual Studio designer.    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Deprecated APIs and future breaking changes

#### Field groups containing invalid field references

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | It is possible for table metadata definitions to have field groups containing invalid field references. If deployed, this can cause runtime failures in Financial Reporting and SQL Server Reporting Services (SSRS). This issue is currently categorized as a *compiler warning* rather than an *error*, meaning that the deployable package creation and deployment can proceed without fixing the issue. To fix this issue:<br><br>1. Remove the invalid field reference from the table field group definition.<br><br>2. Recompile.<br><br>3. Ensure any warnings or errors are addressed. |
| **Replaced by another feature?**   | This warning will be replaced by a compile error in the future. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning is a compile-time error with platform updates for version 10.0.11 of Finance and Operations apps. |

#### Complete list
To access the full list of APIs that are being deprecated, see [Deprecation of methods and metadata elements](deprecation-deletion-apis.md).

## Finance and Operations 8.1 with Platform update 20

### Batch transfer rules for subledger journal account entries
The Synchronous transfer mode is being deprecated in the General ledger parameters.  This mode is replaced by Asynchronous and scheduled batch only, which already exist as options for transfer. For additional information, see the [General Ledger Parameters – Batch transfer rules](https://community.dynamics.com/365/financeandoperations/b/financials/archive/2019/03/15/general-ledger-parameters-batch-transfer-rules) blog.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | We are removing the synchronous option due to performance impact to the system. |
| **Replaced by another feature?**   | Asynchronous and scheduled batch are options to use in place of Synchronous.   |
| **Product areas affected**         | General Ledger, Accounts payable, Accounts Receivable, Procurement, Expense    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is the 10.0 version.|

### Electronic reporting for Russia
Feature for configuring .txt and .xml file formats of declarations. 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with Electronic reporting. |
| **Replaced by another feature?**   | Yes. |
| **Product areas affected**         | General Ledger |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Financial reports generator for Russia
A tool for setting up data collection for accounting and tax reports, and to export data to XLS and DOC report templates. Functional parts: Export data to XLS and DOC report templates, queries, fixed requisites are removed. 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Removed parts are replaced with Electronic reporting. |
| **Replaced by another feature?**   | Yes. Financial reports setup user interface should be used for setting up data collection rules by GL accounts or tax registers. Export data to various file types, fixed requisites and query-like data collection rules should be configured in Electronic reporting. |
| **Product areas affected**         | General ledger. |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Integration with external providers for sending electronic reporting through communication channels for Russia
Feature exporting generated electronic files of declarations to folder for further sending to official providers of electronic reporting as well as importing state back.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with electronic messages configurable feature. |
| **Replaced by another feature?**   | Yes.  |
| **Product areas affected**         | General Ledger, Tax |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |


### Profit tax register wizard
Feature for creating templates for new profit tax registers. This feature creates X++ objects for new registers, which are then  created as templates with the appropriate calculation logic added in.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Feature is not compatible with the Finance and Operations extensibility model. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Tax |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Payroll and Human Resources for Russia
Russian country specific module for managing staff administration information, timesheet details for employees, payroll accounting, and creating pay statements. 

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Payroll is not included in the global strategic focus of the Dynamics 365 portfolio. Partners and ISVs are best positioned to provide payroll functionality that is compliant with local regulations and tax updates.|
| **Replaced by another feature?**   | No|
| **Product areas affected**         | Russian Payroll and Human Resources Management |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is one of future updates of the 10.0 version. |

## Finance and Operations 8.0 with Platform update 15
No features have been removed or deprecated with this release. Platform update 15 is cumulative and contains new or changed features from Platform update 13, Platform update 14, and Platform update 15.

## Finance and Operations, Enterprise edition 7.3 with Platform update 12

### Personalized product recommendations 
Starting February 15, 2018, retailers will no longer be able to display personalized product recommendations on a point of sale (POS) device. For more information, see [Product recommendations overview](../../../commerce/product-recommendations.md).  

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | We are removing the current version of the product recommendation service as we redesign this feature with a better algorithm and newer retail-oriented capabilities.  |
| **Replaced by another feature?**   | No. However, after Spring 2018, we plan to bring back this feature to leverage a new recommendation service.   |
| **Product areas affected**         | Personalized product recommendations in POS.                                                    |
| **Deployment option**              | All                                                                                      |
| **Status**                         |Removed as of February 15, 2018. This affects customers running Dynamics 365 for Operations 1611 and later.  |

### Extension of the list of Electronic reporting (ER) functions
The possibility to introduce custom functions to be used in the ER expression builder (for more information, see [Extend the list of Electronic reporting (ER) functions](../../dev-itpro/analytics/general-electronic-reporting-formulas-list-extension.md)) is not supported any more. Due to changes of the ER APIs, the API to call built-in functions from the ER expression builder became internal and can’t be extended any longer.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Code sealing initiative  |
| **Replaced by another feature?**   | None. Whenever a new built-in function is needed, a new extension request must be addressed to the ER framework team.<br><br>As a temporary work around while the requested function is under development by the ER team, the required logic can be programmed as a method of a custom application class. This method can be accessed in an ER expression as a property of the added ER data source of the **Application\Class** type that refers to that custom application class.  |
| **Product areas affected**         | Electronic reporting framework                                                      |
| **Deployment option**              | All                                                                                      |
| **Status**                         | Removed as of Finance and Operations, Enterprise edition 7.3.    |

### Inventory by item group and Inventory by inventory dimension aging reports

These two reports are no longer supported in Finance and Operations. Instead, the **Inventory aging** report can be used to improve the user experience.

| &nbsp;  | &nbsp; |
|--------------|-----------------------|
| **Reason for deprecation**       | Duplicate functionality  |
| **Replaced by another feature?** | Yes. The two reports have been replaced by the **Inventory aging** report.     |
| **Product areas affected**       | Inventory management, Cost management        |
| **Deployment option**        | All|
| **Status**                       | Deprecated: The menu items for the two reports have been removed in version 7.3. However, the code for the reports remains in the product. The plan is to remove the code in a future release. |

### Power BI content packs available on AppSource
The **Cost management**, **Financial performance**, and **Retail channel performance** content packs, available on the [Microsoft AppSource](https://appsource.microsoft.com) site, are deprecated as a consequence of product updates in Microsoft Power BI. System administration forms used to deploy these content packs to PowerBI.com are also being deprecated in Finance and Operations.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Product updates in Microsoft Power BI. |
| **Replaced by another feature?**   | The **Cost management**, **Financial performance**, and **Retail channel performance** content packs, available on the [AppSource](https://appsource.microsoft.com) site, are being replaced by analytical applications which allow for solution integrations at the database level. For more information about analytical applications, see [Embedded Power BI in workspaces](../../dev-itpro/analytics/embed-power-bi-workspaces.md).    |
| **Product areas affected**         | Cost management, Finance, and Retail                                                                                               |
| **Deployment option**              | Cloud only (Integration with PowerBI.com is not supported in on-premises deployments.)                                                                                                            |
| **Status**                         | Deprecated: Target timeframe for the functionality removal is Q2 2018.    |

### Standard UI in data management workspace

The standard UI in data management is the legacy UI, which is the default UI presented to the users when they visit the data management workspace.

| &nbsp;  | &nbsp; |
|------------------|-------------------------|
| **Reason for deprecation/removal** | We are investing in providing new user experiences in the new UI.             |
| **Replaced by another feature?**   | The new UI called *Enhanced views* is replacing the old UI.            |
| **Product areas affected**         | Data management workspace                                                     |
| **Deployment option**              | All                                                                           |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is Q2 2018. |

### Excise, Sales Tax, Service Tax for India

These taxes have been subsumed into Indian GST.

|  &nbsp;                                           |      &nbsp;                                                                   |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | These taxes have been subsumed into Indian GST.                          |
| **Replaced by another feature?**            | Indian GST                                                              |
| **Product areas affected**                  | Tax                                                                     |
| **Deployment option**                       | All modules                                                   |
| **Status**                                  | Deprecated: A removal date has not been set for this feature. |    

### File Validation Utility (FVU) for India

|              &nbsp;                               |      &nbsp;                                                                   |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.   |        

### TDS/TCS certificate for India

Users can download this from the government portal.

|             &nbsp;                                |    &nbsp;                                                                     |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                   |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.     |    

### Export/import (EXIM) incentive scheme for India


|              &nbsp;                               |        &nbsp;                                                                 |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Import and export                                                       |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.  |    


## Dynamics 365 for Retail 7.2

### Personalized product recommendations 
Starting February 15, 2018, retailers will no longer be able to display personalized product recommendations on a point of sale (POS) device. For more information, see [Product recommendations overview](../../../commerce/product-recommendations.md).  

|  &nbsp; |  &nbsp;|
|------------|--------------------|
| **Reason for deprecation/removal** | We are removing the current version of the product recommendation service as we redesign this feature with a better algorithm and newer retail-oriented capabilities.  |
| **Replaced by another feature?**   | No. However, after Spring 2018, we plan to bring back this feature to leverage a new recommendation service.   |
| **Product areas affected**         | Personalized product recommendations in POS.                                                    |
| **Deployment option**              | All                                                                                      |
| **Status**                         |Removed as of February 15, 2018. This affects customers running Dynamics 365 for Retail 7.2  and later. |


## Finance and Operations, Enterprise edition July 2017 with Platform update 8

### Currency conversion for accounting and reporting currencies

Currency conversion for accounting and reporting currencies was introduced when the euro was introduced.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage and addition of the Copy legal entity functionality as a replacement.      |
| **Replaced by another feature?**   | No, but the Copy legal entity and Configurations features were added to make it easier to move to a company that has changing core requirements. |
| **Product areas affected**         | Financial management     |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |


### Warehouse mobile devices portal

Warehouse mobile devices portal (WMDP) was a standalone component that was intended for on-premises self-deployment. This component is no longer supported in Finance and Operations. A native app that improves the user experience has replaced the functionality of WMDP.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality.       |
| **Replaced by another feature?**   | Yes. This feature has been replaced by Finance and Operations - Warehousing. For more information about setup and prerequisites, see [Install and configure the Warehousing app overview](../../../supply-chain/warehousing/install-configure-warehousing-app.md). |
| **Product areas affected**         | Warehouse management, Transportation management     |
| **Deployment option**              | Warehouse mobile devices portal (WMDP) was a standalone component that was intended for on-premises self-deployment.               |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is Q4 2019.   |

### Advanced bank reconciliation matching rule for manual matching

A matching rule was used to select and mark a bank document when documents were manually matched in the reconciliation worksheet.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage.                                                                         |
| **Replaced by another feature?**   | No. Column filtering capabilities should be used to find documents for reconciliation. |
| **Product areas affected**         | Cash and bank management                                                               |
| **Deployment option**              | All                                                                                    |
| **Status**                         | Removed as of July 2017.                                                               |

## Dynamics 365 for Operations 1611 with Platform update 3

### AEB payment formats for Spain

The Consejo Superior Bancario payment formats were used to send remittance files to the bank for customer payments and vendor payments. The content of these formats was determined by the Asociación Española de Banca. It covers Cuaderno 19, 32, 58, 34.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                  |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer and Direct debit payment formats for Spain |
| **Product areas affected**         | Accounts payable, Accounts receivable                                    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.           |

### Bank payments transfer for Lithuania

Bank payment transfers were generated and printed by using the Payment transfer (LT) export format for Lithuania. The Lithuanian market began to use LITAS, the unified electronic banking system, in 2005.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Lithuania     |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### BBS Direkte Remittering payment formats for Norway

BBS Direkte Remittering payment formats include customer payment collection export (direct debit) and return message import.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.  |
| **Replaced by another feature?**   | The AvtaleGiro customer payment format for Norway can be used to generate direct debit messages. Return message import will be implemented in future releases. |
| **Product areas affected**         | Accounts payable, Accounts receivable   |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                                                                                                 |

### Chart of Accounts tool for Spain

This tool is used when a chart of accounts in Spain requires major changes. Users can import a new chart of accounts in Microsoft Excel or text format, and can also import financial statements.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Dom80 payment format for Belgium

Legacy Belgian payment format for payment collection (direct debit).

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Belgium         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### DTA/EZAG payment formats for Switzerland

DTA/EZAG formats are integrated into the ESR system, because they can carry on the reference number. Because the reference number isn’t mandatory, these formats can be used to process any vendor payments. These formats are used by companies that have a bank account in a location other than “Postfinance.”

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Switzerland   |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### EDIFACT-DIRDEB payment format for Austria

EDIFACT-DIRDEB payment format for payment collection (direct debit).

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Austria         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### EDIVAT for Belgium

EDIVAT is an obsolete Belgian standard for electronic declaration via secure mail. Dynamics AX 2012 retains the read-only solution to enable access to the historical data.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The functionality is no longer used.                           |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### eGiro EDIFACT CREMUL payment import format for Norway

eGiro is based on the international UN EDIFACT CREMUL (Multiple Credit Advice Message) standard that is used for automatic posting of customer payments. In Dynamics AX, eGiro is implemented as a customer payment import format.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 notification import. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### External inventory for Poland

Evidence of goods that are taken from a vendor for sales without purchase. Goods that are handled in external inventory don’t affect standard inventory, and can be sold and then purchased automatically. This process creates real inventory movements.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                    |
| **Replaced by another feature?**   | Yes, the core Inbound consignment functionality                |
| **Product areas affected**         | Accounts payable, Inventory management                         |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Financial reports generator for Eastern Europe

A tool is used to set up data collection for accounting and tax reports, and to export data to XLS and DOC report templates.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                                            |
| **Replaced by another feature?**   | No. The tool will be replaced by Electronic reporting configurations in future releases. |
| **Product areas affected**         | General Ledger                                                                           |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### Import of customer payment transactions for Finland

You can select an import format for Finnish payments to import customer payment transactions from an external file that the bank provides.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 notification import. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### Import of payment transactions into a general ledger journal for Finland

A format that is specific to Finland is used to import accounting transactions into the general ledger.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.053 bank statement import using Advanced Bank Reconciliation. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### Integration with Isabel synchronized (CIS) for Belgium

Isabel is the framework for electronic banking in Europe and is a de-facto standard in Belgium.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Integration with Isabel client has been discontinued.   |
| **Replaced by another feature?**   | No. The payment formats that are no longer used are replaced by ISO20022 Credit transfer payment format for Belgium. |
| **Product areas affected**         | Accounts payable     |
| **Status**                         | Deprecated: A removal date has not been set for this feature.    |

### Modifications in the chart of accounts and accounting rules for Spain

This feature is used for changes in the chart of accounts and accounting rules in Spain. It maps accounts to help transform the old chart of accounts into the new chart of accounts, and compares the previous fiscal year with the new fiscal year, even if they were posted to different account numbers.

|  &nbsp; |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Pagamento Fornittori vendor payment format

Legacy Italian payment format for credit transfers.

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Italy         |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Payment export formats for Estonia

The Telehansa and Teleservice formats are used for bank payment export.

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Estonia       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Payment file archive for Norway

When payment files are generated, the file archive automatically archives all files that are created, even files that were previously written or read.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                        |
| **Replaced by another feature?**   | Yes, Electronic reporting archived jobs                            |
| **Product areas affected**         | Accounts payable, Accounts receivable, Organization administration |
| **Status**                         | Deprecated: A removal date has not been set for this feature.     |

### Payment import formats for Estonia

The Telehansa and TeleTeenus formats are used for bank payment import.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                                    |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 bank notification import. |
| **Product areas affected**         | Accounts receivable                                                                        |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                             |

### Payroll information in Human Resources

Human Resources Payroll information

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by core Payroll and Human Resources pages.  |
| **Replaced by another feature?**   | **Benefits**, **Earnings**, and other related pages that were previously in US Payroll have been reconfigured, and are now part of the core Human Resources configuration to help support external payroll processing. This functionality is accessed by using the **Human Resources 1** \> **Payroll** configuration key. |
| **Product areas affected**         | Human Resources, Payroll   |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.    |

### Performance management goal workflow

Performance management includes goal management and integration with performance reviews.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance management was redesigned, and the number of goal pages was reduced to simplify the process.                 |
| **Replaced by another feature?**   | No. Goals are visible to managers through the Manager Self Service portal, and can be changed and viewed by the manager. |
| **Product areas affected**         | Human capital management       |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.    |

### Postgirot and Postgirot Utland payment formats for Sweden

Postgirot and Postgirot Utland payment formats for Sweden.

|&nbsp;   |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Sweden        |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Radio frequency identifier

Radio Frequency Identification (RFID) is a data-collection technology that uses electronic tags to store identification data and a no-line-of-sight requirement reader to capture the identification data.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set.   |
| **Replaced by another feature?**   | No                                              |
| **Product areas affected**         | Inventory management                            |
| **Status**                         | Removed as of Dynamics 365 for Operations 1611. |

### Report about state invoices numbering for Latvia

Latvian legislation provides specific rules about the numbering of sales invoices. The functionality lets you assign specific numbers to sales invoices, based on the user or user group. You can then generate a report or an XML file. You can also print a report about invoice numbers that are used.

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The state invoice numbering no longer has to be maintained. The report about used invoice numbers is no longer required. |
| **Replaced by another feature?**   | No       |
| **Product areas affected**         | Accounts receivable    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Set up the names of the manager and general accountant of a company for Lithuania

The names of the manager and the general accountant of a company can be specified in the company information and used in different local report printouts.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                     |
| **Replaced by another feature?**   | Yes, the setup of officials can be used for the same purpose.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Shipping carrier interface

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality   |
| **Replaced by another feature?**   | Partially replaced by Transportation management |
| **Product areas affected**         | Sales and marketing, Inventory management  |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.  |

### Telepay payment formats for Norway

Telepay payment formats include vendor payment export (credit transfer) and customer payment collection (direct debit).

|&nbsp;   |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format and AvtaleGiro customer payment format for Norway, as well as pain.002 and camt.054 bank notification return files import. |
| **Product areas affected**         | Accounts payable, Accounts receivable                                                          |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                                 |

### Vendor payment export formats for Finland

Two formats for exporting payments are available for Finland. LM02 (FI) is used for domestic payments, and LUM2 (FI) is used for foreign payments.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Finland       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Warehouse management II

|  &nbsp; |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The Warehouse management II solution (WMS II) that was available in the **Inventory management** module duplicates functionality that is in the **Warehouse management** module that was released in Dynamics AX 2012 R3.                                                                         |
| **Replaced by another feature?**   | The **Warehouse management** module that was released in AX 2012 R3, Dynamics AX 2012 R3 CU8, and Dynamics AX 2012 R3 CU9 replaces the Warehouse management II features. The new module has more advanced features and more flexible warehouse management processes than Warehouse management II. |
| **Product areas affected**         | Inventory management, Sales and marketing, Procurement and sourcing   |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.    |

### Worker reminders in Human Resources

Human Resources Payroll information

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage                                                           |
| **Replaced by another feature?**   | No                                                                  |
| **Product areas affected**         | Human resources                                                     |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611 |

### Workflow for creating goals

A workflow for managing the creation of employee goals is one of several workflows that were available to help coordinate the performance management process.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance management has been completely redesigned in Finance and Operations.     |
| **Replaced by another feature?**   | The redesigned Performance management feature gives more control over the content of the goals, the measurements that are used to track progress, and the attachment of supporting documentation. Goals can be stored as templates and then reused. This feature can help you set up additional goals for your employees more quickly. |
| **Product areas affected**         | Human capital management                 |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611. |

## Dynamics AX 7.0 


### Ability to cancel changes to a vendor invoice

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance enhancement        |
| **Replaced by another feature?**   | No                             |
| **Product areas affected**         | Accounts payable               |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### AIF, AxD, and AxBC integrations

In Application Integration Framework (AIF), data can be exchanged with external systems through business logic that is exposed as services. Dynamics AX includes services that are based on documents and .NET Business Connector (AxBC). A document is created by using XML. The XML includes header information that is added to create a *message* that can be transferred into or out of Dynamics AX. Examples of documents include sales orders and purchase orders. However, almost any entity, such as a customer, can be represented by a document. Services that are based on documents use the **Axd \<Document\>** classes.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The architecture of AIF and AxDs could not be scaled to a cloud service. There were performance issues around bulk import.                                        |
| **Replaced by another feature?**   | This feature is replaced by the Data Import/Export framework, which supports recurring bulk import/export. For AxBC, we recommend that you use the actual tables. |
| **Product areas affected**         | AxDs, AxBCs, and AIF   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Billing code rate scripts

Billing scripts were used to calculate billing rates for billing codes. This scripts required custom development in the C Sharp or Visual Basic programming language. In the current version of Dynamics AX, the **billing code rate scripts** are not supported.

| &nbsp;  |&nbsp;  |
|------------|--------------------|
| **Reason for deprecation/removal** | The support for the custom C Sharp or Visual Basic scripts was not added in Dynamics AX 7.0. |
| **Replaced by another feature?**   | No                                                                                      |
| **Product areas affected**         | Public sector, Accounts receivable                                    |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                          |

### BOMs without BOM versions

When the **BOM versions** configuration key was disabled, bill of materials (BOM) versions were hidden in all forms, and the system forced a 1:1 relationship between released products and BOMs. In the current version of Dynamics AX, the **BOM versions** configuration key can't be disabled.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Using a configuration key to control BOM versions doesn't scale in a cloud environment. |
| **Replaced by another feature?**   | No                                                                                      |
| **Product areas affected**         | Product information management, Inventory management                                    |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                          |

### Brazilian Bordero

Specific method of payment for Brazilian companies

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Support for the Brazilian Bordero method of payment has been discontinued from Brazilian localization |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Accounts payable   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Brazilian Sintegra statement

Federal tax statement for ICMS tax

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This statement is no longer applicable in some Brazilian states. |
| **Replaced by another feature?**   | No. Users can use Generic Electronic reporting tool to configure the statement if required under specific situations. |
| **Product areas affected**         | Fiscal books    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### Brazilian SCAN contingency mode for NF-e

(SCAN) contingency environment is used to generate, export, and import the status of a Nota Fiscal eletrônica (NF-e) when the environment of Secretaria da Fazenda (SEFAZ) is not available.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This method of contingency is no longer applicable in all Brazilian states |
| **Replaced by another feature?**   | No                                                                          |
| **Product areas affected**         | Accounts receivable                                                         |
| **Status**                         | Deprecated: A removal date has not been set for this feature.              |

### Business Analyzer

This mobile application let users review key business metrics.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature.   |
| **Replaced by another feature?**   | The Monitor financial performance content pack for Microsoft Power BI will include key financial metrics that were previously available in Business Analyzer. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Deprecated: The use of Business Analyzer has been deprecated.    |

### Business statistics

The setup of business statistics inquiries that can help you analyze the performance of the organization

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Legacy approach to business intelligence (BI), low customer usage, and a limited feature set |
| **Replaced by another feature?**   | New BI solutions for the current version of Dynamics AX                                      |
| **Product areas affected**         | Procurement and sourcing, Accounts payable, Sales and marketing, Accounts receivable         |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                               |

### Change document date function in Invoice approval journal

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage                                                               |
| **Replaced by another feature?**   | Yes. The document date on the posted vendor transaction can be changed. |
| **Product areas affected**         | Accounts payable                                                        |
| **Status**                         | Removed as of Dynamics AX 7.0.                                          |

### ClieOp03 payment format for the Netherlands

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in the Netherlands, because it has been replaced by SEPA functionality. |
| **Replaced by another feature?**   | SEPA payments export  |
| **Product areas affected**         | All modules     |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### Compliance Center

The Compliance Center was an Enterprise Portal site for managing the documentation requirements for compliance initiatives that are related to the Sarbanes-Oxley law.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Lack of customer usage. Microsoft SharePoint includes the same capability that was available in the Compliance Center. |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Compliance and internal controls  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Connector for Microsoft Dynamics

This tool was used to integrate key data from Microsoft Dynamics CRM to Dynamics ERP applications.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature. |
| **Replaced by another feature?**   | Dataverse                                      |
| **Product areas affected**         | Connector for Dynamics                         |
| **Status**                         | Removed as of Dynamics AX 7.0.                           |

### Container unit and multi dimension on-hand

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality |
| **Replaced by another feature?**   | Yes. Since AX 2012, this functionality has been replaced by the consolidated batch orders feature set. This feature set includes the consolidated on-hand view. |
| **Product areas affected**         | Product information management, Production control, Inventory management, Sales and marketing  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Cue group metadata

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Cue groups were used to display one or more Cues in the FactBox area. There was limited uptake, and there were also performance concerns, because a record change in a parent form caused one query per Cue in the Cue group. |
| **Replaced by another feature?**   | No      |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Cue metadata

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Cue metadata was limited to count or sum information.    |
| **Replaced by another feature?**   | Tile metadata was introduced to provide more flexibility for modeling. For example, you can model current counts, navigation, and key performance indicators (KPIs). Count tile metadata is the direct replacement of the Cue metadata. |
| **Product areas affected**         | All modules           |
| **Status**                         | Removed as of Dynamics AX 7.0      |

### Danish check format

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Support for the Danish check format layout has been discontinued, and the report has been removed from DK localization. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | All modules    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Data partitions

Data partitions provide a logical separation of data in the Dynamics AX database.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Data partitions were introduced in Dynamics AX 2012 R2 to enable data isolation. In a common scenario, a company has subsidiaries, and the data from one subsidiary should not be visible to another subsidiary, even though both subsidiaries are managed by the same IT department. However, extra scripts and management overhead throughout the program were required in order to create new partitions and populate them with data, and to back up partition data. In the cloud, where we have access to platform as a service (PaaS) database services (Microsoft Azure SQL Database), it's much more efficient to use a database as the isolation container than to do isolation in the program. Regardless of whether data partitioning is required for subsidiaries, for multiple tenants, or just for scale, we believe that the scenarios can be handled better through multiple instances of Finance and Operations. |
| **Replaced by another feature?**   | Customers using data partitions must use multiple instances of Finance and Operations if database level separation is a critical issue.    |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.  |


### Database and file share storage for attachments

Dynamics AX 2012 allowed storage of attachments in the database and in file shares. Both of those options are no longer supported.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Files share storage is no longer supported because cloud-hosted environments cannot communicate with local file shares. Database storage has been deprecated in favor of Azure Blob storage. Azure Blob storage is equivalent to storage in the database, as documents can only be accessed through Finance and Operations client forms. This provides the added benefit of providing storage that doesn't negatively affect the performance of the database. Blob storage is the default storage mechanism for Document Management and works immediately. |
| **Replaced by another feature?**   | Database storage has been deprecated in favor of Azure Blob storage.   |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Delimitation

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Time and attendance                    |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Desktop client

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The Dynamics AX client experience has been redesigned to improve usability across multiple platforms and devices.                      |
| **Replaced by another feature?**   | The new web client is based on the desktop Form metadata and programming model that have been modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Direct database connection

In Dynamics AX 2012 R3, Retail Modern POS could connect directly to the Channel DB in similar fashion to Enterprise POS. This was in addition to the standard communication method of Retail Modern POS communicating through Retail Server.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Direct database connectivity required lower security protocols and was primarily used to achieve the highest levels of performance. Due to the performance and security enhancements that have occurred in Finance and Operations, this functionality now causes more issues than it solves. |
| **Replaced by another feature?**   | No. Only standard Retail Server communication is now supported.  |
| **Product areas affected**         | Channel DB/Retail Modern POS   |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Dutch SWIFT MT940

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Generic functionality is now used instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### eBilanz (XBRL for Germany)

This functionality provided eXtensible Business Reporting Language (XBRL) output that is intended specifically for the German eBilanz taxonomy.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Lack of customer usage  |
| **Replaced by another feature?**   | This feature hasn't been replaced by another feature, but multiple specialized XBRL packages that provide rich XBRL functionality are available for the German market. |
| **Product areas affected**         | Management Reporter      |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Enterprise Portal client

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | A single client platform has been provided.  |
| **Replaced by another feature?**   | The new web client is based on the desktop form metadata and programming model that have been modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Environmental sustainability

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set  |
| **Replaced by another feature?**   | No              |
| **Product areas affected**         | Compliance and internal controls, Accounts payable  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Form ActiveX and Managed Host controls

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The ActiveX and Managed Host controls are based on the deprecated desktop client. |
| **Replaced by another feature?**   | The extensible control framework supports building new controls that are based on HTML, CSS, and JavaScript, and is a first-class control in the Microsoft Visual Studio Tooling environment. |
| **Product areas affected**         | All modules     |
| **Status**                         | Removed as of Dynamics AX 7.0.       |

### Generate prenotes by using a batch

Prenote generation can't be done by using a batch, but it can still be done by a user.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | No form exists to persist and display the resulting prenote file when it's generated by using a batch. |
| **Replaced by another feature?**   | Prenotes can still be generated, and the user has control over the location where the file is saved.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management  |
| **Status**                         | Removed as of AX 7.0.    |

### German DTAUS payment export and account statement import (totals and transactions)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in Germany, because it has been replaced by Single Euro Payments Area (SEPA) functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by SEPA payment export and advanced bank reconciliation functionality for importing account statements. |
| **Product areas affected**         | All modules  |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### German DTAZV payment format in domestic Currency

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in Germany, because it has been replaced by SEPA functionality. |
| **Replaced by another feature?**   | SEPA payments export    |
| **Product areas affected**         | Accounts payable   |
| **Status**                         | Deprecated: A removal date has not been set for this feature.    |

### German MT940 import

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Generic functionality is now used instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### German XML EU Sales list

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The XML format for German EU Sales List reporting is no longer supported. Only the ELMA5 text file format can be used to submit the EU Sales List report to the German Tax Office. |
| **Replaced by another feature?**   | No         |
| **Product areas affected**         | Tax        |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### GL SSRS reports

Reports that include the following menu items have been removed: **Summary trial balance**, **Detailed trial balance**, **Chart of accounts**, **Audit trail**, **Balances**, and **Balance list**.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Financial Microsoft SQL Server Reporting Services (SSRS) reports have been replaced by Management Reporter capabilities and default reports. |
| **Replaced by another feature?**   | Management Reporter (labeled **Financial reporting** in the current version of Dynamics AX)    |
| **Product areas affected**         | General ledger   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### InfoPart and FormPart metadata

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | InfoPart and FormPart metadata enabled the creation of FactBoxes for two different clients. |
| **Replaced by another feature?**   | InfoPart metadata, which was a simplified form definition, is converted into a Form by upgrade tooling. FormPart metadata, which referenced a Form, is replaced by a more direct reference that is created by upgrade tooling. |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0.        |

### Main account list page

A list of accounts for the legal entity and related balance information

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Balance information is available on the **Trial balance** list page by account and dimension.  |
| **Replaced by another feature?**   | **Main accounts** contains the same list of accounts that the **Main account** list page contained. The grid view in **Main accounts** also shows an even smaller, grid-like view. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Malaysia and Singapore bank cash flow report

This feature let the user print a cash flow report that shows transactions and details of the cash inflows and outflows for a specific date range for selected bank accounts.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The same information can be obtained from the Inquiry bank transaction. |
| **Replaced by another feature?**   | The Inquiry bank transaction                                            |
| **Product areas affected**         | Cash and bank management                                                |
| **Status**                         | Deprecated: A removal date has not been set for this feature.          |

### Mexican CFD electronic invoice

This feature enabled the generation of Mexican electronic invoices by using the Comprobante Fiscal Digital (CFD) method, where the company signs the invoice by requesting the related authorization from the government. This feature also provides a monthly report that includes all electronics invoices that were issued in the period.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The method is no longer applicable. The generation of electronic invoices by using the CFD method was deprecated by the tax authorities and replaced by the Comprobante Fiscal Digital a través de Internet (CFDI) method, where the signing is delegated to the third-party provider (PAC). The monthly report has been removed, and an inquiry option lets users inquire about historical transactions. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | Account receivables, Project   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Mexico realized and unrealized VAT

Dynamics AX 2012 managed unrealized value-added tax (VAT) by using Mexico-specific functionality for unrealized tax.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality  |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by standard conditional sales tax functionality that is provided by Core. |
| **Product areas affected**         | Tax   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Microsoft Outlook integration


| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by Microsoft Exchange Server integration. |
| **Replaced by another feature?**   | Yes                                                                            |
| **Product areas affected**         | Sales and marketing                                                            |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                 |

### Private blocking of inventory and warehouse management journals

The inventory and warehouse journals no longer support the ability to mark a journal as private for a selected user. Only the process of blocking journals as private for user groups and blocking during editing is supported.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Inventory management                   |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Product builder

Product builder was used to dynamically configure items from a sales order, purchase order, production order, sales quotation, project quotation, or item requirement. Based on a product model that had modeling variables, the user could select values to meet the customer requirements and get a unique product variant that had a BOM and route.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Product builder exposed X++ code to end users and isn't supported in the current version of Dynamics AX. It has been removed to avoid duplicate maintenance efforts on overlapping, sizeable codebases.  |
| **Replaced by another feature?**   | Yes. The constraint-based configuration was introduced in Dynamics AX 2012 where the depreciation of Product builder in future versions was already announced. The constraint-based configuration technology is selected on the product masters to enable the configuration. To learn more, see [Product configuration overview](../../../supply-chain/pim/build-product-configuration-model.md). |
| **Product areas affected**         | Product information management, Sales and marketing  |
| **Status**                         | Removed as of Dynamics AX 7.0.      |

### Production Floor app
This is the app for tablet devices running Windows 8.1 RT and Windows 8.1 Pro.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | With the change to a web-based client, it is possible to deliver similar functionality through the native Dynamics AX 7.0 client. The Job Card Device provides a production floor user interface that is optimized for touch and tablet form factors. |
| **Replaced by another feature?**   | Yes. The Job Card Device, which is a native part of Dynamics AX 7.0.                                                                           |
| **Product areas affected**         | Production control                                                |
| **Status**                         | Deprecated: A removal date from the Microsoft store has not yet been set for this feature.                                                |


### Rename product dimension

This feature let you change the name of one of the three standard product dimensions (size, color, or style) to a name that better suited your business requirements. Renaming included all the labels where the product dimension name was used.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The current version of Dynamics AX doesn't support label changes at run time. |
| **Replaced by another feature?**   | No                                                                            |
| **Product areas affected**         | Product information management                                                |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                |

### Retail Server connectivity using HTTP

In Dynamics AX 2012 R3, the Retail Server could function using HTTP communication (non-secured). This was in addition to the standard communication using HTTPS.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Due to new security requirements, only secured communication using TLS 1.2 (or above, as available) is now supported. The self-service installer will automatically configure the computer for this communication. |
| **Replaced by another feature?**   | No. Only standard HTTPS communication is now supported. |
| **Product areas affected**         | Retail Server  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Role Center pages

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Role Center pages were built on the deprecated Enterprise Portal platform, which has been replaced by the new web client platform in the current version of Dynamics AX. |
| **Replaced by another feature?**   | The new Workspace form pattern provides users with a process-centered design that provides easy access to commonly used tasks within that process.                       |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0   |

### Sales tax jurisdictions

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set |
| **Replaced by another feature?**   | No                                           |
| **Product areas affected**         | US sales tax                                 |
| **Status**                         | Removed as of Dynamics AX 7.0.               |

### Sites Services

Sites Services let you build websites that extend your business processes to the Internet without IT support.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The Microsoft Azure infrastructure that is used by Dynamics AX has new capabilities that can be used instead (for example, Azure sites). |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | HR recruiting, Case management, Request for quotes, Vendor registration, Collaborative workspaces for opportunities and campaigns  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### SSAS demand forecasting strategy

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The design of the feature cannot be supported in the new cloud architecture. |
| **Replaced by another feature?**   | Azure Machine Learning demand forecasting strategy                           |
| **Product areas affected**         | Master planning                                                              |
| **Status**                         | Removed as of Dynamics AX 7.0.                                               |

### Vendor invoice pool excluding posting details

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage. This functionality has been replaced by the Invoice journal that has workflow functionality. |
| **Replaced by another feature?**   | Workflow capabilities of the Invoice journal.     |
| **Product areas affected**         | Accounts payable |
| **Status**                         | Removed as of Dynamics AX 7.0.    |


### Virtual company accounts

The virtual companies feature is no longer supported in Dynamics AX. The virtual companies feature let users set up tables that could be shared by a set of companies. For a description of the feature, see [Company accounts and Virtual company accounts](../../fin-ops/get-started/ax4-content-retired.md). The feature works by grouping tables into collections that are assigned to virtual companies, which are groups of existing “real” companies. Queries are created so that all the companies in the virtual company can access the data in the tables of the associated table collections.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | - Virtual companies must be set up before data is stored in the tables. Retrofitting virtual companies onto an existing implementation is very difficult.<br><br>- Because there has been so much data normalization in the current version of Dynamics AX, it has become difficult to know what to add to the table collections. For example, it's difficult to know which tables to share. All the tables referenced from tables that are in a virtual company must also added. Because of table normalization, even simple master data that is spread across multiple tables must be part of the virtual company. Any mistake that is made here will cause functional issues.<br><br>- When a table is part of a virtual company, it loses information about the origin of the data, and only the virtual company is recorded.   |
| **Replaced by another feature?** | Global tables can be used to make tables accessible from all companies. Currently, there is no replacement. |   
| **Product areas affected**       | All modules |   
| **Status**                       | Removed as of Dynamics AX 7.0.   |   

### Windows 8 tablet app

The Windows 8 tablet app provided functionality for expense entry and approval.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Finance and Operations is compatible with tablets. The tablet app is no longer required.    |
| **Replaced by another feature?**   | No.          |
| **Product areas affected**         | Expense management   |
| **Status**                         | Removed: This functionality is only available for Dynamics AX 2012 R3. |

### Workplanner

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage |
| **Replaced by another feature?**   | No, but the **Profile relation** page, which is opened from the **Profile groups** page, supports the same business scenario as the deprecated **Workplanner** page. |
| **Product areas affected**         | Time and attendance     |
| **Status**                         | The code has not been removed. However, the form, JmgWorkPlanner, was not migrated.    |

### X++ financial statements

| &nbsp;  | &nbsp; |
|-------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| <strong>Reason for deprecation/removal</strong> |                         This functionality has been replaced by another feature.                         |
|  <strong>Replaced by another feature?</strong>  | Management Reporter (labeled <strong>Financial reporting</strong> in the current version of Dynamics AX) |
|     <strong>Product areas affected</strong>     |                                              General ledger                                              |
|             <strong>Status</strong>             |                                      Removed as of Dynamics AX 2012                                      |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

