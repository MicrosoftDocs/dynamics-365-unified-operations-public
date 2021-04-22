---
# required metadata

title: Assessed tax declaration (Russia)
description: This topic explains how to set up and use assessed tax declarations for Russia.
author: ShylaThompson
ms.date: 01/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2019-05-01
ms.dyn365.ops.version: 10.0.1

---

# Assessed tax declaration (Russia)

[!include [banner](../includes/banner.md)]

According to the tax code of the Russian Federation, realty assets are subject to assessed tax.

The tax period for assessed tax is one year. The advance payments must be calculated and paid to tax authorities for the first quarter, the second quarter (six months or half year), and the third quarter (nine months).

At the end of the tax period, a company must report an assessed tax declaration that also includes information about the amounts of quarterly advance payments. Before the year 2019, at the end of each quarter, the company had to report an assessed tax advance payments calculation declaration. Starting from the year 2019, the assessed tax advance payments calculation declaration is canceled.

The assessed tax declaration should be submitted to one of the following tax authorities:

- The tax authority where the realty is located. In this case, the code **281** should be entered for the **at place of** attribute.
- The tax authority where the company is registered. In this case, the code **214** should be entered for the **at place of** attribute.
- If the organization is a greatest taxpayer, the tax authority where the organization is registered as a greatest taxpayer. In this case, the code **213** should be entered for the **at place of** attribute.

The tax base for the calculation of assessed tax is either the annual average cost of the realty asset or the cadastral cost of the realty asset.

The annual average cost is calculated as the sum of residual values (net book values) for the realty fixed asset on the first day of each month of the tax (or reporting) period, and on the first day of the month after the tax (or reporting) period. This sum is then divided by the number of months in the tax period plus one. Realty assets that are taxed at the annual average cost are reported in section 2 of the assessed tax declaration.

The cadastral cost is defined by cadastral authorities and should be specified by the user on the fixed asset card. Realty assets that are taxed at the cadastral cost are reported in section 3 of the assessed tax declaration.

This topic explains how to perform the following tasks:

