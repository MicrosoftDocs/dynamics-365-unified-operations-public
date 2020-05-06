---
title: VAT declaration for Germany
---

This topic explains how to set up and generate the value-added tax (VAT)
declaration for legal entities in Germany.

For general information about how to set up the VAT statement, see *VAT
reporting for Europe*.

Set up sales tax reporting codes for VAT reporting
==================================================

Set up sales tax reporting codes by following the instructions in Set up sales
tax reporting codes. The following table provides an example of sales tax
reporting codes for Germany.

| **Code**                                                                                                                                    | **Description**                                                                                                                                                                                                                                                                                                                       | **Element in the XML file of the VAT declaration**                      | **Tax base or tax amount** |
|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|----------------------------|
| **Tax-free sales with input tax deduction for intra-community supplies (§4, no. 1, letter b of the UStG [Umsatzsteuergesetz, or VAT law])** |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 41                                                                                                                                          | Intra-community shipment (§4, no. 1b of the UStG) to customers with tax registration.                                                                                                                                                                                                                                                 | Kz41                                                                    | Tax base                   |
| 44                                                                                                                                          | Intra-community deliveries of new vehicles to customers without a VAT ID.                                                                                                                                                                                                                                                             | Kz44                                                                    | Tax base                   |
| 49                                                                                                                                          | Intra-community deliveries of new vehicles outside a company.                                                                                                                                                                                                                                                                         | Kz49                                                                    | Tax base                   |
| 43                                                                                                                                          | Additional tax-free sales with input tax deduction (for example, exports).                                                                                                                                                                                                                                                            | Kz43                                                                    | Tax base                   |
| **Tax-free sales without input tax deduction (for example, sales according to §4, no. 8 through 28 of the UStG)**                           |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 48                                                                                                                                          | Tax-free sales without input tax deduction.                                                                                                                                                                                                                                                                                           | Kz48                                                                    | Tax base                   |
| **Taxable sales**                                                                                                                           |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 81                                                                                                                                          | Tax base for deliveries or services that are charged at 19 percent.                                                                                                                                                                                                                                                                   | Kz81                                                                    | Tax base                   |
| 181                                                                                                                                         | Tax amount for deliveries or services that are charged at 19 percent.                                                                                                                                                                                                                                                                 | Not shown separately in the XML file but considered in the total (Kz83) | Tax amount                 |
| 86                                                                                                                                          | Tax base for deliveries or services that are charged at 7 percent.                                                                                                                                                                                                                                                                    | Kz86                                                                    | Tax base                   |
| 186                                                                                                                                         | Tax amount for deliveries or services that are charged at 7 percent.                                                                                                                                                                                                                                                                  | Not shown separately in the XML file but considered in the total (Kz83) | Tax amount                 |
| 35                                                                                                                                          | Tax base for deliveries or services at other tax rates.                                                                                                                                                                                                                                                                               | Kz35                                                                    | Tax base                   |
| 36                                                                                                                                          | Tax amount for deliveries or services at other tax rates.                                                                                                                                                                                                                                                                             | Kz36                                                                    | Tax amount                 |
| 77                                                                                                                                          | Deliveries of agricultural and forestry businesses, according to §24 of the UStG, to customers who have a VAT ID.                                                                                                                                                                                                                     | Kz77                                                                    | Tax base                   |
| 76                                                                                                                                          | Tax base of turnover that tax is payable for, according to §24 of the UStG (sawmill products, beverages and alcoholic liquids, such as wine).                                                                                                                                                                                         | Kz76                                                                    | Tax base                   |
| 80                                                                                                                                          | Tax amount of turnover that tax is payable for, according to §24 of the UStG (sawmill products, beverages and alcoholic liquids, such as wine).                                                                                                                                                                                       | Kz80                                                                    | Tax amount                 |
| **Intra-community acquisitions and VAT payable for such acquisitions**                                                                      |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 91                                                                                                                                          | Tax-free intra-community acquisitions.                                                                                                                                                                                                                                                                                                | Kz91                                                                    | Tax base                   |
| 89                                                                                                                                          | Tax base for the acquisition of goods from countries in the European Union (EU), charged at 19 percent.                                                                                                                                                                                                                               | Kz89                                                                    | Tax base                   |
| 189                                                                                                                                         | Tax amount for the acquisition of goods from countries in the EU, charged at 19 percent.                                                                                                                                                                                                                                              | Not shown separately in the XML file but considered in the total (Kz83) | Tax amount                 |
| 93                                                                                                                                          | Tax base for the acquisition of goods from countries in the EU, charged at 7 percent.                                                                                                                                                                                                                                                 | Kz93                                                                    | Tax base                   |
| 193                                                                                                                                         | Tax amount for the acquisition of goods from countries in the EU, charged at 7 percent.                                                                                                                                                                                                                                               | Not shown separately in the XML file but considered in the total (Kz83) | Tax amount                 |
| 95                                                                                                                                          | Tax base for the acquisition of goods from countries in the EU at other tax rates.                                                                                                                                                                                                                                                    | Kz95                                                                    | Tax base                   |
| 98                                                                                                                                          | Tax amount for the acquisition of goods from countries in the EU at other tax rates.                                                                                                                                                                                                                                                  | Kz98                                                                    | Tax amount                 |
| 94                                                                                                                                          | Tax base for intra-community acquisitions of new vehicles (§1b, paragraphs 2 and 3 of the UStG) from suppliers without a VAT ID, at the general tax rate.                                                                                                                                                                             | Kz94                                                                    | Tax base                   |
| 96                                                                                                                                          | Tax amount for intra-community acquisitions of new vehicles (§1b, paragraphs 2 and 3 of the UStG) from suppliers without a VAT ID, at the general tax rate.                                                                                                                                                                           | Kz96                                                                    | Tax amount                 |
| **Additional information about sales**                                                                                                      |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 42                                                                                                                                          | Deliveries by the first customer for intra-community triangular transactions (§25b of the UStG).                                                                                                                                                                                                                                      | Kz42                                                                    | Tax base                   |
| 60                                                                                                                                          | Taxable sales of the performing entrepreneur that the service recipient owes the tax for, according to §13b (5) of the UStG.                                                                                                                                                                                                          | Kz60                                                                    | Tax base                   |
| 21                                                                                                                                          | Other non-taxable services according to §18b, sentence 1, no. 2 of the UStG.                                                                                                                                                                                                                                                          | Kz21                                                                    | Tax base                   |
| 45                                                                                                                                          | Other non-taxable sales (where the place of performance isn't in Germany).                                                                                                                                                                                                                                                            | Kz45                                                                    | Tax base                   |
| **Beneficiary as tax debtor (§13b of the UStG)**                                                                                            |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 46                                                                                                                                          | Tax base for other services in accordance with §3a (2) UStG of an entrepreneur that is located in the rest of the community (§13b (1) of the UStG).                                                                                                                                                                                   | Kz46                                                                    | Tax base                   |
| 47                                                                                                                                          | Tax amount for other services in accordance with §3a (2) UStG of an entrepreneur that is located in the rest of the community (§13b (1) of the UStG).                                                                                                                                                                                 | Kz47                                                                    | Tax amount                 |
| 73                                                                                                                                          | Tax base of turnover that is covered by the property transfer tax law – in particular, deliveries of land for which the performing entrepreneur has opted for tax liability in accordance with §9 (3) of the UStG.                                                                                                                    | Kz73                                                                    | Tax base                   |
| 74                                                                                                                                          | Tax amount of turnover that is covered by the property transfer tax law – in particular, deliveries of land for which the performing entrepreneur has opted for tax liability in accordance with §9 (3) of the UStG.                                                                                                                  | Kz74                                                                    | Tax amount                 |
| 84                                                                                                                                          | Tax base of other services (§13b (2), no. 1, 2, and 4 through 11 of the UStG).                                                                                                                                                                                                                                                        | Kz84                                                                    | Tax base                   |
| 85                                                                                                                                          | Tax amount of other services (§13b (2), no. 1, 2, and 4 through 11 of the UStG).                                                                                                                                                                                                                                                      | Kz85                                                                    | Tax amount                 |
| **Deductible input tax amounts**                                                                                                            |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 66                                                                                                                                          | Tax on input from invoices of other companies (§15, paragraph 1, no. 1 of the UStG).                                                                                                                                                                                                                                                  | Kz66                                                                    | Tax amount                 |
| 61                                                                                                                                          | Input VAT amount from intra-community acquisitions of objects (§15, paragraph 1, no. 3 of the UStG).                                                                                                                                                                                                                                  | Kz61                                                                    | Tax amount                 |
| 62                                                                                                                                          | Import sales tax that is incurred (§15, paragraph 1, no. 2 of the UStG).                                                                                                                                                                                                                                                              | Kz62                                                                    | Tax amount                 |
| 67                                                                                                                                          | Input tax amounts from services within the meaning of §13b of the UStG (§15, paragraph 1, clause 1, no. 4 of the UStG).                                                                                                                                                                                                               | Kz67                                                                    | Tax amount                 |
| 63                                                                                                                                          | Input tax amounts that are calculated according to general average rates (§23 and §23a of the UStG).                                                                                                                                                                                                                                  | Kz63                                                                    | Tax amount                 |
| 64                                                                                                                                          | Correction of input tax deduction (§15a of the UStG).                                                                                                                                                                                                                                                                                 | Kz64                                                                    | Tax amount                 |
| 59                                                                                                                                          | Input tax deduction for intra-community deliveries of new vehicles outside a company (§2a of the UStG) and small businesses within the meaning of §19 (1) of the UStG (§15 (4a) of the UStG).                                                                                                                                         | Kz59                                                                    | Tax amount                 |
| **Other tax amounts**                                                                                                                       |                                                                                                                                                                                                                                                                                                                                       |                                                                         |                            |
| 65                                                                                                                                          | Tax because of changes in the form of taxation, and after-tax on taxed down payments, and so on, because of changes in tax rate.                                                                                                                                                                                                      | Kz65                                                                    | Tax amount                 |
| 69                                                                                                                                          | Tax amounts that are shown incorrectly or unjustifiably on invoices (§14c of the UStG), and also tax amounts that are owed in accordance with §6a (4), sentence 2; §17 (1), sentence 6; and §25b (2) of the UStG, or tax amounts that are owed by an outsourcer or warehouse keeper in accordance with §13a (2) 1, no. 6 of the UStG. | Kz69                                                                    | Tax amount                 |
| 39                                                                                                                                          | Deduction of the stipulated special advance payment for long-term extension (which usually will be completed only in the last advance notification of the taxation period).                                                                                                                                                           | Kz39                                                                    | Tax amount                 |
| 83                                                                                                                                          | Total VAT amount (VAT advance payment or VAT surplus). On the VAT declaration in XML format, the value in this box is automatically calculated as the sum of reporting codes 181, 186, 36, 80, 189, 193, 98, 96, 47, 74, and 85, minus reporting codes 66, 61, 62, 67, 63, 64, 59, 69, and 39.                                        | Kz83                                                                    | Tax amount                 |

**Note:** For sample forms of advance VAT returns that include declaration row
codes, see Forms in the VAT procedure for the year 2020.

Set up sales tax codes
======================

Set up sales tax codes by following the instructions in *Sales tax codes for VAT
reporting* and Sales tax overview.

**Note:** In a German legal entity, sales tax codes for tax-free sales should be
set up according to the following rules:

-   The tax rate is more than 0 (zero).

-   The tax code is marked as **Exempt** on the **Sales tax groups** page.

Create a VAT declaration in XML format
======================================

1.  In Microsoft Dynamics Lifecycle Services (LCS), in the **Shared asset
    library**, download the latest versions of the Electronic reporting (ER)
    configurations for the VAT declaration format:

-   **Elster (DE)**

>   For more information, see Download Electronic reporting configurations from
>   Lifecycle Services.

1.  Go to **Tax \> Setup \> Sales tax \> Electronic tax declaration setup**.

2.  In the **Format mapping** field, select the **Elster (DE)** format that you
    downloaded earlier.

3.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

4.  In the **Report sales tax for settlement period** dialog box, set the
    following fields.

| **Field**                 | **Description**                                                                                                                                                                                                                                                                         |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period         | Select the applicable reporting period.                                                                                                                                                                                                                                                 |
| From date                 | Enter the first date of the sales tax settlement period that sales tax should be calculated for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page.                                                                                 |
| Transaction date          | Enter the date when the sales tax report is calculated. The default value is the current date. The sales tax payment is calculated for all transactions that were posted during the settlement period.                                                                                  |
| Sales tax payment version | Select the type of sales tax settlement. If this sales tax settlement is the first sales tax settlement for the period, select **Original**. If a sales tax settlement has already been generated, select **Latest corrections**. For more information, see Create a sales tax payment. |

5.  Select **OK**.

6.  In the **German sales tax report** dialog box, set the following fields.

| **Field**                      | **Description**                                                                                                                                                 |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create electronic tax document | Set this option to **Yes** to create an electronic document that contains the details of the report.                                                            |
| Documents submitted separately | Set this option to **Yes** if the printed report isn't submitted together with the electronic document. In the XML file, code Kz22 should have the value **1**. |

7.  Select **OK**. A new line is created on the **Electronic tax declaration
    log** page (**Tax \> Declarations \> Sales tax \> Electronic tax declaration
    log**).

![](media/f5ae2f817d889a3c04378d40caa4f86f.png)

>   A screenshot of a cell phone Description automatically generated

Preview the XML file
====================

1.  Go to **Tax \> Declarations \> Sales tax \> Electronic tax declaration
    log**.

2.  On the **Electronic tax declaration log** page, select the **Preview** tab
    to preview the reported values.

3.  To review or save the XML file for further submission (outside of the
    system), select the line on the **Electronic tax declaration log** page, and
    then select the paper clip symbol in the upper-right corner.

4.  The **Document handling** page appears and shows the generated file. Select
    **Open** at the top of the page to open the file in the application that is
    associated with the .xml extension in your system.

Submission the VAT declaration to ELSTER
========================================

ELSTER (Elektronische Steuererklärung, or electronic tax declaration) is a
German online tax office system that was designed by the Federal Central Tax
Office for online submission of tax declarations.

The Developers area of the ELSTER website provides examples that show how
developers can interact with ELSTER Rich Client (ERiC) for the submission of VAT
declarations in XML file format. Examples are provided for C++, C\#, and Java.
To access this area of the website, you must be registered as a developer. An
example might help you create your own executable file that you can use to
submit XML files via ERiC. To use an executable file to submit XML files to
ELSTER, you must download ERiC dynamics-link libraries (DLLs).

For more information about ERiC releases, see ELSTER website.

Example
=======

The following example shows how you can set up sales tax codes and sales tax
reporting codes, post transactions, and generate the German VAT declaration.

1.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**, and set up
    the following sales tax codes.

| **Sales tax code** | **Percentage** | **Description**                                                                       |
|--------------------|----------------|---------------------------------------------------------------------------------------|
| VAT19              | 19             | Domestic sales at a rate of 19 percent.                                               |
| VAT7               | 7              | Domestic sales at a rate of 7 percent.                                                |
| InVAT19            | 19             | Domestic purchases at a rate of 19 percent.                                           |
| InVAT7             | 7              | Domestic purchases at a rate of 7 percent.                                            |
| EU19               | 19             | EU purchases at a rate of 19 percent, where the **Use tax** option is set to **Yes**. |
| EU7                | 7              | EU purchases at a rate of 7 percent, where the **Use tax** option is set to **Yes**.  |
| EUS                | 19             | EU sales where the **Exempt** option is set to **Yes**.                               |
| THIRD              | 19             | Export sales where the **Exempt** option is set to **Yes**.                           |

2.  On the **Sales tax codes** page, on the **Report setup** FastTab, assign
    reporting codes to sales tax codes.

>   The following table shows how to assign the sales tax reporting codes to
>   sales tax codes.

| **Sales tax code** | **Taxable sales** | **Tax-free sale** | **Sales tax payable** | **Taxable purchases** | **Sales tax receivable** | **Taxable import** | **Use tax** | **Offset use tax** |
|--------------------|-------------------|-------------------|-----------------------|-----------------------|--------------------------|--------------------|-------------|--------------------|
| VAT19              | 81                |                   | 181                   |                       |                          |                    |             |                    |
| VAT7               | 86                |                   | 186                   |                       |                          |                    |             |                    |
| InVAT19            |                   |                   |                       |                       | 66                       |                    |             |                    |
| InVAT7             |                   |                   |                       |                       | 66                       |                    |             |                    |
| EU19               |                   |                   |                       |                       |                          | 89                 | 189         | 61                 |
| EU7                |                   |                   |                       |                       |                          | 93                 | 193         | 61                 |
| EUS                |                   | 41                |                       |                       |                          |                    |             |                    |
| THIRD              |                   | 43                |                       |                       |                          |                    |             |                    |

>   **Note:** The preceding configuration is just an example and depends on the
>   structure of the sales tax codes that are used. If you want values to be
>   calculated and transferred to the sales tax report, for each tax code that
>   is used in the sales tax payment process, you must set a relevant sales tax
>   reporting code in one or more fields on the **Report setup** FastTab.

1.  Go to **Tax \> Setup \> Sales tax \> Electronic tax declaration setup**.

2.  In the **Format mapping** field, select the **Elster (DE)** format that you
    downloaded earlier.

3.  Post the following transactions. For example, for customer invoices, go to
    **Accounts receivable \> Invoices \> All free text invoices**. For vendor
    invoices, go to **Accounts payable \> Invoices \> Invoice journal**.

| **Date**        | **Transaction type**      | **Amount net** | **VAT amount** | **Sales tax code** | **Expected tax base – reporting code** | **Expected tax amount – reporting code** |
|-----------------|---------------------------|----------------|----------------|--------------------|----------------------------------------|------------------------------------------|
| January 1, 2020 | Customer invoice          | 100            | 19             | VAT19              | 81                                     | 181                                      |
| January 1, 2020 | Vendor invoice (EU)       | 100            | 7              | EU7                | 93                                     | 193 – Tax payable 61 – Tax deduction     |
| January 1, 2020 | Customer invoice (EU)     | 100            | 0              | EUS                | 41                                     | Not applicable                           |
| January 1, 2020 | Customer invoice (export) | 100            | 0              | THIRD              | 43                                     | Not applicable                           |

4.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

5.  In the **Report sales tax for settlement period** dialog box, set the
    following fields to the specified values:

    -   **Settlement period:** Mon

    -   **From date:** 1/1/2020

6.  Select **OK**.

7.  In the **German sales tax report** dialog box, select the **Create
    electronic tax document** check box.

8.  Select **OK**.

9.  Go to **Tax \> Declarations \> Sales tax \> Electronic tax declaration
    log**, and select the required line.

10. On the **Electronic tax declaration log** page, select the **General** tab,
    and review the general information.

![](media/5111b776232c1ab240d4a7f8a5549f1e.png)

>   A screenshot of a cell phone Description automatically generated

1.  Select the **Preview** tab, and review the reported values.

![](media/6cea6c691e3c5541743883800957c70a.png)

>   A screenshot of a social media post Description automatically generated

1.  Select the paper clip symbol in the upper-right corner.

2.  Select **Open** at the top of the page, and review the XML file.

![](media/2bfa3e98f3f6f7c7be09dee43e75e67c.png)

>   A screenshot of a cell phone Description automatically generated

Correction transactions
-----------------------

1.  Post a new transaction. For example, to post a customer invoice, go to
    **Accounts receivable \> Invoices \> All free text invoices**.

| **Date**        | **Transaction type**        | **Amount net** | **VAT amount** | **Sales tax code** | **Expected tax base – Reporting code** | **Expected tax amount – Reporting code** |
|-----------------|-----------------------------|----------------|----------------|--------------------|----------------------------------------|------------------------------------------|
| January 1, 2020 | Customer invoice (domestic) | 100            | 7              | VAT7               | 86                                     | 186                                      |

2.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

3.  In the **Report sales tax for settlement period** dialog box, set the
    following fields to the specified values:

    -   **Settlement period:** Mon

    -   **From date:** 1/1/2020

4.  Select **OK**.

5.  In the **German sales tax report** dialog box, select the **Create
    electronic tax document** check box.

6.  Select **OK**.

7.  Go to **Tax \> Declarations \> Sales tax \> Electronic tax declaration
    log**, and select the required line.

8.  Select the **Preview** tab, and review the reported values.

![](media/b459d3ed1d569025ba25f3b277ce241e.png)

>   A screenshot of a cell phone Description automatically generated

>   Note that a correction transaction is added to the declaration in codes
>   **86** and **83**.

1.  Select the paper clip symbol in the upper-right corner.

2.  Select **Open** at the top of the page, and review the XML file.

![](media/ff6823f95d9fd6e26c706524795a83d0.png)

>   A screenshot of a cell phone Description automatically generated

>   Note that a correction transaction is added to the declaration in codes
>   **86** and **83**.

Review sales tax report amounts 
================================

You can optionally review sales tax amount in SSRS report.

Set up the report layout for sales tax authorities
--------------------------------------------------

1.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax authorities**.

2.  On the **Sales tax authorities** page, select the sales tax authority that
    will be used in the sales tax codes for the sales tax settlement period.

3.  In the **Report layout** field, select **German report layout**.

Generate a sales tax payment and print the German sales tax report
------------------------------------------------------------------

At the end of the VAT reporting period, calculate the sales tax amounts for the
settlement period.

1.  Go to **Tax \> Declarations \> Sales tax \> Settle and post sales tax**.

2.  In the **Settle and post sales tax** dialog box, set the required fields as
    described earlier.

3.  Select **OK**.

4.  In the **German sales tax report** dialog box, set the **Create electronic
    tax document** option to **No**.

5.  Select **OK** to generate the sales tax payment and review the report.

If you post transactions as described in step 5 of the example earlier in this
topic, you will see the following data.

![A screenshot of a cell phone Description automatically generated](media/83b3c318c4623d826f19395b8cafa548.png)

![A close up of a device Description automatically generated](media/b0c82374958390951b9abd847b6f30ad.png)

Print a sales tax payment report from a sales tax payment
---------------------------------------------------------

1.  Go to **Tax \> Inquiries and reports \> Sales tax payments**.

2.  On the **Sales tax payment** page, select the record, and then select
    **Print report**.

3.  In the dialog box, set the fields as described in the previous section, and
    then select **OK**.

Report sales tax for the settlement period
------------------------------------------

You can also generate the German sales tax report by using the **Report sales
tax for settlement period** inquiry.

1.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

2.  In the **Report sales tax for settlement period** dialog box, set the
    **Settlement period** and **From date** fields as described in the Generate
    a sales tax payment and print the German sales tax report section earlier in
    this topic.

3.  In the **Sales tax payment version** field, select one of the following
    values:

-   **Original** – Generate a report for sales tax transactions of the first
    posted settlement calculation for the period.

-   **Corrections** – Generate a report for sales tax transactions of subsequent
    settlement calculations for the period.

-   **Total list** – Generate a report for all sales transactions for the
    period. These transactions include original and corrected transactions.

1.  Select **OK**.

2.  Go to **Tax \> Declarations \> Sales tax \> Settle and post sales tax**.

3.  In the **Settle and post sales tax** dialog box, in the **Sales tax payment
    version** field, select **Original**.

4.  Print the report, and review the data.

| **Reporting code** | **Sales tax amount** |
|--------------------|----------------------|
| 41                 | 100                  |
| 43                 | 100                  |
| 61                 | 7                    |
| 81                 | 100                  |
| 93                 | 100                  |
| 181                | 19                   |
| 193                | 7                    |

5.  Go to **Tax \> Declarations \> Sales tax \> Settle and post sales tax**.

6.  In the **Settle and post sales tax** dialog box, in the **Sales tax payment
    version** field, select **Latest corrections**.

7.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

8.  In the **Report sales tax for settlement period** dialog box, in the **Sales
    tax payment version** field, select **Corrections**. The following table
    shows the result.

| **Reporting code** | **Sales tax amount** |
|--------------------|----------------------|
| 86                 | 100                  |
| 186                | 7                    |

9.  Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement
    period**.

10. In the **Report sales tax for settlement period** dialog box, in the **Sales
    tax payment version** field, select **Total list**. The following table
    shows the result.

| **Reporting code** | **Sales tax amount** |
|--------------------|----------------------|
| 41                 | 100                  |
| 43                 | 100                  |
| 61                 | 7                    |
| 81                 | 100                  |
| 86                 | 100                  |
| 93                 | 100                  |
| 181                | 19                   |
| 186                | 7                    |
| 193                | 7                    |
