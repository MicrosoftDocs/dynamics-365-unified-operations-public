---
title: Post TDS/TCS on non-filers at a higher rate of tax
description: Learn how to post Tax Deducted at Source (TDS)/Tax Collected at Source (TCS) on non-filers at a higher rate of tax, including outlines on setting up filers.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form: 
ms.dyn365.ops.version: 
---

# Post TDS/TCS on non-filers at a higher rate of tax

[!include [banner](../../includes/banner.md)]

This article explains how to post Tax Deducted at Source (TDS) and Tax Collected at Source (TCS) on non-filers at a higher rate of tax in Microsoft Dynamics 365.
Section 206AB of the Income Tax Act was recently introduced by the Finance Act, 2021. It applies to any sum or income, or the amount paid, payable, or credited by one person (referred to as the deductee) to a "specified person." A "specified person" is someone who didn't file income tax returns for the two assessment years that are relevant to the two previous years that immediately precede the previous year in which tax must be either deducted or collected.
The following conditions must also be verified:

- The time limit for filing tax returns under subsection (1) of section 139 of the Act expired for both assessment years.
- The aggregate of TDS and TCS in this case is 50,000 Indian rupees (Rs. 50,000) or more in each of the two previous years.
- The specified person isn't a non-resident who doesn't have a permanent establishment in India.

Additionally, section 206AB doesn't apply in cases where the tax must be deducted under section 192, 192A, 194B, 194BB, 194LBC, or 194N of the Act.

## Check income tax return filings to determine the applicability of section 206AB

The government is expected to provide a new utility for its income tax software, so that a deductor or collector can get the details of their income tax return filings when they enter the permanent account number (PAN) of the buyer or seller.
However, the assessee should keep a copy of the supplier's income tax returns for the previous two financial years as confirmation, to ensure that TDS or TCS is correctly deducted or collected at the applicable rate.
This provision might be an additional burden on the taxpayer. However, it's an extra step that the government took to catch people who don't file their income tax returns even when their tax is deducted or collected and is shown in 26AS.
Given the preceding provisions, if you fall under the purview of section 194Q (if you're a buyer of goods) or section 206(1H) (if you're a seller of goods), as of July 1, 2021, you must determine whether the counterparty filed its income tax returns for the previous two financial years. (Because the applicability is from July 1, 2021, the previous two financial years are 2019–202020 and 2020–2021.) You must also determine whether the aggregate of TDS/TCS is Rs. 50,000 or more in each of the previous two financial years. If it is, the TDS/TCS is charged at a higher rate under section 206AB (unless section 192, 192A, 194B, 194BB, 194LBC, or 194N of the Act applies).

## Applicability of sections 206AA and 206CCA

Section 206AB comes after the previously existing section 206AA of the Act. Another new section, 206CCA, comes after the previously existing section 206CC. The existing sections provide for a higher rate of TDS/TCS when no PAN is provided.

**Section 206AA**: This section applies when the specified person doesn't provide PAN information.
**Section 206AB**: This section applies when the specified person doesn't file income tax returns for the last two years.

Under each section, the person who is responsible for either deducting or collecting the tax must apply the tax rate described in the following table.

| Section   206AA: Failure to submit PAN information                                                                                                                                                                 | Section 206AB: Failure to file   returns for the last two years                                                                                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tax   must be deducted at the highest of the following rates: <br>- The rate   that is specified in the relevant provision of the Act.  <br>- The rate or rates that are in   effect. <br>- A rate of 20 percent.  | Tax must be deducted at the   highest of the following rates: <br>- Two times the rate that is   specified in the relevant provision fo the Act. <br> - Two times the   rate or rates that are in effect. >br>- A rate of five percent.  |

**Section 206CC**: This section applies when the specified person doesn't provide PAN information.
**Section 206 CCA**: This section applies when the specified person doesn't file income tax returns for the last two years.

Under each section, the person responsible for collecting the tax must apply the tax rate described in the following table.

| Section   206CC: Failure to submit PAN information                                                                                                                                | Section 206CCA: Failure to file   returns for the last two years                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tax   must be collected at the higher of the following rates: <br>- Two times   the rate that is specified in the relevant provision of the Act. <br>-   A rate of five percent.  | Tax must be collected at the   higher of the following rates: <br> Two times the rate that is   specified in the relevant provision of the Act. <br> - A rate of five   percent.  |

