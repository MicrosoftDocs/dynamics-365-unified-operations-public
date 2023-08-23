---
title: What's new or changed in Dynamics 365 for Operations version 1611 (November 2016)
description: This article describes features that are either new or changed in Dynamics 365 for Operations version 1611.
author: sericks007
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 221294
ms.assetid: 357931ed-f843-4bf5-bc85-0da3de0619ec
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Operations version 1611 (November 2016)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Operations version 1611.

## Cost accounting

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Define cost element dimensions, and import cost element dimension members.</td>
<td>Cost elements are used in Cost accounting to categorize costs and document the flow of costs. The primary cost elements are imported either by using a Microsoft Dynamics 365 for Operations data connector to get main accounts directly from Operations or by using a generic data connector, where you get main accounts via Microsoft Excel from any other type of source system. After main accounts are imported into Cost accounting, they are used as cost element dimension members. The secondary cost elements are user-defined and are used in allocations to document the flow of costs.</td>
</tr>
<tr>
<td>Map cost element dimensions.</td>
<td>If the main accounts across your legal entities can't be shared because of statutory accounting requirements, you can map them after you import them into Cost accounting to get a holistic view across the organization.</td>
</tr>
<tr>
<td>Define cost object dimensions, and import cost object dimension members.</td>
<td>Cost objects are any type of object that costs are assigned to. Typical cost objects include products, projects, resources, departments, cost centers, and geographic regions. You can either use a Microsoft Dynamics 365 for Operations data connector to get financial dimensions and values from Operations or use a generic data connector, where you can get dimensions and values via Excel from any other type of source system. For example, if you use the Cost center financial dimension as the object dimension, all cost centers that are imported are the dimension members for the cost object.</td>
</tr>
<tr>
<td>Define or import statistical dimensions.</td>
<td>Statistical dimension members are measured in nonmonetary units, such as machine hours, number of employees, and square. They are used in statements, or as the basis for allocations and distributions.</td>
</tr>
<tr>
<td>Create statistical measure provider templates.</td>
<td>A statistical measure provider template is used to transform Dynamics 365 for Operations data into statistical measures. The template is then associated with a given statistical dimension member. The templates are prefiltered so that they show only tables that are associated with financial dimensions.</td>
</tr>
<tr>
<td>Create cost accounting ledgers.</td>
<td>A cost accounting ledger is an agnostic ledger that uses its own calendar and currency. It plays an important role in the processing of all cost transactions. For example, a cost accounting ledger classifies costs based on its own cost elements and aggregates costs based on its own object dimensions. You can create as many cost accounting ledgers as you require to do management reporting from various perspectives.</td>
</tr>
<tr>
<td>Create cost control units.</td>
<td>Cost control units make up the cost structure and define the flow of costs in a cost accounting ledger. They must be associated with cost object dimensions to represent the cost object dimensions in the ledger.</td>
</tr>
<tr>
<td>Process general ledger entries.</td>
<td>To measure actual performance, you must have data. The data is imported by using the connectors that you define for the cost accounting ledger. When you process the general ledger entries, the data is imported incrementally.</td>
</tr>
<tr>
<td>Process budget entries.</td>
<td>To measure budgeted performance, you must have data. The data is imported by using the connectors that you define for the cost accounting ledger. When you process the budget entries, the data is imported incrementally.</td>
</tr>
<tr>
<td>Create and apply cost behavior policies.</td>
<td>You use a cost behavior policy to classify costs as fixed, variable, or semi-variable. A policy is rule-based and date-effective. By default, all costs are marked as unclassified until you apply a cost behavior policy and calculate the effects of the rule. After the calculation, the costs are classified.</td>
</tr>
<tr>
<td>Trace costs.</td>
<td>To help you understand the impact of cost policies, Cost accounting lets you trace costs to the source values and applied rules where they originate. This functionality provides full traceability about when costs occurred, what types of costs occurred, and which cost behavior rules were applied.</td>
</tr>
<tr>
<td>Define dimension hierarchies.</td>
<td>You can create dimension hierarchies for either categorization or classification purposes. For example, you can define a categorization hierarchy that is based on a cost element dimension and its members. Alternatively, you can define a classification hierarchy that is based on a cost object dimension and its members. The reporting structures are used in the following situations:
<ul>
<li>You define allocations, cost rates, and cost rollup rules.</li>
<li>You view statements by using the workspace.</li>
<li>You define access to view aggregated data.</li>
<li>You view data in Excel.</li>
</ul></td>
</tr>
<tr>
<td>Create statements that can be viewed in the workspace.</td>
<td>Use the workspace to get a quick overview of actual and budgeted costs, and also deviations. You can filter the data by period or cost level. The workspace is designed for managers who are responsible for cost control. It adheres to the access rules that are defined for the dimension hierarchies.</td>
</tr>
<tr>
<td>Create reports by using Excel.
[!NOTE] You must run Microsoft Excel 2016.
</td>
<td>You can export Cost accounting data directly to Excel through data entities and use Microsoft PivotTable to create reports.</td>
</tr>
</tbody>
</table>

## Expense management

| What you can do | Why this is important |
|-----------------|-----------------------|
| Reassign terminated employee credit card transactions. | Sometimes, when an employee is terminated, their Active Directory Domain Services (AD DS) account is disabled when active credit card transactions that must be expensed are imported. Previously, you couldn't assign a delegate for expense entry or attach the credit card transactions to an expense report. You can now use the **Credit card transactions** page to reassign the employee for any credit card transaction where the associated employee has been terminated. After you reassign the credit card transaction, the transaction can be selected for an expense report and paid through the regular process for expense report reimbursement. |
| Change the expense credit card information for pending and past employees. | You can change Expense management credit card information for pending workers and past workers. Previously, you could change the expense credit card information only if the worker is an active employee. |
| Copy an expense report. | You can now copy an existing expense when you create a new expense on the same expense report. You can copy an expense report and all the associated non–credit card expenses to a new expense report. You must still perform any required itemizations and attach required receipts, based on defined expense policies and categories. You can add credit card transactions to the expense report by selecting to add unreconciled expenses. |
| Bulk-edit expenses. | Some credit card transactions might not be mapped to an expense category, or they might be incorrectly mapped when they are imported. In this case, employees must manually change the associated expense category. When you manage the unreconciled expenses, you can now bulk-edit the expense category for the selected expenses. Additionally, when you manage selected expenses for a specific expense report, you can bulk-edit the project and the additional information. |
| Change the exchange rate for credit card transactions. | The actual exchange rate that is used for a credit card transaction might differ from the exchange rate that is set up in the system. Previously, employees couldn't change the exchange rate for any credit card transaction that was imported into Expense management. You now can set a parameter on the **Expense management parameters** page to allow the exchange rate to be changed for credit card transactions. |
| Set up anticorruption attestation for expenses. | Some employees for an organization might have business with government officials, and some expenses that occur as part of that business might be perceived as bribery. In Expense management, you can now set up an anticorruption attestation that is shown for selected expense categories, such as meals and gifts. Employees must select whether expenses that are set up for anticorruption attestation meet the criteria that are defined by your organization's policies. |
| Prevent manual entry of expenses for specific expense categories. | An expense category can be set up to represent a credit card transaction that the category can't be changed for. An example is a fee for late payment of the credit card. You can now set up an expense category that allows expenses to be created only through import. This feature prevents employees from manually creating an expense for the category. It also doesn't allow the category to be changed for transactions that have been imported and that use this category. |
| Attach a receipt to multiple expenses. | A receipt that is uploaded to Expense management might be related to multiple expenses. Previously, a receipt that was related to multiple expenses had to be uploaded one time for each expense. You can now attach a receipt to an expense that has already been uploaded and attached to another expense on the same expense report. Additionally, if you upload a receipt to the header of the expense report, you can select one or more lines to attach the receipt to. |
| Create future-dated expenses. | When you copy an expense report, for example, the transaction date for an expense might have a future date. Previous releases don't allow for future-dated expenses. You can now create and save expenses that have a future date. However, you can't submit a future-dated expense. |
| Configure expense taxes for a state/province. | In some country/regions, expenses that are incurred in different states/provinces might be subject to different sales tax rates. You can now set up the expense tax configurations at the state/province level, not just at the country/region level. If you leave the **State/Province** field blank on the **Tax configuration** page, the sales tax group applies to all states/provinces for the specified country/region. |
| Set up expense credit card types. | Previously, there was no page where you could create new credit card types, such as Visa, MasterCard or AMEX, that could be used with Expense management. You can now create credit card types to use with Expense management. The page is located in the **Setup** area, in the **Calculations and codes** section. |
| Define a multilevel approval workflow for expense reports. | A new workflow for expense reports supports a multilevel approval process. Employees enter the interim approvers and final approvers when they create the expense report. The workflow then routes the expense report to the interim approvers first. After the expense report is approved at that level, the workflow routes it to the final approvers for final approval. |
| Create and maintain expenses that aren't attached to an expense report. | User can now create expenses and maintain them (for example, by attaching or itemizing receipts, or assigning guests) without first having to create an expense report. One or more expenses can be selected and added to a new expense report, so that they can be submitted for approval. A new page for maintaining expenses is available at **Expense management** &gt; **My expenses** &gt; **Expenses**. |

