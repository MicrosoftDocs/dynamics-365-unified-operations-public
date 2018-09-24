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

|   |  |
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