Furthermore, subsection (2) of section 206AB provides for cases where both sections 206AA and 206AB are applicable (that is, the specified person doesn't provide PAN information and also doesn't file income tax returns for the last two years). In these cases, the tax must be deducted at the higher rate between both sections. In other words, TDS must be deducted at the higher of the rate under section 206AA and the rate under section 206AB.

The following illustration summarizes the tax rates under sections 206AA and/or 206AB.

 :::image type="content" source="../media/tds-higher-rate-01.png" alt-text="Summary of tax rates under sections 206AA and/or 206AB.":::

The following illustration summarizes the tax rates under sections 206CC and/or 206CCA.

 :::image type="content" source="../media/tds-higher-rate-02.png" alt-text="Summary of tax rates under sections 206CC and/or 206CCA.":::

## Set up TDS and TCS at a higher rate for non-filers of returns

Set up TDS and TCS at a higher rate for non-filers of income tax returns in two ways:

- Recommended approach: Define an additional threshold definition for a specific TDS or TCS type.
- Create an additional withholding tax code and withholding tax group for a specific TDS or TCS type.

Define a threshold definition for the Rent TDS type

1. Go to **Tax** > **Set up** > **Withholding tax** > **Threshold definitions**.
1. Select **New**.
1. In the **Name** field, enter **Rent**.
1. In the **Description** field, enter **Rent-194 I**.

   :::image type="content" source="../media/tds-higher-rate-03.png" alt-text="Screenshot of the Description field, Rent-194 I.":::
  
### Create an additional threshold definition for non-filing of returns

1. Go to **Tax** > **Set up** > **Withholding tax** > **Threshold definitions**.
1. Select **New**.
1. In the **Name** field, enter **Rent RNF**.
1. In the **Description** field, enter **Rent-194I return not filed**.

   :::image type="content" source="../media/tds-higher-rate-04.png" alt-text="Screenshot of the Description field, Rent-194I return not filed.":::

1. Select **Threshold designer**.
1. On the **Threshold designer** page, select **Rent**, then select **New** to define the first slab.
1. On the **General** FastTab, in the **Effective from** field, enter **4/1/2021** (April 1, 2021). In the **Effective to** field, enter **3/31/2022** (March 31, 2022).
1. In the **Lower limit** field, enter **0.00**. In the **Upper limit** field, enter **240,000.00**.
1. On the **Calculation** FastTab, in the **Type** field, select **Cumulative**.
1. Set the **Final level** option to **Yes**.

   :::image type="content" source="../media/tds-higher-rate-05.png" alt-text="Screenshot of the Final level option set to Yes.":::

1. Select **New** again to define the second slab.
1. On the **General** FastTab, in the **Effective from** field, enter **4/1/2021**. In the **Effective to** field, enter **3/31/2022**.
1. In the **Lower limit** field, enter **240,000.00**. In the **Upper limit** field, enter **0.00**.
1. On the **Calculation** FastTab, in the **Type** field, select **Cumulative**.
1. Set the **Final level** option to **Yes**.

   :::image type="content" source="../media/tds-higher-rate-06.png" alt-text="Screenshot of the second slab, Final level option set to Yes.":::
  
1. Close the **Threshold designer** page.

### Define a threshold definition for non-filing of returns

1. Go to **Tax** > **Set up** > **Withholding tax** > **Threshold definitions**.
1. Select **Threshold designer**.
1. On the **Threshold designer** page, select **Rent RNF**, then select **New** to define the first slab.
1. On the **General** FastTab, in the **Effective from** field, enter **4/1/2021**. In the **Effective to** field, enter **3/31/2022**.
1. In the **Lower limit** field, enter **0.00**. In the **Upper limit** field, enter **240,000.00**.
1. On the **Calculation** FastTab, in the **Type** field, select **Cumulative**.
1. Set the **Final level** option to **Yes**.

   :::image type="content" source="../media/tds-higher-rate-07.png" alt-text="Screenshot of the threshold definitions Final level option set to Yes.":::
  
1. Select **New** again to define the second slab.
1. On the **General** FastTab, in the **Effective from** field, enter **4/1/2021**. In the **Effective to** field, enter **3/31/2022**.
1. In the **Lower limit** field, enter **240,000.00**. In the **Upper limit** field, enter **0.00**.
1. On the **Calculation** FastTab, in the **Type** field, select **Cumulative**.
1. Set the **Final level** option to **Yes**.

   :::image type="content" source="../media/tds-higher-rate-08.png" alt-text="Screenshot of the second slab, threshold definitions Final level option set to Yes.":::