## Financial management

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Track fixed asset valuations by using a single "book" concept.</td>
<td>Previously, two separate types of valuation were used to track fixed asset values: value models and depreciation books. In the current version, these two concepts have been merged into a single valuation concept that is named books. Books have all the functionality of both value models and depreciation books. For example, you can turn off posting to the general ledger. Books that post to the general ledger are typically used for corporate financial reporting. Books that don't post to the general ledger can be used for tax reporting purposes.</td>
</tr>
<tr>
<td>Perform the General ledger year-end close for multiple legal entities.</td>
<td>To speed up the year-end closing process, you can now run the year-end close for multiple legal entities from a shared year-end close page. Groups of legal entities can be defined, together with settings that should be retained from one year to the next. Other usability enhancements have also been made to the year-end closing process.</td>
</tr>
<tr>
<td>Take advantage of enhancements to General ledger foreign currency revaluation.</td>
<td>The following enhancements have been made to the General ledger process for foreign currency revaluation:
<ul>
<li>An exchange rate type has been added to the main account. This exchange rate type is now used to determine the exchange rate during currency revaluation. If no exchange rate type is defined, the process continues to use the exchange rate type that is defined on the ledger.</li>
<li>It's now easier to select a range of main accounts and currencies to run the revaluation process for.</li>
<li>Revaluation can be run for multiple legal entities.</li>
<li>The system now maintains a history of every revaluation process that was performed, as it does for the Accounts receivable (AR) and Accounts payable (AP) revaluation processes.</li>
<li>When you run the process, you can now preview the results of the revaluation. The preview shows the results for all legal entities that the process was run for. You can then post all the legal entities, or a subset of them, from the preview. You can also export the results in the preview to Excel.</li>
</ul></td>
</tr>
<tr>
<td>View transactions for additional posting layers.</td>
<td>On the <strong>Trial balance</strong> list page and the <strong>Dimension statement</strong> report, you can now select the additional posting layers that have been added to General ledger. When you select the additional posting layers, the adjustments for those posting layers are included in the balances on the list page or report.</td>
</tr>
<tr>
<td>Attach how-to documentation to the financial period close template.</td>
<td>Previously, you could attach documentation after a task was completed. For example, you could attach a report that was generated. You can now also attach a how-to document to the template. This how-to document is then copied to every task in the financial period schedule, so that the task owner can view instructions about how to complete the task.</td>
</tr>
<tr>
<td>Define the intercompany accounting setup from a shared page.</td>
<td>The <strong>Intercompany accounting setup page</strong> is now shared, so that an organization can define all the pairs of legal entities that can transact with each other. Additionally, you can now enter a transaction in the originating legal entity but not from the destination legal entity. If either legal entity can initiate an intercompany transaction, the reciprocal pair must be defined. Therefore, the destination legal entity is also set up as an originating legal entity.</td>
</tr>
<tr>
<td>Submit justification documents for budget plans.</td>
<td>You can create a justification template as supplemental documentation for any requested budget amounts. Users can fill in the details of the template and attach the template to the budget plan, so that it can be used during the approval process.</td>
</tr>
<tr>
<td>Enable advanced rules for budget register entries.</td>
<td>If advanced rules are configured in General ledger, those rules can be used for new entries and transfers in the budget register.</td>
</tr>
<tr>
<td>Take advantage of enhanced visibility of prepayment invoicing activity.</td>
<td>A new <strong>Open prepayments</strong> list page provides a snapshot of the status of prepayment invoicing activity. The page provides the AP department with information about purchase orders that have remaining prepayment values that must be invoiced, invoiced values that must be paid, and paid invoice values that must be applied to standard invoices. Additionally, enhancements to the automatic application of paid prepayment invoices to standard invoices help invoicing clerks do data entry more efficiently.</td>
</tr>
<tr>
<td>Use the <strong>Vendor collaboration invoicing</strong> workspace.</td>
<td>A new <strong>Invoicing</strong> workspace in the <strong>Vendor collaboration</strong> area lets external vendors securely access their own invoice information. For example, vendors can see whether an invoice has been paid and submit their own invoice. This change promotes more efficient and timely communication with external vendors. Therefore, the invoicing clerks have fewer interruptions.</td>
</tr>
<tr>
<td>Switch legal entities during invoice entry.</td>
<td>Enhancements let invoicing clerks who must enter invoices for multiple legal entities quickly change the legal entity from the invoicing pages. This feature saves the invoicing clerks time, because they must no longer sign out of the current legal entity and sign in to a different legal entity. Both the <strong>Global invoice journal</strong> page and the <strong>Vendor invoices</strong> page let users change the legal entity during data entry.</td>
</tr>
<tr>
<td>Support for electronic files for the Internal Revenue Service (IRS) 1099 Combined Federal/State filing program</td>
<td>When the <strong>US</strong> configuration key is enabled, the 1099 electronic filing process provides additional functionality that complies with IRS regulations for the Combined Federal/State filing program. The IRS established this program so that it can electronically forward information returns to participating states.</td>
</tr>
<tr>
<td>Settlement enhancements</td>
<td>Enhancements help payment clerks do settlement more efficiently, because clerks can allow multiple unposted payments to be settled against the same invoice.</td>
</tr>
<tr>
<td>Cross-company view</td>
<td>Centralized payment clerks can now view past-due invoices across companies. The <strong>Vendor payments</strong> and <strong>Customer payments</strong> workspaces now provide better visibility into and control over overdue invoices by providing a way to view and filter across companies that are part of a centralized payment organizational hierarchy.</td>
</tr>
<tr>
<td>Use the <strong>Bank management</strong> workspace.</td>
<td>A new <strong>Bank management</strong> workspace helps track bank accounts and balances for your legal entities. Current and pending balances are immediately available for all accounts, and you can drill back from the balances into the detailed transaction vouchers. You can also see the historical balance data for each bank account, or a summary for all bank accounts in the company, in both short-term and long-term views. You can gain better insight into bank account reconciliation, because the date of the last reconciliation is reported for each bank account, and there is also an indicator for reconciliations that are in progress.</td>
</tr>
<tr>
<td>Import electronic bank statements for all legal entities in a single step.</td>
<td>You can now import electronic bank statements for all legal entities in a single step. Bank statement files can contain statements from many bank accounts and legal entities, and zip files can contain multiple bank statement files. By using a single import process, you can start the reconciliation for all reported bank accounts in all legal entities. This feature helps save you time, because you don't have to switch between companies and multiple statement imports. You can also automatically run matching rules against all imported statements in each company.</td>
</tr>
<tr>
<td>Valuation tracking</td>
<td>A single fixed asset can have multiple valuations for different accounting standards and can optionally post the associated transactions to the general ledger. Previously, these valuations were tracked by using either value models or depreciation books. You can now track these valuations, which are now known as books, by using a common set of journals, inquiries, and reports. The unified experience simplifies implementation and reduces the number of interfaces that the periodic processes require.</td>
</tr>
<tr>
<td>Take advantage of enhancements to cross-company depreciation runs.</td>
<td>You can now start a depreciation run for assets across all legal entities from a single page. You can also automatically post the journals after they are created. You can send the creation and posting of the journals to batch processing, so that the depreciation runs in the background. These enhancements reduce inefficiencies, because you don't have to start individual depreciation runs separately for each company. The enhancement also enables better centralized management of your fixed assets.</td>
</tr>
</tbody>
</table>

