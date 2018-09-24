---
# required metadata

title: Financial reporting (Russia)
description: This topic provides information about financial reporting for Russia.
author: AnastasiaYashenina
ms.date: 09/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Financial reports (Russia)

[!include [banner](../includes/banner.md)]



The Financial reports setup allows you to configure list and content of “boxed” reports like
Balance sheet. For each report box or cell, the data collection for ledger
transactions, budget transactions, and calculated profit tax registers can be
configured. 

You should also configure report output in GER (electronic reporting) in a way where ER
configuration takes the data calculated according to user setup of the
financial report and generates the file output according to format
configuration (for example Excel and/or XML).


You should also configure Electronic message processing where one of the steps allows authorized user to
run the ER configuration of the financial report, generate report and store generated
report data.

## Financial reports setup

You should complete the following steps to set up the report:

   •	Setup list of report names
   
   •	Setup cells of the report
   
   •	Setup calculation criteria for report cells


### Setup list of report names
1.	Go to **General ledger > Financial reports setup > Financial reports**.
The **Overview** tab displays a list of all the reports that are set up in the system.
2.	Create new report. Enter a brief, and full names of the report in the **Report code** and **Description** fields.

3. Go to the **General** tab which displays the general parameters for report generation. 

4. In the **Currency** fielf, define whether the data in the report will be presented in the company's default currency (“Base currency”), or  reporting currency (“Reporting currency”). This setup can also be defined for each cell separately.
   
5. In the **Period** field, define the default transaction calculation period. Data of the report will be calculated for the chosen period based on the specified date at the report run.
   
6. In the **Line type** field, define the default data source for the report from the list. The following values are available:

| **Line type**| **Description** |
|------------|--------------------|
| “Transactions” | Data from posted transactions for ledger accounts are placed in the report. If this value is selected, define also setting of reversing entry usage for calculation in the field **Transaction usage**: "All",  "Only reversing entry", "Without reversing entry".|
|  “Budget” | Data from budget entries for ledger accounts are placed in the report. If this value is selected, also choose the default budget model in the field **Budget model**. |
|  “Register” | Data from the calculated profit tax registers are placed in the report. |
|  “Constant” | Values of the defined constants for cells are placed in the report. |
|  “Contractor” | Data from the active/passive balances of the contractors are placed in the report. |
|  “Dimension set balance” | Balances for the chosen dimension set are placed in the report. If this value is selected, also choose the default financial dimension set in the field **Dimension set**. |


7. In the **Factor** field, enter the value that the report data will be divided by. 
      
      For example, if the report needs to be present in thousands of rubles, enter a value of 1,000. If the data must be displayed in the report in full rubles, the factor's value should be 1.

8. Go to the **Transaction type** tab which displays the list of transaction types to be considered in calculation. 


9. Create a new line. In the **Transaction type** field choose the module name to determine which module's transactions will be used in generating the report. Create a line for each required module.
      
      For example, when the transaction type “Bank” is selected, the report will include transactions that are generated from the **Bank management** module. If no lines are created, the filter will not be used. 

10.	Go to the **Posting layer** tab which displays the list of posting layers to be considered in calculation. 
If no lines are created, the filter will not be used.

11.	Go to the **Financial dimensions** tab which displays the dimension filters, if the report must be generated for a particular dimension values but not for all values of a financial dimension.

12. Create a new line. In the **Reference** field, select the Dimension name. In the **From** and **To** fields, select the starting and ending code for the dimension range, which should be considered in calculations. Create a line for each required dimension range. If no lines are created, the filter will not be used.


## Setup cells of the reports

You can setup the cells of report manually or by copying from another report. 

### Copy financial reports settings
In the **Financial reports** page, click **Copy**. In the dialog box that opens, select the **Company** and **Report code** to be copied (**SOURCE REPORT** group of fields), and select a **Report code** from the list or enter a new one, into which the settings will be copied (**TARGET REPORT** group of fields). If the target report already has settings that are specified, they will be overwritten.

### Create report cells manually
In the **Financial reports** page, click **Setup**. The upper section of the form displays a list of report cells and their main parameters.

<add here screenshot 1. Cels setup.jpg>

Create a new line. 
Enter unique identification of the report cell in the field **Code**. You can setup any convenient rule for naming of unique identificators, considering that name of each cell must be unique within the same report. **Electronic reporting** configuration, which is configured for report output, should filter list of report values by cell codes in binding between report values and format elements.

      Tip. As example, you can use concatenation of XML tags names of official electronic format of the report. 

