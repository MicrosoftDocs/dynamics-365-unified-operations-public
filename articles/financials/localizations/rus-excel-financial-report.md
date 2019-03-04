---
# required metadata

title: Configure financial reports in Excel (Russia)
description: This topic walks you through creating a new Electronic reporting (ER) configuration that contains a template for generating a financial report in an Excel format. 
author: Anasyash
ms.date: 03/01/2019
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
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.1

---

# Configure financial reports in Excel (Russia)

[!include [banner](../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a template for generating financial report in Excel format.

Before reviewing this topic, you should review the topic [Create Electronic reporting (ER) configurations](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/electronic-reporting-configuration?toc=/fin-and-ops/toc.json) and all topics behind this one.



## Set up Financial report

Set up a financial report with the list of financial report cells and rules for calculation of financial reports cells.

1.  As example, upload data management package settings **RU Accounting reporting 5.07 (2016).zip** as described in the topic [Accounting reporting in electronic format](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/rus-act-reporting/articles/financials/localizations/rus-accounting-reporting.md).

2.  Go to **General ledger \> Financial reports setup \> Financial reports**. Click on the line with value *Баланс* in the column **Code**.

3.  Click **Setup**. On the page **Requisites setup**, set up calculation rules for report cells as described in the topic [Financial reporting (Russia)](rus-financial-reports#set-up-calculation-rules-for-report-cells.md)


## Create Excel template for financial report

Create Excel template for your financial report. As minimum, you should assign names to all Excel cells which should have values in the generated report.

As an example, download the Excel template example for a Russian balance sheet here: [balance_sheet_template_russia.xlsx]()
<!--- will add link to the download after copy edit -->

## Create ER configuration for financial report in Excel

Create ER configuration format based on ER model **Financial reports model**.

Before going to next steps, learn how to set up ER configuration which generates the report in Excel format, in the topic [ER Design a configuration for generating reports in OPENXML format (November 2016)](../../dev-itpro/analytics/tasks/er-design-reports-openxml-2016-11.md?toc=/fin-and-ops/toc.json)

1.  Download the latest version of the Electronic reporting (ER) configurations:

  -   Financial reports model
  -   Financial reports model mapping (RU)
  -   Balance sheet format Excel example (RU)

For Fix downloading instructions see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2.  Go to **Workspaces \> Electronic reporting**. Click **Reporting configurations**.

3.  Learn how to create a new format for financial report in Excel.

    1.  Select **Financial reports model** configuration

    2.  On the Action Pane click **Create configuration \> Format based on data model Financial reports model**. Give it a name.

    3.  In the **Format type** field, select **Excel**

    4.  In the **Data model definition**, select **Financial report.**

    5.  Click **Create configuration.**

    6.  Select created configuration and click **Designer**.

    7.  In the **Import from Excel** dialog box, click **Import \> Import from Excel**. Click **Add template.** Select the Excel file **Balance sheet.xls**

    8.  Select “Yes” in the **Create Excel Sheet format element**

    9.  Click **OK**. Review the cells created from the Excel template names:

        ![Format mapping cells](media/rus-format-designer-mapping.jpg)

    10. Close the page.
    

5.  Learn how ER format **Balance sheet format Excel example (RU)** is configured.

    1.  Select **Balance sheet format Excel example (RU)** ER configuration and click **Designer**.

    2.  Expand format elements **Excel = "Balance sheet"** and **Sheet\<стр.1_2\>.** Review all cells which will contain data in the financial report output

    3.  Click tab **Mapping**. Review Financial reports model elements which are sources for financial report cells.

    4.  Review that cells **DD, MM, YYYY, Company name**, … etc. up to **PrevPrevYear** are mapped to various Model elements from the group **Header** which contains various information about organization and report.

        Note. If your Financial report contains any information about organization which is not in scope **Financial reports model**, you could do the following:

        -   Create format User input parameter in case missed data is external to the Dynamics 365 for Finance and operations

        -   Create a derived model based on the **Financial reports model**, add new model elements. Create a derived model mapping based on **Financial reports model mapping** and bind new model elements to Dynamics 365 for Finance and operations data sources

        Find more details about how to create ER data models in the topic: [ER Design domain specific data model](../../dev-itpro/analytics/tasks/er-design-domain-specific-data-model-2016-11.md?toc=/fin-and-ops/toc.json)

        Find more details about how to map data model elements to data sources, in the topics:

        - [Define ER model mappings and select data sources for them](../../dev-itpro/analytics/tasks/er-define-model-mapping-select-data-sources-2016-11.md?toc=/fin-and-ops/toc.json)

        - [ER Map data model to selected data sources](../../dev-itpro/analytics/tasks/er-map-data-model-selected-data-sources-2016-11.md?toc=/fin-and-ops/toc.json)
        

    5. Review that cells where the financial report values are exported, for example, *АктивВнеОбАНематАктПояснения*, *АктивВнеОбАНематАктСумОтч*, *АктивВнеОбАНематАктСумПрдщ*, *АктивВнеОбАНематАктСумПрдшв* are mapped to the calculated field: **Calculations.'\$Values'("\<Input parameter = Cell name\>").Value**, or **Calculations.'\$Values'("\<Input parameter = Cell code\>").Text**
       The calculated field **Calculations.'\$Values'** contains the value of the financial report cell with code equals to the “Input parameter”.

       Find more details about the Financial reports model in the topic [Configure ER to use the results of financial report calculations](rus-financial-reports#configure-er-to-use-the-results-of-financial-report-calculations.md)
       

6. Learn how to quickly bind the calculated values of financial report cells to the ER format cells elements.

    1.  Click on the ER format cell *АктивВнеОбАНематАктПояснения*. Click **Unbind**

    2.  Repeate step 1. for the following ER format cells: *АктивВнеОбАНематАктСумОтч*, *АктивВнеОбАНематАктСумПрдщ*, *АктивВнеОбАНематАктСумПрдшв*

    3. Click **Format**. Enter the value in the field **Name** for all 4 cell. Value in the field **Name** must be equal to the value in the field **Cell code** in the financial report. In this example, enter to the **Name** field the value which is equal to the value in the field **Excel range**: *АктивВнеОбАНематАктСумОтч*, *АктивВнеОбАНематАктСумПрдщ*, *АктивВнеОбАНематАктСумПрдшв*


![Format mapping field name](media/rus-format-designer-format.jpg)



   4.  Click **Mapping**. Expand the container **Calculations**, expand the calculated field **\$Values**, click on the element **Text**.

   5.  In the list of Excel format cells, click on the cell *АктивВнеОбАНематАктПояснения*. Click **Bind**

![Format mapping text string](media/rus-format-designer-mapping-text-string.jpg)



   6.  On the **Mapping** tab, click on the element **Value**

   7.  In the list of Excel format cells, click on the cell *АктивВнеОбАНематАктСумОтч*. Click **Bind**

   8.  Repeat steps 5.6-5.7 for other 2 Excel cells which were unbounded on step 5.2


## Run financial report format

You can configure Electronic messages feature to run any ER configuration. Find more details in the topic [Configure electronic messages to generate the financial report and store the results](rus-financial-reports#configure-electronic-messages-to-generate-the-financial-report-and-store-the-results.md)

To run the ER format which is based on the **Financial reports model**, do the following:

1.  Go to **General ledger \> Inquiries and reports \> Financial reports (Russia)**.

2.  In the **Financial reports (Russia)** dialog box, in the field **Format mapping**, select the ER format which should be run.

3.  As example, select the ER format **Balance sheet format Excel example (RU)**. Click **OK**.

4.  In the dialog box **Electronic report parameters** define the report parameters:

| **Field**    | **Description**  |
|---------------|-----------------|
| Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the Signatory          |
| To date                                                          | Enter the base date for the financial report  |
| Approval date                                                    | Enter the approval date of the financial report  |
| Reporting date                                                   | Enter the reporting date for corrective report |
| Economic activity type code                                      | Enter the Economic activity type code (“ОКВЭД”) |
| Organizational form code                                         | Enter the Organizational form code (“ОКОПФ”)  |
| Ownership form code                                              | Enter the Ownership form code (“ОКФС”)         |
| Report                                                           | Select the financial report which should be calculated. In this example, select “Баланс” |

5.  Click **OK**. Review the generated Excel report for Balance sheet.