## Human capital management

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Create a performance journal.</td>
<td>Before you complete your review, you often gather information about activities or events that contributed to your success as an employee during the review period. You can add an entry to your performance journal to document those activities and events. You can also connect those activities and events to a goal or a performance review to provide more information to the reviewer.</td>
</tr>
<tr>
<td>Create more detailed goals.</td>
<td>You have more control over the content of the goals that you set. You can create measurements for the goals, link performance journal entries to the measurements, and attach and view documents. You can store goals as templates and reuse them for quick setup.</td>
</tr>
<tr>
<td>Create more detailed performance reviews.</td>
<td>Performance reviews, which are formally known as discussions, are now flexible enough to support both continuous feedback and more formal reviews. You can pull in active goals and post comments about them, and add sections for a review of your competencies. Additional sections are provided, where you can add or view measurements, performance journal entries, attachments, and signoffs that are related to the review.</td>
</tr>
<tr>
<td>Associate additional position hierarchies with workflows.</td>
<td>You can associate a workflow with a position hierarchy. You can also modify the workflow steps to optimize the approval process so that it fits your business requirements. Therefore, you can define an effective approval structure that fits the various reporting relationships that your organization uses.</td>
</tr>
<tr>
<td>Workflow support for entering personal identification numbers (PINs) in Employee self-service.</td>
<td>Workflow capability for Human resources (HR) has been expanded and now includes support for PINs. Employees can add and edit their PIN to improve efficiency. However, HR workers can review this information for accuracy and completeness before they add it to the employee's record.</td>
</tr>
<tr>
<td>Create goal templates, and use them to add new goals.</td>
<td>You can create goal templates for goals that are shared by many employees in the company. Employees can add their own goals from a template, managers can add goals for their team from a template, and HR team members can add goals for employees across the company.</td>
</tr>
<tr>
<td>Create goal groups, and use them to add new goals.</td>
<td>You can add goal templates to a group, and use the group to create one or more goals for an employee, a team, a position, a department, or the company.</td>
</tr>
<tr>
<td>Have more control over the review process.</td>
<td>You can use a workflow to control the review process. You can create review templates and use them to create reviews. You can also add ratings to a review.</td>
</tr>
<tr>
<td>Use review periods to define the time frame for the review.</td>
<td>You can define a time period for a performance review and the start and end dates of the review are entered automatically. However, you can change those default dates as needed.</td>
</tr>
<tr>
<td>Access five new Power BI content packs for Human resources</td>
<td>The new content packs enable human resource organizations and human resources managers to analyze the following:
<p>Workforce metrics</p>
<ul>
<li>Demographic breakdowns by age, gender, and marital status</li>
<li>Compare attrition rates year over year and see a list of reasons employees have given for leaving the organization</li>
<li>View a list of open positions, as well as a comparison of open to closed positions</li>
</ul>
<p>Compensation and benefits</p>
<ul>
<li>Compare hourly and salaried employees</li>
<li>View the number of employees enrolled in available benefits</li>
<li>View employees by employment type</li>
</ul>
<p>Recruiting</p>
<ul>
<li>Analyze applicants based on the number of applicants, where they're coming from, and what positions they're applying for</li>
</ul>
<p>Organizational training</p>
<ul>
<li>Course registration by location</li>
<li>Course attendance by status</li>
<li>List of employees registered for courses</li>
</ul>
<p>Employee competencies and development</p>
<ul>
<li>List of skills held by employees</li>
<li>Breakdown of skill types by team member</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Localizations

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Localizations are available for 18 additional countries/regions:
<ul>
<li>Austria</li>
<li>Belgium</li>
<li>Brazil</li>
<li>China</li>
<li>Czech Republic</li>
<li>Estonia</li>
<li>Finland</li>
<li>Hungary</li>
<li>Italy</li>
<li>Latvia</li>
<li>Lithuania</li>
<li>Norway</li>
<li>Poland</li>
<li>Saudi Arabia</li>
<li>Spain</li>
<li>Sweden</li>
<li>Switzerland</li>
<li>Thailand</li>
</ul>
<p>The following countries/regions also require the Retail localization. The Retail localization for these countries/regions hasn't been completed and is planned only for H1 CY2017:</p>
<ul>
<li>Brazil</li>
<li>Czech Republic</li>
<li>Estonia</li>
<li>Hungary</li>
<li>Latvia</li>
<li>Lithuania</li>
<li>Malaysia</li>
<li>Poland</li>
<li>Sweden</li>
</ul>
</td>
<td>Dynamics 365 for Operations is available in 18 additional countries/regions. As part of our effort to make localization easier and more configurable, regulatory electronic reporting features have been converted to Electronic reporting (ER) configurations, and some regulatory Microsoft SQL Server Reporting Services (SSRS) reports have been converted to ER configurations that use Excel templates. These converted features are specifically mentioned later in this table.</td>
</tr>
<tr>
<td>Japan – Group fixed assets when you print the form 26 and its appended tables.</td>
<td>The form 26 must be submitted to each city where the corporation operates. To save you effort when you print the form 26, fixed assets can be automatically grouped and sorted by location.</td>
</tr>
<tr>
<td>Japan – See the amounts for accelerated and additional depreciation on the profile.</td>
<td>The profile can provide an accurate estimate of the amounts for accelerated and additional depreciation.</td>
</tr>
<tr>
<td>Japan – Progressively calculate withholding tax.</td>
<td>The Japanese government requires that you calculate withholding tax progressively, based on the payment amount.</td>
</tr>
<tr>
<td>Japan – Import the postal code file for specific large enterprise buildings.</td>
<td>The postal code file that the authority provides for specific large enterprise buildings can be imported into system. Address can then be derived from the postal codes.</td>
</tr>
<tr>
<td>Japan – Configure an idle period for fixed assets.</td>
<td>Idle periods let the user pause the fixed asset depreciation during a specified period. This functionality is required by the regulation.</td>
</tr>
<tr>
<td>Europe – Configure a value-added tax (VAT) registration number for a party's address by using the Registration ID framework.</td>
<td>You can configure a VAT registration number for a party's address by using the Registration ID framework and a new <strong>VAT ID</strong> registration category.</td>
</tr>
<tr>
<td>Finland – Configure a customs customer number for a party's address by using the Registration ID framework.</td>
<td>You can configure a customs customer number for a party's address by using the Registration ID framework and a new <strong>Customs customer ID</strong> registration category.</td>
</tr>
<tr>
<td>France – Print customer invoices in a layout that is specific to France.</td>
<td>Customer invoice printout is adjusted to meet France-specific requirements.</td>
</tr>
<tr>
<td>France – Enforce chronological numbering of documents by fiscal period.</td>
<td>To meet France-specific requirements for the numbering of customer invoices, you can set up number sequences for customer invoices per fiscal period.</td>
</tr>
<tr>
<td>Austria localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list XML format for Austria</li>
<li>Intrastat format for Austria</li>
<li>ISO20022 Credit transfer payment format for Austria</li>
<li>ISO20022 Direct debit payment format for Austria</li>
<li>Austrian EDIFACT-PAYMUL format</li>
<li>VAT declaration for Austria</li>
</ul>
</td>
</tr>
<tr>
<td>Belgium localization – ER configurations</td>
<td>
<ul>
<li>BLWI format for Belgium</li>
<li>EU Sales list XML format for Belgium</li>
<li>Fixed assets report for Belgium</li>
<li>Intervat format for Belgium</li>
<li>Intrastat format for Belgium</li>
<li>Invoice turnover report for Belgium</li>
<li>Ledger transaction export format for Belgium</li>
<li>SWIFT vendor payment format for Belgium</li>
<li>CODA bank statement import format for Belgium</li>
<li>ISO20022 Credit transfer payment format for Belgium</li>
<li>ISO20022 Direct debit payment format for Belgium</li>
</ul>
</td>
</tr>
<tr>
<td>Brazil localization – ER configurations</td>
<td>
<ul>
<li>GIA SP for Brazil</li>
<li>GIA-ST for Brazil</li>
</ul>
</td>
</tr>
<tr>
<td>Czech Republic localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list XML format for Czech Republic</li>
<li>Intrastat format for Czech Republic</li>
<li>VAT declaration for Czech Republic</li>
</ul>
</td>
</tr>
<tr>
<td>China localization – ER configurations</td>
<td>
<ul>
<li>Customer aging report format for China</li>
<li>Customer due amount analysis report format for China</li>
<li>Vendor aging report format for China</li>
<li>Vendor due amount analysis report format for China</li>
<li>Aging analysis of receivable payment format for China</li>
<li>Customer balance report format for China</li>
<li>Ledger account balance report format for China</li>
<li>Vendor balance report format for China</li>
<li>GBT file for China</li>
<li>Format for Golden tax export file</li>
<li>Production consumption variance report format for China</li>
</ul>
</td>
</tr>
<tr>
<td>Estonia localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list XML format for Estonia</li>
<li>Intrastat format for Estonia</li>
<li>Inventory reclassification statement for Estonia</li>
<li>ISO20022 Credit transfer payment format for Estonia</li>
<li>Customer vendor balance notice report for Estonia</li>
<li>VAT declaration for Estonia</li>
</ul>
</td>
</tr>
<tr>
<td>Finland localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list TXT format for Finland</li>
<li>Intrastat format for Finland</li>
<li>ISO20022 Credit transfer payment format for Finland</li>
</ul>
</td>
</tr>
<tr>
<td>Hungary localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list XML format for Hungary</li>
<li>Intrastat format for Hungary</li>
<li>Intrastat simplified format for Hungary</li>
<li>Export format for Invoice list for Hungary</li>
<li>VAT declaration for Hungary</li>
<li>Itemized VAT declaration for Hungary</li>
<li>Inventory statement for Hungary</li>
<li>MultiCash payment format for Hungary</li>
</ul>
</td>
</tr>
<tr>
<td>Italy localization – ER configurations</td>
<td>
<ul>
<li>Intrastat format for Italy</li>
<li>Project invoice format for Italy</li>
<li>Sales invoice format for Italy</li>
<li>ISO20022 Credit transfer payment format for Italy</li>
<li>ISO20022 Direct debit payment format for Italy</li>
<li>RIBA collection remittance format for Italy</li>
<li>Domestic tax transactions report for Italy</li>
<li>Blocklist report for Italy</li>
<li>Modello770 report for Italy</li>
<li>Yearly tax communication report for Italy</li>
</ul>
</td>
</tr>
<tr>
<td>Latvia localization – ER configurations</td>
<td>
<ul>
<li>Cash receipts usage report (LV)</li>
<li>EU sales list XML format for Latvia</li>
<li>EU Sales list corrections XML format for Latvia</li>
<li>Intrastat (A) format for Latvia</li>
<li>Intrastat (B) format for Latvia</li>
<li>Inventory counting list for Latvia</li>
<li>Inventory counting statement for Latvia</li>
<li>Inventory movement for Latvia</li>
<li>Internal transfer delivery note for Latvia</li>
<li>Inventory reclassification document for Latvia</li>
<li>ISO20022 Credit transfer payment format for Latvia</li>
<li>VAT declaration for Latvia</li>
</ul>
</td>
</tr>
<tr>
<td>Lithuania localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list XML format for Lithuania</li>
<li>Intrastat format for Lithuania</li>
<li>Inventory statement for Lithuania</li>
<li>ISO20022 Credit transfer payment format for Lithuania</li>
<li>Customer vendor inter-reconciliation report for Lithuania</li>
<li>VAT declaration for Lithuania</li>
</ul>
</td>
</tr>
<tr>
<td>Norway localization – ER configurations</td>
<td>
<ul>
<li>Collection letter format for Norway</li>
<li>AutoGiro payment format for Norway</li>
<li>AvtaleGiro customer payment format for Norway</li>
<li>eFaktura customer payment format for Norway</li>
<li>ISO20022 Credit transfer payment format for Norway</li>
<li>NETS payment format for Norway</li>
</ul>
</td>
</tr>
<tr>
<td>Poland localization – ER configurations</td>
<td>
<ul>
<li>Intrastat format for Poland</li>
<li>Warehouse documents for Poland</li>
<li>Inventory reclassification document for Poland</li>
<li>MultiCash payment format for Poland</li>
<li>MultiCash foreign payment format for Poland</li>
<li>Customer vendor balance confirmation report for Poland</li>
</ul>
</td>
</tr>
<tr>
<td>Saudi Arabia localization – ER configurations</td>
<td>Bank LC Misc. Charge Allocation format for Saudi Arabia</td>
</tr>
<tr>
<td>Spain localization – ER configurations</td>
<td>
<ul>
<li>EU Sales list TXT format for Spain</li>
<li>Intrastat format for Spain</li>
<li>Project invoice format for Spain</li>
<li>Sales invoice format for Spain</li>
<li>ISO20022 Credit transfer payment format for Spain</li>
<li>ISO20022 Direct debit payment format for Spain</li>
<li>Spanish VAT register book format</li>
<li>Spanish VAT register book summary format</li>
<li>Declaration 347 export to ASCII for Spain</li>
<li>Declaration 347 report for Spain</li>
</ul>
</td>
</tr>
<tr>
<td>Sweden localization – ER configurations</td>
<td>
<ul>
<li>Intrastat format for Sweden</li>
<li>Bankgirot Autogiro customer payment format for Sweden</li>
<li>Bankgirot vendor payments format for Sweden</li>
<li>SWIFT vendor payment format for Sweden</li>
<li>SIE export format for Sweden</li>
<li>ISO20022 Credit transfer payment format for Sweden</li>
</ul>
</td>
</tr>
<tr>
<td>Switzerland localization – ER configurations</td>
<td>
<ul>
<li>DebitDirect payment format for Switzerland</li>
<li>LSV direct debit payment format for Switzerland</li>
<li>ISO20022 Credit transfer payment format for Switzerland</li>
<li>ISO20022 Direct debit payment format for Switzerland</li>
<li>ESR bank statement import format for Switzerland</li>
</ul>
</td>
</tr>
<tr>
<td>Germany – Export vendor payments in DTAZV format</td>
<td>Germany requires DTAZV with foreign format specification, which represents a credit transfer (vendor payment) message according to specification for cross-border payments from Germany to an account in a foreign bank or to a domestic bank in a foreign currency.</td>
</tr>
</tbody>
</table>

