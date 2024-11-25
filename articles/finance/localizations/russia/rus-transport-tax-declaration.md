---
title: Transport tax declaration (Russia)
description: Learn about the Transport tax declaration for Russia, including outlines on setting up transport taxes and setting up tax allowances.
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

# Transport tax declaration (Russia)

[!include [banner](../../includes/banner.md)]

According to the tax code of the Russian Federation, vehicles are subject to
transport tax.

The tax period for transport tax is one year. At the end of the tax period, a
company must report a transport tax declaration.

The transport tax declaration should be submitted to the tax authority where the
vehicle is located. In this case, code **260** should be entered for the **at
place of** attribute. However, the greatest taxpayers can submit declarations to
the tax authority where the organization is registered as a greatest taxpayer.
In this case, code **216** should be entered for the **at place of** attribute.

The tax base for the calculation of transport tax is one of the following
criteria:

-   Engine power, measured in horsepower

-   Jet thrust, measured in kilograms of the power

-   Gross tonnage, measured in vessel tons

The transport tax calculation includes all fixed assets of the **Vehicle** asset
type for which the fixed asset record contains a transport tax code. If the
fixed asset is written off or sold during the accounting period, the tax
calculation uses data for the month when legal registration and removal from the
register occurred.

This article explains how to perform the following tasks:

