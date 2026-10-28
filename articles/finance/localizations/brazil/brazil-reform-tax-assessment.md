---
title: Tax assessment in Brazil Reformed Tax (Preview)
description: Learn how to generate booking periods, run CBS and IBS tax assessments, post the tax payment, and finalize the tax assessment for Brazil tax reform in Microsoft Dynamics 365 Finance.
author: yananSong
ms.author: yanansong
ms.topic: how-to
ms.date: 10/27/2026
ms.custom: bap-template
ms.service: dynamics-365-finance
---

# Tax assessment in Brazil Reformed Tax (Preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!IMPORTANT]
> This feature is in preview. Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

In Brazil tax reform, tax assessments for CBS and IBS run for each fiscal establishment and each monthly booking period. The tax assessment summarizes the debits and credits of the period, takes into account the debits that are already extinguished, and calculates the balance to pay or carry forward.

Before you run the tax assessment, import the results of the assisted assessment (*apuração assistida*) from the tax authority. The results show how each debit is settled, or *extinguished* (*extinção*), for example, when a CBS debit is offset by CBS credits. For more information, see [Tax assessment APIs in Brazil Reformed Tax](brazil-reform-tax-assessment-api.md).

## How the process works

The tax assessment process has three phases. The following diagram shows the steps of each phase.

:::image type="content" source="media/brazil-reform-tax-assessment-workflow.png" alt-text="Diagram of the tax assessment workflow in three phases. Phase A, one-time setup: step 1, setup. Phase B, CBS debit extinction, before you generate the booking periods: step 2, post the invoice; step 3, download the JSON file outside Finance; step 4, import the JSON file; step 5, the batch job runs. For a partial extinction, steps 4 and 5 are repeated for each file. Phase C, tax assessment, monthly for each booking period: step 6, generate booking periods; step 7, synchronize; step 8, create the assessment; step 9, review; step 10, tax payment; step 11, verify the general ledger vouchers; step 12, finalize." lightbox="media/brazil-reform-tax-assessment-workflow.png":::

**A. One-time setup.** Complete the setup once before you start.