### Electronic reporting

| What you can do | Why this is important |
|-----------------|-----------------------|
| Configure ER reports to insert data, in several formats, from Document Management storage into electronic messages that are generated. | ER reports can insert data into electronic messages that are generated from the Document Management storage. Therefore, the attachments of a business document can be added to electronic messages that are generated for that document, in accordance with the legal requirements. Currently, these attachments can be added in MIME format to an XML message that is generated. Alternatively, the attachments can be added in Base64 format to a binary message that is generated. |
| Configure ER reports to generate electronic documents in Excel, Microsoft Word, or PDF format. | One configuration enables ER reports to generate electronic documents in three different formats: OpenXML worksheet (Excel), Word, and XML Forms Data Format (XFDF) (PDF). Users can select a format by adding a format template to an ER report as an Excel, Word, or PDF document. |
| Configure ER reports to insert data into page headers and footers of electronic documents that are generated in OpenXML worksheet format, and to control page breaks. | ER reports can enter business data into page headers and footers, and also control where page breaks occur. Therefore, the reports can support static top and bottom sections for pages of the electronic documents that are generated. They can also support specific paging of those documents, so that they comply with legal requirements. |
| Configure the destination of ER reports so that the output is sent as email, and so that business data and ER logic (expressions) can be used to specify, at run time, the email address to use. | Previously, when you configured an ER destination, the email address of the output's recipient could be defined at design time. You can now configure an expression in the ER format. This expression can then be selected in a destination as the source of the email address for each format configuration and each output component (folder or file) separately. Therefore, when an ER report is running, each file that is generated can be mailed to a different recipient, and the email address can be defined based on ER logic and business data. |
| Configure the destination of ER reports so that the output is sent to the Microsoft SharePoint folder as either a new named file or a new version of the existing file, and so that business data can be used in the Microsoft Power BI framework as either a data set or a report. | When you configure ER reports, you can now easily (without coding) prepare the requested business data so that it can be used by the Power BI framework. When you run those ER reports, you can provide the Power BI framework with appropriate business data and/or Excel reports that are already available. If you schedule the report runs in recurrent mode, you can establish the scheduled push of business data from Dynamics 365 for Operations to Power BI to support the update schedule of Power BI–based reports. |
| Configure ER reports to use the part of the electronic document that has already been generated as a data source to generate the rest of that document. | You can configure ER reports that create the output in text format to do the document's line counting. This information can then be used in other parts of the document to create lines that include summary details. The summary information (totals and numbers) can be computed and printed to the electronic documents that are generated, without requiring additional transformations of the data. Therefore, this feature improves the performance of report execution and helps keep the future maintenance of the configured ER format easier. |
| Configure ER reports to specify the file name extension for electronic documents that are generated in text format. | You can configure ER reports to create the output in text format, so that it can be saved as a file that has a specific extension. In addition to the default .txt extension, you can configure extensions such as .csv and .prn, in accordance with the format specification. |
| Create new ER reports that are based on a specific version of an ER model. | Previously, when you created a new ER format, only the most recent version of the selected ER model could be used as the format's data source location. You can now select any available version of the selected ER model. This feature lets you maintain ER reports for the current year and design a new version of the ER model for the next year in parallel. |
| Search data sources and formats/models by text or selected artifact in one click. Proactively resolve rebase conflicts, and resolve conflicts between configurations. Configure ER reports to create multiple validation messages for errors that are discovered until report execution is stopped. | Several user experience (UX) improvements in the ER framework help users work with ER more efficiently and easily. |
| Show the **ER** workspace on Power BI reports. | Users can configure the **ER workspace** page so that it includes new menu items and live tiles that run the Power BI–based reports. |

