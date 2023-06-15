---
title: What's new or changed in Dynamics AX 7.0 (February 2016)
description: This article describes features that are either new or changed in Microsoft Dynamics AX 7.0. This version contains both platform and application features and was released in February 2016.
author: sericks007
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 515bc6e7-a85d-4995-95c6-6cab6c8aa0f9
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics AX 7.0 (February 2016)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics AX 7.0. This version contains both platform and application features and was released in February 2016.

## Cost management

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Get a quick overview of the inventory balance, the work in progress (WIP) inventory balance, and what the inventory inflow and outflow have been for the selected fiscal year.</td>
<td>Not applicable</td>
<td>The <strong>Cost administration</strong> workspace contains a section where the inventory statement or WIP inventory statement is presented for the selected fiscal period. The statement is based on a data set cache that, by default, is updated every 24 hours. The data set cache can be configured so that users can manually update it for real-time reporting. The <strong>Data refresh status card</strong> in the <strong>Cost administration</strong> workspace shows when the cache was last updated.</td>
<td>Cost controllers are interested in knowing whether the inventory or WIP inventory statement balance increases or decreases over time. By classifying operational events in the statement, the cost controller can get an overview of how inventory is flowing. If inventory or WIP inventory is evaluated by standard costs, the overall variance registered can also be seen.</td>
</tr>
<tr>
<td>Use the <strong>Cost management</strong> module.</td>
<td>Not applicable</td>
<td>Cost management is introduced as a domain area. Cost-related configuration and insight were scattered throughout Inventory management, Production control, and Accounts Payable.</td>
<td>Because all the tasks that are related to cost management are centralized in one module, it will be easier for cost controllers to maintain the system.</td>
</tr>
<tr>
<td>The posting types that are related to inventory accounting and production accounting have been updated.</td>
<td>The labels in the <strong>InventPosting</strong>, <strong>Resource</strong>, <strong>ResourceGroup</strong>, and <strong>ProductionGroup</strong> forms aren't always aligned with the <strong>LedgerPostingType</strong> labels that are actually used. It's not easy to understand the terminology that is used in the labels.</td>
<td>The labels have been updated so that labels on the <strong>InventPosting</strong>, <strong>Resource</strong>, <strong>ResourceGroup</strong>, and <strong>ProductionGroup</strong> pages match the actual <strong>LedgerPostingType</strong> labels. All the labels have also been renamed so that the labels match the operational events. Note that the actual posting logic hasn't been changed.</td>
<td>It's easier to configure the system, because the new labels are related to the operational events that use this posting type.</td>
</tr>
<tr>
<td>Import/export the purchase price, cost, or sales price from Microsoft Excel into or from a costing version.</td>
<td>You can't correctly import prices or costs into a costing version, because the data model requires an InventDim ID.</td>
<td>The introduction of data entities makes it possible to implement an import/export feature. This feature lets users import/export prices or costs into a costing version.
<ul>
<li>Import a full list of next year's purchase prices that is obtained from the Purchasing department.</li>
<li>Push costs and standard sales prices from headquarters to one or more sales companies in one operation.</li>
</ul></td>
<td>It can save the cost controllers a significant amount of time when they maintain the system, especially when they must maintain predetermined costs for the next fiscal year.</td>
</tr>
<tr>
<td>Get a quick overview of the inventory balance and average unit cost of a cost object.</td>
<td>The user must open the on-hand form and select the inventory dimensions that reflect the cost object. Therefore, the user must know which inventory dimensions were marked for financial inventory for the specific product.</td>
<td>A new <strong>Cost object</strong> page is introduced. By default, this page shows all cost objects that are related to the product. The page shows the current inventory quantity, value, and average unit cost per cost object.</td>
<td>It removes some of the complexity and makes it easier to be a cost controller.</td>
</tr>
<tr>
<td>Use the new <strong>Cost entries</strong> page during inventory control.</td>
<td>It can be complicated to perform inventory control on registered inventory transactions and related settlements, because the same transactions can be physical or financial.</td>
<td>The <strong>Cost entries</strong> page offers a new way to view inventory transactions.
<ul>
<li>Transactions are shown in a chronological order.</li>
<li>Only transactions that contribute to costs are included.</li>
<li>There is no notion of physical costs or financial cost.</li>
<li>There is no notion of physical quantity or financial quantity.</li>
<li>The costs are added incrementally.</li>
</ul></td>
<td>It can save cost controllers a significant amount of time when they must perform inventory control at the transaction level.</td>
</tr>
<tr>
<td>Use the new <strong>Production WIP statement</strong> dialog box to see a summarized view of accumulated costs for a specific product.</td>
<td>Not applicable</td>
<td>The WIP statement shows a summarized WIP balance of the specific production order, grouped into appropriate cost classifications. A chart shows, in chronological order, how operational postings have affected the WIP balance.</td>
<td>It can save cost controllers a significant amount of time when they need to know what the current WIP balance is on a specific production order, or how much material has been consumed on the order.</td>
</tr>
<tr>
<td>Use the View cost comparison feature that has been introduced on production orders. The feature makes it easier to compare costs that are related to a production order.</td>
<td>The user can compare only estimated costs and realized costs. The comparison can be done at the lowest level.</td>
<td>The cost comparison feature lets cost controllers compare the following data:
<ul>
<li>Active cost versus Estimated cost = Planning variance</li>
<li>Estimated cost versus Realized cost = Production variance</li>
<li>Planning variance + Production variance = Total variance</li>
</ul>
This feature works independently of costing methods that are assigned to the produced item. By default, a chart shows the cost comparison by cost group type. The chart lets users drill into more detailed levels.</td>
<td>It lets cost controllers or production managers analyze where the production variances come from, and what causes them.</td>
</tr>
</tbody>
</table>

