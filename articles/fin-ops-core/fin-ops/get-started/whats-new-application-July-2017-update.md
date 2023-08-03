---
title: What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition (July 2017)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations, Enterprise edition (July 2017). This version was released in July 2017 and has a build number of 7.2.11792.56024.
author: sericks007
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition (July 2017)

[!include [banner](../includes/banner.md)]



This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations, Enterprise edition (July 2017). This version was released in July 2017 and has a build number of 7.2.11792.56024.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development.

## Introducing Dynamics 365 Finance and Operations

Users and developers will see an updated product name ("Microsoft Dynamics 365 Finance and Operations") and product icon in the web client. Some platform components (for example, the developer tools and the mobile application) that are shared by Dynamics 365 Finance and Operations, Dynamics 365 for Retail, and Dynamics 365 Human Resources will now appear as "Dynamics 365 Unified Operations."

## Financial management

### Accounts payable check templates using Electronic Reporting

Two default check format templates are provided in Accounts payable. These check templates have been created using the Excel capabilities of the Electronic reporting tool. These checks templates are compatible with US check formats.

For more information, see [Electronic reporting sample check format](../../../finance/accounts-payable/electronic-reporting-sample-vendor-checks.md).

### Budget control data maintenance

You can reprocess documents against budget control. Documents are scanned against a list of potential issues, including any budget register entries that were entered prior to budget control being enabled read-only audit trail is preserved for documents that are found, as well as the results of reprocessing.

### Budgeting Power BI for actual vs budget

The Actual vs budget Power BI content provides visibility into your budget variances based on your budget register. You can analyze budget for the current year, using any of the following details to get a better understanding of any variances:

- Account category
- Budget code
- Main account
- Main account description
- Fiscal period

For more information, see [Actual vs budget Power BI content](../../dev-itpro/analytics/ledger-budgets-power-bi.md).

### CFO Overview workspace

The CFO or accounting manager can view the full state of the business on the CFO Overview workspace. The workspace contains common KPIs and uses embedded analytics to see financials, purchasing, sales, and cash flow data.

For more information, see [CFO overview Power BI content](../../dev-itpro/analytics/CFO-power-bi.md).

### Data validation

The **Data validation checklist** workspace lets you track data validation processes across companies, areas, and people. The checklist can be used during a new implementation, after an upgrade, or after a migration. Depending on your view of the **Data validation checklist** workspace, you'll see either all tasks and statuses for a data validation project.

For more information, see [Data validation checklist workspace](../../dev-itpro/user-interface/data-validation-workspace.md).

### Delete a main account and dimension value

As companies go live, oftentimes there are main accounts or dimension values that are no longer needed. To understand when you can remove a financial dimension, see [Financial dimensions](../../../finance/general-ledger/financial-dimensions.md).

### Display payment information for an expense

This provides visibility into payment information for an expense, such as the related invoice number, payment date, and payment voucher.

### Edit account entries in the allocation journal

You can now edit the account entries in the allocation journal before posting. This means that you can make changes due to exceptions that occur periodically in the allocation process. This saves time having to regularly modify the allocation rule setup.

### Expense management mobile workspace

Many organizations require that a copy of a receipt be attached to a travel-related or business-related report that an employee submits for reimbursement. The **Expense management** mobile workspace lets users quickly create new expense lines on the mobile device of their choice by using an attached photo of a receipt. Alternatively, users can capture a photo of a receipt and then attach it to an expense report later. Employees also can create and manage their expense reports and submit for approval and reimbursement using their mobile device.

Specifically, the **Expense management** mobile workspace enables a user to:

- Take a photo of a receipt, and upload it to Microsoft Dynamics for Finance and Operations. A user can then attach that photo to an expense report later.
- Upload a file as a captured receipt. A user can then attach that file to an expense report later.
- Create a new expense line by using an attached receipt. A user can then add the line item to an expense report later, and submit it for approval and reimbursement.
- Create a new expense report.
- Attach credit card transactions and other previously created expenses to an expense report.
- Create new expenses for an expense report.
- Attach a receipt to any expense for an expense report by either taking a photo of the receipt or uploading a file as a captured receipt.
- Add the list of guests to an expense based on expense policy.
- Itemize expenses based on expense policy.
- Submit an expense report for approval and reimbursement.
- Approve or reject expense reports assigned to the employee as an approver.

For more information, see [Expense management mobile workspace](/dynamics365/project-operations/prod-exp/expense-management-mobile-workspace).

### Expense management: Configuration related to employee's card ID

In prior releases, the employee's expense credit card ID was designed to only allow up to 10 characters and displayed the last 4 digits entered as the card ID. The ability to enter more characters was required for organizations that have an agreement with their credit card company to use another key to identify an employee's credit card number without entering the credit card number. This key is often greater than 10 characters and is typically between 20 and 30 characters.

This feature has lengthened the **Card ID** field for the employee's credit card setup (**Human resources** \> **Workers** \> **Employees** \> **Expense** tab \> **Credit cards**) and provides a parameter to validate whether a 15- or 16-character number is allowed as the card ID. The parameter, **Enter employee credit card number**, is found on the **General** tab of the **Expense management parameters** form (**Expense management** \> **Setup** \> **General** \> **Expense management parameters**). By default, credit card numbers are not allowed as the expense credit card ID.

### Expense management: Configure per diem locations per country/region, state/province, and location

This feature allows expense administrators to configure the per diem locations to be set up based on country/region, state/province, and location. This configuration can provide more granular setup of the per diem rates. To use this feature, go to **Expense management** \> **Setup** \> **Calculations and codes** \> **Per diem locations**.

### Expense management: Display related payment information for an expense report

This feature provides visibility into related Accounts payable invoices that were generated for an expense report and the related payment information. Employees will have insight into the invoice number(s) and the payment voucher number for their expense reports to help them better understand the state of their reimbursement for travel expenses.

A periodic process must be run before the invoice and payment related information can be displayed for an expense report (**Expense management** \> **Periodic tasks** \> **Update expense payment information**). The **Update expense payment information** process can be set up as a recurring batch process and set to update depending on how often the organization reimburses for travel expenses.

If viewing expense reports in the grid view, columns for **Payment date**, **Payment voucher**, and **Invoice** are displayed. If multiple invoices or payments were generated for a selected expense report, the column will display **\<multiple\>**. The information is also displayed in the **Payment details** form for the expense report by clicking the **Payments** button when viewing the details of the expense report.

### Expense management: Export and import expense policies using data management

New data entities are available that enable support of the export and import of expense policies.

The following entities are available to help manage implementation of expense policies:

- Policy type (SysPolicyTypeEntity)
- Policies (SysPolicyEntity)
- Policy rule type (SysPolicyRuleTypeEntity)
- Policy organization (SysPolicyOrganizationEntity)
- Policy organization assignments (SysPolicyInternalOrganizationAssignmentEntity)
- Expense and travel policy rule (TrvPolicyRuleEntity)
- Expense policy translations (TrvPolicyLanguageTxtEntity)

### Expense management: Final approver defaulted for multi-level workflow approval

When expense management workflow is configured to use the multi-approval workflow, the default for the final approver will be based on the employee's manager. Prior to this release, the default final approver was empty and the employee had to enter the final approver and optionally set it as the default. This workflow can be configured for organizations where expense reports must go through a multi-approver process, such as having the project manager approve project related expenses or having a team administrator approve expenses prior to the employee's manager.

### Expense management: Match credit card expenses with manually entered expenses

Employees may need to submit timely expense reports ahead of credit card expenses that are being imported into the system, depending on company policy or agreements with their clients for billing purposes. When the credit card expense is not yet available for an expense report, employees can create the expense for the expense report and submit for approval and reimbursement. Later, the credit card transaction comes in and the employee is unable to remove it from the list of expenses that they need to deal with.

This feature provides support to match a credit card transaction to an existing, manually created expense from the **Expenses** form (**Expense management** \> **My expenses** \> **Expenses**) or from the **Expense report** form (**Expense management** \> **My expenses** \> **Expense reports**). If the manual expense has not yet been included in an expense report submitted for approval, the manual expense line and the credit card transaction will be merged with the credit card transaction as the master for information such as transaction date, merchant, and transaction amount. Any attached receipts, guests, or itemizations that may have been added to the manual expense line will be added to the credit card expense and the manual expense will be deleted.

If the manual expense has been submitted with an expense report for approval, matching the manual expense with the credit card transaction will remove the credit card transaction from the list of expenses for the employee. The employee can remove the match when viewing their matched expenses from the **Matched expenses** form (**Expense management** \> **My expenses** \> **Matched expenses**).

### Expense management: Split credit card expenses

There are times when a credit card transaction expense needs to be split across multiple project activities or expense categories, for example, while keeping the credit card transaction intact for credit card statement reconciliation purposes. This feature provides support for an employee to split a credit card expense across:

- Legal entities
- Expense categories
- Projects
- Project activities
- Billable/nonbillable (Project line property)

To use this feature, go to **Expense management** \> **My expenses** \> **Expense reports** or **Expense management** \> **My expenses** \> **Expenses**.

When viewing the expenses in the details view or the grid view for a credit card expense, click the **Split** button to open a form that will allow the employee to split the expense. The split expenses will be displayed for the credit card expense in the list of expenses when in the details view. A visual indicator will be displayed for credit card expenses that have been split in the grid view.

### Expense management: Support for importing credit card itemization data