## Payroll

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Configure pay records and process payroll by using functionality that is equivalent to the functionality of the <strong>Payroll</strong> module in Microsoft Dynamics AX 2012 R3.</td>
<td>You can now configure and process US payroll by using a feature set that is equivalent to the feature set in AX 2012 R3.
<ul>
<li>You can configure pay cycles and pay periods, work cycles and work periods, earning codes and earning code groups, schedules, leave types, and benefit accrual plans.</li>
<li>You can also set up mandatory deductions for both benefits and taxes, and record payroll information for positions and workers for reporting and analysis purposes.</li>
<li>You can also set up and manage deductions for garnishments and tax levies, and for any associated administrative fees.</li>
</ul>
</td>
</tr>
<tr>
<td>Monitor and process your pay period process by using the new <strong>Payroll management</strong> workspace.</td>
<td>You can now easily monitor your payroll processing. At a glance, payroll administrators can see earning and pay statements that require their attention, so that the pay run will be complete and accurate. The <strong>Payroll management</strong> workspace lets users monitor and run end-to-end processes from a single workspace.</td>
</tr>
<tr>
<td>Generate positive pay files for payroll checks.</td>
<td>There is a new extension to Cash and bank management's positive pay functionality for payroll payments. Separate menu items have been added throughout the core process to enable isolated configuration that is specific to payroll. Functionality is identical to the core positive pay feature that was released in Microsoft Dynamics AX application version 7.0.1 (May 2016). Because of this extension, payroll data is completely isolated from the rest of your positive pay transactions. This isolation helps guarantee that only payroll users can access and see data that is related to payroll.</td>
</tr>
<tr>
<td>Import earnings statement lines from an external source by using the new Earning Statement Line data entity.</td>
<td>An important new data entity enables integration with external time and earning calculation systems. The data entity imports earnings statement lines and performs all the same default logic that the user entered directly on the earning statement. After import, the lines are automatically associated with the appropriate earnings statement document. If an appropriate earnings statement document doesn't exist, a document is created automatically.</td>
</tr>
</tbody>
</table>

## Planning and scheduling

| What you can do | Why this is important |
|-----------------|-----------------------|
| Set default order settings for sales and purchases, based on any active product dimension on the product master. Therefore, you can define default order settings for the stock keeping unit (SKU) or a partial SKU. | You can specify default order settings that apply to a product dimension or a combination of product dimensions.<p>**Example**</p><p>You sell a product that is named Polo T-shirt. This product is available in two colors: Green and Blue. It's also available in two sizes: Small and Medium. Color and Size are active product dimensions for Polo T-shirt. You can block purchases of all green Polo T-shirts, regardless of their size.</p> |

## Product master data

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Set up all default order settings and site-specific order settings at the same time, from one page.</td>
<td>This feature provides a better overview of item settings.</td>
</tr>
<tr>
<td>Create a nomenclature for product variant numbers.</td>
<td>You can include elements such as product dimensions, attributes, and characters in your product variant numbers. When you create a sales order or a purchase order, you can quickly find the specific product variant.</td>
</tr>
<tr>
<td>Search for products and product variants in sales and purchase scenarios.</td>
<td>When you create a sales line or a purchase line, you can search for products by using product dimensions and any product numbers except Global Trade Item Numbers (GTINs) and barcodes. This search is a full-text search that replaces the existing "Begins with" search that is used in the sales and purchase lookup list. This feature lets you find groups of products that have similar properties or a single product that has unique characteristics. To turn on this feature, select the <strong>Enable lookup for product search</strong> parameter on the <strong>Search parameters</strong> page.</td>
</tr>
<tr>
<td>Specify the product variant directly when you create a sales or purchase transaction. Alternatively, you can select in a list of valid dimension combinations.</td>
<td>This feature is a productivity enhancement.
<p><strong>Example</strong></p>
<p>You sell a product that is named Polo T-shirt. This product is available in two colors: Green and Blue. It's also available in two sizes: Small and Medium. Color and Size are active product dimensions for Polo T-shirt. When you enter a sales line for Polo T-shirt that has color Green and size Small, you don't have to enter data in the <strong>Item number</strong>, <strong>Color</strong>, and <strong>Size</strong> fields. You can create the line by following one of these steps:</p>
<ul>
<li>In the <strong>Item number</strong> field, enter the product variant number, the value of a color, or the size. In the lookup, find the specific variant that you want to sell, and create the sales line.</li>
<li>In the <strong>Item number</strong> field, enter the item number. Go to any product dimension field. In the <strong>Product dimension</strong> lookup, you will see all the released dimension combinations that apply to Polo T-shirt. In one step, you can select the product variant that you want to sell.</li>
</ul>
</td>
</tr>
<tr>
<td>Specify whether product numbers appear on transactional pages.</td>
<td>The transactional pages, such as sales orders and purchase orders, show only the <strong>Item number</strong> and <strong>Product name</strong> fields. To see the <strong>Product number</strong> field, select the <strong>Show product numbers on forms</strong> parameter under <strong>Product information management parameters</strong>.</td>
</tr>
</tbody>
</table>