1. Close the **Threshold designer** page.

### Create a withholding tax component group for rent

1. Go to **Tax** > **Setup** > **Withholding tax component groups**.
1. Select **New**.
1. In the **Tax type** field, select **TDS**.
1. In the **Withholding tax component group** field, select **Rent**.
1. On the **General** FastTab, in the **Status** field, select **Resident**.
1. In the **Section code** field, enter **94 I**.
1. Close the page.

   :::image type="content" source="../media/tds-higher-rate-09.png" alt-text="Screenshot of the withholding tax component group for rent.":::

### Create a withholding tax component for rent

1. Go to **Tax** > **Setup** > **Withholding tax component**.
1. Select **New**.
1. In the **Tax type** field, select **TDS**.
1. In the **Withholding tax component** and **Description** fields, select **Rent**.

   :::image type="content" source="../media/tds-higher-rate-10.png" alt-text="Screenshot of the withholding tax component for rent.":::

### Create a withholding tax code for rent

1. Go to **Tax** > **Withholding tax codes**.
1. Select **New**.
1. In the **Withholding tax code** field, select **Rent 194 I**.
1. In the **Withholding tax name** field, enter **Rent new law**.
1. On the **General** FastTab, set the following values:

   - **Currency**: INR
   - **Main account**: 202122
   - **Settlement period**: TDS
   - **Tax type**: TDS
   - **Enable threshold hierarchy**: Yes
   - **Withholding tax component**: Rent

     :::image type="content" source="../media/tds-higher-rate-11.png" alt-text="Screenshot of the General FastTab, withholding tax code for rent fields.":::

1. Select **Threshold references**.
1. On the **Threshold references** page, select **New**, and set the following values:

   - **Account type**: Vendor
   - **Account code**: Group
   - **Account or group**: 60
   - **Threshold**: Rent RNF

     > [!NOTE]
     > Create a separate group for vendors that didn't file income tax returns for the last two years. Then attach the group to the appropriate vendor records.

1. Select **New** again, and set the following values:

   - **Account type**: Vendor
   - **Account code**: All
   - **Threshold**: Rent

   You can leave the **Account or group** field blank for this threshold reference.

   :::image type="content" source="../media/tds-higher-rate-12.png" alt-text="Screenshot of the Account or group field.":::

1. Select **Threshold designer**.
1. On the **Threshold designer** page, select the first cumulative line that has the **Rent RNF** threshold. Then, on the **Tax value** FastTab, select **New**, and set the following values:

   - **PAN status**: Not available
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 0.00

1. Select **New** again, and set the following values:

   - **PAN status**: Received
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 0.00

1. Select the second cumulative line. Then, on the **Tax value** FastTab, select **New**, and set the following values:

   - **PAN status**: Not available
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 20.00

1. Select **New** again, and set the following values:

   - **PAN status**: Received
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 20.00

1. Close the **Threshold designer** page.
1. On the **Threshold references** page, select **New**, and set the following values:

   - **Account type**: Vendor
   - **Account code**: All
   - **Threshold**: Rent

     :::image type="content" source="../media/tds-higher-rate-15.png" alt-text="Screenshot of the new threshold reference for vendor.":::

1. Select **Threshold designer**.
1. Select the first cumulative line. Then, on the **Tax value** FastTab, select **New**, and set the following values:

   - **PAN status**: Not available
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 0.00
 
1. Select **New** again, and set the following values:

   - **PAN status**: Received
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 0.00

1. Select the second cumulative line. Then, on the **Tax value** FastTab, select **New**, and set the following values:

   - **PAN status**: Not available
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 20.00

1. Select **New** again, and set the following values:

   - **PAN status**: Received
   - **Calculate previously nontaxed**: Yes
   - **Calculate tax**: Yes
   - **Include in turnover base**: Yes
   - **Value**: 10.00

1. Close the **Threshold designer** page.
1. Go to **Tax** > **Indirect taxes** > **Withholding tax** > **Withholding tax groups**.
1. Select **New**, and set the following values:

   - **Withholding tax group**: Rent 194 I 
   - **Description**: Rent 194 I New law
   - **Tax type**: TDS

### Create the Rent 194 I withholding tax group