## Developer

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Create web-based solutions in the cloud that are accessible on many devices. | Not available | The current version of Dynamics AX is based on a new web-based client and client framework. | You can provide next-generation solutions to your end users. |
| Use Microsoft Visual Studio to develop your solutions. | Microsoft MorphX is the main development environment, but some development occurs in Visual Studio. | Visual Studio is the only development environment. | It keeps familiar Dynamics AX 2012 concepts, and seamlessly adapts them to the Visual Studio framework and paradigms. It enables standard interoperability with other .NET languages and projects. |
| Compile Common Intermediate Language (CIL) for all features. | X++ is compiled to p-code. | The brand-new X++ compiler generates CIL for all features. CIL is the same intermediate language that is used by other .NET-based languages. | CIL is faster, can efficiently reference classes in managed dynamic-link libraries (DLLs), and can run on a large tool base of .NET utilities. |
| Embed business intelligence (BI) reports and visualizations in the Microsoft Dynamics AX client. | Not available | Create highly-intuitive and fluid visualizations. | It provides decision-making insights that are based on BI. |
| Integrate with Microsoft Office. | Not available | New capabilities include the Excel Data Connector app, **Workbook Designer** page, Export API, and Document management. | You can create productivity solutions for your end users. |
| Automate build, test, and deploy. | Partially available | Deploy the Developer topology by using Developer and Build VM. Auto-configure Build VM to discover, build modules from Visual Studio Online (VSO), and run tests. C\# and X++ module compilation and references are supported. | It increases developer productivity by reducing cost and effort for testing and validations. |
| Customize with overlayering and extensions. | Extensions aren't available. | The current version of Dynamics AX has a new customization model. | You can customize source code and metadata of model elements that are shipped by Microsoft or third-party Microsoft partners. |
| Build new controls and UI elements by using X++ and a modern web framework. | Custom controls rely on external frameworks such as Microsoft ActiveX and Windows Presentation Foundation (WPF). | It's easier to build controls in the current version. The X++ framework can be used for application behavior and business logic, and an HTML/JavaScript-based client allows for modern visualizations. | Your controls can be designed to look and behave just like the Dynamics AX out-of-box (OOB) controls. |
| Evaluate and tune performance by using new tools. | PerfSDK, Data Expansion Toolkit, Trace Parser WEb app, and PerfTimer aren't available. | PerfSDK, Data Expansion Toolkit, Trace Parser Web app, and PerfTimer are new. | The software development kit (SDK) lets you test and validate all critical business processes for performance in a single-user and, if applicable, multi-user test run. The Data Expansion Toolkit lets you correctly expand all performance tests that must have master data and transactional data correctly expanded. The Trace Parser lets you validate a single-user performance test or a multi-user run. The PerfTimer lets you see whether any query or any specific method call is causing a performance issue. Therefore, you don't have to take a trace and analyze everything in detail. |
| Expose updatable view by using OData. | Not available | The current version of Dynamics AX introduces a public OData service endpoint that enables access to Dynamics AX data in a consistent way across a broad range of clients. | Your solutions can interact with RESTful services, share data in a discoverable way, and enable broad integration by using the HTTP stack protocol. |
| Take advantage of the business connector to author business logic and support integration scenarios. | The business connector is available to call into X++ code from managed code. We recommend that you use the business connector only to author business logic in C\#, not for integration scenarios. | The business connector is no longer supported. The authoring requirement is provided by the fact that X++ is compiled into managed code. Therefore, interop is easier. The integration scenarios are met by using OData. | You can't use the business connector going forward. |
| Choose scale (that is, the number of decimal places) on real database fields and extended data types (EDTs). | Scale 16 is the default scale and can't be changed by the developer. | EDTs and fields now have a scale property that can be applied to the individual field and EDT. The default is set to 6, not 16. | Performance with NCCI tables (in-memory support in SQL) is faster by orders of magnitude when a smaller scale is used. Change the scale as your use of the individual fields requires. |

## Financial management

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Export account structures to Microsoft Excel.</td>
<td>Not available</td>
<td>You can now select an account structure and export it to Excel.</td>
<td>Many customers have requested the ability to export account structures to Excel for easier filtering.</td>
</tr>
<tr>
<td>View ledgers and advanced rule structures that are associated with an account structure on a single page.</td>
<td> The user must navigate to multiple forms to see the ledger and the account structure that are used.</td>
<td>FactBoxes have been added to the account structure page.</td>
<td>It's easier to access important information when account structures are defined and edited.</td>
</tr>
<tr>
<td>View ledgers that are associated with a chart of accounts on a single page.</td>
<td>The user must navigate to each company and open the ledger form to see the chart of account that is assigned to the ledger.</td>
<td>FactBoxes have been added to the <strong>Chart of accounts</strong> page.</td>
<td> It's easier to access important information when a chart of accounts is defined and assigned.</td>
</tr>
<tr>
<td>View closing sheet adjustments and closing transactions in separate columns on the <strong>Trial balance</strong> list page.</td>
<td>The user sees both types of transactions in a single column.</td>
<td>An additional parameter has been added to the <strong>Trial balance</strong> list page.</td>
<td>It allows for more concise analysis of data and is also required for regulatory reporting in some countries/regions.</td>
</tr>
<tr>
<td>Use the new <strong>Global general journal</strong> page.</td>
<td>Not available</td>
<td>New <strong>Global general journal</strong> page to enter general journals. Privileges for this page are added to the <strong>Accountant</strong> role.</td>
<td>Makes it possible for a shared service accountant to enter general journals across companies without having to leave the form or to switch company context.</td>
</tr> 
<tr>
<td>Use the new <strong>Accounting source explorer</strong> page.</td>
<td>Available from Dynamics AX 2012 R3 CU10.</td>
<td>New <strong>Accounting source explorer</strong> page and actions to navigate there from the <strong>Trial balance</strong> list page and the <strong>Voucher transactions</strong> page.</td>
<td>Makes it possible view the most detailed information about the source for a trial balance or an accounting entry in general ledger, or for ad-hoc analysis.</td>
</tr>
<tr>
<td>Add additional posting layers.</td>
<td>Adding additional posting layers was a developer experience.</td>
<td>Ten posting layers are now available.</td>
<td>Most customers add additional posting layers.</td>
</tr>
<tr>
<td>Use the Related voucher option.</td>
<td>Not available</td>
<td>The Related voucher option is available for users to see the voucher in the offset company when posting intercompany transactions. From the related vouchers users can click on the details and quickly jump to the offset company voucher.</td>
<td>When posting intercompany transactions, users had no visibility or tracing to the voucher that was posted in the offset company.</td>
</tr>
<tr>
<td>Mass financial period close</td>
<td>Not available</td>
<td>Users are able to update the module access and change the period status for multiple companies at one time.</td>
<td>Prior to the feature, users had to change what company they were logged in, navigate to the ledger calendar form and manually update the module access and period status.</td>
</tr>
<tr>
<td>Have exchange rates powered by Oanda.</td>
<td>Configuring the exchange rate provider to import rates from Oanda was a developer experience.</td>
<td>If users have a key for Oanda they can enter it when configuring the exchange rate provider.</td>
<td>Users can take advantage of out-of-the box functionality by having exchange rates powered by Oanda imported in on a scheduled basis.</td>
</tr>
<tr>
<td>Filter financial reports (Management Reporter) based on dimensions, attributes, dates, and scenarios.</td>
<td> All filtering of Management Reporter reports is handled through the design of the report. For example, if a user who has viewing privileges wants to view a report for a different date, a report designer must make the modification.</td>
<td>Report options have been added, so that different filters can be applied when a user is viewing a report. A new report is then generated based on those filters.</td>
<td>Consumers of financial reports can apply different filters for dimensions, dates, attributes, and scenarios without requiring updates to report designs.</td>
</tr>
<tr>
<td>View financial reports (Management Reporter) within the Microsoft Dynamics AX client.</td>
<td>A separate web client was used to view Management Reporter reports.</td>
<td>All financial reports can be accessed in the Dynamics AX client. The user selects a report to view, and the report is displayed in the client.</td>
<td>You can now view financial reports without having to access a different client/application.</td>
</tr>
<tr>
<td>Print financial reports (Management Reporter) from the Microsoft Dynamics AX client.</td>
<td>Printing a report would use the browser's print options for printing and only prints what the user can see on the screen.</td>
<td>The user can choose the detail level and page setup for a report by using the Print option in the financial report in the Dynamics AX client.</td>
<td>Printed reports print in the way users expect instead of printing a web page.</td>
</tr><tr>
<td>Analyze financial data by using the "Monitor financial performance" Power BI content.</td>
<td>Not available</td>
<td>On PowerBI.com, select <strong>Get Data</strong>, and then select the <strong>Dynamics AX – Financial performance</strong> content pack. Enter the URL for your Dynamics AX endpoint to see your data reflected in the dashboard.</td>
<td>In three to four clicks, organizations can deploy a Power BI dashboard that contains important financial data. Content can be personalized by the organization.</td>
</tr>
<tr>
<td>Track financial period closing processes.</td>
<td>Not available</td>
<td>Closing templates and schedules can be created by using the Financial period close configuration. Use the <strong>Financial period close</strong> workspace to track the progress of closing schedules across multiple companies.</td>
<td>This workspace eliminates manual systems to define, schedule, and communicate close activities. Therefore, the number of days to close is reduced.</td>
</tr>
<tr>
<td>Monitor budget versus actuals, and create ledger forecasts by using the <strong>Ledger budgets and forecasts</strong> workspace and additional inquiry forms.</td>
<td>Not available</td>
<td> The workspace can be accessed through the Dynamics AX dashboard. It includes links to several new inquiry pages: <strong>Actuals vs. budget summary</strong>, <strong>Budget control statistic summary</strong>, <strong>Budget register entries</strong>, and <strong>Budget plans</strong>.</td>
<td>New inquiry pages enable easy access to budget information. The workspace combines all budget maintenance and monitoring tasks in one place that is easy for budget managers or accounting managers to use.</td>
</tr>
<tr>
<td>Create layouts for budget plans and forecasts.</td>
<td>The <strong>Budget plan</strong> document is viewed as a list of lines that have effective dates and amounts for combinations of financial dimensions. The user must create and use Excel templates to view budget plan data in a PivotTable.</td>
<td>An unlimited number of layouts is available for budget plans and forecasts. You can combine selected financial dimensions, user-defined columns, and other row attributes (such as comments, projects, and assets) in the layout. Users can switch the layout for the budget plan document on the fly and edit data by using any selected layout. The configuration of budget planning is simplified by eliminating scenario constraints and using layouts to define which data can be viewed and edited in each stage of the budget plan document.</td>
<td>It gives the flexibility to create and edit budget plans by using both Excel and the Dynamics AX client. Templates for Excel workbooks can be generated by using the Budget plan layout setup.</td>
</tr>
<tr>
<td>Print the <strong>Vendor Invoice Transactions</strong> report by using information from the <strong>Detailed Due Day List</strong> report, which includes the days past due.</td>
<td>You must print two different reports: <strong>Detailed Due Day List</strong> and <strong>Vendor Invoice Transactions</strong>.</td>
<td>The information on the two reports has been consolidated into the <strong>Vendor Invoice Transactions</strong> report. The <strong>Detailed Due Day List</strong> report was deprecated.</td>
<td>It eliminates the need to print two separate but related reports.</td>
</tr>
<tr>
<td>Generate regulatory reports directly in PDF format.</td>
<td>You must first generate a regulatory report in one format and then export it to PDF format.</td>
<td>The PDF format is the default format for regulatory reports.</td>
<td>It provides a unified display experience on both the computer monitor and a printed paper copy.</td>
</tr>
<tr>
<td>Run the sales tax settlement process as a batch process.</td>
<td>Not available</td>
<td>On the <strong>Sales tax settlement period</strong> page, you can specify that the settlement process should be run in batch mode.</td>
<td>For periods that have many tax transactions, the settlement process can be time consuming, and it might be better to run the process in the background as a batch process.</td>
</tr>
</tbody>
</table>