## Project management and accounting

| What you can do | Why this is important |
|-----------------|-----------------------|
| Use late selection when you post invoice proposals in a batch. | Project accountants can set up a batch job to automatically pick up invoice proposals for posting, if those proposals fulfill criteria that are specified on the batch job. This feature improves the automation of invoice posting, because the batch job can run continuously and automatically picks up proposals for posting. |
| Create analytics in Power BI desktop. | Business intelligence (BI) content for project-related and resource-related data can be easily created in Power BI desktop. |
| Use purchase order prepayments, and include them correctly in the project estimate process. | For project purchase orders, prepayments must be processed before some payment can be released to vendors. These prepayment invoices now appear in the project estimation/recognition process for projects of the **Fixed price** type. |
| Access and manage cost and revenue estimates, and item requirements, directly from a work breakdown structure (WBS) task. | You can manage cost estimates, revenue estimates, and item requirements for a specific WBS task in the details dialog box for that task in the WBS planning view. |
| Pick a funding source on fee journals. | If the contract for a project contains multiple funding sources, you can select one specific funding source when fees are posted. If don't select a specific funding source, the funding rules that are specified on the contract are used to allocate the fee. |
| Open project statements in Excel. | New data entities for ledger updates and budget updates let you open project statement data in Excel and create analytics by using Excel functionality. |
| Use just one configuration key to enable functionality for Project management and accounting (PMA). | The project-related configuration keys have been replaced by one project configuration key that turns on PMA functionality. |

## Retail and commerce

### Advanced warehouse management in a retail store

Retailers can use the Advanced warehouse management (WHS) solution in their stores and make the required updates to the current point of sale (POS) features to support it. The processes of the handheld solution should work in a store as they do in any other warehouse. All current retail store inventory processes, and any POS processes that create or update inventory transactions, are updated so that they use the specific requirements for WHS-enabled warehouses.

| What you can do | Why this is important |
|-----------------|-----------------------|
| Use the POS to look up available inventory in WHS-enabled stores. | When you look up inventory, the process should work the same as it worked before. The lookup should show the available quantities at the warehouse level, and should not consider the Location, Inventory status, or License plate dimensions. |
| Use the POS to process a product receipt for a transfer order in a WHS-enabled store. | You can receive transfer orders at the POS for a WHS-enabled store and items. The user should be able to select the locations to receive into, and should be able to enter license plate IDs to automatically populate the receiving lines. |
| Use the POS to process a product receipt for a purchase order in a WHS-enabled store. | You can receive purchase orders at the POS for a WHS-enabled store and items. The user should be able to select the locations to receive into, and should be able to enter license plate IDs to automatically populate the receiving lines. |
| Use the POS to process a shipment of products from a WHS-enabled store. | You can register transfers from the POS for a WHS-enabled store and items. The user should be able to select the locations to ship from, the inventory status should be automatically generated, and license plates should be ignored. |

### Enable seamless omni-channel commerce

Seamless omni-channel commerce refers to management and order processing across brick-and-mortar stores, online storefronts, call centers, and mobile commerce experiences. For this release, the following investments have been made in this area:

- Improvements to publishing for e‑commerce storefronts
- A new consumer-facing mobile app that enables product discovery, account management, and online shopping

| What you can do | Why this is important |
|-----------------|-----------------------|
| Consumer: The current release of the consumer-facing app enables the following features- product search, category browsing, add to cart and guest checkout. Retailers can also apply their company's branding to the app, and then package it for the Android and iOS app stores. | Retailers can easily create a consumer-facing app that lets their customers browse, search products and ship products as a guest from their mobile devices. |
| Customer wish lists for c‑commerce online storefronts | Independent software vendors (ISVs) can use the wish list control to let users create and manage multiple lists in their online storefront, and view/use those lists in the POS. |
| Asynchronous customer creation via e-commerce online storefronts | ISVs can now create customer accounts even when Commerce Data Exchange: Real-time Service is unavailable. |
| Publish channel products from Retail Server to third-party storefronts. | Retail Server now supports service-to-service authentication. ISVs can take advantage of channel product publishing from Retail Server to third-party storefronts. |

### Extensibility

- Commerce runtime projects are now sealed from Retail SDK.
- Easier deployment and servicing through componentized Microsoft component packages and ISV packages for the POS, Retail Server, Databases, Payment and Hardware stations.

| What you can do | Why this is important |
|-----------------|-----------------------|
| CRT/Retail Server: Retailers or ISVs can extend the CRT through extension hooks. Inline code changes are not supported anymore. | To enable continuous integration and continuous deployment, inline code changes should be completely avoided. Also, to support easy uptake of hotfix without any code merge and deployment for CRT components. |

### Personalized product recommendations

| What you can do | Why this is important |
|-----------------|-----------------------|
| View personalized product recommendations at multiple touchpoints on point-of-sale (POS) to determine what a customer might be interested in based on their purchase history, items in their wish list, and items that other customers purchased online and in brick-and-mortar stores | For retailers with large catalogs, personalized recommendations help the customer with product discovery and empower store associates with intelligent clienteling. By showcasing products targeted to a customer's interests and buying habits, product recommendations can help retailers with upsell and can enhance customer retention. In Retail, product recommendations are powered by cognitive services and Microsoft Azure machine learning. |

### POS task recorder

| What you can do | Why this is important |
|-----------------|-----------------------|
| Retailers can use POS task recorder to produce training materials, Business process modeler (BPM) diagrams, and generate Help content to enhance productivity and do better analysis and design of applications. | To enable continuous integration and continuous deployment inline changes should be completely avoided. Also, to support easy uptake of hotfix without any code merge and deployment for CRT components. |
| Real time help in POS. | Cashier/Manager can get real time help from POS on business process without switching context. |

### Store system: Providing a seamless on-premises store experience

Store system is a deployment choice for retailers that helps drive a set of store operations, whether in an on-premises store, Microsoft public cloud, or the customer's own private cloud. For this release, the scope is in-store only. To better support environments that have slow and unreliable network connectivity, we must provide an option for retailers to deploy the channel database and Retail Server in the store. They can then continue to run their core business scenarios even when there is no connectivity to headquarters (HQ). Based on the various data points, which included engineering team discussions, customer survey results, and competitor analysis, we have identified the following solution scope as the ideal fit for our target customers:

- A self-service package is available for Store system.
- The default installation is a one-box deployment, but custom deployment is allowed.
- Enable easy deployment/self-servicing.
- Retail Server and the store database are in the store, together with the Async Client service.
- Retail Server in the store communicates directly with Application Object Server (AOS) in HQ for Store system.
- Support cross-terminal scenarios where there is no HQ connectivity.
- Retail Modern POS and Cloud POS always communicate with Retail Server in the store.
- Support Retail Modern POS and Cloud POS where there is no HQ connectivity.
- Support a Retail Modern POS–specific offline database (isolated to each Retail Modern POS instance) where there is no HQ connectivity.
- Authentication is based on service-to-service only for Store system.
- Real-time Service calls aren't supported if there is no Internet connectivity.
- Direct database connectivity of Retail Modern POS to the channel database isn't supported.
- Enable telemetry/monitoring.

| What you can do | Why this is important |
|-----------------|-----------------------|
| A retailer downloads the Store system self-service installer from the channel database page in Dynamics AX HQ and downloads the configuration file. | The retailer can seamlessly download the self-service package. |
| A retailer installs Store system by using the self-service installer. | The retailer can install Store system by using the self-service package. |
| The IT manager configures Store system in Dynamics 365 for Operations (channel database, channel profile, store, and deployable package). | The IT manager can configure Store system easily and efficiently. |
| A retailer operates Retail Modern POS in the on-premises store and can do real-time operations, such as issue gift cards, when there is connectivity. | The retailer can perform real-time actions from Store system when there is connectivity. |
| A retailer can sync data from the on-premises Store system to HQ whenever there is connectivity. | The retailer can sync to and from Store system when there is connectivity. |
| A retailer can have secure communication between the on-premises Store system and HQ. | The retailer can communicate from Store system securely when there is connectivity. |
| The IT manager and Microsoft Operations can monitor and report on the on-premises Store system (diagnostics and reporting changes). | The IT manager and Microsoft Operations can monitor Store system securely and troubleshoot efficiently. |

