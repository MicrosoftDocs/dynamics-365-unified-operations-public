---
title: Land tax declaration
description: Learn about the land tax declaration for Russia, including outlines on setting up land tax setting up parameters for land tax calculation.
author: evgenypopov
ms.author: evgenypopov
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-01-04
ms.dyn365.ops.version: 10.0.1
---

# Land tax declaration 

[!include [banner](../../includes/banner.md)]


According to the tax code of the Russian Federation, land assets are subject to
land tax. The tax period for land tax is one year. At the end of the tax period,
a company must report a land tax declaration.

The land tax declaration should be submitted to the tax authority where the land
is located. In this case, code **270** should be entered for the **at place of**
attribute. However, the greatest taxpayers can submit declarations to the tax
authority where the organization is registered as a greatest taxpayer. In this
case, code **213** should be entered for the **at place of** attribute.

The tax base for the calculation of land tax is the cadastral cost of the land
asset. The cadastral cost is defined by cadastral authorities and should be
specified by the user on the fixed asset card.

This article explains how to perform the following tasks:

1.  [Set up land tax](#set-up-land-tax)

2.  [Create a land asset and set up parameters for land tax
    calculation](#create-a-land-asset-and-set-up-parameters-for-land-tax-calculation)

3.  [Calculate land tax registers](#calculate-land-tax-registers)

4.  [Generate a land tax declaration](#generate-a-land-tax-declaration)

5.  [Create and post land tax ledger
    transactions](#create-and-post-land-tax-ledger-transactions)

## Set up land tax

Here is an overview of the steps for setting up land tax:

1.  [Set up land tax codes and rates](#set-up-land-tax-codes-and-rates)

2.  [Set up budget revenue codes for land
    tax](#set-up-budget-revenue-codes-for-land-tax)

3.  [Assign a budget revenue code to a sales tax
    code](#assign-a-budget-revenue-code-to-a-sales-tax-code)

4.  [Set up tax allowances](#set-up-tax-allowances)

5.  [Assign tax allowances to a sales tax code as a reduction of the tax rate, a
    reduction of the tax amount, and a tax base
    reduction](#assign-tax-allowances-to-a-sales-tax-code-as-a-reduction-of-the-tax-rate-a-reduction-of-the-tax-amount-and-a-tax-base-reduction)

6.  [Set up the territory code (OKTMO code) for the legal
    entity](#set-up-the-territory-code-oktmo-code-for-the-legal-entity)

7.  [Set up tax authorities and related OKTMO
    codes](#set-up-tax-authorities-and-related-oktmo-codes)

8.  [Optional: Set up company divisions, their registration reason codes (KPP),
    and their OKTMO
    codes](#optional-set-up-company-divisions-their-registration-reason-codes-kpp-and-their-oktmo-codes)

9.  [Set up the organization's locations and assign them to company
    divisions](#set-up-the-organizations-locations-and-assign-them-to-company-divisions)

10. [Set up territories for distributed land
    assets](#set-up-territories-for-distributed-land-assets)

11. [Set up Fixed assets parameters for posting land
    tax](#set-up-fixed-assets-parameters-for-posting-land-tax)

12. [Set up the journal for posting land
    tax](#set-up-the-journal-for-posting-land-tax)

13. [Set up a posting group for land tax
    postings](#set-up-a-posting-group-for-land-tax-postings)

### Set up land tax codes and rates

1.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.

2.  Create a sales tax code.

3.  In the **Type of tax** field, select **Land tax**.

4.  Specify the settlement period and the ledger posting group.

5.  On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code**
    group, select **Values** to open the **Sales tax code values** page.

6.  In the **Value** field, specify the tax rate for the assessed tax.

### Set up budget revenue codes for land tax

1.  Go to **Cash and bank management \> Setup \> Payment order setup \> Budget
    revenue classification**.

2.  Create a budget revenue code for land tax.

### Assign a budget revenue code to a sales tax code

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax
    relations**.

2.  Create a record.

3.  In the **Type of tax** field, select **Land tax**.

4.  In the **Code** field, select the sales tax code for the land tax.

5.  In the **Budget revenue code** field, select the budget revenue code that
    corresponds to the selected sales tax code.

### Set up tax allowances

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Tax allowances**.

2.  Create a record.

3.  Set the following values for the tax allowance.

    | Field       | Description                                                                                                                                                                                                                       |
    |-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Privilege       | Enter the tax allowance code.                                                                                                                                                                                                         |
    | Type of tax     | Select **Land tax**.                                                                                                                                                                                                                  |
    | Benefit type    | Select the type of tax allowance. The following values are applicable to land tax allowances: **Exemption from tax**, **Tax base reduction**, **Reduction of tax rate**, **Reduction of tax amount**, and **Non-taxable area share**. |
    | Name            | Enter the name of the tax allowance.                                                                                                                                                                                                  |
    | Allowance value | Define the tax allowance value, depending on type of tax allowance that you selected in the **Benefit type** field:                                                                                                                   |

    -   **Exemption from tax:** Don't define the allowance value, because exemption
    from tax is always considered 100 percent, and the tax amount is 0 (zero).

    -   **Tax base reduction:** Define the amount, in the local currency, that is
    reducing the tax base amount for each asset.

    -   **Reduction of tax rate:** Define the percentage of the tax rate reduction.
    For example, if the tax rate is 10 percent, and the allowance value is 2
    percent, the reduced tax rate is 8 percent.

    -   **Reduction of tax amount:** Define the amount, in the local currency, that
    is reducing the calculated tax amount for each asset.

    -   **Non-taxable area share:** A value will be defined for each land asset in
    the fixed asset record.

### Assign tax allowances to a sales tax code as a reduction of the tax rate, a reduction of the tax amount, and a tax base reduction

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax
    relations**.

2.  Select the record for the sales tax code.

3.  In the **Allowance by reduction of rate**, **Allowance by reduction of
    tax**, and **Tax base reduction (p.2 art.387)** fields, select the
    appropriate tax allowances, if they are applicable to the sales tax code.

### Set up the territory code (OKTMO code) for the legal entity

1.  Go to **Organization administration \> Organizations \> Legal entities**.

2.  On the **Addresses** FastTab, select **More options \> Advanced**.

3.  On the **Manage addresses** page, on the **Registration ID** FastTab, create
    a line.

4.  In the **Registration type** field, select the registration type for
    OKATO/OKTMO.

    If the required registration type isn't listed, follow these steps to add it:

    1.  On the **Registration types** page (**Organization administration \> Global
    address book \> Registration types \> Registration types**), create a
    registration type.

    2.  On the **Registration categories** page (**Organization administration \>
    Global address book \> Registration types \> Registration categories**),
    assign the new registration type to the **RCOAD** registration category.

    3.  In the **Registration number** field, enter the OKTMO code for the legal
    entity's location.

### Set up tax authorities and related OKTMO codes

You must create the tax authorities that you're required to report assessed tax
declarations to.

1.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax authorities**.

2.  Create a tax authority.

3.  Set the **Authority** and **Name** fields.

4.  In the **STI code** field, enter the four-digit code for the tax authority.

5.  In the **Vendor account** field, select the vendor account party that is
    associated with the tax authority.

6.  Define the main OKTMO code for the tax authority on the vendor account:

    1.  In the record for the vendor account, on the **Addresses** FastTab,
        select **More options \> Advanced**.

    2.  On the **Registration ID** FastTab, add a line.

    3.  In the **Registration type** field, select the registration type for
        OKATO/OKTMO.

    4.  In the **Registration number** field, enter the OKTMO code.

        > [!NOTE]
        > For realty objects that are located at the organization's main
        location, the tax authority that assessed tax is reported to is defined
        as the tax authority that has the same OKTMO code as the legal entity.

### Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes

If the organization has land assets that are located in territories that differ
from the organization's main location, or if the organization has separate
subdivisions, you should set up company divisions.

1.  Go to **Organization administration \> Setup \> Separate divisions**.

2.  Create a company division.

3.  In the **Separate division ID** field, enter the identification code for the
    division.

4.  In the **Name** field, enter the name of the division.

5.  In the **Vendor account** field, select the vendor account number that is
    associated with the division. If there is no vendor account for the company
    division, create one.

6.  Define the OKTMO code for the company division on the vendor account:

    1.  In the vendor account record, on the **Addresses** FastTab, select
        **More options \> Advanced**.

    2.  On the **Registration ID** FastTab, add a line.

    3.  In the **Registration type** field, select the registration type for
        OKATO/OKTMO.

    4.  In the **Registration number** field, enter the OKTMO code.

7.  Repeat step 6 to define the KPP code for the separate division on the vendor
    account. In the **Registration type** field, select the registration type
    that is associated with the **KPP** registration category.

### Set up the organization's locations and assign them to company divisions

If the organization has land assets that are located in territories that differ
from the organization's main location, or if the organization has separate
subdivisions, you should set up organization locations and assign them to
company divisions.

1.  Go to **Fixed assets (Russia) \> Setup \> Location**.

2.  Select an existing location, or create a new location.

3.  On the **General** FastTab, in the **Separate division ID** field, select
    the company division that you created in the previous procedure.
    
    If the **Separate division ID** field is left blank, the location is the
    same as the location of the organization's head office.

    > [!NOTE]
    > For land assets that are located in territories that differ from
    the organization's main location, the tax authority that land tax is
    reported to is defined as the tax authority that has the same OKTMO code as
    the separate division that is associated with the land location. 
    >
    > For information about how to associate a fixed asset with a location, see the
    [Specify the location of the land](#specify-the-location-of-the-land)
    section later in this article.


### Set up territories for distributed land assets

If a land asset is distributed among several territories, it should be reported
under the appropriate OKTMO code. You should set up distribution territories,
assign an OKTMO code to each territory, and associate the OKTMO codes with tax
authorities.

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Distribution**.

2.  Create a territory.

3.  Set the **Territory** and **Name** fields.

4.  Select the sales tax code that is applied in the territory.

5.  In the **RCOAD** field, select the OKTMO code for the territory. Only OKTMO
    codes that are associated with the tax authority of the sales tax code are
    available for selection. If no OKTMO code is available, follow these steps:

    1.  Select the link for the sales tax code to open the **Sales tax codes**
        page.

    2.  Select the link for the settlement period code to open the **Sales tax
        settlement periods** page.

    3.  Select the link for the authority code to open the **Sales tax
        authorities** page.

    4.  On the Action Pane, select **RCOAD codes**.

    5.  Create lines for the OKTMO codes that are related to the tax authority.

> [!NOTE]
>  Alternatively, create all the OKTMO codes, and then assign a code to the tax authority on the **RCOAD codes** page (**Tax \> Setup \> Sales tax \> RCOAD codes**).

### Set up Fixed assets parameters for posting land tax

1.  Go to **Fixed assets (Russia) \> Setup \> Parameters**.

2.  On the **Number sequences** tab, for the **Assessed tax registers journal
    number** reference, select a number sequence for the tax register.

3.  On the **Tax reporting** tab, in the **Land tax** section, in the **Sales
    tax code** field, select the default sales tax code for land tax.

4.  In the **Compression** field, select the level of compression for land tax
    transactions:

    -  **Tax** – A detailed ledger journal for land tax transactions will be
    created for each sales tax code.

    -  **Total** – A ledger journal for land tax transactions will be created as
    one line that has the default sales tax code.

5.  Close the page.

### Set up the journal for posting land tax

If land tax transactions will be automatically created based on calculated tax
registers, you should set up a journal.

1.  Go to **General ledger \> Journal setup \> Journal names**.

2.  Create a line.

3.  Set the **Name** and **Voucher series** fields.

4.  In the **Journal type** field, select **Land tax**.

### Set up a posting group for land tax postings

If land tax transactions will be automatically created based on calculated tax
registers, you should set up posting groups.

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Group of posting
    of taxes**.

2.  Create a line.

3.  In the **Ledger posting group** field, select a ledger posting group for
    land tax.

    If no ledger posting group is listed, create one. In the **Sales tax payable** field, enter the ledger account code for posting land tax.

1.  In the **Account for FA taxes** field, select a ledger account for the land
    tax expenses.

2.  Make sure that the **Sales tax payable** field is set to the ledger account
    code that you entered for the ledger posting group in step 3.

## Create a land asset and set up parameters for land tax calculation

Here is an overview of the steps for creating a land asset and setting up
parameters for land tax calculation:

1.  Create a land fixed asset and define parameters for land tax calculation

2.  [Specify the location of the land](#specify-the-location-of-the-land)

3.  [Specify the distribution for a land asset that is located in several
    territories](#specify-the-distribution-for-a-land-asset-that-is-located-in-several-territories)

4.  [Change the cadastral cost of land and specify the tax allowance
    history](#change-the-cadastral-cost-of-land-and-specify-the-tax-allowance-history)

5.  [Change the cadastral cost of a distributed land
    asset](#change-the-cadastral-cost-of-a-distributed-land-asset)

### Create a land fixed asset and define parameters for land tax calculation

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select an existing fixed asset, or create a new fixed asset.

3.  On the **General** FastTab, in the **Type** field, select **Ground area**.

4.  In the **Flag of ownership** field, select whether the fixed asset is owned,
    under operational management, leased, or owned by someone who is outside
    Russia.

5.  On the **Technical information** FastTab, set the **Category** and
    **Cadastral number** fields for the land asset.

6.  Set the **Start date of building** field if the land was acquired for
    housing construction. Special coefficients that depend on the building
    period will be applied to land assets of this type when land tax is
    calculated. If the construction period exceeded three years during the tax
    period, the land tax declaration will include two occurrences of Section 3:
    one occurrence for land tax before three years passed and one occurrence for
    land tax after three years passed.

7.  On the **Tax reporting** FastTab, in the **Land tax** section, in the **Tax
    base** field, enter the cadastral cost of the land.

8.  In the **Sales tax code** field, select the sales tax code for the assessed
    tax calculation.

9.  If you partially own the fixed asset, in the **Owned share numerator** and
    **Owned share denominator** fields, define your ownership share as a simple
    fraction.

### Specify the location of the land

By default, the assumption is that land assets are located at the organization's
location and reported to the tax authority in the legal entity's territory. (The
OKTMO code of the tax authority matches the OKTMO code of the legal entity, and
land assets are reported under the same OKTMO code.)

If the organization has land assets that are located in different territories
and registered in different tax authorities, you must specify the location of
the land asset.

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the land asset.

3.  On the Action Pane, on the **Fixed asset** tab, in the **History** group,
    select **Transfer**.

4.  Create a line.

5.  Set the **Date** and **New location** fields.

### Specify the distribution for a land asset that is located in several territories

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the land asset.

3.  On the Action Pane, on the **Fixed asset** tab, in the **Distribution**
    group, select **Distribution**.

4.  Create a line.

5.  In the **Location** field, select a territory.

6.  Review the values in the **RCOAD** and **Sales tax code** fields. These
    values are automatically entered from the territory location record.

7.  In the **Tax base** field, specify the cadastral cost of the land in the
    specified territory.

8.  If you partially own the fixed asset, in the **Owned share numerator** and
    **Owned share denominator** fields, define your ownership share in the
    specified territory as a simple fraction.

    > [!NOTE]
    > When the line for the change in cadastral value is created, the **Tax base** and **Sales tax** fields in the fixed asset record can no longer be edited.

### Change the cadastral cost of land and specify the tax allowance history

The cadastral cost of a land asset might change because of a change in
qualitative and quantitative characteristics. Follow these steps to record a
change in cadastral value.

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the land asset.

3.  On the Action Pane, on the **Fixed asset** tab, in the **History** group,
    select **Tax reporting data**.

4.  Create a line.

5.  In the **Period** field, specify the month when the cadastral value is
    changing.

6.  In the **Tax base** field, specify the new cadastral value of the land. Also
    specify any other values that have changed: **Category**, **Cadastral
    number**, **Owned share numerator**, or **Owned share denominator**.

    > [!NOTE]
    > If this change is the first change in cadastral value, you must also create a line for the previous values that were originally entered in the fixed asset record.
    >  
    > When the line for the change in cadastral value is created, corresponding fields in the fixed asset record can no longer be edited. They show the actual values from the tax reporting data history record.
    >  
    > Use the **History of tax reporting data** page to define the history of tax allowance changes.

7.  In the **Land tax exemption (art 387)** field, specify the code for the tax
    allowance as an exemption from tax in accordance with federal law.
    Alternatively, in the **Land tax exemption (art 395)** field, specify the
    code for the tax allowance as an exemption from tax in accordance with
    regional law.

8.  Set the **Land tax allowance as non-taxable share** field, if it's
    applicable.

    When the values for tax allowances are added, corresponding fields in the fixed asset record show the actual values from the tax reporting data history record.

### Change the cadastral cost of a distributed land asset

If the cadastral cost of a land asset that is located in several territories
changes, follow these steps to specify the new cadastral cost in each territory.

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the land asset.

3.  On the Action Pane, on the **Fixed asset** tab, in the **Distribution**
    group, select **Distribution**.

4.  Select the line for the distribution, and then, on the Action Pane, select
    **History**.

5.  Create a line.

6.  In the **Period** field, specify the month when the cadastral value is
    changing.

7.  In the **Tax base** field, specify the new cadastral value of the land. Also
    specify any other values that have changed: **Owned share numerator** or
    **Owned share denominator**.

> [!NOTE] 
> If this change is the first change in cadastral value, you must also create a line for the previous values that were originally entered in the distribution record.
>
> When the line for the change in cadastral value is created, corresponding fields in the distribution record can no longer be edited. They show the actual values from the history record.

## Calculate land tax registers

After you've finished the setup, registered the acquisition of land assets, and
set up all land asset parameters for land tax calculation, you must calculate
land tax registers. The following tax registers are available:

-   **Land tax – ground areas** – This tax register calculates land tax for each
    land asset. For each land asset that is located in a territory that is
    specified by an OKTMO code, the register shows the following information:

    -   The land category and cadastral number.

-   **Design and building period** – The possible values are **3 years** and
        **More than 3 years**.

    -   The cadastral cost, and the owned share as a simple fraction.

    -   Tax allowance codes and amounts.

    -   The tax base in the specified territory and the tax rate.

    -   The ownership period and factor, if the land was acquired or sold during
        the period, or if the housing building period exceeded three years
        during the period.

    -   The cost change period and factor, if the cadastral cost changed during
        the period.

-   **Calculated advance payment/Tax** – If the tax register is calculated
        for the first quarter, second quarter, or third quarter, the tax advance
        amount before tax allowances are applied as a reduction of the tax rate
        or a reduction of tax amount. If the tax register is calculated for the
        year, the land tax amount before tax allowances are applied as a
        reduction of the tax rate or a reduction of the tax amount.

-   **Advance payment amount/Tax amount** – If the tax register is
        calculated for the first quarter, second quarter, or third quarter, the
        final tax advance amount. If the tax register is calculated for the
        year, the final land tax amount.

-   **Land tax** – This tax register calculates total land tax amounts for each
    sales tax code and OKTMO code.

To calculate and approve land tax registers, follow these steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select **New**.

3.  In the **Type of tax** field, either select **Land tax** to create a journal
    only for land tax registers, or leave the field blank to create a journal
    for all the asset's taxes (assessed tax, land tax, and transport tax).

4.  In the **Period types** field, select one of the following values:

    -   **Quarter** – Generate a journal for the calculation of land tax advance
        payments.

    -   **Years** – Generate a journal for the annual land tax calculation.

5.  In the **Period number** field, if you selected **Quarter** in the **Period
    types** field, enter the number of the quarter. If you selected **Years**,
    enter **1**.

6.  In the **Years** fields, enter the reporting year in *YYYY* format.

7.  Select **OK** to create the journal.

8.  Select **Lines** to create lines in the periodic register journal.

9.  You receive a message that states, "Register journal has not been created
    yet. Do you want create it?" Select **Yes**.

10. Review the tax registers that are created. For land tax, the following
    registers are created: **Land tax – ground areas** and **Land tax**.

11. To calculate a specific tax register in the journal, select the register,
    and then select **Calculate current**. To calculate all tax registers in the
    journal, select **Calculate all**.

12. Select **OK**.

13. Select a tax register, and then select **Register lines** to review the
    calculated lines.

14. Select **Print** to print the tax register lines in Microsoft Excel.

15. Select **Reset status** to reset the status of the calculated register to
    **Not calculated**.

16. After you've finished reviewing the data in the tax registers, select the
    **Approved** check box to approve each register.

17. In the **Worker** field, view or change the code for the employee who
    approved the register.

### Create and calculate corrective tax registers

If you've corrected any land asset data for the previous periods, you should
create corrective tax registers to reflect the corrected land tax amounts.

To create corrective registers, follow these steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select the approved journal for the period that must be corrected.

3.  Select **Correction \> Corrections to current journal**.

4.  Select **New**.

5.  In the **Type of tax** field, either select **Land tax** if you must correct
    only land tax registers, or leave the field blank if you must correct all
    the asset's tax registers.

6.  Make sure that the **Period types**, **Period number**, and **Years** fields
    are set to values that are appropriate for the period of the register that
    you're correcting.

7.  Select **OK**.

8.  Create tax register lines, and calculate and approve the tax registers as
    described in the previous procedure.

## Generate a land tax declaration

### Set up the system to generate a land tax declaration

1.  In [Microsoft Dynamics Lifecycle Services
    (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download
    the latest versions of the Electronic reporting (ER) configurations for the
    land tax declaration.

    For example, to generate the land tax declaration for the year 2018 reporting period, download the latest version of the following configurations:

    -   Assets declarations model

    -   Land tax declaration model mapping

    -   Land tax advance calculation format 5.06

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

2.  You can upload Data management package settings to work with the assessed
    tax declaration. Follow these steps:

    -   In the LCS Shared asset library, select **Data package** as the asset
        type.

    -   Download the package that is named **RU Land tax declaration v5.06
        (2018)**. The file that is downloaded is named **RU Land tax declaration
        v5.06 (2018).zip**.

    -   In the **Data
        management** workspace, select **Import**.

    -   In the **Job details** section, set the following values:

        -   Enter a name for the job.

        -   In the **Source data format** field, select **Package**.

    -   Select **Upload** next to the **Upload data file** field, and then
        select the **RU Land tax declaration v5.06 (2018).zip** file that you
        downloaded earlier.

    -   After the data entities are uploaded, select **Import**.

3.  Go to **Tax \> Setup \> Electronic messages \> Electronic message
    processing**, and validate the electronic message processing that is
    imported. (Most of the data that is imported is presented in the Russian
    language.)

    | Processing       | Processing code  | Name                               |
    |----------------------|----------------------|----------------------------------------|
    | Land tax declaration | ЗемНалог 5.06 (2018) | Декларация по земельному налогу (2018) |

4.  Set up the ER format that is run when accounting reporting is generated in
    electronic format:

5.  Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.

6.  Select the **Generate ZEMND 5.06** action, and then select **Edit**.

7.  Set the **Show dialog** option to **Yes**.

8.  In the **Format mapping** field, select the **Land tax declaration format
    5.06** ER configuration that you downloaded earlier.

### Generate a land tax declaration

Before you can generate the land tax declaration for a tax year, you must
calculate the land tax register for the same year, and for the first quarter,
second quarter, and third quarter of the same year. The advance payment amount
for land tax that is exported in the land tax declaration is taken from the tax
registers that were calculated for the first quarter, second quarter, and third
quarter.

1.  Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic
    messages**.

2.  Select the report format to generate.

    For example, to generate a land tax declaration in XML format for the year
    2018, select **ЗемНалог 5.06 (2018)**.

3.  On the **Messages** FastTab, select **New**.

4.  In the **Run processing** dialog box, select **OK**.

5.  Select the message line that is created, and enter a description.

6.  Enter a start date and end date for the report.

    To generate a land tax declaration, enter the year period. For example, for
    the year 2019, enter **01.01.2019** in the **From date** field and
    **31.12.2019** in the **To date** field.

7.  Optional: For a corrective declaration, on the **Message additional fields**
    FastTab, on the line for the **CorrectionNumber** field, in the **Field
    value** field, enter the number of the correction.

8.  On the **Messages** FastTab, select **Update status**.

9.  In the **Run processing** dialog box, select **OK**.

10. Validate that the message status has been changed to **Ready to generate**.

11. On the **Messages** FastTab, select **Generate report**.

12. In the **Electronic reporting parameters** dialog box, on the **Parameter**
    FastTab, set the following values.

    | Field                                                        | Description                                                                                                                             |
    |------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
    | At place of                                                      | Select the place where the declaration is submitted: **Ground location** or **Registration of the largest taxpayer**.                       |
    | Correction number                                                | Enter the number of the correction if you didn't specify it in step 7.                                                                      |
    | Signatory type                                                   | Select the person who signs the accounting reporting: **Taxpayer** or **Representative**.                                                   |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory.                                                                                                       |
    | Representative company                                           | If you selected **Representative** as the signatory type, and if the representative is an organization, enter the name of the organization. |
    | Representative document                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority.                  |

13. On the first **Records to include** FastTab, apply a filter for separate
    divisions, if this type of filter is applicable. In this case, declarations
    will be generated only for the selected separate divisions.

14. On the second **Records to include** FastTab, apply a filter for tax
    authorities, if this type of filter is applicable. In this case,
    declarations will be generated only for the selected tax authorities.

15. Select **OK**.

    When the report is generated, the status of the message is changed to **Generated**. If an error occurs during generation, the status is changed to **Technical error**.

16.  On the **Action log** FastTab, review all user actions for the current
    message.

17.  To review the report that is generated, select the **Attachments** button
    (the paper clip symbol) in the upper-right corner of the page, and then
    select **Open** to view the file.

You must also manually upload the generated file to the special third-party
software for data preview, data updates, and transfer of the land tax
declaration files to the tax authorities through the communication channels.

## Create and post land tax ledger transactions

After you've calculated and approved tax registers, and generated a land tax
declaration, you can create transactions for land tax accruals. Following these
steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select the journal, and then select **Ledger journal \> Land tax**.

3.  Select **New**.

4.  In the **Name** field, select the name of the land tax journal.

5.  Select **Lines** to view the journal lines that have land tax accrual
    transactions that were created based on the tax register data and the
    settings of Fixed assets parameters.

6.  Validate and post the journal.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