Credit transaction amount for the ledger in correspondence with other ledger accounts for the period.Enter Description of the line.

Tabs and list of fields in each tab in the upper section of the page are the same as in the **Financial reports** page. Values entered for report cell on the **Requisites setup** page, supersede those entered for the report.

### Setup calculation rules for the cell.

Use the following procedure to create report cell operations.
1.	In the **Financial reports** page, click **Setup**.
2. In the **Requisites setup** page, select the report cell line or create a new one and in the lower pane, click **Add** to create a line.
      One or more lines with amount calculation parameters can be setup for each report cell. The lines are linked together with a mathematical operator.

<add here screenshot 2. Cells setup - operations.jpg>

3.	In the **Operator** field, select the mathematical operator that is applied to the cell value.

      Note. The Operator field is used to set up the mathematical sign for the amount that is calculated for the cell and is also used as a mathematical sign when you set up multi-line operations.  Credit balance, Credit activity, and Turnover in correspondence credit voucher types should normally use a minus sign (-).
      
4.	In the **Line type** field, select the data source that is used to calculate the selected line. The value is pre-defaulted from the Cell setup on **Requisites setup** page and can be changed. The following line types are available:

| **Line type** | **Data source** | **Available type of operation** |
|-------|--------|----------|
| Transactions | Ledger transactions | Balance, Credit balance, Debit balance, Turnover, Credit activity, Debit activity, Turnover in correspondence, Turnover in correspondence credit, Turnover in correspondence debit, Active balance (debit), and Passive balance (credit) |
| Budget | Budget transactions | Balance, Credit balance, Debit balance, Turnover, Credit activity, and Debit activity |
| Register | Value of the Register field that is specified in the **Register field** on the **Tax registers** tab |
| Constant | Value that is specified in the **Constant value** field of Cell operations | |
| Conractor | Ledger transactions that are related to contractors | Active balance (debit) and Passive balance (credit). The balance values are calculated for analytical level defined in the field **Balance detail** on tab **General** (values "Document", "Agreement",  "Contractor" are available) |
| Dimension set balance | | |

5. If you select “Transactions”, “Budget” or “Contractor” in the **Line type** field, select a type of operation in the **Type of operation** field. THe following values are available:

| **Type of operation** | **Calculation algorithm** |
|----|----|
| Balance | Ledger account transaction amount, on date |
| Credit balance | Credit ledger account transaction amount, on date |
| Debit balance | Debit ledger account transaction amount, on date |
| Turnover | Transaction amount for the ledger for the period |
| Credit activity | Credit transaction amount for the ledger for the period |
| Debit activity | Debit transaction amount for the ledger for the period |
| Turnover in correspondence (only for **Line type** “Transactions”) | Transaction amount for the ledger in correspondence with other ledger accounts for the period |
| Turnover in correspondence credit (only for **Line type** “Transactions”) | Credit transaction amount for the ledger in correspondence with other ledger accounts for the period |
| Turnover in correspondence debit (only for **Line type** “Transactions”) | Debit transaction amount for the ledger in correspondence with other ledger accounts for the period |
| Active balance (debit) (only for **Line type** values “Transactions”, “Contractor”) | Depending on the **Line type** selected, the lines are calculated: for	“Transactions”: First, balances for ledger account across all combinations of financial dimensions are calculated. Second, debit balances for each dimension combination are summarized. The resulting value is cell value. For	“Contractor”: Active balance for the ledger account by customers, contracts, or documents |
| Passive balance (credit) (only for **Line type** values “Transactions”, “Contractor”) | Depending on the **Line type** selected, the lines are calculated: for “Transactions”: First, balances for ledger account across all combinations of financial dimensions are calculated. Second, credit balances for each dimension combination are summarized. The resulting value is cell value. For	“Contractor”: Passive balance for ledger account by counteragents, contracts, or documents |

6. If you select “Balance”, “Credit balance”, “Debit balance”, “Active balance (debit)”, or “Passive balance (credit)” in the **Type of operation** field, define **Balance type**: either “Incoming” or “Outgoing”.

7.	In the **Account/Interval** field choose either “Account” to be able to setup one G/L account in operation or “Interval” to be able to setup interval of G/L accounts.
If you choose “Account”, define G/L account in the field **Account**
If you choose “Interval”, click **Setup > Account interval**. Create a line, and then in the **From** and **To** fields on the **Account interval** tab, select the starting and ending ledger account numbers that are used in the calculation.