1. **Setup.** Import the ER configurations, and set up the tax calculation parameters, the CBS model mapping, the tax adjustment journal, and the payable and settlement accounts. For more information, see [Setup](#step-1-setup).

**B. CBS debit extinction.** Complete this phase before you generate the booking periods.

1. **Post the invoice.** When a sales invoice that has CBS is posted, the system creates a CBS debit for each CBS tax transaction. For more information, see [Post the invoices](brazil-reform-tax-assessment-api.md#step-2-post-the-invoice).
1. **Download the JSON file.** Download the CBS assisted assessment result from the Receita Federal. You download the file outside Finance, either manually or through your own integration. For more information, see [Download the CBS assisted assessment result](brazil-reform-tax-assessment-api.md#step-3-download-the-cbs-assisted-assessment-result).
1. **Import the JSON file.** Import the file by using **Import CBS debit calculation result**. For more information, see [Import the assessment result into Finance](brazil-reform-tax-assessment-api.md#step-4-import-the-assessment-result-into-finance).
1. **Let the batch job run.** The **Process Brazil tax debit staging** batch job matches each debit with its extinction method, such as a CBS credit, and posts the extinction. Wait until the batch job has the **Ended** status. For more information, see [Monitor the batch job](brazil-reform-tax-assessment-api.md#step-5-monitor-the-batch-job).

    For a partial extinction, repeat steps 4 and 5 for each file, one file at a time. For more information, see [Partial extinction](brazil-reform-tax-assessment-api.md#partial-extinction-repeat-steps-4-and-5-for-each-file).

**C. Tax assessment.** Complete this phase every month, for each booking period.

1. **Generate the booking periods.** For more information, see [Generate booking periods](#step-6-generate-booking-periods).
1. **Synchronize the booking period.** Synchronization links the fiscal documents of the period to the booking period. For more information, see [Synchronize the booking period](#step-7-synchronize-the-booking-period).
1. **Create the tax assessment.** Create the CBS or IBS tax assessment for the period. For more information, see [Create a tax assessment](#step-8-create-a-tax-assessment).
1. **Review the tax assessment.** Review the credits, debits, extinguished amount, and balance. For more information, see [Review the tax assessment](#step-9-review-the-tax-assessment).
1. **Create and post the tax payment.** For more information, see [Create and post the tax payment](#step-10-create-and-post-the-tax-payment).
1. **Verify the vouchers in the general ledger.** Verify the extinction voucher and the tax payment voucher. For more information, see [Verify the vouchers in the general ledger](#step-11-verify-the-vouchers-in-the-general-ledger).
1. **Finalize the tax assessment.** For more information, see [Finalize the tax assessment](#step-12-finalize-the-tax-assessment).

## Prerequisites

- The Brazil reformed tax setup is complete. For more information, see [Brazil tax reform setup](brazil-reform-setup.md).
- The CBS and IBS tax codes are set up, and sales invoices calculate CBS and IBS.
- The posting groups and other required fiscal records are set up for the fiscal establishment.

## Phase A: One-time setup

Complete the setup once, before you start.

### Step 1: Setup

Complete the following setup one time for each environment, before you post the invoices that you want to extinguish.

#### Import the Electronic reporting configurations

The import of the CBS debit calculation result is driven by Electronic reporting (ER). Importing the ER configurations is the first step.

To import the Electronic reporting configurations, follow these steps:

1. Go to the **Globalization studio** workspace, and select **Electronic reporting** > **Configurations**.
1. If the CBS tax assessment configurations aren't already present, import the provided configuration files from the Microsoft configuration provider.
1. Verify that the required models and formats appear under **Reporting configurations** for the Microsoft provider.

<!-- SME REVIEW: Confirm the navigation path and the names of the CBS debit assessment ER configurations. These configurations aren't in the download list on the Brazil tax reform setup page. -->

#### Set up the tax parameters

The batch job that processes the import depends on the tax parameters.

To set up the tax parameters, follow theses steps:

1. Go to **Tax** > **Setup** > **Parameters** > **Tax calculation parameters**.
1. Confirm that the tax calculation parameters, the generalized tax parameters, and the sales tax settings are configured.

#### Select the CBS debit assessment model mapping

To select the CBS debit assessment model mapping, follow these steps:

1. Go to **Tax** > **Setup** > **Fiscal books parameters**.

<!-- SME REVIEW: The screenshots show Fiscal books as a separate module (Fiscal books > Common > Booking period). Confirm whether this path is Fiscal books > Setup > Fiscal books parameters. The same applies to the Ledger posting groups path below. -->
1. On the **CBS setup** tab, in the **Electronic reporting** section, select the **CBS debit assessment model mapping**.
1. Select **Save**.

#### Set up the tax adjustment journal

The extinction is posted through a tax adjustment journal. To set up the tax adjustment journal, follow these steps:

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **Sales tax** tab, in the **Tax adjustment journal** field, select the journal name to use for tax assessment.

#### Set up the CBS payable and settlement accounts

Set up the main accounts that are used when the CBS tax amount is posted and offset when the debit is extinguished.

To set up the CBS payable and settlement accounts, follow these steps:

1. Go to **Tax** > **Setup** > **Fiscal books parameters** > **Ledger posting groups**.
1. Open the posting group that the CBS tax code uses.
1. In the **Brazil tax reform – accounts to be allocated** field, set the following accounts:

    - **Payable** – The account that records the CBS tax liability.
    - **Settlement** – The account that receives the offset when the CBS debit is extinguished.

> [!IMPORTANT]
> Use the main accounts that your organization approved for the legal entity and fiscal establishment. Account numbers are specific to each environment.

## Phase B: CBS debit extinction

Complete this phase before you generate the booking periods. Post the invoices, and then import and process the CBS assisted assessment results:

- Step 2: Post the invoice.
- Step 3: Download the CBS assisted assessment result.
- Step 4: Import the assessment result into Finance.
- Step 5: Monitor the batch job.

For partial extinction, repeat steps 4 and 5 for each file, one file at a time.

For the detailed steps, see [CBS debit](brazil-reform-tax-assessment-api.md#cbs-debit) in Tax assessment APIs in Brazil Reformed Tax.

## Phase C: Tax assessment

Complete this phase every month, for each booking period.

### Step 6: Generate booking periods

After you import and process the CBS assisted assessment results, generate the booking periods.

A booking period represents one month for one fiscal establishment. Each booking period contains the tax assessments that you select when you create it.

Booking periods are sequential. You can't create a period if the previous period is missing. Start with the earliest required period, and create each month in order until you reach the period that you want to assess.

To generate booking periods, follow these steps:

1. Go to **Fiscal books** > **Common** > **Booking period**.

    <!-- SME REVIEW: The private preview guide uses Tax > Periodic > Brazil > Booking period. The screenshots show Fiscal books > Common > Booking period. Confirm the path for the release. -->

1. Review the existing booking periods for the fiscal establishment. Reuse existing records. Don't create a duplicate period.
1. On the Action Pane, on the **General** tab, in the **New** group, select **Generate**.
1. In the **Generate booking periods** wizard, on the **Booking period wizard** page, select **Next**.
1. On the **Select the fiscal organization or fiscal establishment** page, move the fiscal establishment, such as **Matriz**, from the **Available** list to the **Selected** list. You can select a fiscal organization to create booking periods for all its fiscal establishments. Select **Next**.
1. On the **Specify the booking periods to create** page, set the **Month** and **Year** for the **Start period** and the **End period**. Select **Next**.
1. On the **Select the tax assessment types** page, set the reformed tax assessments to **Yes**:

    - **CBS**
    - **IBS-State**
    - **IBS-City**

    Leave the legacy tax assessments, such as **ICMS**, **ICMS-ST**, **ISS**, and **IPI**, set to **No** unless you also assess them in this period. Select **Next**.

1. On the **Create booking periods** page, review the booking periods and selected tax assessments that you'll create, and then select **Finish**.

The new booking period appears in the list on the **Booking period** page, such as **Matriz**, **October 2026**.

### Step 7: Synchronize the booking period

Synchronization links the eligible tax documents of the period to the booking period.

To synchronize the booking period, follow these steps:

1. On the **Booking period** page, select the booking period.
1. On the Action Pane, on the **General** tab, in the **Maintain** group, select **Sync**.

> [!TIP]
> If the documents of the period aren't linked after synchronization, check that all previous booking periods exist, that the posting group setup for the fiscal establishment is complete, and that the documents were posted for the selected fiscal establishment and period.

### Step 8: Create a tax assessment

The following steps use the CBS tax assessment as an example. The IBS tax assessment works in the same way.

1. On the **Booking period** page, select the booking period.
1. On the Action Pane, on the **General** tab, in the **Assessment** group, select **CBS**. The **CBS** tax assessment page opens for the selected period, for example, **CBS | October : 2026**.
1. In the **New** group, select **CBS tax assessment**.
1. In the **New tax assessment** dialog box, review the **Booking period**, **Company**, **State**, **Month**, and **Year** fields.
1. Optionally, set **Run in batch** to **Yes** to run the assessment in the background.
1. Select **OK**.

The tax assessment is created with the **Opened** assessment status. The **From date** and **To date** columns show the first and last days of the period.

You can also open the tax assessments from the navigation pane. Go to **Fiscal books** > **Common** > **Tax assessment**, and select **CBS** or **IBS**.

### Step 9: Review the tax assessment

Select the tax assessment. The **CBS tax assessment summary** in the **Related information** pane shows the totals of the assessment.

| Section | Field | Description |
| --- | --- | --- |
| Credits | Credit previous period | The credit balance that carries forward from the previous period. |
| Credits | Credit | The CBS credits of the period, such as from purchase documents. |
| Credits | Total credit amount released | The total credit amount that's released. |
| Debits | Debits | The CBS debits of the period, such as from sales invoices. |
| Debits | Extincted amount | The debit amount that's already extinguished, according to the imported CBS assisted assessment results. |
| Totals | Credit balance | The remaining credit to carry forward to the next period. |
| Totals | Debit balance | The remaining amount to pay. |
| Tax payment | Total amount | The amount of the posted tax payments. |

For example, a period has CBS debits of 9.00 and CBS credits of 1.35, and no debit is extinguished. The debit balance is 9.00 – 1.35 = 7.65.

Select **Refresh** to update the summary.

To review the details of the assessment, use the following options in the **View** group:

- **Fiscal documents** – View the fiscal documents of the period, such as debit notes and credit notes, with their status, model, series, number, and amounts.
- **Tax transactions** – View the tax transactions that are included in the assessment. Each transaction shows its **Tax type**, **Tax assessment classification**, tax base amount, amount, cClassTrib code, and voucher.
- **Tax summary** – View the totals of the assessment.

The **Tax assessment classification** of each transaction shows how it's included in the assessment, such as:

- **Document debit**
- **Document credit**
- **Credit balance from previous period**
- **Informative**

#### Use the reform tax assessment inquiry

To review the reformed tax transactions across tax types, go to **Fiscal books** > **Common** > **Tax assessment** > **Reform tax assessment**. The inquiry shows the CBS, IBS-State, and IBS-City lines with the **Tax assessment classification**, **CFOP**, **cClassTrib**, **Tax base amount**, **Taxable amount**, **Sales tax amount**, and **Extincted amount** of each line.

### Step 10: Create and post the tax payment

The tax payment settles the debit balance of the assessment. To create and post the tax payment, follow these steps:

1. On the tax assessment page, select the tax assessment.
1. In the **Update** group, select **Tax payment**. The **Tax payment** page opens for the period.
1. On the Action Pane, select **Create from assessment**. A payment line is created with the **Periodic** payment type. The **Sales tax amount** and **Amount** fields are set to the debit balance of the assessment, for example, **7.65**.
1. Complete the payment line:

    | Field | Description |
    | --- | --- |
    | Date | The payment date. |
    | Receita Code | The revenue code of the payment. |
    | Due date | The due date of the payment, for example, the last day of the period. |
    | Interest amount | The interest amount, if any. |
    | Fine amount | The fine amount, if any. |
    | Reference month | The reference month of the payment. |

1. On the **General** FastTab, review the **Authority** and **Company** fields.
1. Select **Save**.
1. Select **Post**.

When you post the payment, a message confirms that the voucher is posted, for example, "Voucher BRMF-4008 has been posted." The voucher number appears in the **Voucher** column. To review the posting, select **Voucher**, **Tax transactions**, or **Transactions**.

After you post the payment, the **Total amount** in the **Tax payment** section of the tax assessment summary shows the paid amount.

### Step 11: Verify the vouchers in the general ledger

After the tax payment posts, verify the vouchers in the general ledger. This step verifies both the extinction and the tax payment.

To verify the vouchers in the general ledger, follow these steps:

1. Go to **General ledger** > **Inquiries and reports** > **Voucher transactions**.
1. Find the extinction voucher. Verify that it's posted with the CBS debit and offset amounts on the payable and settlement accounts that you set up. You can also find the posted tax adjustment journal in **General ledger** > **Journal entries** > **General journals** by changing the **Show** filter to **Posted**. If you imported a partial extinction, verify that all portions are posted.
1. Find the tax payment voucher, for example, **BRMF-4008**. Verify that it's posted with the amount of the tax payment.

### Step 12: Finalize the tax assessment

After you verify the vouchers in the general ledger, finalize the tax assessment. To finalize the tax assessment, follow these steps:

1. On the tax assessment page, select the tax assessment.
1. In the **Actions** group, select **Finalize**.

To make changes after you finalize the assessment, select **Reopen**.

In the **Update** group, you can also select **Credit previous period** to manage the credit balance that's carried forward from the previous period.

<!-- SME REVIEW: The screenshots show the tax payment created and posted while the assessment status is Opened, and Finalize isn't selected. Confirm that Finalize is done after the tax payment, and confirm the options under Credit previous period. -->

## Key points

- Booking periods must exist in an unbroken monthly sequence. Generate every period from the required start month through the period that you want to assess.
- Select the reformed tax assessments (**CBS**, **IBS-State**, and **IBS-City**) when you generate the booking period.
- Synchronize the booking period before you create the tax assessment.
- Import and process the CBS assisted assessment results before you generate the booking periods, so that the extinguished amounts are included in the assessment.
- Create the tax payment from the assessment so that the amount matches the debit balance.
- Verify the extinction and tax payment vouchers in the general ledger before you finalize the tax assessment.

## Related information

- [Brazil tax reform overview](brazil-reform-overview.md)
- [Brazil tax reform setup](brazil-reform-setup.md)
- [Tax assessment APIs in Brazil Reformed Tax](brazil-reform-tax-assessment-api.md)