### Universal Windows Platform app for Retail Modern POS

Currently, Retail Modern POS is available only as a Windows 8.1 application for desktop computers and tablets, and as Cloud POS for desktop or tablet browsers. In this release, Retail Moderns POS is being converted to a Universal Windows Platform (UWP) app. This change will enable Retail Modern POS to run on any Windows 10 device (desktop, tablet, or phone) and even switch between views for Continuum-enabled devices.

| What you can do | Why this is important |
|-----------------|-----------------------|
| Enable important POS functionality for small-form-factor devices. | Retail POS functionality is available for phones and other small-form-factor devices that run Windows 10. |

## Supply chain management

### Consignment inventory

| What you can do | Why this is important |
|-----------------|-----------------------|
| As a vendor, you can store raw materials at the customer's warehouse. As a customer, you can postpone the actual purchase until the raw materials are required for production. | Keeping an inventory of raw materials can involve serious cost. By using consignment inventory, a vendor can store raw materials at the customer's warehouse. The customer can then postpone the actual purchase until the raw materials are required for production. Raw materials are ordered and received by using a consignment replenishment order. This replenishment order records physical transactions but doesn't affect the general ledger. To distinguish between customer-owned inventory items and vendor-owned inventory items, you can use the Owner inventory dimension. The change of ownership for inventory is handled by a journal process that handles the transfer of ownership for raw materials from the vendor-owned inventory to the customer-owned inventory. This process triggers the creation of a purchase order and a product receipt.[!NOTE] This feature is limited to inbound consignment of raw materials for production. It isn't integrated with Warehouse management (WHS) and Transportation management (TMS). |
| As a vendor, get information about the amount of consigned inventory that is transferred to the customer. | To bill a customer, the vendor requires information about the raw materials that were purchased from the consignment inventory and the date of purchase. The vendor can also monitor the on-hand inventory at the customer site by using the vendor collaboration interface. |
| Move vendor-owned inventory by using a transfer journal. | To track the physical position of the vendor-owned inventory, you must be able to record the position in the system. By using use a transfer journal, you can record the physical movement of inventory, such as the movement from one location in a warehouse to another location in that warehouse. |
| Adjust vendor-owned inventory by using a counting journal. | It's important that you keep the system on-hand inventory in sync with the actual physical inventory. The vendor-owned inventory can be adjusted in and out by using counting processes such as quantity adjustment and counting journal processes. |
| Find out more about consignment support in Dynamics 365 for Operations | For more information about the support for consignment processes, see [Consignment](../../../supply-chain/inventory/consignment.md), [Setting up consignment](/d365F-O/fin-ops-core/fin-ops/get-started/consignment), [Create a consignment replenishment order (Task guide)](../../../supply-chain/inventory/tasks/create-consignment-replenishment-order.md), and [Change the ownership of consignment inventory based on production demand (Task guide)](../../../supply-chain/inventory/tasks/change-ownership-consignment.md). |

### Vendor collaboration

| What you can do | Why this is important |
|-----------------|-----------------------|
| Enable vendors to respond to each purchase order line and suggest changes. | In some cases, vendors want to accept some purchase order lines but reject others. Vendors can now individually manage purchase order lines. Each line can be rejected, accepted, or accepted with changes. For example, vendors can change the delivery date, split the delivery and quantity, or suggest an alternative item. |
| Enable vendors to manage contact person information. | Vendors can maintain contact person information for their company. This information includes names, email addresses, and phone numbers. Access to this feature is granted through a dedicated security role. |
| Share documents that are related to purchase orders with vendors. | When you must share a document with a vendor, such as a document about requirements, it's convenient to link the document to the relevant purchase order. The vendor can then share notes and attachments with the customer by linking the document to their response to the purchase order. Document management is the underlying supporting framework, and only notes and attachments that are classified as "external" can be shared with vendors. |
| Provision new vendor users. | If your vendors use the vendor collaboration interface, they have a seamless way to request new user accounts when new contacts require access to vendor collaboration. Procurement professionals can submit a request for a user account for a contact person at the vendor organization. A vendor contact person who is already a vendor collaboration user can also submit this type of request. This request eventually creates a new user in Dynamics 365 for Operations that has vendor-specific security roles. It also facilitates a request to the Microsoft Azure B2B portal to provision the user with a new Azure Active Directory (Azure AD) user account. Vendors can also request that specific vendor user accounts be inactivated, or that security roles be modified. |
| Find out more about support for vendor collaboration in Dynamics 365 for Operations. | For more information about vendor collaboration, see [Vendor collaboration with external vendors](../../../supply-chain/procurement/vendor-collaboration-work-external-vendors.md), [Vendor collaboration with customers](../../../supply-chain/procurement/vendor-collaboration-work-customers-dynamics-365-operations.md), [Manage vendor collaboration users](../../../supply-chain/procurement/manage-vendor-collaboration-users.md), [Set up and maintain vendor collaboration](../../../supply-chain/procurement/set-up-maintain-vendor-collaboration.md), and [Vendor collaboration invoicing workspace](../../../finance/accounts-payable/vendor-portal-invoicing-workspace.md). |

### Intercompany order processing

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Define, directly on sales order lines, where the demand should be sourced from, and how it should be sourced.
<p><strong>Example</strong></p>
<p>Create a sales order line, and specify direct delivery as the delivery type. The primary vendor is added to the sales order line as the sourcing point.</p>
</td>
<td>The flow for order taking has been improved significantly. You can now define, directly on sales order lines, where the demand should be sourced from, and how it should be sourced. You no longer have to wait until all lines have been added to the sales order. New options on sales order lines let you specify the delivery type when you specify a vendor. When you associate a vendor with sales order lines, order chains are created for delivery from the vendor.
<ul>
<li>The vendor can be an intercompany vendor that uses an internal purchase order and sales order, or it can be an external vendor that uses an external purchase order.</li>
<li>The delivery type can be <strong>Direct delivery</strong> or <strong>Stock</strong>. The <strong>Stock</strong> delivery type indicates that the vendor should supply to the local inventory before it ships to the customer.</li>
</ul>
</td>
</tr>
<tr>
<td>Create an order promise directly from sales order lines.
<p><strong>Example</strong></p>
<p>Create a sales order line that is sourced from an intercompany vendor. Leave the line. Delivery dates are calculated according to availability in the sourcing company.</p>
</td>
<td>When you create sales order lines that use the new sourcing information, delivery dates are calculated according to the <strong>Delivery date</strong> control. For example, if an intercompany vendor is selected, the availability in the sourcing company is calculated. In this way, order chains are automatically created together with sales order lines. This functionality helps guarantee that delivery dates become visible in the sourcing company, so that the available-to-promise (ATP) profiles can handle the anticipated demands directly as sales orders are created.</td>
</tr>
<tr>
<td>Review product availability across all sourcing locations, and select the best sourcing option.</td>
<td>The <strong>Delivery alternatives</strong> page has been redesigned, and now provides valuable information about all approved internal and external vendors. This information includes sourcing options for vendor procurement. When you select a delivery mode, the system calculates feasible delivery dates. You can seamlessly select the best option for the customer and apply this option to every sales order line.</td>
</tr>
</tbody>
</table>

### Warehouse enhancements for high-volume distribution centers