## Foundation

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Access the client anytime, anywhere.</td>
<td>The AX 2012 desktop client provides a full set of forms, but it can run only on computers that run Microsoft Windows and requires installation. Terminal Server is often used with the desktop client to enable access over a wide area network (WAN). The Enterprise Portal web client provides a reduced set of forms.</td>
<td>The two AX 2012 clients have been replaced by a single, standards-based web client that provides the full set of functionality of the desktop client together with the reach of the Enterprise Portal client.</td>
<td>It prevents development efforts from being split between two UI platforms. By using standard web interfaces, it eliminates the need for Terminal Server.</td>
</tr>
<tr>
<td>Be productive by using the new Task recorder.</td>
<td>The AX 2012 Task recorder requires direct access to an Application Object Server (AOS) computer and elevated privileges, and provides no editing options.</td>
<td>The new Task recorder can be used directly from the web client. Access to Task recorder doesn't require admin privileges. Recorded steps can be viewed live as you record, new editing options have been introduced, and Task recorder supports more scenarios in addition to existing Business process modeler (BPM) scenarios.</td>
<td>The new Task recorder provides a streamlined experience and powers new capabilities in Dynamics AX. Some of these capabilities are available now, and more will follow in the future.</td>
</tr>
<tr>
<td>Help users better understand their upcoming work with workspaces.</td>
<td>Role centers provide an overview of information that pertains to a user's job function in the business or organization.</td>
<td>Workspaces are a new concept in Dynamics AX that are meant to replace role centers as the primary way to navigate to tasks and specific pages. They provide a one-page overview of a business activity and help users to understand the current status, the upcoming workload, and the performance of the process or user. Workspaces are more granular than AX 2012 role centers, and a user may have access to multiple workspaces.</td>
<td>Workspaces are meant to increase user productivity. Developers will need to create a workspace for every significant "activity" supported in the product. A legacy role center from AX 2012 will typically be replaced by multiple workspaces in the current version of Dynamics AX.</td>
</tr>
<tr>
<td>Make forms responsive to browser viewport or device size.</td>
<td>In AX 2012, form content was rigidly laid out using columns, and the overall form height/width was largely determined based on the controls on the form.</td>
<td>With the shift to the web in the latest Dynamics AX, a form's dimensions are now based on the browser viewport size or device. Controls and layout parameters have been modified or added to better respond to changes in viewport size.</td>
<td>Form content needs to be more responsive to optimally utilize the available height/width of the browser or device. Achieving responsiveness may require changes in the way a form is modeled.</td>
</tr>
<tr>
<td>Use patterns for an enhanced form development experience.</td>
<td>Form templates were available as starting points for form development in AX 2012 based on a form style. The Form Style Checker, an optional add-in, provided information on how a form deviated from its corresponding template.</td>
<td>In the current version of Dynamics AX, form patterns have been introduced. Form patterns represent a combination of form templates and the Form Style Checker tightly integrated into the development experience. Patterns have been defined at the form level (like AX 2012) with additional subpatterns now available at the group and tab page level.</td>
<td>Forms that adhere to patterns have many benefits including a more consistent user interface, a simpler development experience, easier form upgrade path, and increased confidence in form layout responsiveness.</td>
</tr>
</tbody>
</table>

## Help

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Access guided procedural Help (task guides) and conceptual topics by clicking <strong>Help</strong>.</td>
<td>The AX 2012 Help system points to HTML topics that are stored on a local web server. Customers and partners can create their own Help.</td>
<td>The Help system in the current version of Dynamics AX displays task guides that are stored in Microsoft Dynamics Lifecycle Services (LCS) BPM. The Help system also displays topics from Microsoft Learn. For more information, see <a href="help-overview.md" data-raw-source="[Help system](help-overview.md)">Help system</a> and <a href="new-task-guides-available-february-2016.md" data-raw-source="[New task guides (February 2016)](new-task-guides-available-february-2016.md)">New task guides (February 2016)</a>.</td>
<td>Task guides provide a guided, interactive experience that leads you through the steps of a task or business process. You can download and customize the task guides that Microsoft provides. The article provides a faster and more flexible way to create, deliver, and update product documentation. Therefore, it helps guarantee that you have access to the latest technical information.</td>
</tr>
</tbody>
</table>

