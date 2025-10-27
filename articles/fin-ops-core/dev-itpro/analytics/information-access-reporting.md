---
title: Information access and reporting
description: Learn about various reporting options, including an overview of the importance of information access and understanding report requirements.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 10/22/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: dbc1ac2d-7079-411c-b768-5f820859e29e
---

# Information access and reporting

[!include [banner](../includes/banner.md)]

This article explains the various reporting options available as part of the platform.

## Why information access is important

Information access is an essential part of an ERP solution. It represents a significant portion of the user engagement with the system. Consider the numerous methods of capturing information related to daily activities and the level of investments required to manage the data. Employees depend on logical interpretations of massive amounts of data to stay on top of their daily tasks. Out of the box, the platform provides a collection of reporting solutions to address the various information access needs of an ERP solution. In an increasingly competitive environment, mergers and acquisitions seem to occur as often as the change in seasons. More than ever before, businesses today are finding ways to expand their global reach to attract more customers. To be successful, they must adapt legacy solutions used to communicate with customers and prepare for the enforcement of regional regulatory requirements associated with new markets. Beyond the primitive functions provided by Microsoft Azure – compute, networking, storage, and authentication – the platform provides tools to manage resources for organizations that span in size from small businesses to global enterprise conglomerates. These tools are designed with flexibility in mind, to accommodate a dynamic world of business.

## What is a "report" in the application?

A *report* is a structured presentation of data. Under ideal circumstances, reports present data in such a way that it allows the user to make informed decisions. The application supports a broad spectrum of information access scenarios: cross company all-up financial reporting; analytical dashboards and tiles; electronically transferable funds; customer sales invoices; checks and tax documents; and many more. Examples of integrated report scenarios that involve the consumption of business data include:

- **Native controls** including list pages, grid controls, and chart visualizations.
- **Dashboards and workspaces** containing predefined and personalized views.
- **Financial reporting** providing all-up views across legal entities.
- **Structured documents** distributed internally to employees or externally to customers and vendors.

Although each of these scenarios at its core involves the presentation of structured business data, the process of accessing these reports and how the results are then consumed varies greatly. Flexibility in the user tooling is essential for scenarios that involve data exploration. By contrast, layout precision is required for compliance with most regulatory documents. Given the diversity of information access scenarios, it's understandable that not all reports are created equal. This article is intended to help familiarize you with the various reporting options available as part of the platform.

## Common myths of reporting

To become a proficient *report* *maker*, it's often useful to let go of past inhibitions. The following section seeks to rebuke three common myths about reporting.

- **Myth \#1: Operational reports require "real-time" data** To the contrary, relatively few reporting scenarios require *real-time* results. And, in the grand scheme of things, taking a critical stance on a request for *real-time* views is recommended given the high development costs and potential heavy burden these solutions may incur on production environments.
- **Myth \#2: The best tool is the one the developer is most comfortable using** Consider a customer request for a report that allows them to monitor company's assets. In the past, a developer would build a static report displaying a list of inventory items with complex calculations relying entirely on the user to provide filters to sufficiently reduce the result set. This solution might function perfectly in developer environments with a reduced data set. However, this approach can unnecessarily consume significant amounts of compute resources when utilized in production.
- **Myth \#3: Developers are good at creating visually compelling designs** In reality, developers are often the worst offenders when it comes to producing elegant design layouts that appeal to the customer's aesthetic preferences. When it comes to analytical reports, you're better off empowering users to both explore the data directly and share personalized views.

## Understanding report requirements

The best reporting solutions are designed with the expertise, daily functions, and information access needs of the target user in mind. The platform offers several tools designed to meet the functional requirements that are common across various reporting experiences. Selecting the right tool that most effectively addresses the *need* requires a clear understanding of the customer experience. You can drastically increase your chances of delivering a complete and robust solution that fully satisfies customer requirements by simply asking the right questions. Here are some leading questions to ask when evaluating customer requirements for reporting solutions:

- **Get to know the user**

  - What is the proficiency of the target persona? Are they familiar with analytical tools like Microsoft Excel?
  - Does the user require a guided parameter experience to refine the dataset?
  - How frequently is the report accessed?

- **Familiarize yourself with the data**

  - Are they looking for transactional, analytical, and predictive information?
  - Does the shape of the data change and if so, how often?
  - Does the report include data from external sources?

- **Determine how the results are used**

  - Are you going to explore the data to gain insights?
  - How are the results shared with others?
  - Is there a fixed document structure for the target output?