| What you can do | Why this is important |
|-----------------|-----------------------|
| Create work after goods have been packed at a packing station. | This feature is useful when there are additional processes after manual packing work (such as palletization, quality inspection, consolidation of shipments, or changes to loading docks). The new **Packed container picking** work type lets you model these tasks by using separate work lines. You can now model packing stations to generate work after packing. This work can be used to organize the movement of packed inventory. |
| Group containers at the packing station. | This feature enables multiple packages to be grouped into one container or license plate at the packing station. For example, an e-commerce/wholesale operator can group 100 individually packed packets into a single container (such as a pallet or cage). This container can then be moved, staged, or loaded through a single work instruction that a worker generates by scanning a single barcode (license plate) for the grouped container. This feature minimizes the work transactions for moving many smaller packed containers. For more information, see [Create a mobile device menu item for license plate consolidation (Task guide)](../../../supply-chain/warehousing/tasks/create-mobile-device-license-plate-consolidation.md). |
| Create a release policy for packed containers. | Work that is triggered by container release can be created either automatically or manually. When it's automatic, work is generated at container closure by using the location directive and work template framework. When the release is manual, the packer can decide whether the work should be generated for a single container or for a group of containers. This feature reduces the risk that closed containers will be picked and moved before they are ready to be moved from the packing station. It also allows for non-system-steered grouped release. |
| Short-picking reallocation | Support has been added for short-pick processes, to help an associate who can't pick the goods and wants to fulfil the order when the item that is required is available at another location. You can use an automatic reallocation process that uses the same location directives to retrieve the goods if they are available at another location. Alternatively, when manual reallocation is used, the mobile device show a list of locations together with the available quantity. The warehouse worker can then select which location to use inventory from. These two methods can be set individually or combined as a single command on the warehouse worker menu. When manual re-allocation is used, the warehouse worker can pick the short-picked item quantity from several locations. For more information, see [Set up short picking item reallocation (Task guide)](../../../supply-chain/warehousing/tasks/set-up-short-picking-item-reallocation.md). |
| Move inventory that has work associated with it. | You can now move inventory that has work associated with it. This feature can be useful if, for example, a worker wants to clear some inbound dock space and move registered pallets that are waiting to be put away to another inbound location. The dock is cleared and can receive an additional load of goods, and the inventory that has been moved is updated with new put-away information. This feature can also be used to free up space at picking locations by moving the inventory that has work associated with it and creating space for replenishment. You can also use it to move loads from one staging location to another without losing the loading work that has been generated. In this way, the feature can help optimize the time that is required to load trucks when they arrive. You can move inventory that has been reserved for sales orders, transfer order issues, transfer order receipts, and purchase orders. Movement is prevented if it will cause lines to be split. For example, if you have a work line for 100 pieces of an item, you can't move only 30 pieces of that item to another location. |
| Merge license plates that have work associated with them. | You can merge license plates that have outbound work associated with them. For example, when a pick has been broken into several pieces of work, it can be useful to allow the license plates to be merged after they are delivered at the staging location. License plates can be consolidated only if they are at the same location, are members of the same load, and have the same shipment information. |
| Freeze picking work that is associated with replenishment at the line level. | You can now freeze work at the line level instead of at the header level, so that workers can fulfil pick lines that aren't frozen by demand replenishment. Therefore, a wholesaler that has large sales orders, or a retailer that has large sales orders or replenishment transfer orders, can allow the picking work to start on all lines that aren't subject to replenishment work. The picking and replenishment work can then be completed in parallel. This feature can be configured so that you can select whether to freeze at the header level or the line level. You can also use both methods and create a work template for each method. The header/line configuration is set on work templates, but you can change it directly on the generated work. |
| Cancel work by using the mobile device. | You can now cancel work by using the mobile device, with or without demand replenishment. Previously, you had to use the rich client. To enable this functionality, create a mobile device menu item that has the mode set to **Indirect** and the activity code set to **Cancel work**. |

### Warehouse operation enhancements

| What you can do | Why this is important |
|-----------------|-----------------------|
| Model different container types. | You might use different container types in the warehouse to optimize storage and for other reasons. The new Container type entity has the physical characteristics of the container types. You can now associate license plates with a specific container type and use location stocking limits. For example, you can use this feature to control how many pallets (or other container types) you allow at a specific location. Container types have also been added to unit sequence groups to add default container types for the receiving process. Container types can be used with inbound and outbound location directives. They can also be used in the on-hand inventory view to help you determine how many container types are currently stored on hand. For more information, see the [Use of license plates associated with a container type to drive warehouse management processes](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/06/20/use-of-license-plates-associated-with-a-container-type-to-drive-warehouse-management-processes/) blog post. Although this blog post describes an update to Microsoft Dynamics AX 2012, the same support has now been added to Dynamics 365 for Operations. |
| Reverse shipments. | In a warehouse, you must be able to handle late changes. For example, some goods might be damaged, so that you can't ship them. Alternatively, a customer might make a late request to cancel or change an order. Dynamics 365 for Operations now lets you reverse a shipment. Therefore, you can cancel a packing slip so that you can update it with the correct quantities later. Similarly, on the inbound flow, you can cancel product receipts so that an updated version can be created. |
| Use pallets that have mixed items. | You can now receive and register a "mixed" pallet. A mixed pallet consists of different items that are assembled onto one pallet for one or several purchase orders or lines. All registrations can be summarized into one target license plate. This process is enabled though the warehouse mobile device. For example, when the pallet of mixed items arrives at the warehouse, the receiving clerk identifies the items and the quantities on the pallet before the pallet is moved to dedicated put-away locations. The put-away locations are identified by work templates and location directives. If the put-away locations are spread over several items that have fixed locations, this feature creates as many put work lines as there are different items on the mixed pallet. This feature makes registration and put-away of the received mixed items pallets faster and more flexible. For more information, see the [Receive and register a pallet with mixed source document lines using one license plate](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/13/receive-and-register-a-pallet-with-mixed-source-document-lines-using-1-license-plate-purchase-order-matching/) blog pot and the information about mixed pallet support in the [announcement of our recent cumulative update](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/06/30/whats-new-in-cu11-for-wms-and-tms/). Although this blog post describes an update to AX 2012, the same support has now been added to Dynamics 365 for Operations. |

### Minor feature enhancements in Supply chain management

<table>
<thead>
<tr>
<th>What you can do</th>
<th>Why this is important</th>
</tr>
</thead>
<tbody>
<tr>
<td>Use new data entities to import and export data.</td>
<td>You can import and export data by using these data entities:
<ul>
<li>Freight invoice</li>
<li>Aggregate on-hand by warehouse and inventory status</li>
<li>Inventory charges</li>
<li>Quotation</li>
</ul>
</td>
</tr>
<tr>
<td>Use the enhanced Gantt control to develop interactive scheduling scenarios.</td>
<td>The enhanced Gantt control lets you develop new interactive scheduling scenarios and deliver enhanced APIs that can be used to customize the appearance of activities. Here are some of the new APIs:
<ul>
<li>Vertical drag-and-drop of activities</li>
<li>Add/remove activities</li>
<li>Preview booked periods in summary bar</li>
<li>Change color and style of activity borders</li>
<li>Change color, style, and background of text in grid</li>
</ul>
</td>
</tr>
<tr>
<td>Better handle material and resource planning.</td>
<td>A few enhancements have been made to material and resource planning:
<ul>
<li>The issue margin is now handled when an item is on hand.</li>
<li>Overwrite the delivery date when you firm planned orders.</li>
<li>Prioritize fulfillment of orders over safety stock.</li>
<li>Prevent scheduling of planned orders in the past.</li>
</ul>
</td>
</tr>
<tr>
<td>Report actual consumption for production, and view inventory status.</td>
<td>You can view actual consumption for production. Additionally, a new <strong>Display inventory status</strong> check box that has been added to <strong>Movement</strong> on the <strong>Work creation</strong> menu item lets you view inventory status.</td>
</tr>
<tr>
<td>Calculate volumetric weight, if the rates for your shipping carrier are based on volumetric weight.</td>
<td>A new TMS rate engine that is based on volumetric weight has been added, so that you can calculate volumetric weight.</td>
</tr>
</tbody>
</table>

## Additional resources

[What's new or changed in finance and operations home page](whats-new-changed.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