## Human capital management

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Transfer skills and certificates to class participants upon course completion.</td>
<td>This is a manual process.</td>
<td>When a course is completed, a new option becomes available to update a participant's records with the new skills and certificates.</td>
<td>It provides a new and efficient way to update employee records.</td>
</tr>
<tr>
<td>Quickly verify employment.</td>
<td>This is a manual process.</td>
<td>Your HR department can quickly verify employment by using a workspace or the employee page.</td>
<td>Your HR department no longer has to access multiple pages to verify the start date, manager, months in the position, and compensation data.</td>
</tr>
<tr>
<td>Let employees view, update, and delete information in the system.</td>
<td>Available, but with limited view and update capabilities.</td>
<td>This feature is enabled, and lets employees and contractors view a wide range of personal data. Optionally, a workflow can be used when information is created, updated, or deleted.</td>
<td>It lets employees take control of their information, whether that involves updating address or contact information, applying for a job, taking a questionnaire, or updating their image. When a workflow is enabled, information can be reviewed by an approver or automatically approved, based on your business processes.</td>
</tr>
<tr>
<td>Let managers view or edit employee information.</td>
<td>Available, but with limited view and update capabilities.</td>
<td>Depending on configuration settings and security, managers can view or edit employee information.</td>
<td>It lets managers access important employee data, so that they can make better decisions about resourcing, performance, and employee development.</td>
</tr>
<tr>
<td>Take advantage of manager self-service functionality.</td>
<td>Not available</td>
<td>Managers can now submit requests for new hires (employees and contractors), transfers and termination (ending employment). Managers can also request a new position, extend a positions duration, or request position changes.</td>
<td>These scenarios were previously only exposed to Human Resources. Enabling these scenarios provides powerful tools to managers in an organization. Optional workflows can be enabled to provide the right level of review and approvals.</td>
</tr>
<tr>
<td>Access the results of compensation processing.</td>
<td>Results are available only at the time of processing.</td>
<td>Compensation processing results can now be accessed at any point after the process has been run.</td>
<td>It provides an excellent audit of the process and the outcome of the process. It also provides a comprehensive view of the data before employee records are updated.</td>
</tr>
<tr>
<td>Access the results of benefit processing.</td>
<td>Results are available only at the time of processing.</td>
<td>Benefits processing results can now be accessed at any point after the process has been run.</td>
<td>It provides a comprehensive view of the data that is updated by benefit enrollment and cost changes.</td>
</tr>
<tr>
<td>View "Date Effective" timeline changes.</td>
<td>Not available</td>
<td>This comparison tool is available for employees, positions, and jobs. It provides a comprehensive view of changes from one version of a record to another.</td>
<td>It saves you time when you view changes that have occurred over time to employees, positions, and job records. It lets you quickly compare two versions of a record, or all records, over time.</td>
</tr>
<tr>
<td>View employees by company.</td>
<td>This is a manual process that is performed through filtering.</td>
<td>Employee and contractor lists are automatically filtered by the company that you're logged on to.</td>
<td>It provides a filtered view of employees who are employed in the logged-on company. For an unfiltered view of all employees and contractors, the worker list is still available. In the current version of Dynamics AX, the system doesn't change company based on the employee that is selected in the list.</td>
</tr>
<tr>
<td>Update the course participants list.</td>
<td>Not available</td>
<td>Course participants can be removed from the participants list.</td>
<td>It provides an easy way to update course participants who registered by mistake.</td>
</tr>
<tr>
<td>Manage compensation events in a group.</td>
<td>Not available</td>
<td>This feature streamlines the processing of compensation changes for employees.</td>
<td>It provides a simple, streamlined process for updating employee records through the compensation workspace and related pages.</td>
</tr>
</tbody>
</table>

## Inventory management

No new features have been added.

## Localization

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Configure and generate electronic documents to meet the legal requirements in various countries/regions.</td>
<td>Electronic documents are hard-coded in X++ or as Extensible Stylesheet Language Transformations (XSLTs). Any format adjustments require development efforts. Access to data and formatting aren't isolated. An adjusted format deployment requires a new Microsoft Dynamics AX hotfix package that overrides the existing format. Custom modifications of each format must be manually ported to the source code of a new Microsoft Dynamics AX hotfix package.</td>
<td>Electronic Reporting (ER) is a new tool for configuring and generating electronic documents that target a business user instead of a developer. ER lets you set up data models that are domain-specific and independent of the Microsoft Dynamics AX database as data sources for document formats. A business user can configure the formats, based on these domain-specific data models (for example, for payments, Intrastat reports, or tax reports). The user configures the formats by using simple visual tools that are similar to Excel. ER currently supports the generation of electronic documents in text, XML, and Excel formats. These documents can be generated simultaneously and packed into zip files. Data models and formats support versioning. Format versions can have effective periods. Each data model or format version is stored in a separate configuration and distributed to partners and customers through LCS. Partners and customers can customize Microsoft data models and formats, or create their own. ER saves partner and customer configuration changes as deltas to Microsoft configurations, which simplifies upgrades to new versions of Microsoft configurations. By using LCS, partners can also share their data model and format configurations with other partners and customers, who can customize and share them. Delta customization and easy upgrade are supported through the whole customization chain.</td>
<td>ER simplifies the creation, maintenance, and upgrade of electronic document formats to meet legal requirements in various countries/regions. ER makes the process of creating or changing electronic document formats faster and easier. These changes can be made by business users instead of developers. ER makes it faster and easier for partners and customers to upgrade their format customizations to new versions of formats that are released by Microsoft or other partners. ER provides one common way (through LCS) for Microsoft and partners to distribute electronic document configurations to other partners and customers. ER also makes it easier for partners and customers to customize, upgrade, and distribute electronic document formats for their specific business requirements.</td>
</tr>
<tr>
<td>(MEX) Generate Mexican value-added tax (VAT) regulatory reports.</td>
<td>You must generate <strong>Sales and Purchases VAT</strong> reports by using the unrealized VAT functionality, so that users can identify transactions that belong to the realized and unrealized sections based on the status.</td>
<td><strong>Sales and Purchases VAT</strong> reports were modified and now consider the conditional tax feature only by using specific settlement periods for the definition of unrealized and realized sales tax codes.</td>
<td>Changes in the configuration of sales tax codes are required before users can generate these reports correctly. A conditional sales tax feature is required, and the user must configure separate settlement periods, unrealized and realized, to identify the transactions in the related section areas.</td>
</tr>
<tr>
<td>(JPN) Manage the Japanese fixed asset accelerated depreciation declaration document.</td>
<td>Not available</td>
<td>Important declaration information is centrally stored in a single document for better maintenance.</td>
<td>Document compliance and ease of management help reduce issues during audits and other reviews.</td>
</tr>
<tr>
<td>(JPN) Verify JBA characters on the bank account.</td>
<td>Not available</td>
<td>You can verify that kana name fields contain only the characters that are permitted by the JBA bank format.</td>
<td>It helps reduce interruptions to users during payment file generation because of invalid characters.</td>
</tr>
<tr>
<td>(JPN) Catch up the Japan fixed asset penny difference at the end of the fiscal year.</td>
<td>Not available</td>
<td>On the <strong>Fixed asset parameters</strong> page, you can choose to catch up at the end of the fiscal period or the fiscal year.</td>
<td>It provides more flexibility to match local practices.</td>
</tr>
<tr>
<td>(JPN) Generate the Japanese Corporate Tax Declaration Appended Tables 16 series at a summarized amount by fixed asset major type.</td>
<td>Not available</td>
<td>On the value models of a fixed asset, you can choose to summarize by major type. By default, this functionality is used for newly created fixed assets.</td>
<td>For large corporations that have thousands of fixed assets, the summarized reports greatly reduce the size of the report that is generated.</td>
</tr>
<tr>
<td>(JPN) Start to allocate Special depreciation reserve from the next fiscal year for Japan fixed assets.</td>
<td>Not available</td>
<td>On the value models of a fixed asset that has an appropriate extraordinary depreciation profile, you can choose to start allocation from the next fiscal period or the next fiscal year.</td>
<td>It provides more flexibility to match local practices.</td>
</tr>
<tr>
<td>(JPN) Generate a Japan consumption tax report that includes the revised tax rates.</td>
<td>The consumption tax report is available for a tax rate of 5 percent.</td>
<td>The consumption tax report contains a section for the revised tax rate (for example, 8 percent).</td>
<td>The layout was newly announced by the government.</td>
</tr>
<tr>
<td>(EU) Configure rounding settings for EU sales list.</td>
<td>Rounding settings for the EU sales list reporting for various countries/regions are hard-coded in X++ or in Extensible Stylesheet Language Transformations (XSLTs).</td>
<td>Rounding settings are added to Foreign trade parameters. You can configure rounding precision, rounding method, output precision, and the behavior for amounts smaller than the rounding precision.</td>
<td>This unifies and simplifies the configuration of the EU sales list reporting. Adjustment of rounding settings no longer requires development efforts.</td>
</tr>
<tr>
<td>(EU) Configure reverse charge applicability rules.</td>
<td>Reverse charge applicability rules are hard-coded for the domestic reverse charge scenario. The applicability threshold can be set up per item group. The functionality is available to Great Britain only.</td>
<td>You can configure reverse charge applicability rules per document type (purchase/sales order, vendor invoice, free text invoice, etc.) and a reverse charge group that combines items, items groups, and purchase/sales categories. The applicability rules are date effective. You can also mark individual sales tax codes in sales tax groups as applicable for reverse charge. The sales invoice report is adjusted to represent details of the applied reverse charge. The functionality is available to all European countries/regions.</td>
<td>This change unifies the configuration of the reverse charge applicability rules and supports the adoption of the domestic reverse charge regulations by European countries/regions.</td>
</tr>
<tr>
<td>(DE) Generate the German audit file - GDPdUGoBD</td>
<td>Users can set up definition of tables containing financial data to be exported in a format accepted by German auditors and authorities.</td>
<td>The feature has been implemented as an electronic reporting configuration. The functionality is available to Germany and Austria.</td>
<td>This change gives user much more possibilities in data formatting, transformations, and also provides all the benefits coming from electronic reporting configuration lifecycle management, like easy configuration exchange, versioning, etc.</td>
</tr>
<tr>
<td>(FR) Balance list with group total accounts report.</td>
<td>Balance list with group total accounts report is implemented as SSRS report (LedgerAccountSum_FR).</td>
<td>Balance list with group total accounts report is implemented as Management Reporter report available in LCS Asset library localized financial reports folder.</td>
<td>This allows users to get all the benefits and freedom in customizations from using financial reports in Management Reporter.</td>
</tr>
<tr>
<td>(EU) Payment advice, Attending note and Control reports for payments.</td>
<td>All those reports are implemented and SSRS reports.</td>
<td>These reports have been implemented as Open XML templates to be used in Microsoft Excel.</td>
<td>Electronic payment configurations contain payment file format setup and templates. This allows users to get all the benefits and freedom in report customizations from using Electronic reporting.</td>
</tr>
<tr>
<td>(EU) Configure rounding settings for Intrastat.</td>
<td>Rounding settings for the Intrastat reporting for various countries/regions are hard-coded in X++ or in Extensible Stylesheet Language Transformations (XSLTs).</td>
<td>Rounding settings are added to foreign trade parameters. You can configure rounding precision, rounding method, output precision, and the behavior for amounts smaller than the rounding precision.</td>
<td>This unifies and simplifies the configuration of the Intrastat reporting. Adjustment of rounding settings no longer requires development efforts.</td>
</tr>
<tr>
<td>(EU) Set up Intrastat commodity codes in category hierarchies.</td>
u<td>Intrastat commodity codes is a separate list. While there is category hierarchy of type Commodity code, these commodity codes could be defaulted in Retail HQent and sales categories.</td>
<td>Separate list of Intrastat commodity codes are merged with product hierarchy of type Commodity code.</td>
<td>This unifies the approach for assigning commodity codes to released products and categories in sales and purchase documents.</td>
</tr>
<tr>
<td>(EU) Report quantity in additional units for Intrastat by using unit conversion setting.</td>
<td>Intrastat commodity code has a text field to identify additional units, and the <strong>Product</strong> card has a field to identify the quantity of additional units in kilograms.</td>
<td>Additional units for Intrastat commodity code is chosen from the list of Units. The quantity of additional units is calculated through unit conversion settings.</td>
<td>This unifies the approach for recalculation from units of transaction to additional units.</td>
</tr>
<tr>
<td>(EU) Assign default transport method to mode of delivery.</td>
<td>Not available</td>
<td>A field for default transport method is added to the Mode of delivery.</td>
<td>This simplifies the preparation of Intrastat reporting.</td>
</tr>
<tr>
<td>(EU) Mark released product not to be reported in Intrastat.</td>
<td>Not available</td>
<td>An option to exclude the item from Intrastat reporting is added to released product.</td>
<td>This simplifies the preparation of Intrastat reporting.</td>
</tr>
</tbody>
</table>