8.	In the **Corr. Account/Interval** field choose either “Account” to be able to setup one G/L account in operation or “Interval” to be able to define interval of G/L accounts 
If you choose “Account”, define G/L account in the field **Corr. account**.
If you choose “Interval”, click **Setup > Account interval**. Create a line, and then in the **From** and **To** fields on the **Offset interval** tab, select the starting and ending ledger account numbers that are used in the calculation.

9.	 If you select “Contractor” in the **Line type** field, select "Document", "Agreement", or "Contractor" in the **Balance detail** field on the **General** tab, to define analytical level for calculation of active or passive balance for contractor.

10.	If you select “Register” in the **Line type** field, make the following settings:

   10.1 on the **Tax registers** tab, in the **Register code** field select Profit tax register code and in the **Register field** field, select a register field name. The data from the register field is considered in calculation than.
   
   10.2 Optionally, setup calculation of Tax register for one Expense code or for interval of Expense codes: in the **Account/Interval** field, either choose “Account” and in the **Account** field, define Expense code, or choose “Interval” and in the **Setup > Account interval** define interval of Expense codes.
   
11.	The **General**, **Posting layer** and **Financial dimensions** tabs contain same fields as tabs on upper part of the **Requisites setup** page **Financial reports** page. Optionally go to these tabs to specify values in respective fields for Operation line (these values supersede default values for Cell and/or Report).

12.	After you create the operation lines, you can arrange them in the correct order. Select a line, and then click **Up** or **Down** buttons to move the selected line one position up or down.


## Configure Electronic reporting to take financial report calculation results

Find more details about how to configure Electronic reporting here: https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lcs-solutions/country-region?toc=/fin-and-ops/toc.json#electronic-reporting 


Below you can find example procedure of how to configure Electronic reporting for taking the results of Financial reports calculation.

1.	Create **Data model** for Financial reports. Create model node of type **Record list** and name it **Items**.

Create the following nodes under **Items**:

| **Node name and data type** | **Data type** | **Description** |
|----|----|---|
| **Code** | String | This node with get information from the report Cell code |
| **Report code** | String | This node will get the code of the Financial report. |
| **Text** | String | This node will get value of the report cell if the calculated value is of “String” type |
| **Value** | Real | This node will get value of the report cell if the calculated value is of “Real” type  |


<Add here screenshot 3. Model.jpg>

2.	Create **Model mapping**

2.1	Create User input parameter for **Report code**:

In the **Model mapping designer**, in the left pane **Mapping \ Data source types**, click on **General \ User input parameter** line.

In the **Data sources** pane click **Add root**. 

Define name of User input parameter as “FinancialReport_UIP” and in the field **Operations data type name (EDT, enum)** choose the extended data type “LedgerRRGRepCode_RU”

<add here screenshot UIP.jpg>


2.2	Create User input parameter for **Base date**:

Define name of User input parameter as **BaseDate_UIP** and in the field **Operations data type name (EDT, enum)** choose the extended data type “BaseDate”

<add here screenshot Base date UIP.jpg>
   
   
2.3 Similarly, create and set up User input parameter for **Reporting date** (for example, use extended data type “ReportingDate_RU”)


2.4	Add class LedgerRRGCustomReportHelper_RU as Data source with name **$RRGCustom** 

<add here screenshot Data Source RRG custom.jpg>
   

2.5	Create Calculated field with name **$DataCustom** and the following formula:

'$RRGCustom'.getCustomReportData(FInancialReport_UIP , BaseDate_UIP, ReportingDate_UIP)

   Note. Function **getCustomReportData** of class **LedgerRRGCustomReportHelper_RU** has **Financial report name**, **Base date** and **Reporting date** as input parameters and returns Record list with all calculated values for all configured Cells of the chosen Financial report considering Base date and Report date. 
   
Output record list contains the following fields in each record line: 

   ParmFieldId – code of Report cell
   
   ParmFieldAmount – value of calculated cell if it has data type “Real”
   
   ParmFieldText – value of calculated cell if it has data type “String”


2.6	Bind data source to Model nodes:

Bind calculated field **$DataCustom** to model node **Items**

<add here screenshot Binding.jpg>

Bind Record list fields in the following way:

   Items / Code <-> ParmFieldId
   
   Items / Text <-> ParmFieldText
   
   Items / Value <-> ParmFieldAmount
   
   Items / ReportCode <-> FinancialReport_UIP


3.	Set up format of the report.

In format configuration, filter the record list *Items* by a constant value of Items.Code and bind Items.Text or Items.Value nodes of filtered line to respective format nodes.

4.	Run the report.

Run report from the **Electronic reporting** workspace.
Define **Calculation date**, **Report code** and optionally, **Reporting date**.