It's understandable that customers *want* a solution that aligns with the existing processes they're comfortable using. However, you can learn a lot through these leading questions used to discover what the customer actually *needs* to be successful in their task. Delight your customers by providing them with solutions that empower them to be more productive.

## Reporting experiences

Applications support information access scenarios that break down into five distinct reporting experiences. Specialized tools meet the complex and diverse reporting needs of various functions throughout the organization.

- **Operational views** – Designed to address the specific needs of a given business persona.
- **Business documents** – Static documents used to capture and exchange processed business data.
- **Analytical tools and visualizations** – Personalized presentations of logical calculations that allow the user to explore their data.
- **Electronic reporting** – Tool used to configure formats for electronic documents.
- **Financial reporting** – Designed to provide in-depth accounting management tools based on standard views of financial activities across legal entities.

### Scorecard

Use the following table as a guide when choosing the right tool for your reporting solution.

|MAKER|Operational views|Business documents|Analytical tools & visualizations|Electronic reporting|Financial reporting|
|-----|-----------|------------------|---------------------------------|--------------------|-------------------|
|Persona|Developer|Developer|Power user|Power user|Power user|
|Authoring tool|Visual Studio|Visual Studio|PowerBl.com<br>PowerBl app|Excel|Management Reporter Designer|
|Time to market|Weeks|Weeks|Hours|Hours|Hours|
|Data sources|Entity DB<br>OLTP|OLTP|Entity DB<br>Azure Catalog|OLTP|OLTP|
|Effort|Days|Days|Minutes|Hours|Hours|

|VIEWER|Operational views|Business views|Analytical tools & visualizations|Electronic reporting|Financial reporting|
|-----|-----------|------------------|---------------------------------|--------------------|-------------------|
|Target|Organization|Back Office|Power user|Power user|Finance officers|
|Data accuracy|Near real-time|Real-time|Near real-time|Real-time|Cached views|
|Personalization|Medium-Modeled|None|High - Free form designer|Low - Expressions|Medium - Modeled|
|Sharing|None|PDF export<br>0365 export<br>Email|Dashboards<br>Reports<br>Tiles|Excel export|Excel export|
|Printing|Screen captures|Local printer<br>Network devices|Screen captures|Excel|Local printer|
|Automation|Autorefresh|Batch integration|Scheduled refresh|Batch jobs|None|
|Scenarios|Monitoring|Transactions|Exploratory|Transactions|Accounting|

> [!NOTE]
> "Near real-time" denotes processed data that's slightly slower than real-time.

## Operational views

Operational views play an essential role in the daily work of most employees. As important as a brush is to a painter, operational views empower people to be productive. These views contain logical presentations of data to help users discover patterns, highlight anomalies, and act on the most important tasks. Targeted experiences satisfy the unique information access requirements for a given persona. These views provide actionable controls that help maximize efficiency for common user actions. For more information about constructing custom operational workspaces, see [Build operational workspaces](../user-interface/build-workspaces.md). Example applications of operational views include controller operations, production floor management, and customer collections monitoring.

:::image type="content" source="./media/operational-views.png" alt-text="Screenshot of operational views interface showing dashboard and controls." lightbox="./media/operational-views.png":::

**What are the characteristics and capabilities?**

- A fully integrated experience with responsive visualizations that understand user context and selections.
- Views that users can personalize to meet their unique and changing needs.
- Actionable controls that let users efficiently transact and monitor activities.
- A combination of analytical data that answers general questions and transactional views that provide access to record details.

**What distinguishes "operational views" from other types of visualizations?**

- General purpose tools designed for use at all levels of the organization.
- Predefined views based on common information access requirements associated with specific roles within the organization.
- Highly responsive to user interactions and changes made to the transactional database.

**What should you consider when selecting this tool?**

- The platform allows users to embed Power BI tiles and links to reports directly in workspaces.
- Users can introduce personalized workspaces to create their own custom operational views.
- Form data sources now support aggregate queries for analytical views using native controls.

## Analytical tools and visualizations

Embedded visuals based on analytical data let users navigate between aggregate views and transactional details. Power BI service integration delivers world-class analytical tools with built-in support for accessing data. These tools empower "citizen developers" to author the reports they need and share the reports with others within the organization. Use the Power BI content packs available in Lifecycle Services to get started. For more information, see [Features and services available through Power BI integration](power-bi-integration.md). Example applications of analytical tools and visualizations include customer sales per quarter, total revenue by region, and inventory turn-over.