## Manufacturing

| What can you do? | Dynamics AX 2012 |
|------------------|------------------|
| Perform a check of material availability for production orders on a separate page that is opened from the **Production floor management** workspace. | Not available |
| Start and report progress on production jobs by using the new **Job card device** page. | The **Job registration** form is primarily targeted at large terminal screens, and the UI is typically accessed via mouse clicks. |

## Master planning and forecasting

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Warn the user if a sales order or production order isn't ready for delivery by the scheduled date. | The warnings that are created by master planning are called *futures messages*. *Futures* is a contract between two parties to buy or sell an asset for a price that is agreed upon today (the *futures price*), although delivery and payment occur at a future point (the *delivery date*). | *Futures messages* and *futures dates* have been renamed *calculated delays* and *delayed dates*, respectively. | The terminology that is used in AX 2012 was inaccurate and led to incorrect translations. |
| Gain quick insight into the status of a master planning run, urgent planned orders, and planned orders that cause delays. | The information is available, but it's scattered across multiple forms. | The **Master planning** workspace offers at-a-glance information about when the last master planning run was completed, whether any errors occurred, what the urgent planned orders are, and which planned orders cause delays. | You benefit from the overview that the workspace provides. Relevant information is put together to guide master planning and help improve productivity. |
| Use Excel to update demand forecasts. | Not available | You can take advantage of seamless integration with Excel when you enter demand forecasts, make updates, and delete demand forecasts. | It helps increase efficiency and productivity. |
| Estimate future demand and create demand forecasts, based on historical transaction data. | In Microsoft Dynamics AX 2012 R3, the forecast models in Microsoft SQL Server Analysis Service are used to create demand forecast predictions. | Estimate future demand by using the power and extensibility of a Microsoft Azure Machine Learning cloud service. It's easy to use and extend the forecast models in Machine Learning to meet customer requirements. The service performs best-match model selection and offers key performance indicators (KPIs) that can be used to calculate forecast accuracy. | Generate more accurate forecasts by using the Machine Learning techniques. |
| Optimize the order date and quantity, based on a visual overview of related actions from the master planning run. | The overview of actions chart is available but shows all the related actions. When actions are applied, they immediately disappear from the view. | The actions chart provides a better overview. It includes options that let you show only applied actions and directly related actions. When actions are applied, they appear dimmed but are still shown. Therefore, the overview is retained. Additional information is added to the actions chart to display the data on one page. | You benefit from productivity improvement, because you focus only on the relevant actions. |

