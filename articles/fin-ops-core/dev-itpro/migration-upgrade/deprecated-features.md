---
title: Removed or deprecated features in previous releases
description: Learn about features that have been removed, or that were planned for removal from Dynamics 365 for Finance and Operations and previous releases.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28 
ms.dyn365.ops.version: AX 7.0.0 
ms.assetid: 31019808-4cbf-47d7-b1ba-d791db4281ae
---

# Removed or deprecated features in previous releases

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This article is no longer updated. To see a current list of features that are removed or deprecated from Finance and Operations apps, search for **"Removed or deprecated features"** content that relates to the app you're using.

This article describes features that Microsoft removed or deprecated from Dynamics 365 for Finance and Operations and previous releases of that product.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Use this list to help you consider these removals and deprecations for your own planning.

You can find detailed information about objects in Finance and Operations apps in the [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61). To learn about objects that changed or were removed in each version of Finance and Operations apps, compare the different versions of these reports.

## Finance 10.0.7 with Platform update 31

### Chinese voucher types without Account groups selection

|&nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Changed to the feature with account groups selection. |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2020, Microsoft plans to no longer support Chinese voucher types set up without Account groups selection. For more details about new feature design, see [What's new in 10.0.7](https://learn.microsoft.com/dynamics365-release-plan/2020/wave-2/dynamics365-finance/removed-deprecated-features). |

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
| **Reason for deprecation/removal** | We're retiring the **setUtcString()** method, because a better replacement method is available. |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Platform |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, we plan to no longer support the **setUtcString()** method. Developers should use the **setUtcDateTime()** method instead. |

### Block list report (IT) – Feature reference IT-00001

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Not legally required. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Italian localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, support ends for this report. |

### Domestic tax report – Feature reference IT-00003

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Not legally required. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Italian localization |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2020, support ends for the **Domestic tax report – Feature reference IT-00003**. |

## October 2019 deprecation announcement

### Flowchart diagrams in Business process modeler

| &nbsp;   | &nbsp; |
|------------|--------------------||
| **Reason for deprecation/removal** | Microsoft is deprecating the flowchart diagrams component in Business process modeler (BPM), because the legacy design caused low usage. |
| **Replaced by another feature?** | No |
| **Areas affected** | Business process modeler |
| **Status** | Deprecated: The flowchart diagrams component in BPM is expected to be removed in 2020. The following functionality is unavailable: All flowcharts are read-only and unavailable for editing. The shape properties that are associated with flowchart activities are also unavailable. These flowcharts include both the default flowcharts that are automatically generated and customized flowcharts that are modified based on those default flowcharts. The process steps are read-only and unavailable for editing. The legacy fit/gap analysis feature is unavailable. Therefore, no gap list is automatically created or available for export. **Note:** This feature was previously deprecated and replaced by Microsoft Azure DevOps integrations. The version history of the flowchart is unavailable. |

## Finance and Operations 10.0.5 with Platform update 29

### US Payroll tax updates

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Microsoft is retiring tax updates for the US Payroll functionality due to low usage and enhanced functionality that's now offered via strategic integrations.  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Payroll |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By July 31, 2024, Microsoft plans to no longer provide tax updates to US Payroll customers. The functionality remains in the product, but Microsoft won't provide enhancements to keep the functionality up to date. Microsoft will evaluate any product defects on a case-by-case basis. |

>[!NOTE]
> This change affects the original discontinuation date of October 1, 2021. For more information, see [Tax updates being retired for US Payroll feature in Microsoft Dynamics 365 for Finance and Operations](https://aka.ms/financepayrollfaq).

### Data management staging clean up

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Doesn't meet the core requirements for scheduling periodic cleanup. |
| **Replaced by another feature?**   | Yes, the job history cleanup feature. It meets the scenarios holistically. |
| **Product areas affected**         | Data management |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: Target timeframe for removal is December 2020. |

## Finance and Operations 10.0.4 with Platform update 28

### France: FEC Accounting data export in XML

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by TXT format. You can access the **French FEC audit file** through **General ledger** > **Periodic tasks** > **Data export**. |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | General ledger |
| **Deployment option**              | All |
| **Status**                         | Deprecated. Target timeframe for removal is July 2020. |

### Legacy navigation bar

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Header alignment with other Dynamics and Office products. For more information, see [Updated navigation bar that aligns with the Office header](/business-applications-release-notes/April19/dynamics365-finance-operations/updatednavbar).
| **Replaced by another feature?**   | Starting in Platform update 24, a restyled navigation bar that features search was introduced. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, the legacy navigation bar isn't available. Until that point, customers can revert to the legacy navigation bar through the **Client performance options** page. |

## Finance and Operations 10.0.2 with Platform update 26

### Legacy default action behavior

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The legacy behavior for default actions in grids results in an unexpected column having the default action link after grid columns are reordered through personalization. The new sticky default action feature corrects this. For more information, see [Sticky default actions in grids](/business-applications-release-notes/October18/dynamics365-finance-operations/sticky-default-action). |
| **Replaced by another feature?**   | Starting in Platform update 21, a feature for "sticky default actions" was introduced. You can enable this feature on the **Client performance options** page. |
| **Product areas affected**         | Grids in the web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, sticky default actions are the default behavior, without a mechanism to revert to the legacy behavior. |

### Legacy "is one of" filtering experience

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The "is one of" filtering experience underwent a redesign in Platform update 22. This change aims to make the updated version the only "is one of" filtering experience. |
| **Replaced by another feature?**   | Starting in Platform update 22, an improved "is one of" filtering experience is available on the **Client performance options** page. For more information, see [Optimized is one of filtering experience](/business-applications-release-notes/October18/dynamics365-finance-operations/improved-isoneof-filtering). |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Starting in April 2020, the improved "is one of" experience is the default behavior, without a mechanism to revert to the legacy behavior. |

### Parameter to enable sales orders with multiple project contract funding sources

Support for creating project-based sales orders where the project contract has multiple funding sources is enabled by using the **Project management parameters** setting **Allow sales orders for project with multiple funding sources**. By default, this parameter isn't enabled.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The functionality is always enabled after the parameter is removed. |
| **Replaced by another feature?**   | No. The functionality to support project-based sales orders with multiple funding sources is always enabled.   |
| **Product areas affected**         | The **Allow sales orders for projects with multiple funding sources** parameter will be removed. The following methods are modified when the parameter is removed: **ctrlSalesOrderTable** method in **ProjStatusType** class, **validate** method for **ProjId** field, and **run** method in **SalescreateOrder** form. The following methods are deprecated when the parameter is removed: **IsSalesOrderAllowedForMultipleFundingSources** in **ProjTable** table file, **IsAllowSalesOrdersForMultipleFundingSourcesParamEnabled** method in **ProjTable** table file, **AllowSalesOrdersForMultipleFundingSources** data field in **ProjParameters** form and **ProjParameterEntity** files, **IsAssociatedToMultipleFundingSourcesContract** private method in **ProjTable** table file. |
| **Deployment option**              | All  |
| **Status**                         | Deprecation is planned for the April 2020 release wave. |

### Legacy workflow reports for tracking and instance status

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The legacy workflow reports for tracking and instance status are deprecated because they're no longer referenced from the navigation. The report names are WorkflowWorkflowInstanceByStatusReport and WorkflowWorkflowTrackingReport. |
| **Replaced by another feature?**   | Use the workflow history form instead. |
| **Product areas affected**         | Web client |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Target timeframe for removal is April 2020. |

## Finance and Operations 10.0.1 with Platform update 25

### Deprecated APIs and potential breaking changes

#### Deriving from internal classes is deprecated

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Before Platform update 25, you could create a class or table that derives from an internal class or table that's defined in another package or module. This practice isn't safe. As of Platform update 25, the compiler displays a warning. |
| **Replaced by another feature?**   | The compiler warning is replaced by an error in Platform update 26. This change is backward compatible at runtime, which means that you can deploy Platform update 25 or newer on any sandbox or production environment without needing to modify custom code. This change only affects development and compile time.|
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning becomes a compilation error in Platform update 26. |

#### Overriding internal methods is deprecated

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Before Platform update 25, you could override an internal method in a derived class that's defined in another package or module. This practice isn't safe. As of Platform update 25, the compiler displays a warning. |
| **Replaced by another feature?**   | This warning is replaced by a compile error in Platform update 26. This change is backward compatible at runtime, which means that you can deploy Platform update 25 or newer on any sandbox or production environment without needing to modify custom code. This change only affects development and compile time. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning becomes a compilation error in Platform update 26. |

## Finance and Operations 10.0.0 with Platform update 24

### Renaming released products

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | When you use the **Rename primary key** function to change the ItemId of a released product, the system updates only direct foreign key references. Any other references to the released product, such as references from production orders, keep the old ItemId. This inconsistency can block business processes. |
| **Replaced by another feature?**   | No. |
| **Product areas affected**         | Product information management |
| **Deployment option**              | All  |
| **Status**                         | Removed as of Finance and Operations 10.0.0 with Platform update 24.|

## Finance and Operations 8.1.3 with Platform update 23

### SQL Server Reporting Services ReportViewer Control

Customers can use the **Export** action provided by the embedded SQL Server Reporting Services (SSRS) ReportViewer control to download documents produced by Finance and Operations applications. This HTML-based presentation of the report offers users a non-paginated preview of the document.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The non-paginated nature of the HTML-based preview experience doesn't deliver fidelity with the physical documents that Finance and Operations ultimately produces. By fully embracing PDF as the standard format for business documents, users can take advantage of a modern viewing experience with improved performance when producing application reports. |
| **Replaced by another feature?**   | Going forward, Finance and Operations renders reports as PDF documents by default.   |
| **Product areas affected**         | This change doesn't impact customer scenarios where reports are distributed electronically or sent directly to printers.    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. The functionality to automatically preview application reports by using an embedded PDF viewer is planned for the May 2019 Platform update. |

### Client KPI controls

A developer can model embedded key performance indicators (KPIs) in Visual Studio, and an end user can customize them.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The native client controls used to define KPIs have low customer uptake and rely on a developer to add trackable metrics. |
| **Replaced by another feature?**   | PowerBI.com service delivers world-class tooling for defining and managing KPIs based on data from external sources.  In an upcoming release, we plan to enable you to embed solutions hosted on PowerBI.com in application workspaces.   |
| **Product areas affected**         | This update prevents developers from introducing new KPI controls in Visual Studio designer.    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Deprecated APIs and future breaking changes

#### Field groups containing invalid field references

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Table metadata definitions can have field groups that contain invalid field references. If you deploy these definitions, they can cause runtime failures in Financial Reporting and SQL Server Reporting Services (SSRS). This issue is currently categorized as a *compiler warning* rather than an *error*, which means that you can create and deploy the deployable package without fixing the issue. To fix this issue:<br><br>1. Remove the invalid field reference from the table field group definition.<br><br>2. Recompile.<br><br>3. Ensure you address any warnings or errors. |
| **Replaced by another feature?**   | This warning will be replaced by a compile error in the future. |
| **Product areas affected**         | Visual Studio development tools |
| **Deployment option**              | All |
| **Status**                         | Deprecated: The warning is a compile-time error with platform updates for version 10.0.11 of Finance and Operations apps. |

#### Complete list

To access the full list of APIs that are being deprecated, see [Deprecation of methods and metadata elements](deprecation-deletion-apis.md).

## Finance and Operations 8.1 with Platform update 20

### Batch transfer rules for subledger journal account entries

The General ledger parameters currently include a synchronous transfer mode that is deprecated. This mode is replaced by asynchronous and scheduled batch only, which already exist as options for transfer. For more information, see the [General Ledger Parameters – Batch transfer rules](https://community.dynamics.com/365/financeandoperations/b/financials/archive/2019/03/15/general-ledger-parameters-batch-transfer-rules) blog.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The synchronous option causes a performance impact on the system. |
| **Replaced by another feature?**   | Use asynchronous and scheduled batch options instead of synchronous.   |
| **Product areas affected**         | General Ledger, Accounts payable, Accounts Receivable, Procurement, Expense    |
| **Deployment option**              | All  |
| **Status**                         | Deprecated: Target timeframe for removal is the 10.0 version.|

### Electronic reporting for Russia

Feature for configuring .txt and .xml file formats of declarations.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by Electronic reporting. |
| **Replaced by another feature?**   | Yes. |
| **Product areas affected**         | General Ledger |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Financial reports generator for Russia

A tool for setting up data collection for accounting and tax reports, and to export data to XLS and DOC report templates. The removed functional parts include exporting data to XLS and DOC report templates, queries, and fixed requisites.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Removed parts are replaced by Electronic reporting. |
| **Replaced by another feature?**   | Yes. Use the Financial reports setup user interface to set up data collection rules by GL accounts or tax registers. Use Electronic reporting to export data to various file types, and to configure fixed requisites and query-like data collection rules. |
| **Product areas affected**         | General ledger. |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Integration with external providers for sending electronic reporting through communication channels for Russia

A feature that exports generated electronic files of declarations to a folder for further sending to official providers of electronic reporting, and imports state back.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by electronic messages configurable feature. |
| **Replaced by another feature?**   | Yes.  |
| **Product areas affected**         | General Ledger, Tax |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Profit tax register wizard

Feature for creating templates for new profit tax registers. This feature creates X++ objects for new registers, which you can use as templates for adding the appropriate calculation logic.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Feature isn't compatible with the Finance and Operations extensibility model. |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Tax |
| **Deployment option**              | All |
| **Status**                         | Removed as of Finance and Operations 8.1 with Platform update 20. |

### Payroll and Human Resources for Russia

Russian country/region specific module for managing staff administration information, timesheet details for employees, payroll accounting, and creating pay statements.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Payroll isn't included in the global strategic focus of the Dynamics 365 portfolio. Partners and ISVs are best positioned to provide payroll functionality that is compliant with local regulations and tax updates.|
| **Replaced by another feature?**   | No|
| **Product areas affected**         | Russian Payroll and Human Resources Management |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is one of future updates of the 10.0 version. |

## Finance and Operations 8.0 with Platform update 15

This release doesn't remove or deprecate any features. Platform update 15 is cumulative and contains new or changed features from Platform update 13, Platform update 14, and Platform update 15.

## Finance and Operations, Enterprise edition 7.3 with Platform update 12

### Personalized product recommendations

Starting February 15, 2018, retailers can't display personalized product recommendations on a point of sale (POS) device. For more information, see [Product recommendations overview](../../../commerce/product-recommendations.md).  

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Microsoft is removing the current version of the product recommendation service to redesign this feature with a better algorithm and newer retail-oriented capabilities.  |
| **Replaced by another feature?**   | No. However, after spring 2018, Microsoft plans to bring back this feature to leverage a new recommendation service.   |
| **Product areas affected**         | Personalized product recommendations in POS.                                                    |
| **Deployment option**              | All                                                                                      |
| **Status**                         | Removed as of February 15, 2018. This change affects customers running Dynamics 365 for Operations 1611 and later.  |

### Extension of the list of Electronic reporting (ER) functions

The product no longer supports introducing custom functions to use in the ER expression builder. For more information, see [Extend the list of Electronic reporting (ER) functions](../../dev-itpro/analytics/general-electronic-reporting-formulas-list-extension.md). Due to changes in the ER APIs, the API to call built-in functions from the ER expression builder is internal and can't be extended.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Code sealing initiative  |
| **Replaced by another feature?**   | None. Whenever you need a new built-in function, submit a new extension request to the ER framework team.<br><br>As a temporary workaround while the requested function is under development by the ER team, you can program the required logic as a method of a custom application class. You can access this method in an ER expression as a property of the added ER data source of the **Application\Class** type that refers to that custom application class.  |
| **Product areas affected**         | Electronic reporting framework                                                      |
| **Deployment option**              | All                                                                                      |
| **Status**                         | Removed as of Finance and Operations, Enterprise edition 7.3.    |

### Inventory by item group and Inventory by inventory dimension aging reports

Finance and Operations no longer supports these two reports. Instead, use the **Inventory aging** report to improve the user experience.

| &nbsp;  | &nbsp; |
|--------------|-----------------------|
| **Reason for deprecation**       | Duplicate functionality  |
| **Replaced by another feature?** | Yes. The two reports have been replaced by the **Inventory aging** report.     |
| **Product areas affected**       | Inventory management, Cost management        |
| **Deployment option**        | All|
| **Status**                       | Deprecated: The product removes the menu items for the two reports in version 7.3. However, the product retains the code for the reports. The plan is to remove the code in a future release. |

### Power BI content packs available on Marketplace

Product updates in Microsoft Power BI deprecate the **Cost management**, **Financial performance**, and **Retail channel performance** content packs that are available on the [Microsoft Marketplace](https://marketplace.microsoft.com) site. Finance and Operations also deprecates system administration forms that you use to deploy these content packs to PowerBI.com.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Product updates in Microsoft Power BI. |
| **Replaced by another feature?**   | Analytical applications which allow for solution integrations at the database level replace the **Cost management**, **Financial performance**, and **Retail channel performance** content packs that are available on the [Marketplace](https://marketplace.microsoft.com) site. For more information about analytical applications, see [Embedded Power BI in workspaces](../../dev-itpro/analytics/embed-power-bi-workspaces.md).    |
| **Product areas affected**         | Cost management, Finance, and Retail                                                                                               |
| **Deployment option**              | Cloud only (Integration with PowerBI.com is not supported in on-premises deployments.)                                                                                                            |
| **Status**                         | Deprecated: Target timeframe for the functionality removal is Q2 2018.    |

### Standard UI in data management workspace

The standard UI in data management is the legacy UI. It's the default UI that users see when they visit the data management workspace.

| &nbsp;  | &nbsp; |
|------------------|-------------------------|
| **Reason for deprecation or removal** | Investments are focused on providing new user experiences in the new UI.             |
| **Replaced by another feature?**   | The new UI called *Enhanced views* replaces the old UI.            |
| **Product areas affected**         | Data management workspace                                                     |
| **Deployment option**              | All                                                                           |
| **Status**                         | Deprecated: Target timeframe for removal is Q2 2018. |

### Excise, sales tax, service tax for India

These taxes are subsumed into Indian GST.

| &nbsp;   | &nbsp; |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | These taxes are subsumed into Indian GST.                          |
| **Replaced by another feature?**            | Indian GST                                                              |
| **Product areas affected**                  | Tax                                                                     |
| **Deployment option**                       | All modules                                                   |
| **Status**                                  | Deprecated: A removal date isn't set for this feature. |

### File Validation Utility (FVU) for India

| &nbsp;   | &nbsp; |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date hasn't been set for this feature.   |

### TDS/TCS certificate for India

Users can download this certificate from the government portal.

| &nbsp;   | &nbsp; |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                   |
| **Status**                                  | Deprecated: A removal date hasn't been set for this feature.     |

### Export/import (EXIM) incentive scheme for India

| &nbsp;   | &nbsp; |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Import and export                                                       |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date hasn't been set for this feature.  |

## Dynamics 365 for Retail 7.2

### Personalized product recommendations

Starting February 15, 2018, retailers can't display personalized product recommendations on a point of sale (POS) device. For more information, see [Product recommendations overview](../../../commerce/product-recommendations.md).  

|  &nbsp; |  &nbsp;|
|------------|--------------------|
| **Reason for deprecation or removal** | Microsoft is removing the current version of the product recommendation service to redesign this feature with a better algorithm and newer retail-oriented capabilities.  |
| **Replaced by another feature?**   | No. However, after spring 2018, Microsoft plans to bring back this feature to leverage a new recommendation service.   |
| **Product areas affected**         | Personalized product recommendations in POS.                                                    |
| **Deployment option**              | All                                                                                      |
| **Status**                         |Removed as of February 15, 2018. This change affects customers running Dynamics 365 for Retail 7.2  and later. |

## Finance and Operations, Enterprise edition July 2017 with Platform update 8

### Currency conversion for accounting and reporting currencies

Currency conversion for accounting and reporting currencies was introduced when the euro was introduced.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Limited usage and addition of the Copy legal entity functionality as a replacement.      |
| **Replaced by another feature?**   | No, but the Copy legal entity and Configurations features were added to make it easier to move to a company that has changing core requirements. |
| **Product areas affected**         | Financial management     |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.   |

### Warehouse mobile devices portal

Warehouse mobile devices portal (WMDP) was a standalone component that you intended to self-deploy on-premises. Finance and Operations no longer supports this component. A native app that improves the user experience replaces the functionality of WMDP.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Duplicate functionality.       |
| **Replaced by another feature?**   | Yes. Finance and Operations - Warehousing replaces this feature. For more information about setup and prerequisites, see [Install and configure the Warehousing app overview](../../../supply-chain/warehousing/install-configure-warehousing-app.md). |
| **Product areas affected**         | Warehouse management, Transportation management     |
| **Deployment option**              | Warehouse mobile devices portal (WMDP) was a standalone component that you intended to self-deploy on-premises.               |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is Q4 2019.   |

### Advanced bank reconciliation matching rule for manual matching

Use this matching rule to select and mark a bank document when you manually match documents in the reconciliation worksheet.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage.                                                                         |
| **Replaced by another feature?**   | No. Use column filtering capabilities to find documents for reconciliation. |
| **Product areas affected**         | Cash and bank management                                                               |
| **Deployment option**              | All                                                                                    |
| **Status**                         | Removed as of July 2017.                                                               |

## Dynamics 365 for Operations 1611 with Platform update 3

### AEB payment formats for Spain

Use the Consejo Superior Bancario payment formats to send remittance files to the bank for customer payments and vendor payments. The Asociación Española de Banca determines the content of these formats. It covers Cuaderno 19, 32, 58, 34.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                  |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer and Direct debit payment formats for Spain |
| **Product areas affected**         | Accounts payable, Accounts receivable                                    |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.           |

### Bank payments transfer for Lithuania

Use the Payment transfer (LT) export format to generate and print bank payment transfers for Lithuania. In 2005, the Lithuanian market started using LITAS, the unified electronic banking system.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Lithuania     |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### BBS Direkte Remittering payment formats for Norway

BBS Direkte Remittering payment formats include customer payment collection export (direct debit) and return message import.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.  |
| **Replaced by another feature?**   | Use the AvtaleGiro customer payment format for Norway to generate direct debit messages. Return message import will be implemented in future releases. |
| **Product areas affected**         | Accounts payable, Accounts receivable   |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                                                                                                 |

### Chart of Accounts tool for Spain

Use this tool when you need to make major changes to a chart of accounts in Spain. You can import a new chart of accounts in Microsoft Excel or text format, and you can also import financial statements.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Dom80 payment format for Belgium

Legacy Belgian payment format for payment collection (direct debit).

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Belgium         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### DTA/EZAG payment formats for Switzerland

The DTA and EZAG formats are part of the ESR system because they support the reference number. Since the reference number isn't mandatory, you can use these formats to process any vendor payments. Companies that use these formats typically have a bank account at a bank other than PostFinance.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO 20022 Credit transfer payment format for Switzerland   |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### EDIFACT-DIRDEB payment format for Austria

The EDIFACT-DIRDEB payment format supports payment collection through direct debit.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Austria         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### EDIVAT for Belgium

EDIVAT is an obsolete Belgian standard for electronic declaration via secure mail. Dynamics AX 2012 retains the read-only solution to enable access to the historical data.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The functionality is no longer used.                           |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### eGiro EDIFACT CREMUL payment import format for Norway

eGiro is based on the international UN EDIFACT CREMUL (Multiple Credit Advice Message) standard that banks use for automatic posting of customer payments. In Dynamics AX, you implement eGiro as a customer payment import format.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 notification import. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                            |

### External inventory for Poland

Evidence of goods that you take from a vendor for sales without purchase. Goods that you handle in external inventory don't affect standard inventory, and you can sell and then purchase them automatically. This process creates real inventory movements.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Replaced by another feature                                    |
| **Replaced by another feature?**   | Yes, the core Inbound consignment functionality                |
| **Product areas affected**         | Accounts payable, Inventory management                         |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Financial reports generator for Eastern Europe

A tool that you use to set up data collection for accounting and tax reports, and to export data to XLS and DOC report templates.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Limited usage                                                                            |
| **Replaced by another feature?**   | No. The tool will be replaced by Electronic reporting configurations in future releases. |
| **Product areas affected**         | General Ledger                                                                           |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                           |

### Import of customer payment transactions for Finland

You can select an import format for Finnish payments to import customer payment transactions from an external file that the bank provides.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 notification import. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                            |

### Import of payment transactions into a general ledger journal for Finland

A format that's specific to Finland is used to import accounting transactions into the general ledger.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.053 bank statement import by using Advanced Bank Reconciliation. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                            |

### Integration with Isabel synchronized (CIS) for Belgium

Isabel is the framework for electronic banking in Europe and is a de facto standard in Belgium.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Integration with Isabel client is discontinued.   |
| **Replaced by another feature?**   | No. The payment formats that are no longer used are replaced by ISO 20022 Credit transfer payment format for Belgium. |
| **Product areas affected**         | Accounts payable     |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.    |

### Modifications in the chart of accounts and accounting rules for Spain

This feature is used for changes in the chart of accounts and accounting rules in Spain. It maps accounts to help transform the old chart of accounts into the new chart of accounts, and compares the previous fiscal year with the new fiscal year, even if they were posted to different account numbers.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Pagamento Fornittori vendor payment format

Legacy Italian payment format for credit transfers.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Credit transfer payment format for Italy         |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Payment export formats for Estonia

The Telehansa and Teleservice formats are used for bank payment export.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO 20022 Credit transfer payment format for Estonia       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Payment file archive for Norway

When you generate payment files, the file archive automatically archives all created files, even files that you previously wrote or read.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Replaced by another feature                                        |
| **Replaced by another feature?**   | Yes, Electronic reporting archived jobs                            |
| **Product areas affected**         | Accounts payable, Accounts receivable, Organization administration |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.     |

### Payment import formats for Estonia

Use the Telehansa and TeleTeenus formats for bank payment import.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The payment formats are no longer used.                                                    |
| **Replaced by another feature?**   | Yes, the ISO20022 Camt.054 bank notification import. |
| **Product areas affected**         | Accounts receivable                                                                        |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                             |

### Payroll information in Human Resources

Human Resources Payroll information

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Core Payroll and Human Resources pages now provide this functionality.  |
| **Replaced by another feature?**   | **Benefits**, **Earnings**, and other related pages that were previously in US Payroll have been reconfigured. They're now part of the core Human Resources configuration to help support external payroll processing. Use the **Human Resources 1** \> **Payroll** configuration key to access this functionality. |
| **Product areas affected**         | Human Resources, Payroll   |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.    |

### Performance management goal workflow

Performance management includes goal management and integration with performance reviews.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Performance management was redesigned, and the number of goal pages was reduced to simplify the process.                 |
| **Replaced by another feature?**   | No. Managers can see goals through the Manager Self Service portal, and they can change and view the goals. |
| **Product areas affected**         | Human capital management       |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.    |

### Postgirot and Postgirot Utland payment formats for Sweden

Postgirot and Postgirot Utland payment formats for Sweden.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, by the ISO 20022 credit transfer payment format for Sweden.        |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Radio frequency identifier

Radio Frequency Identification (RFID) is a data-collection technology that uses electronic tags to store identification data and a no-line-of-sight requirement reader to capture the identification data.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Low customer usage and a limited feature set.   |
| **Replaced by another feature?**   | No                                              |
| **Product areas affected**         | Inventory management                            |
| **Status**                         | Removed as of Dynamics 365 for Operations 1611. |

### Report about state invoices numbering for Latvia

Latvian legislation provides specific rules about the numbering of sales invoices. By using this functionality, you can assign specific numbers to sales invoices based on the user or user group. You can then generate a report or an XML file. You can also print a report about invoice numbers that are used.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | You no longer need to maintain the state invoice numbering. You no longer need to report about used invoice numbers. |
| **Replaced by another feature?**   | No       |
| **Product areas affected**         | Accounts receivable    |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.  |

### Set up the names of the manager and general accountant of a company for Lithuania

You can specify the names of the manager and the general accountant of a company in the company information and use them in different local report printouts.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                     |
| **Replaced by another feature?**   | Yes, use the setup of officials for the same purpose.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.  |

### Shipping carrier interface

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality   |
| **Replaced by another feature?**   | Partially replaced by Transportation management |
| **Product areas affected**         | Sales and marketing, Inventory management  |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.  |

### Telepay payment formats for Norway

Telepay payment formats include vendor payment export (credit transfer) and customer payment collection (direct debit).

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                                        |
| **Replaced by another feature?**   | Yes, ISO 20022 Credit transfer payment format and AvtaleGiro customer payment format for Norway, as well as pain.002 and camt.054 bank notification return files import. |
| **Product areas affected**         | Accounts payable, Accounts receivable                                                          |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                                 |

### Vendor payment export formats for Finland

Two formats for exporting payments are available for Finland. Use LM02 (FI) for domestic payments, and use LUM2 (FI) for foreign payments.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | These payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO 20022 Credit transfer payment format for Finland       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Warehouse management II

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The Warehouse management II solution (WMS II) that was available in the **Inventory management** module duplicates functionality that's in the **Warehouse management** module that was released in Dynamics AX 2012 R3.                                                                         |
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

A workflow for managing the creation of employee goals was one of several workflows that helped coordinate the performance management process.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance management has been completely redesigned in Finance and Operations.     |
| **Replaced by another feature?**   | The redesigned Performance management feature gives more control over the content of the goals, the measurements that are used to track progress, and the attachment of supporting documentation. Goals can be stored as templates and then reused. This feature can help you set up additional goals for your employees more quickly. |
| **Product areas affected**         | Human capital management                 |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611. |

## Dynamics AX 7.0

### Ability to cancel changes to a vendor invoice

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Performance enhancement        |
| **Replaced by another feature?**   | No                             |
| **Product areas affected**         | Accounts payable               |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### AIF, AxD, and AxBC integrations

In Application Integration Framework (AIF), you can exchange data with external systems through business logic that you expose as services. Dynamics AX includes services that are based on documents and .NET Business Connector (AxBC). You create a document by using XML. The XML includes header information that you add to create a *message* that you can transfer into or out of Dynamics AX. Examples of documents include sales orders and purchase orders. However, you can represent almost any entity, such as a customer, by using a document. Services that are based on documents use the **Axd \<Document\>** classes.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The architecture of AIF and AxDs couldn't scale to a cloud service. There were performance problems around bulk import.                                        |
| **Replaced by another feature?**   | This feature is replaced by the Data Import/Export framework, which supports recurring bulk import and export. For AxBC, use the actual tables. |
| **Product areas affected**         | AxDs, AxBCs, and AIF   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Billing code rate scripts

Use billing scripts to calculate billing rates for billing codes. You need to custom develop these scripts by using C# or Visual Basic. In the current version of Dynamics AX, billing code rate scripts aren't supported.

| &nbsp;   | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Dynamics AX doesn't support custom C# or Visual Basic scripts. |
| **Replaced by another feature?**   | No                                                                                      |
| **Product areas affected**         | Public sector, Accounts receivable                                    |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                          |

### BOMs without BOM versions

When you disable the **BOM versions** configuration key, the system hides bill of materials (BOM) versions in all forms and enforces a one-to-one relationship between released products and BOMs. In the current version of Dynamics AX, you can't disable the **BOM versions** configuration key.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Using a configuration key to control BOM versions doesn't scale in a cloud environment. |
| **Replaced by another feature?**   | No                                                                                      |
| **Product areas affected**         | Product information management, Inventory management                                    |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                          |

### Brazilian Bordero

Specific method of payment for Brazilian companies

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Brazilian localization no longer supports the Brazilian Bordero method of payment. |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Accounts payable   |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Brazilian Sintegra statement

Federal tax statement for ICMS tax

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | This statement is no longer applicable in some Brazilian states. |
| **Replaced by another feature?**   | No. Use the Generic Electronic reporting tool to configure the statement if required under specific situations. |
| **Product areas affected**         | Fiscal books    |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.   |

### Brazilian SCAN contingency mode for NF-e

Use the (SCAN) contingency environment to generate, export, and import the status of a Nota Fiscal eletrônica (NF-e) when the environment of Secretaria da Fazenda (SEFAZ) isn't available.

|  &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This method of contingency is no longer applicable in all Brazilian states |
| **Replaced by another feature?**   | No                                                                          |
| **Product areas affected**         | Accounts receivable                                                         |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.              |

### Business Analyzer

This mobile application lets users review key business metrics.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature.   |
| **Replaced by another feature?**   | The Monitor financial performance content pack for Microsoft Power BI includes key financial metrics that were previously available in Business Analyzer. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Deprecated: The use of Business Analyzer is deprecated.    |

### Business statistics

The setup of business statistics inquiries that you can use to analyze the performance of the organization.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Legacy approach to business intelligence (BI), low customer usage, and a limited feature set. |
| **Replaced by another feature?**   | New BI solutions for the current version of Dynamics AX.                                      |
| **Product areas affected**         | Procurement and sourcing, Accounts payable, Sales and marketing, Accounts receivable.         |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                               |

### Change document date function in Invoice approval journal

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Low usage.                                                               |
| **Replaced by another feature?**   | Yes. You can change the document date on the posted vendor transaction. |
| **Product areas affected**         | Accounts payable.                                                        |
| **Status**                         | Removed as of Dynamics AX 7.0.                                          |

### ClieOp03 payment format for the Netherlands

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | This format is no longer applicable in the Netherlands, because it's replaced by SEPA functionality. |
| **Replaced by another feature?**   | SEPA payments export.  |
| **Product areas affected**         | All modules.     |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.   |

### Compliance Center

The Compliance Center was an enterprise portal site for managing the documentation requirements for compliance initiatives that are related to the Sarbanes-Oxley law.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Lack of customer usage. Microsoft SharePoint includes the same capability that was available in the Compliance Center. |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Compliance and internal controls  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Connector for Microsoft Dynamics

Use this tool to integrate key data from Microsoft Dynamics CRM to Dynamics ERP applications.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | This functionality is replaced by another feature. |
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
| **Reason for deprecation/removal** | Cue groups displayed one or more Cues in the FactBox area. There was limited uptake, and there were also performance concerns. A record change in a parent form caused one query per Cue in the Cue group. |
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
| **Reason for deprecation or removal** | Support for the Danish check format layout has been discontinued, and DK localization no longer includes the report. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | All modules    |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.  |

### Data partitions

Data partitions provide a logical separation of data in the Dynamics AX database.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Data partitions were introduced in Dynamics AX 2012 R2 to enable data isolation. In a common scenario, a company has subsidiaries, and the data from one subsidiary shouldn't be visible to another subsidiary, even though the same IT department manages both subsidiaries. However, extra scripts and management overhead throughout the program were required to create new partitions, populate them with data, and back up partition data. In the cloud, where you have access to platform as a service (PaaS) database services (Microsoft Azure SQL Database), it's much more efficient to use a database as the isolation container than to do isolation in the program. Regardless of whether data partitioning is required for subsidiaries, for multiple tenants, or just for scale, Finance and Operations can handle these scenarios better through multiple instances. |
| **Replaced by another feature?**   | Customers using data partitions must use multiple instances of Finance and Operations if database level separation is a critical issue.    |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Database and file share storage for attachments

Dynamics AX 2012 allowed storage of attachments in the database and in file shares. Both of those options aren't supported anymore.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | File share storage isn't supported anymore because cloud-hosted environments can't communicate with local file shares. Database storage is deprecated in favor of Azure Blob storage. Azure Blob storage is equivalent to storage in the database, as you can only access documents through Finance and Operations client forms. This storage option provides the added benefit of not negatively affecting the performance of the database. Blob storage is the default storage mechanism for Document Management and works immediately. |
| **Replaced by another feature?**   | Database storage is deprecated in favor of Azure Blob storage.   |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Delimitation

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Time and attendance                    |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Desktop client

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The Dynamics AX client experience was redesigned to improve usability across multiple platforms and devices.                      |
| **Replaced by another feature?**   | The new web client is based on the desktop Form metadata and programming model that are modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Direct database connection

In Dynamics AX 2012 R3, Retail Modern POS can connect directly to the Channel DB in a similar way to Enterprise POS. This connection is in addition to the standard communication method where Retail Modern POS communicates through Retail Server.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Direct database connectivity requires lower security protocols. Use it primarily to achieve the highest levels of performance. Due to the performance and security enhancements that occurred in Finance and Operations, this functionality now causes more problems than it solves. |
| **Replaced by another feature?**   | No. Only standard Retail Server communication is now supported.  |
| **Product areas affected**         | Channel DB and Retail Modern POS   |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Dutch SWIFT MT940

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Use generic functionality instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                           |

### eBilanz (XBRL for Germany)

This functionality provided eXtensible Business Reporting Language (XBRL) output that's intended specifically for the German eBilanz taxonomy.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Lack of customer usage  |
| **Replaced by another feature?**   | This feature isn't replaced by another feature. However, multiple specialized XBRL packages that provide rich XBRL functionality are available for the German market. |
| **Product areas affected**         | Management Reporter      |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.  |

### Enterprise Portal client

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | A single client platform is provided.  |
| **Replaced by another feature?**   | The new web client is based on the desktop form metadata and programming model. This model is modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Environmental sustainability

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Low customer usage and a limited feature set  |
| **Replaced by another feature?**   | No              |
| **Product areas affected**         | Compliance and internal controls, Accounts payable  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Form ActiveX and managed host controls

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The ActiveX and managed host controls are based on the deprecated desktop client. |
| **Replaced by another feature?**   | The extensible control framework supports building new controls that are based on HTML, CSS, and JavaScript, and is a first-class control in the Microsoft Visual Studio Tooling environment. |
| **Product areas affected**         | All modules.     |
| **Status**                         | Removed as of Dynamics AX 7.0.       |

### Generate prenotes by using a batch

You can't use a batch to generate prenotes, but a user can still generate them.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | No form exists to persist and display the resulting prenote file when you generate it by using a batch. |
| **Replaced by another feature?**   | You can still generate prenotes, and you have control over the location where the file is saved.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management  |
| **Status**                         | Removed as of AX 7.0.    |

### German DTAUS payment export and account statement import (totals and transactions)

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | This format is no longer applicable in Germany, because it's replaced by Single Euro Payments Area (SEPA) functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality is replaced by SEPA payment export and advanced bank reconciliation functionality for importing account statements. |
| **Product areas affected**         | All modules  |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### German DTAZV payment format in domestic currency

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in Germany, because SEPA functionality replaced it. |
| **Replaced by another feature?**   | SEPA payments export    |
| **Product areas affected**         | Accounts payable   |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.    |

### German MT940 import

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Use generic functionality instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.                           |

### German XML EU Sales list

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The XML format for German EU Sales List reporting is no longer supported. You can only use the ELMA5 text file format to submit the EU Sales List report to the German Tax Office. |
| **Replaced by another feature?**   | No         |
| **Product areas affected**         | Tax        |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.   |

### GL SSRS reports

Reports that include the following menu items are removed: **Summary trial balance**, **Detailed trial balance**, **Chart of accounts**, **Audit trail**, **Balances**, and **Balance list**.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Financial Microsoft SQL Server Reporting Services (SSRS) reports are replaced by Management Reporter capabilities and default reports. |
| **Replaced by another feature?**   | Management Reporter (labeled **Financial reporting** in the current version of Dynamics AX)    |
| **Product areas affected**         | General ledger   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### InfoPart and FormPart metadata

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | InfoPart and FormPart metadata enabled the creation of FactBoxes for two different clients. |
| **Replaced by another feature?**   | InfoPart metadata, which was a simplified form definition, is converted into a Form by upgrade tooling. FormPart metadata, which referenced a Form, is replaced by a more direct reference that is created by upgrade tooling. |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0.        |

### Main account list page

A list of accounts for the legal entity and related balance information.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The **Trial balance** list page shows balance information by account and dimension.  |
| **Replaced by another feature?**   | The **Main accounts** list page contains the same list of accounts. It also provides a more streamlined grid view. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Malaysia and Singapore bank cash flow report

This feature lets you print a cash flow report that shows transactions and details of the cash inflows and outflows for a specific date range for selected bank accounts.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | You can get the same information from the **Inquiry bank transaction**. |
| **Replaced by another feature?**   | The **Inquiry bank transaction**.                                            |
| **Product areas affected**         | Cash and bank management.                                                |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature.          |

### Mexican CFD electronic invoice

This feature enabled the generation of Mexican electronic invoices by using the Comprobante Fiscal Digital (CFD) method, where the company signs the invoice by requesting the related authorization from the government. This feature also provides a monthly report that includes all electronic invoices that were issued in the period.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | The method is no longer applicable. The tax authorities deprecated the generation of electronic invoices by using the CFD method and replaced it with the Comprobante Fiscal Digital a través de Internet (CFDI) method, where the signing is delegated to the third-party provider (PAC). The monthly report was removed, and an inquiry option lets users inquire about historical transactions. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | Accounts receivable, Project   |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Mexico realized and unrealized VAT

Dynamics AX 2012 managed unrealized value-added tax (VAT) by using Mexico-specific functionality for unrealized tax.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Duplicate functionality  |
| **Replaced by another feature?**   | Yes, standard conditional sales tax functionality provided by Core replaces this functionality. |
| **Product areas affected**         | Tax   |
| **Status**                         | Deprecated: A removal date hasn't been set for this feature. |

### Microsoft Outlook integration

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Microsoft Exchange Server integration replaces this functionality. |
| **Replaced by another feature?**   | Yes                                                                            |
| **Product areas affected**         | Sales and marketing                                                            |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                 |

### Private blocking of inventory and warehouse management journals

The inventory and warehouse journals no longer support the ability to mark a journal as private for a selected user. They support only blocking journals as private for user groups and blocking during editing.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Inventory management                   |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Product builder

Use product builder to dynamically configure items from a sales order, purchase order, production order, sales quotation, project quotation, or item requirement. Based on a product model that has modeling variables, select values to meet the customer requirements and get a unique product variant that has a BOM and route.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Product builder exposed X++ code to end users and isn't supported in the current version of Dynamics AX. Microsoft removed it to avoid duplicate maintenance efforts on overlapping, sizeable codebases.  |
| **Replaced by another feature?**   | Yes. Constraint-based configuration was introduced in Dynamics AX 2012. Microsoft announced the deprecation of product builder in future versions. Select constraint-based configuration technology on the product masters to enable the configuration. To learn more, see [Product configuration overview](../../../supply-chain/pim/build-product-configuration-model.md). |
| **Product areas affected**         | Product information management, Sales and marketing  |
| **Status**                         | Removed as of Dynamics AX 7.0.      |

### Production Floor app

This app runs on tablet devices that use Windows 8.1 RT and Windows 8.1 Pro.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | With the change to a web-based client, you can deliver similar functionality through the native Dynamics AX 7.0 client. The Job Card Device provides a production floor user interface that is optimized for touch and tablet form factors. |
| **Replaced by another feature?**   | Yes. The Job Card Device, which is a native part of Dynamics AX 7.0.                                                                           |
| **Product areas affected**         | Production control                                                |
| **Status**                         | Deprecated: A removal date from the Microsoft store hasn't yet been set for this feature.                                                |

### Rename product dimension

This feature lets you change the name of one of the three standard product dimensions (size, color, or style) to a name that better suits your business requirements. Renaming includes all the labels where the product dimension name is used.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The current version of Dynamics AX doesn't support label changes at run time. |
| **Replaced by another feature?**   | No                                                                            |
| **Product areas affected**         | Product information management                                                |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                |

### Retail Server connectivity using HTTP

In Dynamics AX 2012 R3, the Retail Server could function by using HTTP communication (non-secured). This option was in addition to the standard communication by using HTTPS.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Due to new security requirements, only secured communication by using TLS 1.2 (or above, as available) is now supported. The self-service installer automatically configures the computer for this communication. |
| **Replaced by another feature?**   | No. Only standard HTTPS communication is now supported. |
| **Product areas affected**         | Retail Server  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Role Center pages

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Role Center pages were built on the deprecated Enterprise Portal platform. The current version of Dynamics AX replaces Enterprise Portal with the new web client platform. |
| **Replaced by another feature?**   | The new Workspace form pattern provides users with a process-centered design that provides easy access to commonly used tasks within that process.                       |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0   |

### Sales tax jurisdictions

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Low customer usage and a limited feature set |
| **Replaced by another feature?**   | No                                           |
| **Product areas affected**         | US sales tax                                 |
| **Status**                         | Removed as of Dynamics AX 7.0.               |

### Sites Services

By using Sites Services, you can build websites that extend your business processes to the Internet without IT support.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Use the new capabilities in the Microsoft Azure infrastructure that Dynamics AX uses, such as Azure sites. |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | HR recruiting, Case management, Request for quotes, Vendor registration, Collaborative workspaces for opportunities and campaigns  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### SSAS demand forecasting strategy

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | The new cloud architecture can't support the design of this feature. |
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

Dynamics AX no longer supports the virtual companies feature. By using the virtual companies feature, you could set up tables that a set of companies shared. For a description of the feature, see [Company accounts and Virtual company accounts](../../fin-ops/get-started/ax4-content-retired.md). The feature works by grouping tables into collections that you assign to virtual companies, which are groups of existing “real” companies. You create queries so that all the companies in the virtual company can access the data in the tables of the associated table collections.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | - You must set up virtual companies before storing data in the tables. Retrofitting virtual companies onto an existing implementation is very difficult.<br><br>- Because the current version of Dynamics AX uses so much data normalization, it can be difficult to know what to add to the table collections. For example, it's difficult to know which tables to share. You must add all the tables referenced from tables that are in a virtual company. Because of table normalization, even simple master data that is spread across multiple tables must be part of the virtual company. Any mistake that you make here causes functional problems.<br><br>- When a table is part of a virtual company, it loses information about the origin of the data, and only the virtual company is recorded.   |
| **Replaced by another feature?** | Use global tables to make tables accessible from all companies. Currently, there is no replacement. |
| **Product areas affected**       | All modules |
| **Status**                       | Removed as of Dynamics AX 7.0.   |

### Windows 8 tablet app

The Windows 8 tablet app provided functionality for expense entry and approval.

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Finance and Operations is compatible with tablets. The tablet app is no longer required.    |
| **Replaced by another feature?**   | No.          |
| **Product areas affected**         | Expense management   |
| **Status**                         | Removed: This functionality is only available for Dynamics AX 2012 R3. |

### Workplanner

| &nbsp;  | &nbsp; |
|------------|--------------------|
| **Reason for deprecation or removal** | Low usage |
| **Replaced by another feature?**   | No, but the **Profile relation** page, which you open from the **Profile groups** page, supports the same business scenario as the deprecated **Workplanner** page. |
| **Product areas affected**         | Time and attendance     |
| **Status**                         | The code isn't removed. However, the form, JmgWorkPlanner, wasn't migrated.    |

### X++ financial statements

| &nbsp;  | &nbsp; |
|-------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| <strong>Reason for deprecation or removal</strong> |                         This functionality is replaced by another feature.                         |
|  <strong>Replaced by another feature?</strong>  | Management Reporter (labeled <strong>Financial reporting</strong> in the current version of Dynamics AX) |
|     <strong>Product areas affected</strong>     |                                              General ledger                                              |
|             <strong>Status</strong>             |                                      Removed as of Dynamics AX 2012                                      |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