:::image type="content" source="./media/supplier-quality-analysis-report.png" alt-text="Screenshot of supplier quality analysis report with charts and data visualizations.":::

**What are the characteristics and capabilities?**

- Near real-time results that provide macro level insights based on micro level activities.
- Common applications include charts, KPIs, and more complex visuals.
- Offer a deep exploratory experience with interactive controls that provide drill-through navigations.

**What distinguishes "analytical tools and visualizations" from other types of reports?**

- Highly graphical nature, these presentations help you find the hidden meaning behind the data.
- Free form web designer that supports rich visualizations with built-in user interactions.
- Utilized by power users to explore data and gain insight through analysis.
- Personal nature by allowing the user to choose which information to include.
- Built-in sharing capabilities and user controlled access management.

**What should you consider when selecting this tool?**

- Developers are responsible for publishing data entities that Power BI can consume.
- Power users can produce mash-up views based on application data combined with external data sources.
- Visuals are highly responsive to user interactions and provide near real-time results when using Direct Query access to the data source.

## Business documents

Use these reporting solutions to capture and communicate the details of business transactions. As such, you need a reporting solution that can produce physical manifestations of business data by using existing devices like network printers. For more information about the enhancements to the Document reporting service, see [Document Reporting Services](document-reporting-services.md). Example applications of business documents include sales invoices, customer statements, and checks.

:::image type="content" source="./media/image-of-business-documents.png" alt-text="Screenshot of business documents including invoices and statements." lightbox="./media/image-of-business-documents.png":::

**What are the characteristics and capabilities?**

- Paginated documents that you print on paper or distribute through email.
- Heavy dependence on parameters to filter and produce the desired result set.
- Business documents capture a snapshot of customer and vendor activity that you can archive for future reference.
- Complex solutions that you develop in Visual Studio and deploy as part of the application.

**What distinguishes "business documents" from other types of visualizations?**

- Asynchronous data access and rendering solution designed to handle relatively large data sets.
- Dedicated reporting services that offer distributed resource utilization.
- Ideal solution for automated processes that involve bulk generation of business documents.
- Built-in support for document archive and data extraction via file export to PDF in addition to Word, Excel, and CSV.

**What should you consider when selecting this tool?**

- Use application suite reports as a starting point for custom solutions.
- Solutions that heavily depend on metadata changes and don't offer personalization.
- You must manage modifications to out-of-box solutions as a metadata change.

## Electronic reporting

Electronic reporting (ER) is the tool to use to configure electronic document formats in accordance with the legal requirements of various countries and regions. For more information about the Electronic reporting tool, see [Electronic reporting (ER) overview](general-electronic-reporting.md). Example applications of electronic reporting include financial auditing, tax reporting, and electronic invoicing.

:::image type="content" source="./media/electronic-reporting-example.png" alt-text="Screenshot of electronic reporting configuration interface.":::

**What are the characteristics and capabilities?**

- Perfect tool for producing TEXT, XML, and OPENXML worksheet formats.
- Tooling is designed for business users familiar with Excel-based formulas.
- Highly adaptable to adhere to changes in regulatory requirements.
- Component versioning is available to manage draft definitions.

**What distinguishes "electronic reports" from other types of visualizations?**

- Designed for electronic submission to banks, governments, and other external entities.
- Use formulas to define data transformations into groups containing summary data and logical calculations.

## Financial reporting

Standard financial reports use the default main account categories. Use the report designer to create or modify traditional financial statements, such as Income statement and Balance sheet, and share the results with other members of your organization. For detailed information about the Financial reporting tooling, see [General ledger and Financial reporting overview](../../../finance/general-ledger/general-ledger.md). Example applications of financial reporting include balance sheets, cash flow, and summary trial balance year over year.

:::image type="content" source="./media/financial-reporting-example.png" alt-text="Screenshot of financial reporting example showing balance sheet data.":::

**What are the characteristics and capabilities?**

- Built-in flexible financial reporting solution designed to handle complex organizational structures.
- Fully integrated with General ledger.
- Create custom financial reports using the default solutions as a starting point.
- Interactive reports with drill-down capabilities to navigate down to transaction details.

**What distinguishes "financial reports" from other types of visualizations?**

- User controls tailored for the specialized needs of financial reporting.
- Create roll-up reports containing data across companies or business units.
- Utilizes a financial data mart for optimized performance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