## Procurement and sourcing

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Use the **Purchase order preparation** workspace to gain quick insight into the status of purchase orders that are being prepared. | Not supported | The **Purchase order preparation** workspace provides an overview of orders from the time when they are created as a draft and traced, through workflow approval states, and onward toward confirmation. | Your purchasing department no longer has to seek information from multiple pages but now benefits from the overview that the workspace provides. |
| Use the **Purchase order receipt and follow-up** workspace to gain quick insight into purchase orders that are pending receipt, to help with follow-up. | Not supported | The **Purchase order receipt and follow-up** workspace provides an overview of confirmed purchase orders that have pending receipts or shipments. The workspace includes lists of post-due receipts and pending receipts to help with proactive review and follow-up by the supplier. The workspace also lists purchase orders that arrival registration has occurred for in the warehouse, to help guarantee that the receipt is posted. Purchase order returns that haven't yet been shipped are also available for review. | Your purchasing department benefits from the overview that the workspace provides. Relevant information is put together to guide follow-up and help improve productivity. |
| Send purchase orders for confirmation to a vendor portal hosted in the Dynamics AX client. Let the vendor confirm or reject. | Not supported | The vendor portal interface allows vendors to receive purchase orders to be confirmed or rejected. It also allows the vendor to have an overview of all the confirmed purchase orders for an account. The purchasing agent can send a purchase order requesting a confirmation from the vendor. The vendor needs to be a registered Microsoft Azure Active Directory (Azure AD) user in Dynamics AX, a contact person for the vendor, and have a dedicated security role. | Your purchasing department benefits from reduced paper work and manually tracking responses on purchase orders, as they flow directly into the system. Having one source of truth reduces misunderstandings between customer and vendor. |

## Projects

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Book workers as resources on projects. | Similar to resources, workers are booked directly on projects in addition to resources. | The Work center table where resources for manufacturing and production are stored can now be used to book workers as resources on a project. | When you book projects, you only have to book resources. |

## Retail sales, marketing, and customer service

### Retail HQ

Microsoft Azure-hosted Retail HQ offers centralized management of and complete visibility into all aspects of commerce operations through a web client.

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Perform merchandizing operations.</td>
<td>Users must access multiple forms to manage this data:
<ul>
<li>Category management</li>
<li>Product management</li>
<li>Channel product attributes</li>
<li>Assortments</li>
<li>Catalog management</li>
<li>Kits</li>
<li>Prices &amp; discounts</li>
</ul></td>
<td>The <strong>Category and product management</strong> workspace enables the following functionality:
<ul>
<li>Assortment management.</li>
<li>Assortment lifecycle tracking.</li>
<li>Released products management.</li>
</ul>
The <strong>Prices and discounts management workspace</strong> enables the following functionality:
<ul>
<li>Price and discount management for a given channel and category.</li>
<li>Category price rule management.</li>
<li>Price and discount priorities, which let you assign priorities to price groups and discounts, so that you can control the order that they are applied in.</li>
<li>Affiliation and catalog discount management.</li>
</ul>
The <strong>Catalog management</strong> workspace enables the following functionality:
<ul>
<li>Summary of active catalogs.</li>
<li>Catalog lifecycle tracking in a single location.</li>
</ul></td>
<td><ul>
<li>Workspaces improve the efficiency and productivity of workers by letting them centrally manage their tasks and actions that are related to the merchandizing role.</li>
<li>The price and discount priorities feature gives customers more control over how prices and discounts are used. The feature also enables new scenarios where higher store prices win over standard prices.</li>
</ul></td>
</tr>
<tr>
<td>Manage retail channel deployments and operations.</td>
<td>The user must access multiple forms to perform the following tasks:
<ul>
<li>Create and configure new channels and related entities.</li>
<li>Manage daily store activities.</li>
<li>Process retail transactions in Microsoft Dynamics AX, generate retail statements, and update Microsoft Dynamics AX inventory and financials.</li>
</ul>
</td>
<td><strong>Channel deployment</strong> workspace lets you perform the following tasks:
<ul>
<li>Create new channels and related entities.</li>
<li>Track the progress of retail store configuration.</li>
<li>Take the required steps to complete a task, or provide information to complete the task.</li>
<li>Track the status of devices, and directly validate and download the Retail Modern POS (MPOS) program installation in stores.</li>
<li>Access all related pages.</li>
</ul>
<strong>Retail store management</strong> workspace lets you perform the following tasks:
<ul>
<li>Manage workers and the workers' point of sale (POS) permissions.</li>
<li>Track shift status for a given store or group of stores.</li>
<li>Directly validate and download the MPOS program installation in stores.</li>
<li>Print reports and access related pages.</li>
</ul>
<strong>Retail store financials</strong> workspace lets you perform the following tasks:
<ul>
<li>Create, calculate, and post statements for a given channel.</li>
<li>Schedule batch jobs to update inventory, and calculate and post statements.</li>
<li>Track open statements.</li>
<li>Track shift status for a given store or group of stores.</li>
<li>Print reports and quickly access all related pages.</li>
</ul></td>
<td>Workspaces improve the efficiency and productivity of workers by letting them centrally manage most of their tasks and actions that are related to channel deployment, store management, and financials.</td>
</tr>
<tr>
<td>Manage retail IT operations.</td>
<td>The user must access multiple forms.</td>
<td>The <strong>Retail IT</strong> workspace enables Commerce Data Exchange inquiries in a single place for a given channel, so that you can perform the following tasks:
<ul>
<li>Download sessions.</li>
<li>Upload sessions.</li>
<li>Track failed sessions, and re-initiate or run them again.</li>
<li>View or run upcoming jobs.</li>
</ul></td>
<td>Workspaces improve the efficiency and productivity of workers by letting them centrally manage their tasks and actions that are related to retail IT operations.</td>
</tr>
<tr>
<td>Import/export data by using data entities.</td>
<td>AX 2012 supports out-of-box Microsoft Dynamics Retail Management System (RMS) migration through the Data Import/Export framework.</td>
<td>Retail data entities have been expanded to support all master and reference data that is related to retail. There is also enhanced support for data entities across the entire Dynamics AX solution.</td>
<td>Data entities lets customers do metadata-driven import and export of data. OData entities also let customers integrate Dynamics AX with third-party programs.</td>
</tr>
<tr>
<td>Perform intelligent analytics by using BI reports from Dynamics Microsoft AX and the POS client.</td>
<td>More than 25 back-office reports and five channel-side reports are available.</td>
<td>More than 30 back-office reports and 10 channel-side reports are available.</td>
<td>These reports let customers have more BI to predict trends, uncover insights, and operate at continual peak performance.</td>
</tr>
<tr>
<td>Analyze retail channel sales data by using the "Monitor Retail Channel performance" Power BI content.</td>
<td>Not available</td>
<td>On PowerBI.com, select <strong>Get Data</strong>, and then select the <strong>Dynamics AX – Retail Channel performance</strong> content pack. Enter the URL for your Dynamics AX endpoint to see your data reflected in the dashboard.</td>
<td>In three to four clicks, organizations can deploy a Power BI dashboard that contains important financial data. Content can be personalized by the organization. Additionally, users can embed Power BI dashboard tiles into their personalized workspaces in Dynamics AX, so that they can then see analytical information at a glance.</td>
</tr>
<tr>
<td>Configure consumer permissions.</td>
<td>Not available</td>
<td>Customers can choose whether POS operations can be available to consumers. Retail Server uses permissions for application programming interface (API) calls.</td>
<td>It provides the ability to configure consumer-level permissions.</td>
</tr>
<tr>
<td>Manage and validate entity configurations.</td>
<td>Not available</td>
<td>The configuration manager and validator feature enables the following functionality:
<ul>
<li>Bulk configuration data upload</li>
<li>Business entity validation</li>
</ul></td>
<td>It provides the ability to bootstrap the configuration, and to validate the status and completeness of the configuration for the various configuration elements.</td>
</tr>
</tbody>
</table>

### Retail Hardware Station

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Enable POS devices to connect to peripherals such as printers, cash drawers, or payment devices. | The MPOS hardware profile is used to specify the devices that are used. | An added hardware profile supports more diverse hardware from one station to the next. A new Hardware Station profile supports a unique terminal ID for each Hardware Station when electronic funds transfer (EFT) transactions are processed. EFT support has been merged into hardware station to reduce the involvement of MPOS in EFT payment processing. | It provides greater flexibility for implementations. It also provides enhanced security and reduced exposure to credit card data. |