1. Go to **Tax** > **Withholding tax** > **Withholding tax code**.
1. Select **New**, and name the new withholding tax group **Rent 194 I**.
1. On the **Setup** FastTab, select **Add**.
1. In the **Withholding tax code** field, select **Rent 194 I**.

   :::image type="content" source="../media/tds-higher-rate-18.png" alt-text="Screenshot of the Withholding tax code field, Rent 194 I.":::

1. Select **Designer**.
1. On the **Designer** page, select **New**.
1. In the **Tax code** field, select **Rent 194 I**.

   :::image type="content" source="../media/tds-higher-rate-19.png" alt-text="Screenshot of the Tax code field, Rent 194 I.":::

1. Close the **Designer** page.

### Attach the withholding tax group to a vendor account

1. Go to **Accounts payable** > **Vendors**.
1. In the list, select vendor account **INMF-000005**.
1. In the **Group** field, select **60**.
1. On the **Invoice and delivery** FastTab, set the **Calculate withholding tax** option to **Yes**.
1. In the **TDS group** field, select **Rent 194 I**.

   :::image type="content" source="../media/tds-higher-rate-20.png" alt-text="Screenshot of the TDS group field, Rent 194 I.":::

### Update the PAN information for a vendor

1. Go to **Accounts payable** > **Vendors**.
1. Open the record for the vendor that you're working with.
1. On the **Vendor details** page, on the **Tax information** FastTab, in the **PAN information** section, in the **Status** field, select **Received**.
1. In the **Number** field, enter **AUNPP6767E**.
1. Close the page.

   :::image type="content" source="../media/tds-higher-rate-21.png" alt-text="Screenshot of the Tax information FastTab.":::

## Example scenarios

This section describes two scenarios and shows the steps that are involved, depending on whether a vendor files income tax returns for the last two years and provides PAN information.

- **Scenario 1**: The vendor doesn't file income tax returns for the last two years.

  - The normal tax rate for Rent (company) is 10 percent.
  - Under the new provision, the higher of the following rates applies:

  - Two times the specified rate (for example, 20 percent)
  - A rate of 5 percent

- **Scenario 2**: The vendor files income tax returns for the last two years.

### Scenario 1: The vendor didn't file returns for the last two years and didn't provide PAN information

In this scenario, the vendor didn't file income tax returns for the last two years and didn't provide PAN information. Follow these steps to create and post the invoice journal for the vendor.

1. Go to **Accounts payable** > **Invoices** > **Vendor invoice journal**.
1. Select **New**.
1. In the **Account type** field, select **Vendor**. Then, in the **Account** field, select **INMF-000005**.
1. In the **Invoice** field, select **IN-8**.
1. In the **Credit** field, enter **250,000.00**.
1. In the **Offset account type** field, select **Ledger**. Then, in the **Offset account** field, select **600120**.

   :::image type="content" source="../media/tds-higher-rate-22.png" alt-text="Screenshot of the new vendor invoice journal line for scenario 1.":::

1. Select **Withholding tax**.
1. On the **Temporary withholding tax transactions** page, notice that the withholding tax is calculated at the defined rate of 20.0 percent for this vendor, because the vendor didn't file income tax returns for the last two years.

   :::image type="content" source="../media/tds-higher-rate-23.png" alt-text="Screenshot of the Temporary withholding tax transactions page for scenario 1.":::

### Scenario 2: The vendor files returns for the last two years and provides PAN information

In this scenario, the vendor files income tax returns for the last two years and provides PAN information. Follow these steps to create and post the invoice journal for the vendor.

1. Go to **Accounts payable** > **Invoices** > **Vendor invoice journal**.
1. Select **New**.
1. In the **Account type** field, select **Vendor**. Then, in the **Account** field, select **INMF-000001**.
1. In the **Invoice** field, select **IN-06**.
1. In the **Credit** field, enter **250000.00**.
1. In the **Offset account type** field, select **Ledger**. Then, in the **Offset account** field, select **600150**.

   :::image type="content" source="../media/tds-higher-rate-24.png" alt-text="Screenshot of the new vendor invoice journal line for scenario 2.":::

1. Select **Withholding tax**.
1. On the **Temporary withholding tax transactions** page, notice that the withholding tax is calculated at the defined rate of 10.0 percent.

   :::image type="content" source="../media/tds-higher-rate-25.png" alt-text="Screenshot of the Temporary withholding tax transactions page for scenario 2.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]