---
title: Transport tax declaration (Russia)
description: Learn how to work with the Transport tax declaration for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/12/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-01-04
---

# Transport tax declaration (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to work with the Transport tax declaration for Russia in Microsoft Dynamics 365 Finance.

According to the tax code of the Russian Federation, vehicles are subject to transport tax.

The tax period for transport tax is one year. At the end of the tax period, a company must report a transport tax declaration.

The transport tax declaration should be submitted to the tax authority where the vehicle is located. In this case, code **260** should be entered for the **at place of** attribute. However, the greatest taxpayers can submit declarations to the tax authority where the organization is registered as a greatest taxpayer. In this case, code **216** should be entered for the **at place of** attribute.

The tax base for the calculation of transport tax is one of the following criteria:

-   Engine power, measured in horsepower
-   Jet thrust, measured in kilograms of the power
-   Gross tonnage, measured in vessel tons

The transport tax calculation includes all fixed assets of the **Vehicle** asset type for which the fixed asset record contains a transport tax code. If the fixed asset is written off or sold during the accounting period, the tax calculation uses data for the month when legal registration and removal from the register occurred.

This article explains how to perform the following tasks:

1. [Set up transport tax](#set-up-transport-tax)
1. [Create a vehicle and set up parameters for transport tax calculation](#create-a-vehicle-and-set-up-parameters-for-transport-tax-calculation)
1. [Calculate transport tax registers](#calculate-transport-tax-registers)
1. [Generate a transport tax declaration](#generate-a-transport-tax-declaration)
1. [Create and post transport tax ledger transactions](#create-and-post-transport-tax-ledger-transactions)

## Set up transport tax

Here is an overview of the steps for setting up transport tax:

1. [Set up transport tax codes and rates](#set-up-transport-tax-codes-and-rates)
1. [Set up budget revenue codes for transport tax](#set-up-budget-revenue-codes-for-transport-tax)
1. [Assign a budget revenue code to a sales tax code](#assign-a-budget-revenue-code-to-a-sales-tax-code)
1. [Set up tax allowances](#set-up-tax-allowances)
1. [Assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount](#assign-tax-allowances-to-a-sales-tax-code-as-a-reduction-of-the-tax-rate-and-a-reduction-of-the-tax-amount)
1. [Set up transport tax increasing factor groups and values](#set-up-transport-tax-increasing-factor-groups-and-values)
1. [Set up the territory code (OKTMO code) for the legal entity](#set-up-the-territory-code-oktmo-code-for-the-legal-entity)
1. [Set up tax authorities and related OKTMO codes](#set-up-tax-authorities-and-related-oktmo-codes)
1. [Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes](#optional-set-up-company-divisions-their-registration-reason-codes-kpp-and-their-oktmo-codes)
1. [Set up the organization's locations and assign them to company divisions](#set-up-the-organizations-locations-and-assign-them-to-company-divisions)
1. [Set up Fixed assets parameters for posting transport tax](#set-up-fixed-assets-parameters-for-posting-transport-tax)
1. [Set up the journal for posting transport tax](#set-up-the-journal-for-posting-transport-tax)
1. [Set up a posting group for transport tax postings](#set-up-a-posting-group-for-transport-tax-postings)

### Set up transport tax codes and rates

To set up transport tax codes and rates, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Create a sales tax code.
1. In the **Type of tax** field, select **Transport tax**.
1. Specify the settlement period and the ledger posting group.
1. On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **Values** to open the **Sales tax code values** page.
1. The transport tax rate depends on the type and power of the vehicle. In the **Lower Limit** and **Upper Limit** fields, enter lower and upper limits for the power interval. Then, in the **Value** field, specify the tax rate for the specified interval.
1. In some cases, the transport tax rate also depends on the actual useful life of the vehicle. To define the tax rate so that it's based on the vehicle's lifetime, on the Action Pane, on the **Transport tax** tab, in the **Transport tax** group, select **By lifetime**. In the **Minimum limit** and **Maximum limit** fields, enter the lower and upper limits for the lifetime. Then, in the **Tax value** field, specify the tax rate for the specified interval.

### Set up budget revenue codes for transport tax

To set up budget revenue codes for transport tax, follow these steps.

1. In Dynamics 365 Finance, go to **Cash and bank management \> Setup \> Payment order setup \> Budget revenue classification**.
1. Create a budget revenue code for transport tax.

### Assign a budget revenue code to a sales tax code

To assign a budget revenue code to a sales tax code, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax relations**.
1. Create a record.
1. In the **Type of tax** field, select **Transport tax**.
1. In the **Code** field, select the sales tax code for the transport tax.
1. In the **Budget revenue code** field, select the budget revenue code that corresponds to the selected sales tax code.

### Set up tax allowances

To set up tax allowances, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Tax allowances**.
1. Create a record.
1. Set the following values for the tax allowance.

    | **Field**                                          | **Description**        |
    |----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Privilege**                                      | Enter the tax allowance code.                                                                                                                                                                            |
    | **Type of tax**                                    | Select **Transport tax**.                                                                                                                                                                                |
    | **Benefit type**                                   | Select the type of tax allowance. The following values are applicable to transport tax allowances: **Exemption from tax**, **Reduction of tax rate**, **Reduction of tax amount**, and **Tax deduction**. |
    | **Name**                                           | Enter the name of the tax allowance.                                                                                                                                                                     |
    | **Allowance value**                                | Define the tax allowance value, depending on type of tax allowance that you selected in the **Benefit type** field:                                                                                       |
    | **Article number**, **Clause**, and **Sub-clause** | Define the article number, clause, and sub-clause of the law in accordance with which the corresponding tax allowance is granted.                                                                        |

> [!NOTE]
> - **Exemption from tax:** Don't define the allowance value, because exemption from tax is always considered 100 percent, and the tax amount is 0 (zero).
> - **Reduction of tax rate:** Define the percentage of the tax rate reduction. For example, if the tax rate is 10 percent, and the allowance value is 2 percent, the reduced tax rate is 8 percent.
> - **Reduction of tax amount:** Define the amount, in the local currency, that is reducing the calculated tax amount for each asset.

### Assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount

To assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax relations**.
1. Select the record for the sales tax code.
1. In the **Allowance by reduction of rate** and **Allowance by reduction of tax** fields, select the appropriate tax allowances, if they are applicable to the sales tax code.

### Set up transport tax increasing factor groups and values

The amount of transport tax should be increased for expensive vehicle models that are defined by the Ministry of Production and Trade in an informational letter and annually reviewed. The coefficient that must be considered depends on both the number of years that have passed since the vehicle's year of manufacture and the cost of vehicle. For example, for a vehicle that costs between 3 million and 5 million rubles, if less than one year has passed since its year of manufacture, the increasing coefficient is 1.5.

To set up transport tax increasing factor groups and values, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed asset (Russia) \> Setup \> Tax reporting \> Transport tax increasing factor groups**.
1. Create a group.
1. On the **Transport tax increasing factor values** FastTab, define the following increasing factor values.

| **Field**      | **Description**                                                                          |
|----------------|------------------------------------------------------------------------------------------|
| From date      | Enter the date when the factor value starts to apply.                                   |
| Upper lifetime | Enter the upper limit of the lifetime from manufacture that the factor value applies to. |
| Factor         | Enter the increasing factor.                                                            |

### Set up the territory code (OKTMO code) for the legal entity

To set up the territory code (OKTMO code) for the legal entity, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. On the **Addresses** FastTab, select **More options \> Advanced**.
1. On the **Manage addresses** page, on the **Registration ID** FastTab, create a line.
1. In the **Registration type** field, select the registration type for OKATO/OKTMO.

    If the required registration type isn't listed, follow these steps to add it:

    1. On the **Registration types** page (**Organization administration \> Global address book \> Registration types \> Registration types**), create a registration type.
    1. On the **Registration categories** page (**Organization administration \> Global address book \> Registration types \> Registration categories**), assign the new registration type to the **RCOAD** registration category.
    1. In the **Registration number** field, enter the OKTMO code for the legal entity's location.

### Set up tax authorities and related OKTMO codes

You must create the tax authorities that you're required to report assessed tax declarations to.

To set up tax authorities and related OKTMO codes, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Indirect taxes \> Sales tax \> Sales tax authorities**.
1. Create a tax authority.
1. Set the **Authority** and **Name** fields.
1. In the **STI code** field, enter the four-digit code for the tax authority.
1. In the **Vendor account** field, select the vendor account party that is associated with the tax authority.
1. Define the main OKTMO code for the tax authority on the vendor account:
    1. In the record for the vendor account, on the **Addresses** FastTab, select **More options \> Advanced**.
    1. On the **Registration ID** FastTab, add a line.
    1. In the **Registration type** field, select the registration type for OKATO/OKTMO.
    1. In the **Registration number** field, enter the OKTMO code.

> [!NOTE]
> For realty objects that are located at the organization's main location, the tax authority that assessed tax is reported to is defined as the tax authority that has the same OKTMO code as the legal entity.

### Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes

If the organization has realty objects that are located in territories that differ from the organization's main location, or if the organization has separate subdivisions, you should set up company divisions.

To set up company divisions, their registration reason codes (KPP), and their OKTMO codes, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Setup \> Separate divisions**.
1. Create a company division.
1. In the **Separate division ID** field, enter the identification code for the division.
1. In the **Name** field, enter the name of the division.
1. In the **Vendor account** field, select the vendor account number that is associated with the division. If there is no vendor account for the company division, create one.
1. Define the OKTMO code for the company division on the vendor account:
    1. In the vendor account record, on the **Addresses** FastTab, select **More options \> Advanced**.
    1. On the **Registration ID** FastTab, add a line.
    1. In the **Registration type** field, select the registration type for OKATO/OKTMO.
    1. In the **Registration number** field, enter the OKTMO code.
1. Repeat step 6 to define the KPP code for the separate division on the vendor account. In the **Registration type** field, select the registration type that's associated with the **KPP** registration category.

### Set up the organization's locations and assign them to company divisions

If the organization has realty objects that are located in territories that differ from the organization's main location, or if the organization has separate subdivisions, you should set up organization locations and assign them to company divisions.

To set up the organization's locations and assign them to company divisions, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Location**.
1. Select an existing location, or create a new location.
1. On the **General** FastTab, in the **Separate division ID** field, select the company division that you created in the previous procedure.

    If the **Separate division ID** field is left blank, the location is the same as the location of the organization's head office.

    > [!NOTE]
    > For vehicles that are registered in territories that differ from the organization's main location, the tax authority that transport tax is reported to is defined as the tax authority that has the same OKTMO code as the separate division that is associated with the vehicle location. For information about how to associate a fixed asset with a location, see [Specify the location of the vehicle](#specify-the-location-of-the-vehicle).

### Set up fixed assets parameters for posting transport tax

To set up fixed assets parameters for posting transport tax, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Parameters**.
1. On the **Number sequences** tab, for the **Assessed tax registers journal number** reference, select a number sequence for the tax register.
1. On the **Tax reporting** tab, in the **Transport tax** section, in the **Sales tax code** field, select the default sales tax code for transport tax.
1. In the **Compression** field, select the level of compression for transport tax transactions:
    - **Tax** – A detailed ledger journal for transport tax transactions is created for each sales tax code.
    - **Total** – A ledger journal for transport tax transactions is created as one line that has the default sales tax code.
1. Close the page.

### Set up the journal for posting transport tax

If transport tax transactions will be automatically created based on calculated tax registers, you should set up a journal.

To set up the journal for posting transport tax, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Journal setup \> Journal names**.
1. Create a line.
1. Set the **Name** and **Voucher series** fields.
1. In the **Journal type** field, select **Transport tax**.

### Set up a posting group for transport tax postings

If transport tax transactions will be automatically created based on calculated tax registers, you should set up posting groups.

To set up a posting group for transport tax postings, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Group of posting of taxes**.
1. Create a line.
1. In the **Ledger posting group** field, select a ledger posting group for transport tax. If no ledger posting group is listed, create one. In the **Sales tax payable** field, enter the ledger account code for posting transport tax.
1. In the **Account for FA taxes** field, select a ledger account for the transport tax expenses.
1. Make sure that the **Sales tax payable** field is set to the ledger account code that you entered for the ledger posting group in step 3.

## Create a vehicle and set up parameters for transport tax calculation

Here is an overview of the steps for creating a vehicle and setting up parameters for transport tax calculation:

1. [Create a vehicle fixed asset and define parameters for transport tax calculation](#create-a-vehicle-fixed-asset-and-define-parameters-for-transport-tax-calculation)
1. [Specify the location of the vehicle](#specify-the-location-of-the-vehicle)
1. [Specify a tax allowance as an exemption from tax](#specify-a-tax-allowance-as-an-exemption-from-tax)

### Create a vehicle fixed asset and define parameters for transport tax calculation

To create a vehicle fixed asset and define parameters for transport tax calculation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Common \> Fixed assets**.
1. Select an existing fixed asset, or create a new fixed asset.
1. On the **General** FastTab, in the **Type** field, select **Vehicle**.
1. In the **Flag of ownership** field, select whether the fixed asset is owned, under operational management, leased, or owned by someone who is outside Russia.
1. On the **Technical information** FastTab, in the **Vehicle** section, set the **Vehicle type**, **Model**, **Registration number**, and **Emission class** fields.

    >[!NOTE]
    > - You create vehicle types on the **Vehicle types** page (**Fixed assets (Russia) \> Setup \> Vehicle \> Vehicle types**).
    > - You create vehicle models on the **Vehicle models** page (**Fixed assets (Russia) \> Setup \> Vehicle \> Vehicle models**).

1. In the **Useful life** section, in the **Output year** field, specify the year of manufacture.
1. In the **Government registration** section, set the **Date of the registration** and **Removal from the register date** fields.
1. On the **Tax reporting** FastTab, in the **Transport tax** section, in the field **Tax base** field, specify the vehicle power. In the **Unit** field, specify the unit of measure for the vehicle power.
1. If you partially own the fixed asset, in the **Owned share numerator** and **Owned share denominator** fields, define your ownership share as a simple fraction.
1. In the **Sales tax code** field, select the sales tax code for the assessed tax calculation.
1. Set the **Increasing factor group** field.
1. In the **Deduction** field, specify the tax deduction code. In the **Tax deduction amount** field, specify the deduction amount.

### Specify the location of the vehicle

By default, the assumption is that vehicles are located at the organization's location and reported to the tax authority in the legal entity's territory. (The OKTMO code of the tax authority matches the OKTMO code of the legal entity, and realty objects are reported under the same OKTMO code.)

If the organization has vehicles that are located in different territories and registered in different tax authorities, you must specify the location of the vehicle.

To specify the location of the vehicle, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Common \> Fixed assets**.
1. Select the line for the vehicle.
1. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Transfer**.
1. Create a line.
1. Set the **Date** and **New location** fields.

### Specify a tax allowance as an exemption from tax

To specify a tax allowance as an exemption from tax, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Common \> Fixed assets**.
1. Select the line for the vehicle.
1. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Tax reporting data**.
1. Create a line.
1. In the **Period** field, specify the month when a tax allowance as an exemption from tax applies. In the **Exemption from tax** field, select the code for the tax allowance as an exemption from tax.

## Calculate transport tax registers

After you've finished the setup, registered the acquisition of the vehicle, and set up all vehicle parameters for transport tax calculation, you must calculate transport tax registers. The following tax registers are available:

- **Vehicle - tax calculation** – This tax register calculates transport tax for each vehicle. It shows the following information:

    - The vehicle type, serial number, model, and registration number.
    - The dates of vehicle registration and removal from the register.
    - The tax base and the units of measure for the tax base.
    - The useful lifetime, in years, after the year of manufacture, and the output year.
    - The owned share as an indication that the vehicle is partially owned.
    - **Factor Kp** – The increasing factor for expensive vehicles.
    - The ownership factor if the vehicle was acquired or sold during the period. This factor is the ratio of the ownership period to the number of calendar months in the period.
    - **Calculated advance payment / Tax** – If the tax register is calculated for the first quarter, second quarter, or third quarter, the tax advance amount before tax allowances are applied. If the tax register is calculated for the year, the transport tax amount before tax allowances are applied.
    - **Exemption from tax** – The code for the tax allowance as an exemption from tax.
    - The amount of the tax allowance as an exemption from tax.
    - **Grace period** – The number of months when there is no tax exemption allowance.
    - **Allowance factor** – The ratio of the grace period to the number of calendar months in the tax period.
    - **Privilege** – The code for the tax allowance as a reduction of the rate or a reduction of tax.
    - **Tax allowance amount** – The amount of the tax allowance as a reduction of the tax rate or a reduction of the tax amount.
    - **Deduction** – The code for the tax deduction.
    - **Tax allowance amount** – The amount of the tax deduction.
    - The transport tax rate, budget revenue code, separate division ID, and location of the vehicle, and the tax authority that the tax for the vehicle will be reported to.
- **Transport tax** – This tax register calculates total transport tax amounts for each sales tax code and OKTMO code.

To calculate and approve transport tax registers, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
1. Select **New**.
1. In the **Type of tax** field, either select **Transport tax** to create a journal only for transport tax registers, or leave the field blank to create a journal for all the asset's taxes (assessed tax, land tax, and transport tax).
1. In the **Period types** field, select one of the following values:
    - **Quarter** – Generate a journal for the calculation of transport tax advance payments.
    - **Years** – Generate a journal for the annual transport tax calculation.
1. In the **Period number** field, if you selected **Quarter** in the **Period types** field, enter the number of the quarter. If you selected **Years**, enter **1**.
1. In the **Years** fields, enter the reporting year in *YYYY* format.
1. Select **OK** to create the journal.
1. Select **Lines** to create lines in the periodic register journal.
1. You receive a message that states, "Register journal has not been created yet. Do you want create it?" Select **Yes**.
1. Review the tax registers that are created. For transport tax, the following registers are created: **Vehicle – tax calculation** and **Transport tax**.
1. To calculate a specific tax register in the journal, select the register, and then select **Calculate current**. To calculate all tax registers in the journal, select **Calculate all**.
1. Select **OK**.
1. Select a tax register, and then select **Register lines** to review the calculated lines.
1. Select **Print** to print the tax register lines in Microsoft Excel.
1. Select **Reset status** to reset the status of the calculated register to **Not calculated**.
1. After you've finished reviewing the data in the tax registers, select the **Approved** checkbox to approve each register.
1. In the **Worker** field, view or change the code for the employee who approved the register.

### Create and calculate corrective tax registers

If you've corrected any vehicle data for the previous periods, you should create corrective tax registers to reflect the corrected transport tax amounts.

To create and calculate corrective registers, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
1. Select the approved journal for the period that must be corrected.
1. Select **Correction \> Corrections to current journal**.
1. Select **New**.
1. In the **Type of tax** field, either select **Transport tax** if you must correct only transport tax registers, or leave the field blank if you must correct all the asset's tax registers.
1. Make sure that the **Period types**, **Period number**, and **Years** fields are set to values that are appropriate for the period of the register that you're correcting.
1. Select **OK**.
1. Create tax register lines, and calculate and approve the tax registers as described in the previous procedure.

## Generate a transport tax declaration

### Set up the system to generate a transport tax declaration

In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the **Shared asset library**, download the latest versions of the electronic reporting (ER) configurations for the assessed tax declaration.

For example, to generate the transport tax declaration for the year 2019 reporting period, download the latest version of the following configurations:
    - Assets declarations model
    - Transport tax declaration model mapping
    - Transport tax declaration format 5.05

Learn more in [Download Electronic reporting configurations from Lifecycle Services](/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

You can upload Data management package settings to work with the transport tax declaration. 

To set up the system to generate a transport tax declaration, follow these steps.

1. In the LCS Shared asset library, select **Data package** as the asset type.
1. Download the package that is named **RU Transport tax declaration v5.05 (2019)**. The file that is downloaded is named **RU Transport tax declaration v5.05 (2019).zip**.
1. In Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
1. In the **Job details** section, enter a name for the job.
1. In the **Source data format** field, select **Package**.
1. Select **Upload** next to the **Upload data file** field, and then select the **RU Transport tax declaration v5.05 (2019).zip** file that you downloaded earlier.
1. After the data entities are uploaded, select **Import**.
1. Go to **Tax \> Setup \> Electronic messages \> Electronic message processing**, and validate the electronic message processing that is imported. (Most of the data that is imported is presented in the Russian language.)

    | **Processing**            | **Processing code**  | **Name**                                  |
    |---------------------------|----------------------|-------------------------------------------|
    | Transport tax declaration | ТрансНал 5.05 (2019) | Декларация по транспортному налогу (2019) |

1. Set up the ER format that is run when accounting reporting is generated in electronic format:
1. Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.
1. Select the **Generate TRAND 5.05** action, and then select **Edit**.
1. Set the **Show dialog** option to **Yes**.
1. In the **Format mapping** field, select the **Transport tax declaration format 5.05** ER configuration that you downloaded earlier.
1. Set up the economic activity type code (OKVED):
1. Go to **Tax \> Setup \> Electronic messages \> Additional fields**.
1. Select the **EconomicActivityTypeCode** record.
1. On the **Value** FastTab, select **Add**, and then enter the value of the code.

### Generate a transport tax declaration

Before you can generate the transport tax declaration for a tax year, you must calculate the transport tax registers for the same year, and for the first quarter, second quarter, and third quarter of the same year. The advance payment amount for transport tax that is exported in the transport tax declaration is taken from the tax registers that were calculated for the first quarter, second quarter, and third quarter.

To generate a transport tax declaration, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
1. Select the report format to generate. For example, to generate a transport tax declaration in XML format for the year 2019, select **ТрансНал 5.05 (2019)**.
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, select **OK**.
1. Select the message line that is created, and enter a description.
1. Enter a start date and end date for the report. To generate a transport tax declaration, enter the year period. For example, for the year 2019, enter **01.01.2019** in the **From date** field and **31.12.2019** in the **To date** field.
1. Optional: For a corrective declaration, on the **Message additional fields** FastTab, on the line for the **CorrectionNumber** field, in the **Field value** field, enter the number of the correction.
1. On the **Messages** FastTab, select **Update status**.
1. In the **Run processing** dialog, select **OK**.
1. Validate that the message status has been changed to **Ready to generate**.
1. On the **Messages** FastTab, select **Generate report**.
1. In the **Electronic reporting parameters** dialog, on the **Parameter** FastTab, set the following values.

    | **Field**                                                        | **Description**                                                                                                                             |
    |------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
    | At place of                                                      | Select the place where the declaration is submitted: **Vehicle location** or **Registration of the largest taxpayer**.                     |
    | Correction number                                                | Enter the number of the correction if you didn't specify it in step 1.                                                                     |
    | Signatory type                                                   | Select the person who signs the accounting reporting: **Taxpayer** or **Representative**.                                                  |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory.                                                                                                      |
    | Representative company                                           | If you selected **Representative** as the signatory type, and if the representative is an organization, enter the name of the organization. |
    | Representative document                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority.                 |

1. On the first **Records to include** FastTab, apply a filter for separate divisions, if this type of filter is applicable. In this case, declarations are only generated for the selected separate divisions.
1. On the second **Records to include** FastTab, apply a filter for tax authorities, if this type of filter is applicable. In this case, declarations will be generated only for the selected tax authorities.
1. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs during generation, the status is changed to **Technical error**.
1. On the **Action log** FastTab, review all user actions for the current message.
1. To review the report that is generated, select the **Attachments** button (the paper clip symbol) in the upper-right corner of the page, and then select **Open** to view the file.

You must also manually upload the generated file to the special third-party software for data preview, data updates, and transfer of the transport tax declaration files to the tax authorities through the communication channels.

## Create and post transport tax ledger transactions

After you've calculated and approved tax registers, and generated a transport tax declaration, you can create transactions for transport tax accruals.

To create and post transport tax ledger transactions, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
1. Select the journal, and then select **Ledger journal \> Transport tax**.
1. Select **New**.
1. In the **Name** field, select the name of the transport tax journal.
1. Select **Lines** to view the journal lines that have transport tax accrual transactions that were created based on the tax register data and the settings of Fixed assets parameters.
1. Validate and post the journal.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