1.  [Set up transport tax](#set-up-transport-tax)

2.  [Create a vehicle and set up parameters for transport tax
    calculation](#create-a-vehicle-and-set-up-parameters-for-transport-tax-calculation)

3.  [Calculate transport tax registers](#calculate-transport-tax-registers)

4.  [Generate a transport tax
    declaration](#generate-a-transport-tax-declaration)

5.  [Create and post transport tax ledger
    transactions](#create-and-post-transport-tax-ledger-transactions)

## Set up transport tax

Here is an overview of the steps for setting up transport tax:

1.  [Set up transport tax codes and
    rates](#set-up-transport-tax-codes-and-rates)

2.  [Set up budget revenue codes for transport
    tax](#set-up-budget-revenue-codes-for-transport-tax)

3.  [Assign a budget revenue code to a sales tax
    code](#assign-a-budget-revenue-code-to-a-sales-tax-code)

4.  [Set up tax allowances](#set-up-tax-allowances)

5.  [Assign tax allowances to a sales tax code as a reduction of the tax rate
   -and-a-reduction-of-the-tax-amount](#assign-tax-allowances-to-a-sales-tax-code-as-a-reduction-of-the-tax-rate-and-a-reduction-of-the tax amount)

6.  [Set up transport tax increasing factor groups and
    values](#set-up-transport-tax-increasing-factor-groups-and-values)

7.  [Set up the territory code (OKTMO code) for the legal
    entity](#set-up-the-territory-code-oktmo-code-for-the-legal-entity)

8.  [Set up tax authorities and related OKTMO
    codes](#set-up-tax-authorities-and-related-oktmo-codes)

9.  [Optional: Set up company divisions, their registration reason codes (KPP),
    and their OKTMO
    codes](#optional-set-up-company-divisions-their-registration-reason-codes-kpp-and-their-oktmo-codes)

10. [Set up the organization's locations and assign them to company
    divisions](#set-up-the-organizations-locations-and-assign-them-to-company-divisions)

11. [Set up Fixed assets parameters for posting transport
    tax](#set-up-fixed-assets-parameters-for-posting-transport-tax)

12. [Set up the journal for posting transport
    tax](#set-up-the-journal-for-posting-transport-tax)

13. [Set up a posting group for transport tax
    postings](#set-up-a-posting-group-for-transport-tax-postings)

### Set up transport tax codes and rates

1.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.

2.  Create a sales tax code.

3.  In the **Type of tax** field, select **Transport tax**.

4.  Specify the settlement period and the ledger posting group.

5.  On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code**
    group, select **Values** to open the **Sales tax code values** page.

6.  The transport tax rate depends on the type and power of the vehicle. In the
    **Lower Limit** and **Upper Limit** fields, enter lower and upper limits for
    the power interval. Then, in the **Value** field, specify the tax rate for
    the specified interval.

7.  In some cases, the transport tax rate also depends on the actual useful life
    of the vehicle. To define the tax rate so that it's based on the vehicle's
    lifetime, on the Action Pane, on the **Transport tax** tab, in the
    **Transport tax** group, select **By lifetime**. In the **Minimum limit**
    and **Maximum limit** fields, enter the lower and upper limits for the
    lifetime. Then, in the **Tax value** field, specify the tax rate for the
    specified interval.

### Set up budget revenue codes for transport tax

1.  Go to **Cash and bank management \> Setup \> Payment order setup \> Budget
    revenue classification**.

2.  Create a budget revenue code for transport tax.

### Assign a budget revenue code to a sales tax code

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax
    relations**.

2.  Create a record.

3.  In the **Type of tax** field, select **Transport tax**.

4.  In the **Code** field, select the sales tax code for the transport tax.

5.  In the **Budget revenue code** field, select the budget revenue code that
    corresponds to the selected sales tax code.

### Set up tax allowances

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Tax allowances**.

2.  Create a record.

3.  Set the following values for the tax allowance.

| **Field**                                          | **Description**                                                                                                                                                                                           |
|----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Privilege**                                      | Enter the tax allowance code.                                                                                                                                                                             |
| **Type of tax**                                    | Select **Transport tax**.                                                                                                                                                                                 |
| **Benefit type**                                   | Select the type of tax allowance. The following values are applicable to transport tax allowances: **Exemption from tax**, **Reduction of tax rate**, **Reduction of tax amount**, and **Tax deduction**. |
| **Name**                                           | Enter the name of the tax allowance.                                                                                                                                                                      |
| **Allowance value**                                | Define the tax allowance value, depending on type of tax allowance that you selected in the **Benefit type** field:                                                                                       |
| **Article number**, **Clause**, and **Sub-clause** | Define the article number, clause, and sub-clause of the law in accordance with which the corresponding tax allowance is granted.                                                                         |

-   **Exemption from tax:** Don't define the allowance value, because exemption
    from tax is always considered 100 percent, and the tax amount is 0 (zero).

-   **Reduction of tax rate:** Define the percentage of the tax rate reduction.
    For example, if the tax rate is 10 percent, and the allowance value is 2
    percent, the reduced tax rate is 8 percent.

-   **Reduction of tax amount:** Define the amount, in the local currency, that
    is reducing the calculated tax amount for each asset.

### Assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax
    relations**.

2.  Select the record for the sales tax code.

3.  In the **Allowance by reduction of rate** and **Allowance by reduction of
    tax** fields, select the appropriate tax allowances, if they are applicable
    to the sales tax code.

### Set up transport tax increasing factor groups and values

The amount of transport tax should be increased for expensive vehicle models
that are defined by the Ministry of Production and Trade in an informational
letter and annually reviewed. The coefficient that must be considered depends on
both the number of years that have passed since the vehicle's year of
manufacture and the cost of vehicle. For example, for a vehicle that costs
between 3 million and 5 million rubles, if less than one year has passed since
its year of manufacture, the increasing coefficient is 1.5.

1.  Go to **Fixed asset (Russia) \> Setup \> Tax reporting \> Transport tax
    increasing factor groups**.

2.  Create a group.

3.  On the **Transport tax increasing factor values** FastTab, define the
    following increasing factor values.

| **Field**      | **Description**                                                                          |
|----------------|------------------------------------------------------------------------------------------|
| From date      | Enter the date when the factor value starts to apply.                                    |
| Upper lifetime | Enter the upper limit of the lifetime from manufacture that the factor value applies to. |
| Factor         | Enter the increasing factor.                                                             |

### Set up the territory code (OKTMO code) for the legal entity

1.  Go to **Organization administration \> Organizations \> Legal entities**.

2.  On the **Addresses** FastTab, select **More options \> Advanced**.

3.  On the **Manage addresses** page, on the **Registration ID** FastTab, create
    a line.

4.  In the **Registration type** field, select the registration type for
    OKATO/OKTMO.

>   If the required registration type isn't listed, follow these steps to add
>   it:

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

        **Note:** For realty objects that are located at the organization's main
        location, the tax authority that assessed tax is reported to is defined
        as the tax authority that has the same OKTMO code as the legal entity.

### Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes

If the organization has realty objects that are located in territories that
differ from the organization's main location, or if the organization has
separate subdivisions, you should set up company divisions.

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

If the organization has realty objects that are located in territories that
differ from the organization's main location, or if the organization has
separate subdivisions, you should set up organization locations and assign them
to company divisions.

1.  Go to **Fixed assets (Russia) \> Setup \> Location**.

2.  Select an existing location, or create a new location.

3.  On the **General** FastTab, in the **Separate division ID** field, select
    the company division that you created in the previous procedure.

    **Note:** For vehicles that are registered in territories that differ from
    the organization's main location, the tax authority that transport tax is
    reported to is defined as the tax authority that has the same OKTMO code as
    the separate division that is associated with the vehicle location. For
    information about how to associate a fixed asset with a location, see the
    [Specify the location of the vehicle](#specify-the-location-of-the-vehicle)
    section later in this article.

    If the **Separate division ID** field is left blank, the location is the
    same as the location of the organization's head office.

### Set up Fixed assets parameters for posting transport tax

1.  Go to **Fixed assets (Russia) \> Setup \> Parameters**.

2.  On the **Number sequences** tab, for the **Assessed tax registers journal
    number** reference, select a number sequence for the tax register.

3.  On the **Tax reporting** tab, in the **Transport tax** section, in the
    **Sales tax code** field, select the default sales tax code for transport
    tax.

4.  In the **Compression** field, select the level of compression for transport
    tax transactions:

-   **Tax** – A detailed ledger journal for transport tax transactions will be
    created for each sales tax code.

-   **Total** – A ledger journal for transport tax transactions will be created
    as one line that has the default sales tax code.

1.  Close the page.

### Set up the journal for posting transport tax

If transport tax transactions will be automatically created based on calculated
tax registers, you should set up a journal.

1.  Go to **General ledger \> Journal setup \> Journal names**.

2.  Create a line.

3.  Set the **Name** and **Voucher series** fields.

4.  In the **Journal type** field, select **Transport tax**.

### Set up a posting group for transport tax postings

If transport tax transactions will be automatically created based on calculated
tax registers, you should set up posting groups.

1.  Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Group of posting
    of taxes**.

2.  Create a line.

3.  In the **Ledger posting group** field, select a ledger posting group for
    transport tax.

>   If no ledger posting group is listed, create one. In the **Sales tax
>   payable** field, enter the ledger account code for posting transport tax.

1.  In the **Account for FA taxes** field, select a ledger account for the
    transport tax expenses.

2.  Make sure that the **Sales tax payable** field is set to the ledger account
    code that you entered for the ledger posting group in step 3.

## Create a vehicle and set up parameters for transport tax calculation

Here is an overview of the steps for creating a vehicle and setting up
parameters for transport tax calculation:

1.  [Create a vehicle fixed asset and define parameters for transport tax
    calculation](#create-a-vehicle-fixed-asset-and-define-parameters-for-transport-tax-calculation)

2.  [Specify the location of the vehicle](#specify-the-location-of-the-vehicle)

3.  [Specify a tax allowance as an exemption from
    tax](#specify-a-tax-allowance-as-an-exemption-from-tax)

### Create a vehicle fixed asset and define parameters for transport tax calculation

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select an existing fixed asset, or create a new fixed asset.

3.  On the **General** FastTab, in the **Type** field, select **Vehicle**.

4.  In the **Flag of ownership** field, select whether the fixed asset is owned,
    under operational management, leased, or owned by someone who is outside
    Russia.

5.  On the **Technical information** FastTab, in the **Vehicle** section, set
    the **Vehicle type**, **Model**, **Registration number**, and **Emission
    class** fields.

>   **Note:** You create vehicle types on the **Vehicle types** page (**Fixed
>   assets (Russia) \> Setup \> Vehicle \> Vehicle types**). You create vehicle
>   models on the **Vehicle models** page (**Fixed assets (Russia) \> Setup \>
>   Vehicle \> Vehicle models**).

1.  In the **Useful life** section, in the **Output year** field, specify the
    year of manufacture.

2.  In the **Government registration** section, set the **Date of the
    registration** and **Removal from the register date** fields.

3.  On the **Tax reporting** FastTab, in the **Transport tax** section, in the
    field **Tax base** field, specify the vehicle power. In the **Unit** field,
    specify the unit of measure for the vehicle power.

4.  If you partially own the fixed asset, in the **Owned share numerator** and
    **Owned share denominator** fields, define your ownership share as a simple
    fraction.

5.  In the **Sales tax code** field, select the sales tax code for the assessed
    tax calculation.

6.  Set the **Increasing factor group** field.

7.  In the **Deduction** field, specify the tax deduction code. In the **Tax
    deduction amount** field, specify the deduction amount.

### Specify the location of the vehicle

By default, the assumption is that vehicles are located at the organization's
location and reported to the tax authority in the legal entity's territory. (The
OKTMO code of the tax authority matches the OKTMO code of the legal entity, and
realty objects are reported under the same OKTMO code.)

If the organization has vehicles that are located in different territories and
registered in different tax authorities, you must specify the location of the
vehicle.

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the vehicle.

3.  On the Action Pane, on the **Fixed asset** tab, in the **History** group,
    select **Transfer**.

4.  Create a line.

5.  Set the **Date** and **New location** fields.

### Specify a tax allowance as an exemption from tax 

1.  Go to **Fixed assets (Russia) \> Common \> Fixed assets**.

2.  Select the line for the vehicle.

3.  On the Action Pane, on the **Fixed asset** tab, in the **History** group,
    select **Tax reporting data**.

4.  Create a line.

5.  In the **Period** field, specify the month when a tax allowance as an
    exemption from tax applies. In the **Exemption from tax** field, select the
    code for the tax allowance as an exemption from tax.

## Calculate transport tax registers

After you've finished the setup, registered the acquisition of the vehicle, and
set up all vehicle parameters for transport tax calculation, you must calculate
transport tax registers. The following tax registers are available:

-   **Vehicle - tax calculation** – This tax register calculates transport tax
    for each vehicle. It shows the following information:

    -   The vehicle type, serial number, model, and registration number.

    -   The dates of vehicle registration and removal from the register.

    -   The tax base and the units of measure for the tax base.

    -   The useful lifetime, in years, after the year of manufacture, and the
        output year.

    -   The owned share as an indication that the vehicle is partially owned.

    -   **Factor Kp** – The increasing factor for expensive vehicles.

    -   The ownership factor if the vehicle was acquired or sold during the
        period. This factor is the ratio of the ownership period to the number
        of calendar months in the period.

    -   **Calculated advance payment / Tax** – If the tax register is calculated
        for the first quarter, second quarter, or third quarter, the tax advance
        amount before tax allowances are applied. If the tax register is
        calculated for the year, the transport tax amount before tax allowances
        are applied.

    -   **Exemption from tax** – The code for the tax allowance as an exemption
        from tax.

    -   The amount of the tax allowance as an exemption from tax.

    -   **Grace period** – The number of months when there is no tax exemption
        allowance.

    -   **Allowance factor** – The ratio of the grace period to the number of
        calendar months in the tax period.

    -   **Privilege** – The code for the tax allowance as a reduction of the
        rate or a reduction of tax.

    -   **Tax allowance amount** – The amount of the tax allowance as a
        reduction of the tax rate or a reduction of the tax amount.

    -   **Deduction** – The code for the tax deduction.

    -   **Tax allowance amount** – The amount of the tax deduction.

    -   The transport tax rate, budget revenue code, separate division ID, and
        location of the vehicle, and the tax authority that the tax for the
        vehicle will be reported to.

-   **Transport tax** – This tax register calculates total transport tax amounts
    for each sales tax code and OKTMO code.

>   To calculate and approve transport tax registers, follow these steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select **New**.

3.  In the **Type of tax** field, either select **Transport tax** to create a
    journal only for transport tax registers, or leave the field blank to create
    a journal for all the asset's taxes (assessed tax, land tax, and transport
    tax).

4.  In the **Period types** field, select one of the following values:

    -   **Quarter** – Generate a journal for the calculation of transport tax
        advance payments.

    -   **Years** – Generate a journal for the annual transport tax calculation.

5.  In the **Period number** field, if you selected **Quarter** in the **Period
    types** field, enter the number of the quarter. If you selected **Years**,
    enter **1**.

6.  In the **Years** fields, enter the reporting year in *YYYY* format.

7.  Select **OK** to create the journal.

8.  Select **Lines** to create lines in the periodic register journal.

9.  You receive a message that states, "Register journal has not been created
    yet. Do you want create it?" Select **Yes**.

10. Review the tax registers that are created. For transport tax, the following
    registers are created: **Vehicle – tax calculation** and **Transport tax**.

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

If you've corrected any vehicle data for the previous periods, you should create
corrective tax registers to reflect the corrected transport tax amounts.

To create corrective registers, follow these steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select the approved journal for the period that must be corrected.

3.  Select **Correction \> Corrections to current journal**.

4.  Select **New**.

5.  In the **Type of tax** field, either select **Transport tax** if you must
    correct only transport tax registers, or leave the field blank if you must
    correct all the asset's tax registers.

6.  Make sure that the **Period types**, **Period number**, and **Years** fields
    are set to values that are appropriate for the period of the register that
    you're correcting.

7.  Select **OK**.

8.  Create tax register lines, and calculate and approve the tax registers as
    described in the previous procedure.

## Generate a transport tax declaration

### Set up the system to generate a transport tax declaration

1.  In [Microsoft Dynamics Lifecycle Services
    (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download
    the latest versions of the Electronic reporting (ER) configurations for the
    assessed tax declaration.

>   For example, to generate the transport tax declaration for the year 2019
>   reporting period, download the latest version of the following
>   configurations:

-   Assets declarations model

-   Transport tax declaration model mapping

-   Transport tax declaration format 5.05

>   For more information, see [Download Electronic reporting configurations from
>   Lifecycle
>   Services](/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

1.  You can upload Data management package settings to work with the transport
    tax declaration. Follow these steps:

    -   In the LCS Shared asset library, select **Data package** as the asset
        type.

    -   Download the package that is named **RU Transport tax declaration v5.05
        (2019)**. The file that is downloaded is named **RU Transport tax
        declaration v5.05 (2019).zip**.

    -   In the **Data
        management** workspace, select **Import**.

    -   In the **Job details** section, set the following values:

        -   Enter a name for the job.

        -   In the **Source data format** field, select **Package**.

    -   Select **Upload** next to the **Upload data file** field, and then
        select the **RU Transport tax declaration v5.05 (2019).zip** file that
        you downloaded earlier.

    -   After the data entities are uploaded, select **Import**.

2.  Go to **Tax \> Setup \> Electronic messages \> Electronic message
    processing**, and validate the electronic message processing that is
    imported. (Most of the data that is imported is presented in the Russian
    language.)

| **Processing**            | **Processing code**  | **Name**                                  |
|---------------------------|----------------------|-------------------------------------------|
| Transport tax declaration | ТрансНал 5.05 (2019) | Декларация по транспортному налогу (2019) |

3.  Set up the ER format that is run when accounting reporting is generated in
    electronic format:

4.  Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.

5.  Select the **Generate TRAND 5.05** action, and then select **Edit**.

6.  Set the **Show dialog** option to **Yes**.

7.  In the **Format mapping** field, select the **Transport tax declaration
    format 5.05** ER configuration that you downloaded earlier.

8.  Set up the economic activity type code (OKVED):

9.  Go to **Tax \> Setup \> Electronic messages \> Additional fields**.

10. Select the **EconomicActivityTypeCode** record.

11. On the **Value** FastTab, select **Add**, and then enter the value of the
    code.

### Generate a transport tax declaration

Before you can generate the transport tax declaration for a tax year, you must
calculate the transport tax registers for the same year, and for the first
quarter, second quarter, and third quarter of the same year. The advance payment
amount for transport tax that is exported in the transport tax declaration is
taken from the tax registers that were calculated for the first quarter, second
quarter, and third quarter.

1.  Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic
    messages**.

2.  Select the report format to generate.

    For example, to generate a transport tax declaration in XML format for the
    year 2019, select **ТрансНал 5.05 (2019)**.

3.  On the **Messages** FastTab, select **New**.

4.  In the **Run processing** dialog box, select **OK**.

5.  Select the message line that is created, and enter a description.

6.  Enter a start date and end date for the report.

    To generate a transport tax declaration, enter the year period. For example,
    for the year 2019, enter **01.01.2019** in the **From date** field and
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

| **Field**                                                        | **Description**                                                                                                                             |
|------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| At place of                                                      | Select the place where the declaration is submitted: **Vehicle location** or **Registration of the largest taxpayer**.                      |
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

>   When the report is generated, the status of the message is changed to
>   **Generated**. If an error occurs during generation, the status is changed
>   to **Technical error**.

1.  On the **Action log** FastTab, review all user actions for the current
    message.

2.  To review the report that is generated, select the **Attachments** button
    (the paper clip symbol) in the upper-right corner of the page, and then
    select **Open** to view the file.

You must also manually upload the generated file to the special third-party
software for data preview, data updates, and transfer of the transport tax
declaration files to the tax authorities through the communication channels.

## Create and post transport tax ledger transactions

After you've calculated and approved tax registers, and generated a transport
tax declaration, you can create transactions for transport tax accruals.
Following these steps.

1.  Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.

2.  Select the journal, and then select **Ledger journal \> Transport tax**.

3.  Select **New**.

4.  In the **Name** field, select the name of the transport tax journal.

5.  Select **Lines** to view the journal lines that have transport tax accrual
    transactions that were created based on the tax register data and the
    settings of Fixed assets parameters.

6.  Validate and post the journal.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