Many organizations have expense policies requiring certain expenses, such as hotel, car rental, and airline expenses, to have itemization details entered before submitting the expense for approval. Organizations can work with their credit card company to receive files that contain itemization details for import. This feature provides the ability for expense administrators to set up mapping codes for the expense itemization subcategories and the ability to import the itemization details using data management.

A new form is provided to configure the mapping of the itemization subcategories to the credit card codes provided by the credit card company. To import the file provided by the credit card company, the system administrator can import the file using data management by selecting to import into the **Credit card itemizations** entity (TrvPBSItemizationsEntity).

To use this feature, go to **Expense management \> Setup \> Calculations and codes \> Subcategory codes**.

### Expense management: Usability enhancements

Multiple features have been added to improve the usability of creating and managing expense reports. Enhancements include:

- A new **Expense management** workspace to simplify the navigation for creating and managing expense reports.
- Ability for an employee to view their list of expense reports in a grid view.
- Providing visibility to the employee that a receipt is required for an expense when the expense is saved or modified, depending on company policies. A visual indicator is displayed for the expense if viewing expenses in detail. If expenses are displayed in grid view, columns for **Receipt required** and **Receipt attached** are displayed.
- The details view will be displayed as the default with a view. Receipts, guests, itemizations, and financial dimensions will be displayed next to the expense details in the same view. The employee will be able to easily find how to enter this information for a selected expense.
- Enhanced visibility into expenses with policy violations by providing a visual indicator with the expense. The visual indicator will include hover text that displays the message provided by the expense policy.
- Simplified entry of itemizations for an expense including the ability to copy itemizations from one day to the next.

### Expense management: View detailed workflow history for an expense report

The workflow history for an expense report can be complicated depending on how many levels of approval your organization has or if the expense report has come back to the submitter multiple times for various reasons. This feature will provide a more user-friendly way to view the workflow history for an expense report. Clicking the **View history** button opens the **View history** form and displays the workflow history, including any comments provided at each workflow step.

### Financial dimensions in Financial reporting report definition

You can select what financial dimensions are relevant for a report in the Financial reporting report definition. For example, if you're generating a balance sheet, and the organization only wants to evaluate it by main account and business unit, you can select those as the financial dimensions for the report. You will only see those in the drill down and analysis. This helps personalize and make the reporting experience more streamlined, only presenting the information that is necessary for a report.

### Financial dimensions in Power BI

The financial dimensions in the Financial performance content pack are now available for analyzing financial data. For more information, see [Financial performance PowerBI.com solution](../../dev-itpro/analytics/financial-performance-power-bi-content-pack.md).

### Financial report generation

You can generate financial reports from the Financial reports list page and select the date and units of the reporting hierarchy. This saves time because you no longer need to view a prior version of the report. You can open the Report designer, and only view the units of the reporting hierarchy that are relevant.

### Maintain carry-forward status

This feature provides an alternate way to report on carry-forward budget. This maintains the carry-forward status on relieving documents, which are based on an originating document that was carry-forward.

### Map credit card data (itemization details)

This feature allows you to map level 3 credit card data (itemizations) to subcategories, which makes it easy to import itemization details received from your credit card company.

### Mobile invoice approvals

New mobile capabilities allow you to review and approve vendor invoices that have been submitted through workflow using a mobile device.

For more information, see [Mobile invoice approvals](../../../finance/accounts-payable/mobile-invoice-approvals.md).

### Configuration data packages

Configuration data packages are available as process data packages from Lifecycle Services (LCS) for core Financial modules. These data packages can help improve the repeatability of implementations and accelerate the configuration of Dynamics 365 Finance and Operations.

The data packages contain configuration entity spreadsheets. These entity spreadsheets have best practice data, which you can use to create an initial 'golden' build. The data entities in the data packages are also sequenced appropriately, to help ensure a successful single-click import of the data. For more information, see [Configuration data packages](../../dev-itpro/data-entities/configuration-data-packages.md).


### Save Financial reports to SharePoint

The standard functionality for sending reports to SharePoint is now available for reports generated through Financial reporting. When choosing to export or print a generated financial statement, you can now select to publish the financial report to SharePoint. Using the standard functionality, you can define a notification when a report is available.

### Suspended and inactive dimension values hidden from dimension value lookups

When a company decides to no longer use a specific dimension value, the value is hidden from the dimension value lookups. This makes the user experience consistent with the segmented entry control, and prevents re-active steps when validation messages are experienced during posting.

You will see the date that used to determine whether the financial dimension value is active. If you want to see all possible financial dimension values, click **Show all**.

### Travel requisition functionality (Dynamics AX 2012 parity)

This feature enables the travel requisition functionality in parity with Dynamics AX 2012. Employees can create and submit travel requisitions for approval and reconcile them with expense reports. Your organization may require that a travel requisition be submitted before an employee incurs an expense that is charged to the organization. This applies whether the employee is charging expenses to a corporate credit card, spending cash received from a cash advance, or incurring out-of-pocket expenses that will be reimbursed by the organization.

Travel requisitions and policies can be used to help with budget control. For example, if your organization is working on a fixed-price project that requires travel, the travel expenses of the project team members must fit within the budget of the project. Requiring that travel expenses be approved before they are incurred can help to ensure that the project stays within budget.

### Vendor invoice attachment enhancements

As organizations look to streamline their Accounts payable processes, invoice processing is often one of the top process areas that needs efficiency. Oftentimes, organizations offload the paper invoice processing to a third-party optical character recognition (OCR) service provider to get machine readable invoice metadata along with the scanned image of the invoice. To help with automation, a solution is built in the invoicing system to enable consumption of these artifacts. Dynamics 365 Finance and Operations enables this automation out of the box. 

The basic premise of invoice automation is to enable a standard interface that can accept invoice metadata for invoice header and invoice lines, as well as the attachments that are applicable to the invoice. Any external system that can generate the artifacts and comply with the interface will be able to send the feed to Finance and Operations for automatic processing of invoices and attachments. 

The following components make up the solution footprint of vendor invoice automation. 

- Data entities for invoice header, invoice lines, and invoice attachments. 
- Exception processing for invoices. This is a business user-friendly UI to manage invoices that failed to get created.
- A side-by-side attachment viewer in invoices in exception handling forms, pending invoices, and invoice journal inquiries.

For more information, see [Vendor invoice automation](../../../finance/accounts-payable/vendor-invoice-automation.md).

### View detailed workflow history for an expense report

The workflow history for an expense report can be complicated depending on how many levels of approval your organization has or if the expense report has come back to the submitter multiple times for various reasons. This feature provides a more user-friendly way to view the workflow history for an expense report.

## Financial management \| Supply chain management

### Cross legal entities reporting in Cost accounting

This feature lets you run multiple legal entities on different versions or instances of the same version by connecting the data from instances in Dynamics AX 2012 R3 CU11 or later to Dynamics 365 Finance and Operations. You can cross the boundaries of legal entities to address both organizational and statutory reporting needs.

For more information, see [Cost accounting overview](../../../finance/cost-accounting/cost-accounting-home-page.md).

### Cost accounting allocation bases

The allocation base feature has been extended so Cost accountants can create an allocation base that matches their requirement.

The following allocation base types have been introduced:

- **Predefined dimension member allocation base** – All cost element dimension members and statistical dimension members are, by default, created as predefined dimension member allocation bases.
- **Formula allocation base** – A formula can include one or more allocation bases of any type and can include user-defined constants. The following operators are supported: + , - , \* , = , \< , \> , ( , )
- **Hierarchy allocation bases** – Combine an allocation base of any type with a cost object dimension hierarchy node to limit the range.

For more information, see [Allocation bases](../../../finance/cost-accounting/allocation-bases.md).

### Cost accounting dimension hierarchies

Cost accounting dimension hierarchies provide a way for you to move a hierarchy node to a new parent node in the hierarchy or perform a simple re-order of nodes within a parent node by using the **Move up** or **Move down** buttons. This significantly reduces amount of the time spent maintaining dimension hierarchies.

For more information, see [Dimension hierarchies](../../../finance/cost-accounting/dimension-hierarchy.md).

### Cost accounting Get started wizard

The Get started wizard provides an easy way to get started with Cost accounting. Basic master data and reference data is automatically generated based on how you answer a few simple questions in the wizard.

Transactional data is also processed, which allows you to populate the Cost control workspace with your own data.

The wizard provides a good foundation for further exploring the capabilities of Cost accounting.