### Retail Server and data management

Retail Server and data management lets consumers and enterprises create an omni-channel shopping experience across online, in-store, and call center channels.

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Connect to a commerce runtime (CRT) database that stores business data for the channel by using CRT services.</td>
<td>OData V3 is supported.</td>
<td>OData V4 is supported.</td>
<td>It helps the customer stay current with OData standards. It also creates a robust omni-channel experience by integrating sales across in-store, mobile, and online channels.</td>
</tr>
<tr>
<td>Support Retail services as a hostable set of services.</td>
<td>The E-commerce API isn't supported through Retail Server.</td>
<td>The E-commerce API is now available through Retail Server to support online scenarios.</td>
<td>It provides hosted and scalable e-commerce services that can be used with third-party online stores.</td>
</tr>
<tr>
<td>Move data between the Microsoft Dynamics AX back office and channels by using Commerce Data Exchange.</td>
<td>Commerce Data Exchange is a system that transfers data between Microsoft Dynamics AX and retail channels, such as online stores or brick-and-mortar stores. For more information, see <a href="/dynamicsax-2012/appuser-itpro/commerce-data-exchange">Commerce Data Exchange [AX 2012]</a>.</td>
<td>There is functional parity with Microsoft Dynamics AX 2012 CU8. However, note the following details:
<ul>
<li>Commerce Data Exchange has been re-engineered for the cloud.</li>
<li>Async service uses direct database access to the channel database.</li>
<li>Commerce Data Exchange: Real-time Service is hosted as a Microsoft Dynamics AX custom service.</li>
<li>MPOS manages synchronization between offline databases and Retail Server.</li>
</ul></td>
<td>Commerce Data Exchange has been re-engineered for the cloud platform. It continues to manage the transfer of data between Microsoft Dynamics AX and retail channels, such as online stores or brick-and-mortar stores.</td>
</tr>
<tr>
<td>Support plug and play, semi-integrated cross-channel payment processing by using the payment SDK.</td>
<td>AX 2012 provides the following functionality:
<ul>
<li>Support for all channels: POS, e-commerce, and call center.</li>
<li>Support for card present and card not present.</li>
<li>Page for accepting payment.</li>
<li>Peripheral support for LS5300 and MX925 as sample code in the Retail SDK.</li>
</ul></td>
<td>The current version of Dynamics AX supports all existing Microsoft Dynamics AX for Retail 2012 credit/debit card features and four new enhancements.</td>
<td>It lets the customer process credit/debit card transactions for payments.</td>
</tr>
<tr>
<td>Activate devices by using a Microsoft account (Microsoft Azure Active Directory (Azure AD)).</td>
<td>Not available</td>
<td>The following functionality is provided:
<ul>
<li>Enhanced security by Azure AD-based activation for the cloud.</li>
<li>Enhanced security for token management.</li>
<li>Improved reliability, troubleshooting, and error messaging during activation</li>
<li>Simplified IT administration tasks that are related to activation.</li>
<li>Revisited threat model and fixed security issues.</li>
</ul></td>
<td>It provides the following benefits:
<ul>
<li>Security is enhanced through Azure AD and device token/ID (RS calls that use a token, user-specific app storage).</li>
<li>It stops unauthorized remote use of MPOS (brick device).</li>
<li>It tracks MPOS devices for PCI-compliance purposes.</li>
<li>It maps physical devices with a business entity (register) by using a device token.</li>
<li>It initializes settings for smooth MPOS functionality (number sequences and hardware profiles) as the first touch point of MPOS.</li>
<li>It reports device information from headquarters.</li>
</ul></td>
</tr>
<tr>
<td>Manage rich media content for authoring and serving through Media Gallery.</td>
<td>Not available</td>
<td><ul>
<li>Support image upload, and also view, manage, and delete, from Media Gallery for both externally-hosted and Retail-hosted images.</li>
<li>Support image upload and view from entity pages (<strong>Products</strong>, <strong>Catalogs</strong>, and so on) by linking an image from the gallery and uploading an image from the desktop.</li>
<li>Optimize the images for thumbnail, custom size, and original.</li>
<li>Bulk link entities by using a template and background jobs for bulk association.</li>
<li>Microsoft Excel integration overwrites the attribute group limitation of naming conventions and predefined paths.</li>
<li>Support offline images and secure images for personally identifiable information (PII) content, such as Retail-hosted employee and customer images.</li>
</ul></td>
<td><ul>
<li>It addresses pain points around externally-hosted images, so that you can avoid going back and forth, and instead manage in a single place.</li>
<li>It provides powerful content management through Media Gallery for uploaded and externally-hosted images, and also provides filtering to help you find images.</li>
<li>It lets you easily create bulk associations between externally-hosted images and entities such as products and catalogs.</li>
<li>It supports Retail-hosted storage for images, and Excel integration for easy updates.</li>
</ul></td>
</tr>
</tbody>
</table>

### Rich clientele experience

Retail offers immersive mobile experiences anywhere, any time, and on any device. This functionality enables enhanced shopping and store experiences across all channels.

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Search, browse, look up, or scan products, add products to a cart, accept payment, and check out by using an intuitive, touch-friendly, rich and immersive user experience on MPOS.</td>
<td>AX 2012 enables the following features:
<ul>
<li>Perform sales, returns, and voids.</li>
<li>Create, modify, and pick up customer orders.</li>
<li>Perform shift and drawer operations.</li>
<li>Pick and receive orders, and perform stock counts.</li>
<li>View in-store reports.</li>
</ul></td>
<td>Functional parity with AX 2012 MPOS is provided. This includes the following functionality:
<ul>
<li>Customer lookup across stores/channels.</li>
<li>The ability to create customer orders without accessing Real-time Service.</li>
<li>Improved device activation workflows, status, and error messages.</li>
<li>Extensibility improvements, such as pre-post triggers and activity support to improve customization.</li>
</ul></td>
<td>Sales staff can process sales transactions and customer orders, and perform daily operations and inventory management, by using mobile devices anywhere in the store.</td>
</tr>
<tr>
<td>Start POS as a web app via Cloud POS.</td>
<td>Not available</td>
<td>Functional parity with MPOS is provided. This includes the following functionality:
<ul>
<li>Device activation by using AAD</li>
<li>Responsive layout design</li>
<li>Support for Edge, Internet Explorer and Chrome browsers.</li>
</ul></td>
<td>It provides a web app POS that has functionality that is compatible with MPOS, and that can be used across platforms and browsers at no deployment cost.</td>
</tr>
<tr>
<td>Integrate with content management systems to create an omni-channel e-Commerce website.</td>
<td>Microsoft SharePoint and third-party storefronts are supported.</td>
<td>An e-Commerce platform is provided that supports third-party storefronts. The platform includes the following features:
<ul>
<li>A rich consumer API.</li>
<li>Authentication integration to any third-party open ID providers.</li>
<li>Payment integration.</li>
</ul></td>
<td>Customers now have the flexibility to use the content management system of their choice.</td>
</tr>
<tr>
<td>Target customers via mail order catalogs, and streamline operations through fast order entry, assisted sales, and fulfillment by using Call Center.</td>
<td><ul>
<li>Call Center channel</li>
<li>Mail order catalogs</li>
<li>Fast order entry and assisted sale</li>
<li>Enhanced order fulfillment</li>
<li>Customer service</li>
<li>Integrated pricing and promotions/discounts</li>
</ul></td>
<td>Feature parity with the AX 2012 Call Center solution is available, with the exception of price overrides.</td>
<td>Call centers are a type of retail channel that lets workers take orders from customers over the phone and create sales orders.</td>
</tr>
</tbody>
</table>