1. [Set up assessed tax](#set-up-assessed-tax)
2. [Create a realty asset and set up parameters for assessed tax calculation](#create-a-realty-asset-and-set-up-parameters-for-assessed-tax-calculation)
3. [Calculate assessed tax registers](#calculate-assessed-tax-registers)
4. [Generate an assessed tax declaration](#generate-an-assessed-tax-declaration)
5. [Create and post assessed tax ledger transactions](#create-and-post-assessed-tax-ledger-transactions)

## Set up assessed tax

Here is an overview of the steps for setting up assessed tax:

1. [Set up assessed tax codes and rates](#set-up-assessed-tax-codes-and-rates)
2. [Set up budget revenue codes for assessed tax](#set-up-budget-revenue-codes-for-assessed-tax)
3. [Assign a budget revenue code to a sales tax code](#assign-a-budget-revenue-code-a-to-sales-tax-code)
4. [Set up methods for assessed tax base calculation](#set-up-methods-of-assessed-tax-base-calculation)
5. [Set up tax allowances](#set-up-tax-allowances)
6. [Assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount](#assign-tax-allowances-to-a-sales-tax-code-as-a-reduction-of-the-tax-rate-and-a-reduction-of-the-tax-amount)
7. [Set up the territory code (OKTMO code) of the legal entity](#set-up-the-territory-code-oktmo-code-of-the-legal-entity)
8. [Set up tax authorities and related OKTMO codes](#set-up-tax-authorities-and-related-oktmo-codes)
9. [Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes](#optional-set-up-company-divisions-their-registration-reason-codes-kpp-and-their-oktmo-codes)
10. [Set up the organization's locations and assign them to company divisions](#set-up-the-organizations-locations-and-assign-them-to-company-divisions)
11. [Set up territories for distributed realty assets](#set-up-territories-for-distributed-realty-assets)
12. [Set up railway assets factors](#set-up-railway-assets-factors)
13. [Set up Fixed assets parameters for posting assessed tax](#set-up-fixed-assets-parameters-for-posting-assessed-tax)
14. [Set up the journal for posting assessed tax](#set-up-the-journal-for-posting-assessed-tax)
15. [Set up a posting group for assessed tax postings](#set-up-a-posting-group-for-assessed-tax-postings)

### Set up assessed tax codes and rates

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
2. Create a sales tax code.
3. In the **Type of tax** field, select **Assessed tax**.
4. Specify the settlement period and the ledger posting group.
5. On the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **Values** to open the **Sales tax code values** page.
6. In the **Value** field, specify the tax rate for the assessed tax.

### Set up budget revenue codes for assessed tax

1. Go to **Cash and bank management \> Setup \> Payment order setup \> Budget revenue classification**.
2. Create a budget revenue code for assessed tax.
3. Select the **SSGS** check box to indicate that the budget revenue code belongs to the Standard System of Gas Supply (SSGS).

### Assign a budget revenue code a to sales tax code

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax relations**.
2. Create a record.
3. In the **Type of tax** field, select **Assessed tax**.
4. In the **Code** field, select the sales tax code for the assessed tax.
5. In the **Budget revenue code** field, select the budget revenue code that corresponds to the selected sales tax code.

### Set up methods of assessed tax base calculation

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Methods of assessed tax base calculation**.
2. For each asset kind code, specify the method of assessed tax base calculation (**Yearly average value** or **Cadastral value**), as shown in the following table.

    | Code | Description                                                                 | Method of tax base calculation as of January 1, 2019 |
    |------|-----------------------------------------------------------------------------|------------------------------------------------------|
    | 1    | Unified gas supply system                                                   | Yearly average value                                 |
    | 2    | Realty that is located in different territories                             | Yearly average value                                 |
    | 3    | Other                                                                       | Yearly average value                                 |
    | 4    | Realty that is located abroad and tax that is paid abroad                   | Yearly average value                                 |
    | 5    | Realty that is located in the Kaliningrad special zone                      | Yearly average value                                 |
    | 7    | Sea hydrocarbon fields                                                      | Yearly average value                                 |
    | 8    | Gas objects                                                                 | Yearly average value                                 |
    | 9    | Railway objects                                                             | Yearly average value                                 |
    | 10   | Power lines and pipelines                                                   | Yearly average value                                 |
    | 11   | Realty that is taxed at the cadastral cost                                  | Cadastral value                                      |
    | 12   | Realty of a foreign entity that is taxed at the cadastral cost              | Cadastral value                                      |
    | 13   | Realty that isn't accounted as fixed assets and taxed at the cadastral cost | Cadastral value                                      |

### Set up tax allowances

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Tax allowances**.
2. Create a record.
3. Set the values for the tax allowance.

    | Field           | Description |
    |-----------------|-------------|
    | Privilege       | Enter the tax allowance code. |
    | Type of tax     | Select **Assessed tax**. |
    | Benefit type    | Select the type of tax allowance. The following values are applicable for assessed tax allowances: **Exemption from tax**, **Tax base reduction**, **Reduction of tax rate**, and **Reduction of tax amount**. |
    | Name            | Enter the name of the tax allowance. |
    | Allowance value | Define the tax allowance value, depending on type of tax allowance that you selected in the **Benefit type** field:<ul><li><strong>Exemption from tax</strong> – Don't define the allowance value, because exemption from tax is always considered 100 percent, and the tax amount is 0 (zero).</li><li><strong>Tax base reduction</strong> – Define the amount, in the local currency, that is reducing the tax base amount for each asset.</li><li><strong>Reduction of tax rate</strong> – Define the percentage of the tax rate reduction. For example, if the tax rate is 10 percent, and the allowance value is 2 percent, the reduced tax rate is 8 percent.</li><li><strong>Reduction of tax amount</strong> – Define the amount, in the local currency, that is reducing the calculated tax amount for each asset.</li><ul> |

### Assign tax allowances to a sales tax code as a reduction of the tax rate and a reduction of the tax amount

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Sales tax relations**.
2. Select the record for the sales tax code.
3. In the **Allowance by reduction of rate** and **Allowance by reduction of tax** fields, select the appropriate tax allowances, if they are applicable to the sales tax code.

### Set up the territory code (OKTMO code) of the legal entity

1. Go to **Organization administration \> Organizations \> Legal entities**.
2. On the **Addresses** FastTab, select **More options \> Advanced**.
3. On the **Manage addresses** page, on the **Registration ID** FastTab, create a line.
4. In the **Registration type** field, select the registration type for OKATO/OKTMO.

    If the required registration type isn't listed, follow these steps:

    1. On the **Registration types** page (**Organization administration \> Global address book \> Registration types \> Registration types**), create a registration type.
    2. On the **Registration categories** page (**Organization administration \> Global address book \> Registration types \> Registration categories**), assign the new registration type to the **RCOAD** registration category.
    3. In the **Registration number** field, enter the OKTMO code for the legal entity's location.

### Set up tax authorities and related OKTMO codes

You must create the tax authorities that you're required to report assessed tax declarations to.

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax authorities**.
2. Create a tax authority.
3. Set the **Authority** and **Name** fields.
4. In the **STI code** field, enter the four-digit code of the tax authority.
5. In the **Vendor account** field, select the vendor account party that is associated with the tax authority.
6. Define the main OKTMO code of the tax authority on the vendor account:

    1. In the record for the vendor account, on the **Addresses** FastTab, select **More options \> Advanced**.
    2. On the **Registration ID** FastTab, add a line.
    3. In the **Registration type** field, select the registration type for OKATO/OKTMO.
    4. In the **Registration number** field, enter the OKTMO code.

    > [!NOTE]
    > For realty objects that are located at the organization's main location, the tax authority that assessed tax is reported to is defined as the tax authority that has an OKTMO code that matches the OKTMO code of the legal entity.

### Optional: Set up company divisions, their registration reason codes (KPP), and their OKTMO codes

If the organization has realty objects that are located in territories that differ from the organization's main location, or if the organization has separate subdivisions, you should set up company divisions.

1. Go to **Organization administration \> Setup \> Separate divisions**.
2. Create a company division.
3. In the **Separate division ID** field, enter the identification code for the division.
4. In the **Name** field, enter the name of the division.
5. In the **Vendor account** field, select the vendor account number that is associated with the division. If there is no vendor account for the company division, create one.
6. Define the OKTMO code of the company division on the vendor account:

    1. In the vendor account record, on the **Addresses** FastTab, select **More options \> Advanced**.
    2. On the **Registration ID** FastTab, add a line.
    3. In the **Registration type** field, select the registration type for OKATO/OKTMO.
    4. In the **Registration number** field, enter the OKTMO code.

7. Repeat step 6 to define the KPP code of the separate division on the vendor account. In the **Registration type** field, select the registration type that is associated with the **KPP** registration category.

### Set up the organization's locations and assign them to company divisions

If the organization has realty objects that are located in territories that differ from the organization's main location, or if the organization has separate subdivisions, you should set up organization locations and assign them to company divisions.

1. Go to **Fixed assets (Russia) \> Setup \> Location**.
2. Select an existing location, or create a new location.
3. On the **General** FastTab, in the **Separate division ID** field, select the company division that you created in the previous procedure.

    > [!NOTE]
    > For realty objects that are located in territories that differ from the organization's main location, the tax authority that assessed tax is reported to is defined as the tax authority that has an OKTMO code that matches the OKTMO code of the separate division that is associated with the realty location. For information about how to associate a fixed asset with a location, see the [Specify the location of the realty](#specify-the-location-of-the-realty) section later in this topic.

If the **Separate division ID** field is blank, the location is the same as the location of the organization's head office.

### Set up territories for distributed realty assets

If a realty asset is distributed among several territories, it should be reported under the appropriate OKTMO code. You should set up distribution territories, assign an OKTMO code to each territory, and associate the OKTMO codes with tax authorities.

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Distribution**.
2. Create a territory.
3. Set the **Territory** and **Name** fields.
4. Select the sales tax code that is applied in the territory.
5. In the **RCOAD** field, select the OKTMO code of the territory. Only OKTMO codes that are associated with the tax authority of the sales tax code are available for selection. If no OKTMO code is available, follow these steps:

    1. Select the link for the sales tax code to open the **Sales tax codes** page.
    2. Select the link for the settlement period code to open the **Sales tax settlement periods** page.
    3. Select the link for the authority code to open the **Sales tax authorities** page.
    4. On the Action Pane, select **RCOAD codes**.
    5. Create lines for the OKTMO codes that are related to the tax authority.

        Alternatively, create all the OKTMO codes, and then assign a code to the tax authority on the **RCOAD codes** page (**Tax \> Setup \> Sales tax \> RCOAD codes**).

### Set up railway assets factors

If the organization has railways, set up the railway assets factors.

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Railway assets factors**.
2. Select **New**.
3. In the **Tax period number** field, enter the tax reporting year.
4. In the **Factor** field, enter the railway factor value.
5. Specify effective and expiration dates for the factor value.

### Set up Fixed assets parameters for posting assessed tax

1. Go to **Fixed assets (Russia) \> Setup \> Parameters**.
2. On the **Number sequences** tab, for the **Assessed tax registers journal number** reference, select a number sequence for the tax register.
3. On the **Tax reporting** tab, in the **Assessed tax** section, in the **Sales tax code** field, select the default sales tax code for assessed tax.
4. In the **Compression** field, select the level of compression for assessed tax transactions:

    - **Tax** – A detailed ledger journal for assessed tax transactions will be created for each sales tax code.
    - **Total** – A ledger journal for assessed tax transactions will be created as one line that has the default sales tax code.

5. Close the page.

### Set up the journal for posting assessed tax

If assessed tax transactions will be automatically created based on calculated tax registers, you should set up a journal.

1. Go to **General ledger \> Journal setup \> Journal names**.
2. Create a line.
3. Set the **Name** and **Voucher series** fields.
4. In the **Journal type** field, select **Assessed tax**.

### Set up a posting group for assessed tax postings

If assessed tax transactions will be automatically created based on calculated tax registers, you should set up posting groups.

1. Go to **Fixed assets (Russia) \> Setup \> Tax reporting \> Group of posting of taxes**.
2. Create a line.
3. In the **Ledger posting group** field, select a ledger posting group for assessed tax.

    If no ledger posting group is listed, create one. In the **Sales tax payable** field, enter the ledger account code for posting assessed tax.

4. In the **Account for FA taxes** field, select a ledger account for the assessed tax expenses.
5. Make sure that the **Sales tax payable** field is set to the ledger account code that you entered for the ledger posting group in step 3.

## Create a realty asset and set up parameters for assessed tax calculation

Here is an overview of the steps for creating a realty asset and setting up parameters for assessed tax calculation:

1. [Define the date of including in the tax base for a realty asset](#define-the-date-of-including-in-the-tax-base-for-a-realty-asset)
2. [Register realty as a fixed asset](#register-realty-as-a-fixed-asset)

### Define the date of including in the tax base for a realty asset

1. Go to **Fixed assets (Russia) \> Setup \> Parameters**.
2. On the **Tax reporting** tab, in the **Assessed tax** section, in the **Date of including in the tax base** field, specify when the realty asset should be entered in the tax base of the assessed tax register:

    - **Putting into operation date** – The date when the realty asset is put into operation.
    - **Date of the registration** – The registration date of the realty asset.

### Register realty as a fixed asset

#### Create a realty fixed asset and define parameters for assessed tax calculation

1. Select **Fixed assets (Russia) \> Common \> Fixed assets**.
2. Select an existing fixed asset, or create a new fixed asset.
3. On the **General** FastTab, in the **Type** field, select **Realty**.
4. In the **Flag of ownership** field, select whether the fixed asset is owned, under operational management, leased, or owned by someone who is outside Russia.
5. On the **Technical information** FastTab, set the **Date of the registration** and **Removal from the register date** fields.
6. Specify the cadastral value of the realty object. If the realty object is a room inside the building, also set the **Room cadastral value** field.
7. On the **Tax reporting** FastTab, in the **Assessed tax** section, in the **Asset kind** field, select the asset kind code of the realty.
8. In the **Sales tax code** field, select the sales tax code for the assessed tax calculation.
9. If you partially own the fixed asset, in the **Owned share numerator** and **Owned share denominator** fields, define your ownership share as a simple fraction.
10. In the **Code by OKOF** field, specify the code from the all-Russia classifier of fixed assets.
11. In the **Privilege** field, specify the tax allowance of the **Exemption of tax** and **Tax base reduction** types, if these tax allowance types are applicable.
12. In the **Tax base** field, review the method of assessed tax base calculation.
13. On the **Address** FastTab, specify the address of the realty object. If the realty object doesn't have a cadastral number, the address is exported to section 2.1 of the assessed tax declaration.

#### Specify the location of the realty

By default, realty objects are considered to be located at the organization's location and reported to the tax authority in the legal entity's territory. (The OKTMO code of the tax authority matches the OKTMO code of the legal entity, and realty objects are reported under the same OKTMO code.)

If the organization has realty objects that are located in different territories and registered in different tax authorities, you must specify the location of the realty asset.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. Select the line for the realty asset.
3. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Transfer**.
4. Create a line, and set the **Date** and **New location** fields.

#### Specify the distribution for a realty asset that is located in several territories

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. Select the line for the realty asset.
3. On the Action Pane, on the **Fixed asset** tab, in the **Distribution** group, select **Distribution**.
4. Create a line.
5. In the **Location** field, select a territory.
6. Review the values in the **RCOAD** and **Sales tax code** fields. These values are automatically entered from the territory location record.
7. In the **Distribution share numerator** and **Distribution share denominator** fields, define the distribution share as a simple fraction. These fields will be used to calculate the realty's value in the territory.

#### Change the cadastral cost of realty that is taxed according to cadastral rules

The cadastral cost of a realty asset might change because of a change in qualitative and quantitative characteristics. Follow these steps to record the change in cadastral value.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets**.
2. Select the line for the realty asset.
3. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Tax reporting data**.
4. Create a line.
5. In the **Period** field, specify the month when the cadastral value is changing.
6. In the **Cadastral number** field, enter a new cadastral number.
7. If the realty is a room in the building, set the **Room cadastral number** field.
8. In the **Owned share numerator** and **Owned share denominator** fields, define the new owned share as a simple fraction.

> [!NOTE]
> If this change is the first change in cadastral value, you must also create a line for the previous values that were originally entered in the fixed asset record. When the line for the change in cadastral value is created, corresponding fields in the fixed asset record can no longer be edited. They show the actual value from the tax reporting data history record.

## Calculate assessed tax registers

After you've finished the setup, registered the acquisition of realty assets, and set up all realty asset parameters for assessed tax calculation, you must calculate assessed tax registers. The following tax registers are available:

- **Cost calculation** – Depending on the method of tax base calculation, this tax register calculates either the net book values of each realty asset as of the first day of each month in the reporting period or the cadastral cost of each asset during that period. These amounts will be used as the basis for the tax base calculation for the tax amount that must be paid in the territory that is identified by the OKTMO code. The register also shows the following information:

    - The owned share, if the realty is partially owned
    - The distributed property share, if the realty is distributed (asset kind 02)
    - The ownership period and factor, if the realty was acquired or sold during the period
    - The cost change period and factor, if the cadastral cost changed during the period
    - The assessed tax rate, budget revenue code, asset kind code, separate division ID, and location of the realty, the tax authority that the tax for the realty will be reported to, the acquisition date of the realty, and the code for tax allowance through exemption from tax or tax base reduction

- **Totals of net book value calculation** – This tax register is a technical register that is calculated based on the data in the **Cost calculation** tax register. Depending on the method of tax base calculation, it shows either the tax-exempt net book values as of the first day of each month in the reporting period or the tax-exempt cadastral cost of the asset.
- **Assessed tax** – This tax register is the basis for an assessed tax declaration. It's calculated based on the data in the **Totals of net book value calculation** tax register. For each OKTMO code, budget revenue code, and realty asset, this register shows the following data that must be reported in the declaration:

    - The average cost and average cost of exempt realty, or the cadastral value and cadastral value of exempt realty, depending on the method of tax base calculation for the realty, and the code for tax allowance through exemption from tax or tax base reduction
    - The owned share, if the realty is partially owned
    - The distributed property share, if the realty is distributed
    - The ownership period and factor, if the realty was acquired or sold during the period
    - The cost change period and factor, if the cadastral cost changed during the period
    - The tax rate and the code for tax allowance through reduction of the tax rate
    - The tax base, tax amount (or advance payment amount), advance amount for previous periods, and code and amount for tax allowance through reduction of the tax amount
    - The tax amount that is paid outside Russia (This value isn't automatically calculated. If it's required, it must be manually entered.)

To calculate and approve assessed tax registers, follow these steps.

1. Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
2. Select **New**.
3. In the **Type of tax** field, either select **Assessed tax** to create a journal for assessed tax registers only, or leave the field blank to create a journal for all the asset's taxes (assessed tax, land tax, and transport tax).
4. In the **Period types** field, select one of the following values:

    - **Quarter** – Generate a journal for the assessed tax advance payments calculation.
    - **Years** – Generate a journal for the annual assessed tax calculation.

5. In the **Period number** field, if you selected **Quarter** in the **Period types** field, enter the number of the quarter. If you selected **Years**, enter **1**.
6. In the **Years** fields, enter the reporting year in the format *YYYY*.
7. Select **OK** to create a journal.
8. Select **Lines** to create lines in the periodic register journal.
9. You receive a message that states, "Register journal has not been created yet. Do you want create it?" Select **Yes**.
10. Review the tax registers that are created. For assessed tax, the following registers are created: **Cost calculation**, **Totals of net book value calculation**, and **Assessed tax**.
11. To calculate a specific tax register in the journal, select the register, and then select **Calculate current**. To calculate all tax registers in the journal, select **Calculate all**.
12. Select **OK**.
13. Select a tax register, and then select **Register lines** to review the calculated lines.
14. Select **Print** to print the tax register lines in Microsoft Excel.
15. Select **Reset status** to reset the status of the calculated register to **Not calculated**.
16. After you've finished reviewing the data in the tax registers, select the **Approved** check box to approve each register.
17. In the **Worker** field, view or modify the code of the employee who approved the register.

### Create and calculate corrective tax registers

If you've corrected any realty asset data for the previous periods, you should create corrective tax registers to reflect the corrected assessed tax amounts.

To create corrective registers, follow these steps.

1. Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
2. Select the approved journal for the period that must be corrected.
3. Select **Correction \> Corrections to current journal**.
4. Select **New**.
5. In the **Type of tax** field, either select **Assessed tax** if you must correct only assessed tax registers, or leave the field blank if you must correct all the asset's tax registers.
6. Make sure that the **Period types**, **Period number**, and **Years** fields are set to values that are appropriate for the period of the register that you're correcting.
7. Select **OK**.
8. Create tax register lines, and calculate and approve the tax registers as described in the previous procedure.

## Generate an assessed tax declaration

### Set up the system to generate an assessed tax declaration

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the assessed tax declaration.

    For example, to generate the assessed tax declaration for the year 2019 reporting period, download the latest versions of the following configurations:

    - Assets declarations model
    - Property tax declaration model mapping
    - Property tax declaration format 5.06

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2. You can upload Data management package settings to work with the assessed tax declaration. Follow these steps:

    1. In the LCS Shared asset library, select **Data package** as the asset type.
    2. Download the package that is named **RU Property tax declaration v5.06 (2019)**. The file that is downloaded is named **RU Property tax declaration v5.06 (2019).zip**.
    3. In Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
    4. In the **Job details** section, set the following values:

        - Enter a name for the job.
        - In the **Source data format** field, select **Package**.

    5. Select **Upload** next to the **Upload data file** field, and then select the **RU Property tax declaration v5.06 (2019).zip** file that you downloaded earlier.
    6. After the data entities are uploaded, select **Import**.

3. Go to **Tax \> Setup \> Electronic messages \> Electronic message processing**, and validate the electronic message processing that is imported. (Most of the data that is imported is presented in the Russian language.)

    | Processing               | Processing code      | Name                                    |
    |--------------------------|----------------------|-----------------------------------------|
    | Property tax declaration | НалИмущД 5.06 (2019) | Декларация по налогу на имущество(2019) |

4. Set up the ER format that is run when accounting reporting is generated in electronic format.
5. Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.
6. Select the **Generate IMUD 5.06** action, and then select **Edit**.
7. Set the **Show dialog** option to **Yes**.
8. In the **Format mapping** field, select the **Property tax declaration format 5.06** ER configuration that you downloaded earlier.

### Generate an assessed tax declaration

Before you can generate the assessed tax declaration for a tax year, you must calculate the assessed tax register for the same year, and assessed tax registers for the first, second, and third quarters.

1. Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**, and select the report format to generate.

    For example, to generate an assessed tax declaration in XML format for the year 2019, select **НалИмущД 5.06 (2019)**.

2. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
3. Select the message line that is created, and enter a description.
4. Enter a start date and end date for the report. To generate an assessed tax declaration, enter the year period. For example, for the year 2019, enter **01.01.2019** in the **From date** field and **31.12.2019** in the **To date** field.
5. Optional: On the **Message additional fields** FastTab, on the line for the **CorrectionNumber** field, in the **Field value** field, enter the number of the correction for a corrective declaration. Then, on the **Messages** FastTab, select **Update status**.
6. In the **Run processing** dialog box, select **OK**.
7. Validate that the message status has been changed to **Ready to generate**.
8. On the **Messages** FastTab, select **Generate report**.
9. In the **Electronic reporting parameters** dialog box, on the **Parameter** FastTab, set the following values.

    | Field                                                            | Description |
    |------------------------------------------------------------------|-------------|
    | At place of                                                      | Select the place where the declaration is submitted: **Realty location**, **Registration of the largest taxpayer**, or **Registration of the taxpayer**. |
    | Correction number                                                | Enter the number of the correction if you didn't specify it in step 7. |
    | Signatory type                                                   | Select the person who signs the accounting reporting: **Taxpayer** or **Representative**. |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory. |
    | Representative company                                           | If you selected **Representative** as the signatory type, and if the representative is an organization, enter the name of the organization. |
    | Representative document                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |

10. On the first **Records to include** FastTab, apply a filter for separate divisions, if this type of filter is applicable. In this case, declarations will be generated only for the selected separate divisions.
11. On the second **Records to include** FastTab, apply a filter for tax authorities, if this type of filter is applicable. In this case, declarations will be generated only for the selected tax authorities.
12. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs during generation, the status is changed to **Technical error**.
13. On the **Action log** FastTab, review all user actions for the current message.
14. To review the report that is generated, select the **Attachments** button (the paper clip symbol) in the upper-right corner of the page, and then select **Open** to view the file.

You must also manually upload the generated file to the special third-party software for data preview, data updates, and transfer of the assessed tax declaration or assessed tax advance payments calculation files to the tax authorities through the communication channels.

## Create and post assessed tax ledger transactions

After you've calculated and approved tax registers, and generated an assessed tax declaration, you can create transactions for assessed tax accruals. Follow these steps.

1. Go to **Fixed assets (Russia) \> Journals \> Tax register journal**.
2. Select the journal, and then select **Ledger journal \> Assessed tax**.
3. Select **New**.
4. In the **Name** field, select the name of the assessed tax journal.
5. Select **Lines** to view the journal lines that have assessed tax accrual transactions that were created based on the tax register data and the settings of Fixed assets parameters.
6. Validate and post the journal.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]