For more information, see [Get started with Cost accounting](https://youtu.be/1pUDtJQZ8FU).

### Cost accounting ledger administration workspace

The Cost accounting ledger administration workspace provides Cost accountants with an overview of the status of individual cost accounting ledgers. All functions required for the administration of a cost accounting ledger can easily be accessed directly from this workspace.

The health of the cost accounting ledger and its related master data and reference data are monitored, such as cost objects dimensions, dimension hierarchies, and rules. This makes it easy to manage cost accounting ledgers.

For more information, see [Cost control mobile workspace](https://youtu.be/imsuTg8rUVk) and [Use Excel for cost analysis](https://youtu.be/-HKHYdClvx8).

## Globalization & translation

### Belgian Enterprise number Registration ID is used for customer and vendor accounts

The enterprise number is a unique identification code assigned by the Belgian government to each Belgian company to replace the nine-digit VAT number. For example, the enterprise number can be assigned to vendor accounts and customer accounts. The enterprise number is used for regulatory reporting, to generate the EU sales list, the Annual sales list, or to declare VAT.

Setup of the enterprise number for vendor and customer accounts was aligned with how setup was previously used for legal entities. Now it uses Registration IDs and enterprise number setup for reporting.

### Enhancements to the German audit file (GDPdU)

The following enhancements have been implemented to the GDPdU\\GoBD sample electronic reporting configurations:

- Significantly improved performance with use of filter() function in calculated fields.
- Primary registration numbers for customer and vendor accounts are now exported instead of tax exempt numbers.
- Labels are used in configurations.
- Encoding of index.xml file is updated.
- DTD file attachment embedded in the format configuration.

For more information, see [German audit file (GDPdU/GoBD)](../../../finance/localizations/emea-deu-gdpdu-audit-data-export.md).

### Global coverage – Configurable Electronic Reporting

The following features have been added to the Electronic Reporting (ER) engine.

**Improved ER configurations management** – You can now designate, other than application's hotfixes, software components as prerequisites for an ER configuration. Each version of ER configuration can be marked as dependent on a specific version (or range of versions) for the following software:

- Application
- Application model
- Application hotfix package
- ER configuration

Information about prerequisites is used to automatically recognize and import to your instance of the application the only compatible ER configuration to ensure smooth functioning. You can also check the compatibility of a selected ER configuration with your current environment. Doing this, you will be informed about all prerequisites required to successfully run that ER configuration and missing in the current application. That will allow you to install prerequisites in advance.

**Management of ER model mappings independently from ER models** – You can now manage your data models in ER model configurations that do not contain model mappings. This means that you can maintain your single data model as an abstract definition of a certain business domain independent from any application that provides this model with actual data at run-time. In addition, you can manage application-specific model mappings in ER model mapping configurations. The same ER model can be used in different applications with different application-specific ER model mapping configurations. With this approach, when you have an ER model with multiple subordinated ER formats and need to migrate them to another version of the application or even to a new application, you only need to update the appropriate ER model mapping, if needed. This allows customers to significantly reduce the effort needed to complete such migration.

**Improved Office-based reports** –  You are now able to configure ER reports for generation of outputs in Office formats (Excel and Word) that contain images and shapes. This allows customers to easily satisfy specific requirements to present images and shapes in generated documents (for example, in payment checks) company logo, signatures, QR codes, etc.

**Configurable update of application data** – You can now configure a single ER format for generation of outgoing electronic documents and update of application data based on information of outgoing documents within a single execution. This allows customers to configure (without coding) the following scenarios using ER framework:

- When a customer wants to mark application data right after its usage for generation of electronic documents, to prevent repeated usage in subsequent processes.
- When a customer wants to store the details of document processing that have been generated by using ER logic, to consume these details later in post-reporting processes.

**ER configurations design improvement** – We improved the ER Operation designer so that a business person can design abstract data models and formats of business documents using these models as data sources, without dependency on data model mappings. An application specialist can design model mappings for this data model in parallel and independently from a business person. The completed model mapping will be needed only at run-time. This empowers customers to quickly complete all necessary components of the entire ER solution.

**Improved design of Excel-based reports** – We improved ER Operations designer to better support Excel-based reports. With just a few clicks, you can now synchronize the structure of earlier designed and already available ER format with the content of the updated Excel document that is used as a template for generating electronic documents. This allows customers to quickly adopt new requirements for recipients waiting for generated by ER reports in Office formats.

**Extended ER parameters** – We introduced a new parameter to configure the number of parallel threads for importing ER configurations from the Lifecycle Services (LCS) asset library. This allows customers to improve communications with the LCS service and improve performance.

**JSON format support** – You are now able to configure a single ER report for generation of output in JSON format. This allows customers to easily satisfy requirements for specific recipients like web-based services.

**New built-in functions** – We introduced several new functions that can be used in ER expressions. This enables customers to configure required business logic: support necessary data types transformation to align incoming information with structure of application data, generate QR codes to present them in generated documents as images, etc.

**Electronic reporting features as configurations** – We continued moving electronic reporting features of the application to ER framework, to simplify further customization of these features by our partners and customers and allow for easy upgrade in case of regulatory changes. More than 170 features for 34 released countries/regions have been ported to ER configurations, including all payment formats to handle outgoing and incoming messages and all formats for electronic invoices.

### Global coverage – Languages

This feature allows ISVs and partners to create a new language in Dynamics 365 Finance and Operations, including managing this process throughout upgrades and updates of source labels via extensions.

### Global coverage – Retail

Regulatory Retail features for Sweden have been added to support local requirements for cash registers, including general requirements to continuous use of cash registers, as well as an example of integration of Retail POS with a fiscal device (control unit).

For more information, see [Cash registers for Sweden](../../../commerce/localizations/emea-swe-cash-registers.md).

### Reverse charge functionality for European countries/regions

You can configure reverse charge applicability rules per document type (purchase/sales order, vendor invoice, free text invoice, etc.) and a reverse charge group that combines items, items groups, and purchase/sales categories. The applicability rules are date effective. You can also mark individual sales tax codes in sales tax groups as applicable for reverse charge. The sales invoice report is adjusted to represent details of the applied reverse charge. The functionality has been made available to all European countries/regions.

For more information, see [Reverse charges](../../../finance/localizations/emea-reverse-charge.md).

### Substitution/adjustment invoices for Thailand

The Substitution/adjustment invoice feature has been implemented to track printing of copies of invoices. When a copy of an invoice needs to be printed, it is required to specify the reason for the substitution. A special remark is printed in the invoice copy that includes the reason of the substitution and the number of copies printed.

In addition, if the Adjustment option is used, it is also possible to adjust the customer information printed in the invoice, including the customer name, address, contact information, tax registration number, and branch number and name. The Adjustment invoice gets a new invoice number and date, and references the original invoice.

### Tax invoices and tax reports for Thailand

Tax invoice and other tax report layouts have been adjusted to comply with local requirements in Thailand. Sales invoices, free text invoices, debit/credit notes, and project invoices can now be printed using the Thai tax invoice layout. The Purchase/Sales VAT reports and the Withholding Tax Certificate report have also been amended.

Several enhancements have been implemented to the invoicing process. Tax registration number and Branch number are now required in the Vendor master. It is not possible to post a vendor invoice with a date in the future or older than 6 months. Return reason is required for sales credit/debit notes. Original invoice reference and amount are copied to a sales credit/debit note.

## Human resources

### Benefits workspace

Benefits workspace allows you to easily view and manage benefits offered to workers in a central location. This workspace lets you:

-Gain insight into benefits not being used by employees.
- View which benefits are being phased out at the end of the year.
- Keep track of benefit costs and how costs may have changed in the past year.

### Configurable business processes

The Configurable business process feature allows you to create a business process template for processes that need to be completed within your organization. For example, your company may have a HR audit that is performed each year. A template can be created to track all the tasks that need to be completed as part of the audit process. Templates can be re-used or copied for recurring processes.

After a template is created, you can start a process, and track it in the **Business process** workspace. When a business process is started, the tasks will be assigned to the appropriate individuals with the appropriate due date.

Configurable business processes let you:

- Define templates for processes within your organization.
- Define calendars to apply to tasks for all processes.
- Define a process owner for each business process template.
- Analyze past due tasks and identify bottlenecks in the process.
- Provide instructions to all tasks.
- Assign checklists at any point in the process.
- Re-assign tasks and update due dates.

### Direct deposit

Within ESS individuals can set up their direct deposit information, which lets employees easily distribute their paycheck to multiple accounts.

Direct deposit lets employees:

- Add multiple bank accounts.
- Set priority of bank disbursements.
- Direct any remaining funds to a specific account.

### Employee and manager self-service

Employee self-service (ESS) and Manager self-service (MSS) pages offer a single location for employees to view and update their personal information, as well as view upcoming activities. Employees can view all items that have been assigned to them and review their compensation.

Managers can view anyone in their organization from a single workspace, including employee summaries, position assignments, compensation, and performance.

### Mobile – Company directory and My team mobile workspaces

The mobile solution includes two new workspaces to provide a phone experience for employees and managers. All employees will have access to the company directory as a direct line of contact with others in the organization. Managers can view information about their team or any individual within their organization.

Company directory mobile workspace provides the following:

-Contact list for all employees in the organization.
- Search for any employee or contractor.
- View public information.
- Call, text, or email individuals from the director.

For more information, see [Company directory mobile workspace](../../dev-itpro/mobile-apps/company-directory-mobile-workspace.md).

My team mobile workspace provides the following:

- View your direct reports and all employees in your organization.
- View team members and open position.
- View key information for employees and contractors.
- Send praise.

For more information see [My team mobile workspace](../../dev-itpro/mobile-apps/manager-self-service-mobile-workspace.md).

## Intelligence

### Analytics and insights through Power BI

Gain deeper insight about your most valuable resource, your people, using the flexible and comprehensive analysis provide by Finance and Operations. By taking advantage of Power BI, Finance and Operations provides embedded analytics that contains data visualizations that allow you to gain a deeper understanding of the talent in your organization.

Analytics and insights provide the following data and visualizations:

- Benefits management
- Benefit plan analysis
- Employee group enrollment metrics
- Compensation management
- Compensation plan analysis
- Compensation analysis
- Position pay analysis
- Personnel management
- People metrics
- Headcount and FTE analysis
- Workforce demographics
- Attrition analysis
- Employee milestones
- Recruitment management
- Recruitment project analysis
- Applicant analysis
- Recruiting costs
- Applicant status

For more information, see [Power BI content home page](../../dev-itpro/analytics/power-bi-home-page.md).

## Cash flow forecasting Power BI

Managing cash flow effectively is a key function of the finance division in your organization. Cash flow analysis Power BI reports provide visibility into your cash flow and provide forecasts that allow you to make better decisions leading to healthy cash flows.

You can analyze your future cash inflow and outflows, both at a high-level summary and at detailed levels. You can analyze cash inflows by legal entity, bank account, and currency to get a better understanding of surpluses and short falls. Overall, you can get a temporal view of gaps and address them proactively.

For more information, see [Cash flow forecasting](../../../finance/cash-bank-management/cash-flow-forecasting.md).

### Cost accounting Power BI reports

Cost accounting Power BI reports provide the ability to build rich visualizations for C-level managers highlighting the performance of the entire organization in a common currency

These reports allow you to view performance at any organizational or individual cost object level, such as cost centers and product groups. You can validate overhead calculation and view the net change by cost object origin from cost center allocations with cost roll-up details.

You can also combine statistical elements and cost elements by cost objects.

For more information, see [Cost accounting analysis Power BI content](../../dev-itpro/analytics/cost-accounting-analysis-content-pack.md).

### Credit and collections management Power BI

The Credit and collections management Power BI content pack provides deep insights into your credit management and collection process to help you effectively manage your credit and collections. This is an indispensable tool for credit and collection managers, collections clerk, as well as account managers, in that it provides the information needed to make decisions backed by data. Using key measures such as days sales outstanding (DSO) and customers over credit limit, you can locate customers, customer groups, and regions that are contributing to poor collections. You can take corrective action backed by data to avoid process delays and bottlenecks.

You can use this tool to provide rich insights to your account and sales managers on customers' collection performance, to enable them to identify valuable customers. You can encourage your customer-facing staff to seek valuable partnerships backed by data, and encourage sales staff to promote products and services with the right combination of pricing and terms. Power BI reports help you to become a master of managing by exception. You can identify customers over or nearing their credit limits and understand the likelihood of payment delays and past due payments, so that you can intervene before it's too late. Reports can be used to detect payments and customer groups before they reach past due stage, so you will be able to understand probabilities of past due payments and define alert conditions to notify you in case of exceptions. Comprehensive reporting and dashboard capabilities built into Power BI mean that your collections and account management teams can proactively manage their customers. 

For more information, see [Credit and collections management Power BI content](../../../finance/accounts-receivable/credit-collections-power-bi.md).

### Embedded Power BI reports licensed for all users

In the August 2016 update of Dynamics 365 for Operations (referred to as Dynamics AX 7.0), users could pin full page Power BI reports to their workspaces. With full page, interactive reports, you could explore data and perform what-if analysis over large volumes of data. Accessing and pinning Power BI reports required you to have a PowerBI.com subscription. As additional reports are delivered by Microsoft and our partner ecosystem, Power BI capability is becoming a crucial reporting option for all users of your organization.

All user can now access Power BI reports based on Entity store, the operational data warehouse that is included with Dynamics 365 Finance and Operations, Enterprise edition.

No Power BI licenses are required to access these reports, which are embedded in the Finance and Operations application. If a user requires access to Power BI reports and functionality outside of this embedded experience, a Power BI license must be obtained separately. Features that were introduced to pin tiles and reports from PowerBI.com will continue to be supported.

### Embedded Practice manager Power BI content

The Practice manager Power BI content pack has been embedded into the Project management workspace **Analytics** tab.

The Practice manager Power BI content pack is also available in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS.md).

The Practice manager Power BI content was created for practice managers and project managers. It provides key metrics that are related to the projects that the organization is working on. The content gives an overview of the projects and related customers. The Power BI content pulls data from the project accounting aggregate measurements for Microsoft Dynamics 365 Finance and Operations.

The Practice manager Power BI content contains five report pages: one overview page and four pages that provide details about project costs, revenues, earned value management, and hour metrics that are split out across various dimensions. For more information, see [Practice manager Power BI content](../../dev-itpro/analytics/practice-manager-power-bi.md).

### Fixed asset management workspace and embedded Power BI content

The Fixed asset management workspace provides accountants quick access to their fixed asset data. It has information regarding asset acquisitions and disposals, as well as direct navigation to the depreciation proposal and fixed asset journal. The Find fixed assets section allows you to search for specific assets by number, group, name, location, or person responsible and easily view financial details about the assets and associated books.

Embedded Fixed asset management Power BI reports provide CFOs and Operations management with deep insights into fixed assets, including acquisitions, book value, and depreciation.

You can view key asset book lifetime metrics, such as net book value (NBV.md), depreciation, and accumulated depreciation by asset category and location. You can dive into patterns and understand trends that lie hidden beneath the data, and make strategic decisions, such as major upgrades and plant re-tooling proactively, backed with data.

For more information, see [Fixed asset management workspace](../../../finance/fixed-assets/fixed-asset-management-workspace.md).

### Power BI reporting with financial dimensions

Financial dimensions are user defined "configuration" data that enables the ledger chart of accounts to retain additional information. By adding financial dimensions, a user can configure additional data fields to be included with the chart of accounts as well as with Financial reports. This enables the ledger chart of accounts to be sliced and diced with those fields.

This is very powerful in Financial analysis and reporting because you will be able to explore ledger data using the newly added financial dimensions. With this capability, when Entity store is refreshed, all available Financial dimensions are expanded within corresponding data tables. As a user, you can slice and dice your Power BI reports with ease.

Ready-made Power BI reports in Finance and Operations benefit from this capability without a developer having to make any changes. However, as a partner or an ISV developer, you can model the ways in which financial dimensions are added to Entity store. When you define an aggregate measurement that is backed with financial dimension fields, Entity store refresh automatically expands the aggregate measurement by adding additional tables and relationships into the data model. 

You can empower your users to create Power BI reports that leverage this capability. When you define a report with modeled financial dimensions, they can be refreshed to include expanded fields.

For more information, see [Add financial dimensions to aggregate measurements](../../dev-itpro/analytics/add-financial-dimensions-aggregate-measurements.md).

### Purchase spend analysis Power BI reports

The Purchase spend analysis content pack for Microsoft Power BI was created for purchasing managers and managers who are responsible for budgets. It's designed to help them monitor purchase spending. It uses purchase transactional data from Dynamics 365 Finance and Operations and provides both an aggregate view of the company-wide purchase figures and a breakdown of purchase spending by vendor and product. Reports highlight changes in purchase spending over time. Therefore, they can be used to alert managers about positive and negative spending trends for individual vendors and products. Charts show purchase spending for different procurement categories and vendor groups. Category and regional managers might find it useful to use these charts to help identify changes in spending behavior. The content pack lets purchase managers and managers who are responsible for budgets to analyze purchase spending in the following ways: 

- Year-to-date purchase (by vendor group and individual vendors, procurement category and individual products, and vendor location).
- Year-over-year purchase change (by vendor group and procurement category).

The Purchase spend analysis Power BI content pack is available via the Lifecycle Services (LCS) Asset library and as an embedded report in Dynamics 365 Finance and Operations.

For more information, see [Purchase spend analysis Power BI content](../../dev-itpro/analytics/purchase-content-pack-for-power-bi.md).

### Purchasing analysis Power BI content

The Purchasing analytics Power BI content pack equips purchasing managers with deep insights that enable them to streamline their processes, and manage the cash flow while building relationships with suppliers.

Whether you are a distributor or a manufacturer relying on strategic suppliers or a professional services company leveraging services of suppliers, as a purchasing manager, you are responsible for managing vital relationships. With comprehensive visibility into orders, payments, and payables, you can manage processes and take action where needed.

Power BI reports can be used foster relationships with your strategic suppliers by ensuring compliance with pre-negotiated payment terms. You can quickly dive into exceptions and delays to take corrective action, as well as analyze trends and define alerts to be notified in case of exceptions.

As a purchasing manager, you contribute to the financial health of the company. Power BI reports let you identify large payments and decide whether you should negotiate early settlement discounts proactively. You can also analyze options such as paying early versus waiting for the due date. By taking a strategic view of payments, you can help to proactively manage cash flow.

Monitor and improve the effectiveness of your internal processes by reviewing the case load of invoices. Get insights into key metrics such as Number of days spent from receipts to posting. Load balance invoice processing among your staff members by reviewing and forecasting the case load.

Comprehensive reporting and Dashboarding capabilities built into Power BI enables your purchasing managers to monitor, analyze and take action backed by data. They can author reports and KPIs without help from IT and pin them to workspaces for contextual insights.

### Sales and profitability performance Power BI reports

This content pack was created for sales managers to monitor the key sales metrics of revenue, gross profit, and profit margins. It uses sales transactional data from Dynamics 365 Finance and Operations, Enterprise edition and provides both an aggregate view of the company-wide sales figures and a breakdown of sales performance for customers and products. By highlighting changes in the revenue and profit growth over time, reports can be used to alert managers about positive and negative trends for individual customers and products. Category and regional managers will find it useful to have charts that compare revenue and profitability of different product categories and customer groups to each other to single out laggards and leaders. A comprehensive report that plots individual customer's revenue versus profit margin offers account managers a data-backed foundation to attune their sales and marketing efforts to each customer's respective profile. The Sales and profitability performance content pack enables sales managers to analyze sales performance by: 

- Revenue, year-to-date (by customer group and individual customers, sales categories, and individual products and geographies).
- Revenue change, year-over-year (by customer regions and sales categories).

Profitability can be analyzed by:

- Gross profit and profit margin (by customer groups and product sales categories).
- Gross profit change, year-over-year.
- Customer profitability (by revenue versus gross margin).

The Sales and profitability performance Power BI content pack is available via the Lifecycle Services (LCS) Asset library and as an embedded report in Dynamics 365 FinanceFinance and Operations.

For more information, see [Sales and profitability performance Power BI content](../../dev-itpro/analytics/sales-profitability-performance-content-pack.md).

### Vendor payment analysis Power BI

Vendor payment analysis Power BI reports provide visibility into your open invoices and posted vendor payments, enabling better decisions in your account payable processes. You can analyze overdue invoices, upcoming invoices that are due in the future, as well as your discount history.

For more information, see [Vendor payment workspace](../../../finance/accounts-payable/Vendor-payments-workspace.md).

### Warehousing Power BI reports

With Warehousing Power BI reports, the warehouse and supply chain manager can easily take advantage of the rich visualization and dashboard capabilities to analyze warehouse performance in the past, present, and future.

Warehouse and operations managers can monitor the key inbound, outbound, and inventory metrics. This feature uses product and other transactional data from Dynamics 365 Finance and Operations to provide both an aggregate view of the warehouse performance and a breakdown for customers, vendors, product groups, and product sites and warehouses. For more information, see [Warehouse performance Power BI content](../../dev-itpro/analytics/warehouse-power-bi-content.md).

## Manufacturing

### Cross docking from production to transfer orders

A new option allows you to do cross docking from a production or batch order to released transfer orders. This is relevant in manufacturing scenarios if the material that's been produced is immediately transferred to remote warehouse and distribution centers and not stored at the production site. A work policy is used to query for cross docking opportunities. This includes the product and the location for the produced goods.

### Flushing principle Available at location

A new flushing principle, Available at location, allows you to indicate that material should be automatically consumed with a picking journal when it becomes available on the production input location. The material either becomes available when warehouse work for raw material picking is completed or it is already available on the production input location, when it is released from the production order.

The new flushing principle can be helpful for long-running production orders, such as machine assemblies, from where material is picked on a continuous basis to be consumed in the area where the machine is assembled. With this new flushing principle, the material is automatically flushed when picking of the material is completed. This will help you maintain a correct value of work in progress without having to manually register and post the material consumption each time pick work is completed.

### Optimize scheduling for planned production orders with overlap jobs

The enhanced scheduling functionality optimizes how planned production orders are scheduled when there are overlapping jobs and resources with different calendars. With this setup, you can avoid scheduling planned orders too early.

### Production output location added to the resource group member

The Resource group member is now part of the defaulting mechanism that you can use to find the production output location when you report a production or batch order as finished. The Resource group member supports a definition of the output location per resource, which allows for more granularity than when the output location is defined per resource group.

The mechanism for defaulting the production output location, when reporting a production or batch order as finished, has so far been controlled by a defaulting hierarchy where the search for an output location starts by the resource group that was used for the last operation in the production route. If no output location was defined on the resource group, the system will use the output location defined on the warehouse as a fallback location.

The defaulting hierarchy has now been enhanced to also include the Resource group member. The Resource group member associates the resource to a specific resource group and is date efficient with an Effective date and an Expiration date. The Resource group member is located on the **Resource group** page under the **Resources** FastTab or on the Resource page under the **Resource groups** FastTab. The default production output location is now found by traversing the hierarchy in this order: Resource group member, Resource group, Warehouse.

### Turn off planning processes per company

Master planning takes a snapshot of the item's net requirements before planning. The last step in the planning process is to take into consideration any changes that may have occurred in the net requirements since the snapshot was taken. All changes to the item's net requirements, such as a sales order line quantity increase or transfer order line quantity decrease, are logged in a table called **InventSumLogTTS**. This table is used to maintain the state of the dynamic plan, by keeping track of all changes in demand and supply that occurred since the last master planning regeneration. This table is only cleaned up by a master planning regeneration. If it is never cleaned, the table keeps growing and clogs system performance. If you do not intend to run master planning or any other planning processes (explosion, production order scheduling with finite material, CTP delivery date control) in a specific company, set the **Master planning** \> **Setup** \> **Master planning parameters** \> **Disable all planning processes** parameter to **Yes**. This will prevent records from being logged in the **InventSumLogTTS** table.

When a new company is created, this parameter is by default set to **Yes**. This means that if you intend to implement planning processes in a company, you need to manually set **Master planning** \> **Setup** \> **Master planning parameters** \> **Disable all planning processes** parameter to **No**.

### Visual scheduling

The capabilities of the production Gantt have been enhanced to allow jobs in the production order view to be moved along with dependent jobs. You can switch the sequence of jobs on a resource. You can also trigger re-scheduling from the Gantt and show resulting actions and delays, which allows the ability to re-assign a job to a different resource.

### Withdrawal kanban for warehouse processes

Support has been added for the withdrawal of kanban in production to replenish material on the production floor for lean, discrete, and process manufacturing. This makes it possible to release work for kanban picking for the withdrawal kanban, so that items can be picked from non-fixed locations in the warehouse.

### Lean scheduling board

A new scheduling board for kanbans has been introduced. The kanban board offers these main capabilities.

- A graphical overview of scheduled kanbans in a work cell for a selected period.
- Tools to schedule unplanned kanban jobs.
- Reschedule already scheduled jobs as a drag-and-drop activity.
- Reassign kanban jobs across time periods.
- An overview of the work cell capacity and capacity load that is updated when new kanban jobs are loaded to the board.
- Use of colors to distinguish between kanban jobs.
- Detailed information about the kanban and status icon showing when a kanban is overdue.

In the kanban schedule board, these call outs are added to key elements.

- Menu bar
- Filter fields
- Button for unplanned jobs
- Period node
- Kanban job
- Capacity bar
- Time scale

## Mobile

### Cost controlling mobile workspace

The **Cost controlling** mobile workspace provides an instant view of the current performance of cost centers by comparing actual costs against the budgeted costs. You can drill down to view statuses of individual cost elements.

The data in the **Cost controlling** mobile workspace is secured by user credentials. Cost center managers are only allowed to view data for the cost center that they own. The access-level security is managed in the Cost accounting module.

### Inventory on-hand mobile workspace

We know that every company has multiple shipments and multiple receipts of inventory each day, and that these movements constantly affect the inventory on-hand status. We have introduced a cross-organizational, on-hand view that can be accessed in any place, at any time, by people working in the warehouse, purchasing, sales, manufacturing, management, and other roles. We have enabled instant viewing of the on-hand status across facilities and enabled actions to be carried out from the mobile device such as: view on-hand across facilities, view current material reservations, view unreserved on-hand, view pending material movements (inbound/outbound), scan item numbers or license plates to query on-hand inventory, and create advanced view filters.

This mobile workspace empowers people to get mobile insights in current reserved/available stock levels at any time, in any facility.

### Purchase order approvals mobile workspace

This functionality allows users to review and approve purchase orders that have been submitted through workflow using their mobile device.

### Sales orders mobile workspace

View sales order details, sales order lines, status, customer contact information, order taker contact information, and historical shipping transactions. This mobile workspace will empower salespeople to gain valuable insights into customer information and sales orders at any time and in any place.

### Vendor collaboration mobile workspace

With the **Vendor collaboration** mobile workspace, vendors can stay up-to-date on the purchase orders that have been sent to them for approval. This also allows vendors to view information about new and updated purchase orders and view contacts.

## Other

### Configuration data project templates

Configuration data project templates provide over 20 pre-defined lists of entities for each module area. The templates are sequenced to handle entities that are dependent on other entities. You can add one or more templates to a configuration data project and the sequences will align correctly.

For more information, see [Configuration data templates](../../dev-itpro/data-entities/configuration-data-templates.md).

### Upgrade

You can upgrade from Dynamics AX 2012 to Dynamics 365 Finance and Operations. The complete Dynamics AX 2012 database can be brought forward, and your AX 2012 codebase can be upgraded to finance and operationsFinance and Operations. You can migrate from Dynamics AX 2009 to Finance and Operations via a migration toolset to bring forward master data and opening balances.

Upgrade is now more predictable, which reduces the overall cost of the upgrade process. Upgrade kicks off with an automated analysis phase, which defines the preparation tasks required to reduce the time and cost to upgrade, as well as the ongoing future cost of Finance and Operations. Post upgrade, an automated validation phase provides statistics and metrics on the success of the upgrade process. The validation details can be used to quickly assess the state of the upgrade, so you can continue with functional testing and sign off.

In Finance and Operations there are no expensive upgrades needed to stay current and take advantage of continuous innovation. You can update to the latest versions of the product with a click of a button. The product supports rich customizations but the need for costly code upgrade is gone. Extensions-based customizations easily migrate with every upgrade. New features introduced in the product are opt-in, which means that business processes will not be affected by the upgrade process. The Administrator can enable new features using the product post-upgrade, as they see fit. To minimize risks, upgrade enforces a workflow of an upgrade sandbox, validation, and then release to production.

For more information, see the following topics:

- [Upgrade from AX 2012 to finance and operations](../../dev-itpro/migration-upgrade/upgrade-overview-2012.md)
- [Upgrade from AX 2012 - Plan by using the Upgrade analyzer tool](../../dev-itpro/migration-upgrade/upgrade-analyzer-tool.md)
- [Upgrade from AX 2012 - Estimate effort by using the Code upgrade service](../../dev-itpro/migration-upgrade/analyze-code-upgrade.md)
- [Upgrade from AX 2012 - Deploy a demo environment for analysis](../../dev-itpro/migration-upgrade/analysis-sandbox.md)
- [Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade](../../dev-itpro/migration-upgrade/prepare-data-upgrade.md)
- [Upgrade from AX 2012 - Data upgrade in development environments](../../dev-itpro/migration-upgrade/data-upgrade-2012.md)
- [Upgrade from AX 2012 - Data upgrade in sandbox environments](/d365F-O/fin-ops-core/fin-ops/get-started/data-upgrade-self-service)
- [Upgrade from AX 2012 - Post-upgrade tasks](../../dev-itpro/migration-upgrade/app-validation-process.md)
- [Upgrade from AX 2012 - Cutover testing (Mock cutover)](../../dev-itpro/migration-upgrade/upgrade-cutover-testing.md)
- [Upgrade from AX 2012 - Functional test passes](../../dev-itpro/migration-upgrade/upgrade-functional-validation.md)
- [Upgrade from AX 2012 - Prepare for go-live](../../dev-itpro/migration-upgrade/upgrade-go-live-prep.md)

## Project management \| Accounting

### Allow a project resource to delegate timesheet entry and submission to any user

A timesheet resource can have a delegate assigned who can enter and submit timesheets on behalf of the resource. This feature provides the ability to assign a delegate who may not be employed in the same legal entity as the timesheet resource. The delegate does not need to be set up as a project resource. A new security role (Timesheet delegate user) has been created and must be assigned to anyone who is designated as a timesheet delegate. To use this feature, go to **Project management and accounting** \> **Setup** \> **Timesheets** \> **All delegates**.

### Assign resources to draft work breakdown structure

This feature allows project managers and resource managers the ability to assign resources to tasks in the work breakdown structure while it is in a draft status. Prior to this release, resources could only be assigned to tasks in work breakdown structures that are published.

Before assigning resources to the tasks in the work breakdown structure, be sure to define your team for the project. To define the team for the project, go to **Project management and accounting** \> **Projects** \> **All projects** \> **Project team and scheduling** tab.

After the project team is defined, open the **Work breakdown** structure on the **Plan** tab of the project. Create the tasks for the project. The resource can be assigned to the task while the work breakdown structure is still in draft status.

### Manage or view a project work breakdown structure using Microsoft Project Client

Planning and maintaining a project schedule can be complex and project managers need to use tools that help them manage this. This feature provides support to open and manage the project work breakdown structure using the Microsoft Project Client Application. The project manager will be able to publish any changes back to Finance and Operations project work breakdown structure.

To enable the integration, a Dynamics 365 add-in is required to be installed in the user's client Microsoft Project application. This is done by opening the **Project management workspace**. Click the **Configure project client add-in** link in the **Setup** section under **Links**.

A work breakdown structure that is in a draft status can be opened in the Microsoft Project Client Application by clicking **Open in Microsoft Project** from the project form (**Project management and accounting \> Projects \> All projects**) or can be opened from within Microsoft Project Client by clicking **Open** in the **Dynamics 365 for Operations** tab. Users can make necessary changes to the draft work breakdown structure, including assigning resources. If a project team has already been added to the project in Finance and Operations, the resource list will be populated with the team members. If a project team has not yet been added to the project, you can select the resources and build the team within Microsoft Project Client by clicking the **Resources** button on the **Dynamics 365 for Operations** tab. Edits to the work breakdown structure is published back to Finance and Operations.

### Project time entry mobile workspace

As part of their daily work, project resources are often on-site or traveling. The **Project time entry** mobile workspace lets users enter their billable or non-billable time against a project on the mobile device of their choice. Therefore, project resources can record time entries anytime and anywhere. They can also view time entries that have already been recorded.

Specifically, the **Project time entry** mobile workspace provides these features:

- For any selected date, enter the number of hours that you spent on a specific task.
- Search by project name or customer to find the project to enter time for.
- Specify the category and activity for the time that you spent.
- Record the time as billable or non-billable for the project.
- Optionally enter any external or internal comments.

To implement the **Project time entry** mobile workspace, see the related documentation for Microsoft Dynamics 365 for Operations. For more information, see [Project time entry mobile workspace](/dynamics365/project-operations/prod-pma/project-time-entry-mobile-workspace).

### Rename project stages

There are now 8 default project stages that can be used for the different project types. This feature provides the ability to give the default project stages a different name for each legal entity and provide language translation support for the project stage name.

To view or edit the project stage name, go to **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**, and select the **Project stage** tab.

The **Stage** column will display the default project stage names. To rename, you need to enter the new project stage name in the **Project stage** column, and then select which project types the project stage applies.

To translate the project stage name to another language, simply click the **Language** drop-down button, and then select the language to translate.

### Worker can be a project resource in multiple legal entities at the same time

This feature provides support for a worker that has employment in more than one legal entity to also be a project resource in multiple legal entities at the same time. Prior releases only allowed a worker to be mapped to a single project resource.

Included in this feature is the ability to view schedulable resources, non-schedulable resources, or all resources in the **Resources list** page. This will help project managers and resource managers better understand if a resource is schedulable.

You can enter an As of date to display resource data, such as sales price and cost price, as of a specific date. By default, the current date will be used. This date will also be used to allow users to view the project resource data for workers that may already be terminated, by changing the As of date to include when the worker was employed. To use this feature, go to **Project management and accounting** \> **Project resources** \> **Resources list**.

## Retail

### Next generation Retail extensibility framework

The POS extensibility framework has been redesigned and enhanced to simplify the developer experience and to do seamless servicing. With the new extensibility patterns, you can customize the application without modifying the core retail code. The new message-driven extensibility framework for POS allows you to isolate the extension from standard to support continuous integration and deployment. You can manage and maintain your code at your own pace. With the new model, multiple ISVs/partners can customize the solution independently without any code merge. There is also support for multiple individual POS extension packages.

The benefits of this include:

- Simplified customization model.
- Easy maintenance.
- No code merge.
- Reduced cost and time to implement.
- Always on the latest and greatest version.

With this new extensibility framework, you can uptake any hotfix or upgrade easily without any code merge. Previously you needed to do a code merge and update your code if there were conflicts between your code and core application code. If you also had ISV code, you needed to involve them in the process of servicing, retesting, and re-deploying it. In the new model, the core POS solution is completely isolated from the extension layer, so you no longer need to do any code merge to uptake a hotfix or upgrade. You can apply a hotfix or upgrade seamlessly, and you can continuously service your own customizations without modifying the core application code.

To isolate the extension and core application in this release, we modified the extensibility patterns and sealed the retail components code from the Retail SDK. To customize the application in the sealed world, extension points and APIs are exposed to support all customization scenarios. The following component code is sealed/removed from the Retail SDK in this release and is available either as binary or APIs for extension:

- POS (Modern POS and Cloud POS)
- Commerce runtime (CRT)
- Hardware station
- Channel DB
- Retail proxy

**Even though the code is sealed or removed from the Retail SDK, we still support extensibility through the extension points and APIs. In the new model, you will follow the extensibility pattern and customize the product without inline changes.**

All the retail components will be completely sealed, and no inline changes will be supported, starting with this release. For any extension, you need to follow the extensibility pattern and extend it. In addition to the above retail components sealing, headquarters will also be sealed (no overlayering). In Retail, extensibility is supported only through extensions.

### Configuration driven extension

The attribute framework now supports configuration-driven development for customer and sales order entities. You can use the attribute framework to add custom fields in customer master, sales order, cash and carry transactions, or call center orders. In previous versions you needed to modify POS, CRT, channel DB. With this new model, this can be done through configuration without any code changes.

**Customer attributes** – With the new customer attribute framework, you can use configurations to add new fields to the customer add/edit or customer details screens in POS or HQ. Configure the customer attribute group, and POS and HQ will automatically show the new attribute without any code change or customization. The screen layout designer will also show the customer attributes in the transaction screen - customer panel.

**Order attributes** – The attribute framework supports attributes in cash and carry transactions, customer orders, and call center orders. You can edit and set values directly in HQ or in CRT/POS. All this can be done through configurations, without any database changes. (You can use customization for core business logic only, not for basic CRUD operations.)

### CRT handlers and extensible enums

**Granular CRT handlers** – We are continuously improving our code base to simplify the customization experience. We have enhanced many of the CRT handlers with more granular message handlers, so you can easily override or add triggers at specific extension points instead of owning the entire service or operation. For example, loyalty service is enhanced with more granular handlers to support customization at earn (sale and return), redeem, calculation, or validation. Previously, to skip some standard checks you needed to override the entire calculate service but now this can be done just by overriding or adding pre/post triggers for the validation check request handlers. Refer to the commerce runtime messages.chm file in the Retail SDK folder for the available requests and responses for customization.

**Extensible enums** – We have enhanced the CRT to support extensible enums. Extensible enums can be now accessed using the new API exposed in CRT. Using this new API you can easily set/get or validate values based on the enum type. In previous versions you needed to manually define the enums in the CRT layer and type match it without direct mapping between Finance and Operations enums and CRT enums. With the new extensible API exposed in CRT, you can directly map between Finance and Operations enums and CRT enums without manually creating the enums in CRT. Multiple partners and ISVs can create extensible enums and use them in their code independently, without any code merge. For example, if you create a new discount type extension enum, the same enum will be available for you in CRT. In your code you can check if discount type is equal to my discount enum type, instead of manually validating with some hardcoded values.

### Support for multiple Retail server extensions

Previously there was support for only one Retail server library, and all the extensions needed to be merged into one extension. If a customer wanted to use both an ISV extension and a partner extension, they needed to either merge both sets of code or reference one extension library from the other. In this release, the customer or partner can have multiple independent Retail server extensions, which will work seamlessly without any manual merge and build required.

### POS extensibility enhancements

POS extensibility framework is enhanced to support seamless servicing and extension without over layering or inline changes. In this release, the core POS code is removed from the SDK to avoid inline changes, and we exposed the POS.API project in the Retail SDK to support extensibility. By referencing this POS.API, you can customize POS for your business scenario. The typescript retail proxy is also enhanced to support proxy generation by extension to isolate extension from ISVs and partners. The following list shows the extension points added in this release based on the new extensibility pattern. Refer to the Retail SDK documentation for the full list.

- New operation and views
- Modify existing views
- Add custom logic
- Order and customer attributes
- Triggers (pre-and post before any operations)
- POS Controls (refer the SDK documentation for all the controls information)

    - App bar, dialog, Custom controls, Data list, Date, Time
    - Menu, Pivot, Toggle switch
    - Loader

- Localization and logging frameworks

### Enhanced channel database extension model

Extension to channel database can now be done using the extension schema without modifying the existing schema. All CRT database extension can be done in the extension schema, which supports CRUD operations for all extensions and for calling standard procedures and views from the extension. If you want to add new tables, procedures, functions, or views you can now do that all in the new extension schema. CRT data service is given access to extension schema to perform custom operations. Previously, you needed to modify the Microsoft schema to do this kind of change and it impacted the upgrade and hotfix uptake. You also needed to merge the custom script with the Microsoft script to avoid any overriding if there was any customization, so a partner or IT pro need to be involved in the upgrade process. With the new extension model, you can easily uptake a hotfix or upgrade without any script merge because the extensions are done in separate schema and maintained separately from the core scripts. Both are completely isolated, so the hotfix uptake will be as easy as a few button clicks.

CRT data service now exposes the primary key for performing your custom extension scenario as post operation. For example, if you want to extend the shared retail parameters data service and fetch custom information, you can use the post triggers and do the extension. The post triggers expose the primary key and properties of the entities to perform any extension. From the extension, you can query the custom tables using the primary key and other information exposed through the entities. You can update the response with custom information as extension properties, which will be available in the client.

### CDX extensibility enhancements

We extended the Retail initialize feature to support custom table and field initialization for data sync between HQ and channel, and vice versa, without overlayering. The CDX seed data initialization class can be extended for custom tables and fields using the new extension points. These extension points will help you to initialize the custom tables and fields in different environments for data push and pull without overlayering. Previously, to achieve this you needed to modify the CDXDatagenerator class inline. Now all of this can be done using the extension. We have also enhanced the class to include a custom resource file to support custom tables and columns as extensions. Because the custom fields and tables information is added as an extension to the core class, you can now easily uptake any hotfix or upgrade without any code merge. You can also separate your code from different ISV and partner extensions. All extensions can be maintained and serviced separately, even if there are multiple ISV and partner extensions you can still perform servicing for your code or Microsoft code without disturbing or merging with the other extensions or core product code.

### Retail peripheral compatibility

The Peripheral simulator for Retail introduces an important update to the previously released peripheral simulator. New to the Peripheral simulator for Retail is a point of sale simulator that can test peripheral devices for compatibility with the Modern point of sale and Hardware station without the need to deploy those components.

Depending on the scenario, the POS simulator can simulate the peripheral business logic built into the Modern POS, or it can simulate a standalone hardware station as it would interact with point of sale peripherals. Traditionally, testing devices for compatibility with the point of sale has required deployment of back office followed by configuration and deployment of the point of sale application. With point of sale simulation capability, testing peripherals for compatibility no longer requires product knowledge or access. This enables peripheral manufacturers to test their devices for compatibility without the need to ship physical devices to Microsoft or ISVs for testing.

Supported devices:

- Line display
- Cash drawer
- MSR
- PIN pad
- Printer
- Scale
- Signature capture pad
- Bar code scanner

For each supported device, the POS simulator provides the ability to test device specific capabilities for ad hoc testing, such as card swipe or displaying specific strings of text on a line display. Each supported device also has a specific self-test routine that is used for official device compatibility testing. Results from compatibility testing can be sent to Microsoft to be listed as approved for new deployments of Retail.

For a description of the Peripheral simulator, see [Retail Peripheral simulator](../../../commerce/dev-itpro/retail-peripheral-simulator.md).

For more information about the compatibility program and how to participate, contact <drpc@microsoft.com>.

For information about peripherals that have been previously tested by Microsoft, visit [Microsoft-tested peripheral devices](../../../commerce/retail-peripherals-overview.md). This page will also be updated with a link to the POS simulator-tested devices as soon as that page becomes available.

### Omni-channel coupons

To improve the omni-channel experience, retailers can offer their customers call center coupons and retail discounts as part of one feature. Retailers can define and issue coupons that can be redeemed and tracked across all channels. In Microsoft Dynamics AX 2012 and previous versions of Microsoft Dynamics 365 for Operations, call center coupons and discount codes on retail discounts were two unrelated features that shared a common purpose; they enabled discount targeting and discount controls for a retailer. With these features, a retailer could control which customers are entitled to the discount.

Call center coupons are merged with retail discounts to provide a unified experience for managing and accepting coupons in all retail channels. The combined experience uses the codes and bar codes from coupons to apply the discount value from retail discounts.

For more information about coupons, see [Create coupons for retail sales](../../../commerce/retail-coupons.md).

### Discounts – Quantity limit and exclude discount lines

You can add a quantity limit to simple discounts and specify a number on a discount, which limits the maximum quantity of a product or a category of products. The quantity limit value can be set at the discount header, but it will be applied at the discount line. When you set a quantity limit each discount line will have that limit applied independently.

You can also include or exclude property to discount lines. You can define the set of products a discount applies to with a combination of include and exclude discount lines. For example, you can have a discount with one discount line for the **Fashion** category set to **Include** and a second discount line for the product **81327** set to **Exclude**. This discount would then apply to all products in the **Fashion** category tree except for product **81327**. All previously existing discount lines are set to **Include**. This makes it easier for merchandizers to define discounts for some scenarios.

For more information about discounts, see [Price adjustments and discounts](../../../commerce/price-adjustments-discounts.md).

### POS Inventory visibility improvements

With the improved inventory visibility feature, cashiers can use POS to get a clear picture of the inventory status of any product in their store. They can also check the inventory status in other stores and warehouses of the company, thus helping customers to find the products that they want. The Inventory lookup form now displays the reserved inventory and incoming order quantity along with the total inventory to help the cashier with the following scenarios:

- Customer is looking for a product that is not on the shelf and the cashier wants to verify if the current store or any nearby store has it in stock.
- Store manager realizes that the stock of a product is running low and wants to know if this product has been ordered for replenishment.

An additional capability named "Available to promise" (also known as ATP) is now available in POS. This allows cashiers to see when and how much new stock is expected to be delivered to current and other stores and warehouses. This future product stock information can help the cashier answer questions regarding the stock quantities on any future date.

### POS search improvements

With the search improvement feature we have improved both product and customer search scenarios with the goal of enabling the cashiers and sales associates to quickly find what they are searching. The search bar now enables the cashiers to choose whether they want to search for products or customers prior to performing the search. The search bar can be configured to display the product suggestions while typing, thus empowering the cashiers to search the products quickly. The retailers also have the flexibility to configure whether the product search results should match 'all search terms' or match 'any search term'. Additionally, the product search now searches in the 'Searchable' property of the products as well, thus ensuring higher product discoverability. Customer search is smarter now and can search for customers with or without the phone number masks, which means that reliable results are returned every time.

### Upgrade and support for previous versions

**Upgrade support** – For Dynamics AX 2012, you had the option to perform the data upgrade for Retail, where all historical data, posted or unposted, was upgraded. Now you can upgrade from Dynamics AX 2012 R3 to the current version. The platform will support all the cumulative update versions of Dynamics AX 2012 R3 for upgrade. The back office and channel side are expected to be upgraded together for some customers on existing Dynamics AX 2012 R3 versions while others can leverage the N-1 support. We will support all Dynamics AX 2012 R3 versions from a database upgrade perspective for HQ. The Retailer will upgrade both HQ and Channel if you want to upgrade without N-1 support.

The Retail customer will also have an option for N-1 support if they are using Dynamics AX 2012 R3 CU11 or higher, if they don't want to disturb their existing store and run it against the new HQ. After the database upgrade is complete in HQ, the retargeting of the new Retail channel side components will happen as part of the LCS methodology, so the new channels can work with the upgraded DB. If the Retailer wants N-1 support for Channels when they upgrade to HQ, they will have to ensure that the channel is at least on 2012 R3 CU11 or above.

**Support for previous versions** – Now you can upgrade Dynamics AX 2012 R3 to Dynamics 365 for Retail. N-1 Support will enable existing Dynamics AX 2012 customers to adopt the cloud faster, with minimal interruption to their current business process. N-1 Support will enable existing Dynamics AX 2012 R3 CU 11 and CU12 customers to be able to leverage the benefits of cloud for their businesses using Dynamics 365 Operations as HQ in a hybrid model, while operating their stores in Dynamics AX 2012 R3 CU 11 or CU12. All of this occurs without interrupting the existing infrastructure. For the initial phase, we are targeting customers with Dynamics AX 2012 R3 CU 11 and 12 releases for N-1 support. Because Dynamics AX 2012 store systems are on-premises and distributed, we will support customers' existing Dynamics 2012 R3 store systems connecting to Dynamics 365 Operations HQ after they upgrade to the CU 11 and CU 12 versions. This will ensure minimal disruption in store operations.

Enabling N-1 support requires customers to install the N-1 components that will enable the Dynamics AX 2012 R3 CU 11 or CU12 stores to connect with the new HQ. If the customer is using a pre-CU 11 version, then they must upgrade to at least Dynamics AX 2012 R3 CU 11 to leverage the N-1 support.

For details about Retail upgrade and N-1 support, see [Overview of upgrade and N-1 support](../../../commerce/dev-itpro/overview-upgrade-n-minus1.md) and [N-1 installation and configuration](../../../commerce/dev-itpro/overview-upgrade-n-minus1.md).

## Supply chain management

### Batch and license plate confirmation

Batch confirmation and license plate confirmation has been added to this release of Finance and Operations. With this enhancement, using a mobile device, you can confirm that the correct batch or license plate is being picked.

In previous versions, batch and license plate confirmation for items was not supported. For more information, see [Batch, serial, and license plate confirmation](../../../supply-chain/warehousing/batch-and-license-plate-confirmation.md).

### Consignment inventory

Consignment inventory capabilities have been extended to allow for batch and serial number dimensions.

### Demand replenishment for raw material picking

Wave demand replenishment has been enhanced to include production and Kanban demand replenishment and raw material picking.

In previous versions, demand replenishment only included support for sales orders and transfer orders.

### Item and warehouse migration process uses advanced warehouse management

During a data upgrade, products are blocked if they are associated with a storage dimension group with the Pallet ID inventory dimension active. However, after the upgrade, you can use a set of migration options in the Change storage dimension group for items process to unblock products that were blocked during upgrade. As part of this process you can also use the Enable warehouse setup process to enable an existing warehouse to be used in warehouse management processes and get the pallet ID migrated to the License plate inventory dimension.

Some of your items might already be associated with storage dimension groups where the Site, Warehouse, and Location inventory dimensions are active and physically tracked. In this case, you can use the Change storage dimension group for items process to enable those items to be used in warehouse management processes. This feature is useful if you want to use the warehouse management functionality for existing items.

### Piece picking confirmation

A new piece picking capability allows you to confirm each piece of inventory by picking or counting work on a mobile device. You can also use the quantity and unit of measure (UOM) that is associated with a scanned bar code. This new functionality works for receiving on inbound flows, including mixed license plate receiving, purchase order item, transfer order item, and load item.

In previous versions, it was not possible to, for example, verify item quantities to be picked by scanning item bar codes or to scan bar codes for larger quantities.

For more information, see [Piece picking confirmation](../../../supply-chain/warehousing/piece-picking-confirmation.md).

### Product work confirmation for cluster picking

Dynamics 365 Finance and Operations now supports item scanning and verification in the cluster picking flow.

When cluster picking is applied, item confirmation is crucial to verify the items that are added to clusters. Now you can verify Items in cluster picking during the cluster picking process. In previous versions, it was not possible to confirm item bar codes and verify items using a bar code scanner. For more information, see [Product confirmation for cluster picking](../../../supply-chain/warehousing/cluster-picking-item-confirmation.md).

### Prospect to cash integration capabilities

Prospect to cash integration capabilities deliver first party integration between Dynamics 365 for Sales and Dynamics 365 Finance and Operations, Enterprise edition.

This solution leverages the strengths of the individual Dynamics 365 components and connects them via Dataverse. While the data is flowing seamlessly between Finance and Operations and Dynamics 365 for Sales, customers can carry out sales and marketing activities in Dynamics 365 for Sales and handle the order fulfillment with inventory management in Finance and Operations. This solution provides powerful integration with a flexible solution and simplification of the integration process, without dependency on third-party solutions. These advancements offer the best of both worlds, each with significant productivity enhancements that help businesses and workers achieve more.

- Maintain accounts in Dynamics 365 for Sales and sync them to Finance and Operations as customers.
- Maintain contacts in Dynamics 365 for Sales and sync them to Finance and Operations.
- Maintain products in Finance and Operations and sync them to Dynamics 365 for Sales.
- Create quotes in Dynamics 365 for Sales and sync them to Finance and Operations.
- Generate sales orders in Finance and Operations and sync them to Dynamics 365 for Sales.
- Generate invoices in Finance and Operations and sync them to Dynamics 365 for Sales.

**Easy access to data through the power of Dataverse**

The solution leverages the power of Azure Public Cloud and the combined data will be available via Dataverse. This enables business users to access, visualize, share, and modify the unified Sales and Operations data through Power Apps, Power BI, or create workflow automations using Flow with pre-defined templates for various business processes. This also means that Power BI dashboard lets users gain better insight into the business process information across the two systems.

**Fast implementation**

Integration between different ERP systems have traditionally been known for their rigidity, complexity, and slow deployments and implementations. This release is changing the game in this area by providing prepackaged integration templates. The templates provide the out-of-the-box experience for prospect-to-cash scenarios including synchronization needed for sales processes with accounts, customers, contacts, products, of sales orders. In addition to this an intelligent and easy-to-use setup experience, it is optimized to quickly adjust integration settings for your data structure and business needs.

**Enhanced systems and flexible setup**

The integration comes with a rich solution to optimize the experience and allow for complex process flows between Dynamics 365 for Sales and Dynamics 365 Finance and Operations. Finance and Operations, optimized to support integration with enhanced entities and Dynamics 365 for Sales is optimized with a solution.

For additional information, see [Prospect to cash](../../..//supply-chain/sales-marketing/prospect-to-cash.md).

### Punch-out to external catalog from purchase requisition

Employees can now punch-out to external shopping sites from a purchase requisition. It only takes one click on a requisition line action and a selection of one of the available catalogs as shown on the screenshot. This means that you don't need to maintain a copy of the vendor catalog and risk that the information is out of date. Instead, employees can browse the external catalog on the vendor's shopping site, and select the items that they want. After they've finished, lines will be created for those items and they can be added to the requisition.

When you set up the external catalog, you set it up across all legal entities for which the vendor you choose is set up. The employees access to the external catalog is determined by the procurement categories that are set up for the catalog and purchasing policies. 

The cXML protocol is used to communicate between Finance and Operations and the external catalog residing at the vendor's system.

For more information, see [Use external catalogs for PunchOut eProcurement](../../../supply-chain/procurement/use-external-catalogs-for-punchout.md).

### System grouping on an open work list

You can define your own filters to filter work lists. If, for example, you want to group work by load ID, or by a specific sales order production order, you can set up the filtering from the work list menu item.

In previous versions, the filtering options were limited to work group and it was not possible to filter or group work using work lists.

### Vendor collaboration

Vendor collaboration was enabled in earlier releases. In Dynamics 365 Finance and Operations, we have enabled a seamless consumption of changes to a purchase order when a vendor accepts or suggests changes to a purchase order in the vendor collaboration interface and returns the changed purchase order to the purchasing professionals.

- The vendor's acceptance of the purchase order without changes will automatically update the confirmed delivery date on the purchase order, and, optionally, confirm the order.
- The vendor's suggested changes in quantities or delivery dates or the purchase order header info can easily be transferred to the purchase order. This is a one-click action for purchasing professionals when they receive the response with the suggested changes from the vendor.

Both improvements will reduce time spent in the purchasing department and allow the procurement personnel to handle their tasks more efficiently.

For more information, see [Vendor collaboration with external vendors](../../../supply-chain/procurement/vendor-collaboration-work-external-vendors.md).

### Warehousing

Improvements have been made to the cycle counting process by allowing partial location counting. This helps to ensure data integrity while using the warehousing system.

The integration between production and warehouse has been improved by enhancing the following features:

- Opportunistic X-dock for transfer order when reporting as finished.
- Pick for withdrawing kanbans.
- Enable demand replenishment for raw material picking.
- Enable ability to assign a resource instead of resource group at output location.

Usability has been improved by adding the following capabilities:

Throughout the distribution center operations, enabling piece-by-piece picking and product confirmation for cluster picking processes.

- Batch ID and License plate ID confirmation scan.
- Ability to combine system grouping with work list menu items.

For the next major release, the following features are currently planned and more will be added to this list:

- Allow reservation hierarchy to shift from batch below to batch above for the same item, allowing for ad-hoc reservation of specific batches.
- Improve the rewaving process to increase the visibility of the pick work created.
- Support a split load scenario for the outbound flow.
- Allow to release for a partial quantity of the finished good and release per operation number.
- Allow for partial quantity of the opportunistic X-dock to transfer when reporting as finished.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