### Commerce essentials

A retail and commerce-focused configuration option helps streamline retail-specific deployments.

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Use the Commerce essentials dashboard. | An area page with links to menu items is available. | The Commerce essentials dashboard provides links to frequent tasks, including links to workspaces, the Power BI web control, favorites, recent pages, and current work items. | The enhanced dashboard empowers workers by making them more efficient and providing a flexible starting point for any retail-specific task. |
| Use data entities to access account changes. | Account changes are exported to a folder on the file system. | Account changes are accessible through data entities. | This feature provides greater flexibility when moving data between disparate systems. This feature can be enhanced through OData applications, as well. |
| Use Cloud POS and MPOS. | Only Enterprise POS (EPOS) is supported out-of-the-box. | MPOS and Cloud POS replace the EPOS client. The e-Commerce channel has also been added to Commerce essentials by default. | This feature enables greater out-of-box channel support with rapidly deployable point-of-sale clients. |
| Implement and maintain two-tier architecture. | The Data import/export framework provides the ability to move data between AX 2012 and third-party systems. | Data entities created to enhance support for two-tier architecture. | Data entities and OData applications provide an abstraction layer to make two-tier scenarios easier to implement and maintain. |
| Simplify forms. | Custom code is required to simplify the UI. | Form and menu extensions provide standardized UI simplification. | This feature provides a faster and easier way to fine-tune forms based on retailer's needs. |

### POS Task recorder

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Create and share task guides and documents for Modern POS.</td>
<td>Not available</td>
<td>The MPOS Task recorder supports the following features:
<ul>
<li>Create task recordings for various tasks that are performed in MPOS.</li>
<li>Generate a document that includes steps and screenshots, and associate it with a node in the business process model.</li>
</ul></td>
<td>Partners and independent software vendors (ISVs) can customize MPOS and provide supporting documents to train their users.</td>
</tr>
</tbody>
</table>

### Extensibility

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Support an extensible and easily deployable Retail components across HQ, Call Center, e-Commerce, and the POS.</td>
<td>The components can be extended by using the Retail SDK. No packaging and deployment capabilities are supported.</td>
<td>Extensibility hooks are improved across the various components to better support code isolation and serviceability. Here are some of the features that are included:
<ul>
<li>Workflow, activity, and operation.</li>
<li>Pre-triggers and post-triggers that let you easily extend a workflow.</li>
<li>Application and operation triggers.</li>
</ul>
Additionally, a framework is available that lets you build and package these components by using MSBuild, and then seamlessly deploy your customization through Microsoft Dynamics Lifecycle Services (LCS).</td>
<td>Retailers have very specific requirements based on verticals and geographies of operation. By providing an easily extensible platform, we enable usage across verticals and markets. Because Retail also has a very distributed architecture, the ability to seamlessly deploy greatly improves productivity.</td>
</tr>
</tbody>
</table>

### Lifecycle management

Lifecycle Services (LCS) provides a set of services that customers and partners can use to manage the lifecycle of the system from sign-up to daily operations.

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Manage the program via cloud deployment services.</td>
<td>Not available</td>
<td>The following topologies can be deployed to the cloud:
<ul>
<li>Retail one-box trial topology.</li>
<li>Retail multi-box high-availability topology.</li>
<li>Developer topology with the Retail SDK.</li>
</ul>
There is an improved "low-touch" client component installation via self-service installation:
<ul>
<li>Retail Modern POS.</li>
<li>Retail Hardware Station.</li>
<li>Support for the upload and distribution of customized packages through self-service installation.</li>
</ul></td>
<td>The cloud deployment services provide the following benefits:
<ul>
<li>Significantly reduced deployment effort and complexity for Retail HQ components.</li>
<li>Native deployment to the Microsoft Azure public cloud.</li>
<li>Improved self-service installation of in-store components to make configuration easier and more intuitive</li>
</ul></td>
</tr>
<tr>
<td>Monitor the health of the system, and diagnose errors and issues.</td>
<td>This functionality requires <a href="https://www.microsoft.com/en-us/download/details.aspx?id=58205">System Center 2012 Management Pack for Microsoft Dynamics AX 2012 R3 CU8 Retail</a>.</td>
<td>Monitoring and diagnostics for Retail components is now available through the <strong>Operational Insights</strong> dashboard in LCS.</td>
<td>The <strong>Operational Insights</strong> dashboard is a cloud-based monitoring portal that replaces the need to install the System Center Operations Manager (SCOM) infrastructure.</td>
</tr>
<tr>
<td>Create, configure, download, and install Retail Hardware Station and devices by using self-service.</td>
<td>By using the installation packager and Enterprise Portal, a user can perform an automated installation and configuration of all components that are required on a particular computer, based on a defined topology.</td>
<td>Because there are only two installation packages, one for the MPOS client and the other for the Retail Hardware Station component, self-service has reduced the amount of work that is required at every level to install these client components.</td>
<td>Self-service aims to minimize requirements and make it easier for a user to perform an installation.</td>
</tr>
</tbody>
</table>

## Sales

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Dynamics AX 2012</th>
<th>Dynamics AX 7.0</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Get a quick overview of delivery alternatives when you promise orders to customers.</td>
<td>When there are product availability constraints, and the customer's requested delivery date for one or more products on the order can't be met, the order promising task becomes a challenge. To find alternatives that can offset availability and shipping time issues so that the customer's requested date can be met, or to offer customers a delivery solution that they can accept and trust, the order processor might have to open several forms, each of which offers only a subset of the required information. More specifically, one form shows on-hand quantity across sites, another form shows on-hand quantity in the intercompany setting, a third form lets users calculate the earliest available date for one site/variant at a time, and a fourth form shows supply orders. Therefore, users don't feel confident that they have considered all the relevant options instead of just choosing an immediate but suboptimal solution. Users also don't feel effective, because numerous interruptions occur during the order promising flow as they open and close multiple pages, and combine the insights and options.</td>
<td>Based on the existing algorithms for delivery date calculation, the <strong>Delivery alternatives </strong>page offers a new user experience for order promising:
<ul>
<li>It consolidates relevant information from multiple forms into one space.</li>
<li>It offers "ready-made" alternative delivery packages, such as a combination site/warehousing/variant/transport mode, based on the fastest delivery (earliest available date) criterion that the user can choose from.</li>
<li>It lets the user select options from the simulation interface and transfer them to the sales order line.</li>
</ul></td>
<td>Companies that aspire to provide high customer service while committing to an inventory optimization strategy must be able to promise orders reliably and competitively. After all, their customers' own business requires that products be available on time. The <strong>Delivery alternatives</strong> task page makes the order promising task quicker, easier, and more systematic by identifying and recommending the best alternative order delivery dates in one interactive place.</td>
</tr>
</tbody>
</table>

## Service management

No new features have been added.

## Transportation management

No new features have been added.

## Travel and expense

No new features have been added.

## Warehouse management

| What can you do? | Dynamics AX 2012 | Dynamics AX 7.0 | Why is this important? |
|------------------|------------------|-----------------|------------------------|
| Download, install, and configure the Warehouse Mobile Devices portal. | You can download, install, and configure the portal during the Microsoft Dynamics AX installation process, through a standard setup. It's designed for self-driven on-premises deployment and configuration. | You can download a stand-alone installer through a menu item in Warehouse management. It's designed for self-driven on-premises deployment and configuration. | When you're setting up the mobile device functionality, you must install and configure the Warehouse Mobile Devices Portal locally and get a connection to Dynamics AX in the cloud. |

## Additional resources

[What's new or changed in finance and operations home page](whats-new-changed.md)

[New task guides (February 2016)](new-task-guides-available-february-2016.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

