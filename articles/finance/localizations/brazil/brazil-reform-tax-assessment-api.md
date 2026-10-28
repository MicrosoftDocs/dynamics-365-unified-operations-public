---
title: Tax assessment APIs in Brazil Reformed Tax (Preview)
description: Learn how to import the assisted assessment results from the tax authority APIs into Microsoft Dynamics 365 Finance for the Brazil tax reform tax assessment.
author: yananSong
ms.author: yanansong
ms.topic: how-to
ms.date: 10/27/2026
ms.custom: bap-template
ms.service: dynamics-365-finance
---

# Tax assessment APIs in Brazil Reformed Tax (Preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!IMPORTANT]
> This feature is in preview. Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

In Brazil tax reform, the tax authority runs an assisted assessment (*apuração assistida*). It collects the debits and credits from the fiscal documents that are issued and determines how each debit is settled. Settling a debit is called *extinction* (*extinção*), for example, when a CBS debit is offset by CBS credits. A debit can be fully extinguished at one time, or partially extinguished by several credit portions.

You get the results of the assisted assessment through the tax authority APIs and import them into Finance. The imported results are included in the tax assessment of the period. For more information about the whole process, see [Tax assessment in Brazil Reformed Tax](brazil-reform-tax-assessment.md).

This article describes the following APIs:

- [CBS debit](#cbs-debit)

<!-- AUTHOR NOTE: Add an H2 section for each new API (for example, CBS credit and IBS) when it's released, and add it to the list above. -->

For more information about the CBS APIs, see the [Receita Federal API documentation for CBS assessment](https://docs.receitafederal.gov.br/apuracao-cbs/).

## Prerequisites

- The one-time setup of the tax assessment is complete. For more information, see [Step 1: Setup](brazil-reform-tax-assessment.md#step-1-setup).
- The CBS and IBS tax codes are set up, and sales invoices calculate CBS and IBS.

## CBS debit

Import the CBS debit assessment results before you generate the booking periods. These steps are Phase B of the tax assessment process. The step numbers are the same as in [Tax assessment in Brazil Reformed Tax](brazil-reform-tax-assessment.md). For partial extinction, repeat steps 4 and 5 for each file, one file at a time.

### Step 2: Post the invoice

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**, and select **New**.
1. Create a sales order for a Brazilian customer, and add a line with an item, quantity, and unit price.
1. In **Line details**, on the **Setup** tab, confirm that the CFOP, the sales tax groups, and the tax reform groups are set.
1. On the Action Pane, select **Invoice** \> **Invoice**.
1. Select **Sales tax** to review the **Sales tax transactions** page. Confirm that the CBS and IBS lines, such as **CBSRED**, **IBSCRED**, and **IBSSRED**, appear together with the legacy tax lines.
1. In the **No posting** column, confirm that the CBS and IBS lines are set to post.
1. Post the invoice.

For more information, see [Calculation in Sales order in Brazil Reformed Tax](brazil-reform-calculation-sales-order.md).

When you post the invoice, the system creates one CBS debit status record for each tax transaction. The extinguished amount of the debit is **0**. No extinction matching exists until you import and process an assessment result.

### Step 3: Download the CBS assisted assessment result

After the Receita Federal assesses the period, download the CBS debit assessment result through the CBS APIs. Finance doesn't connect to the CBS APIs. Download the file outside Finance in one of the following ways:

- **Manually** – Download the JSON file from the Receita Federal.
- **Through an integration** – Use your own integration or a partner solution that calls the CBS APIs and saves the JSON file.

Save the JSON file to a location that you can access from Finance.

Don't edit the file that you downloaded. It's the official assessment of the tax authority. Finance imports the file in the format that the CBS APIs return, so no conversion is required.

To test the process in a test environment without a downloaded file, see [Optional: Test with a sample payload](#optional-test-with-a-sample-payload).

### Step 4: Import the assessment result into Finance

Manually import each downloaded JSON file. Finance doesn't import the file automatically.

Before you import a file, ensure that:

- You're in the same legal entity where the invoice was posted.
- The invoice is posted in Finance. Finance matches each debit in the file to the posted invoice by its NF-e access key and invoice number.

1. Go to **Tax** \> **Periodic tasks** \> **Fiscal books** \> **Import CBS debit calculation result**.
1. Select **Browse**, and select the JSON file that you downloaded from the Receita Federal.
1. Optionally, set **Run in the background** to **Yes**.
1. Select **OK**.

<!-- SME REVIEW: Confirm the exact menu path for "Import CBS debit calculation result". -->

Verify that the import completes without a JSON or validation error. When the import succeeds, the system writes a debit update request to staging.

> [!IMPORTANT]
> Import each file only once. Every import adds the debits in the file to staging again, even if they were imported before.

### Step 5: Monitor the batch job

The **Process Brazil tax debit staging** batch job processes the imported requests on its normal cycle. The batch job moves the requests from staging to the extinction matching, and posts the extinction to the general ledger by using the tax adjustment journal. The batch job clears the staging records after it processes them.

The batch job runs in the standard batch framework. Monitor it on the standard **Batch jobs** page, the same way that you monitor other batch jobs.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Filter by company, and find the **Process Brazil tax debit staging** batch job.
1. Verify that the job status changes to **Ended**.
1. Select **Batch job history**, and then select **Logs** \> **Log**. In the summary line, verify that **invalid** is **0** and that there are no error lines.

> [!NOTE]
> The **Ended** status only means that the batch job finished. It doesn't mean that all debits were processed. Always check the log.

The batch job processes all debits that are waiting in staging in the legal entity, not only the debits from the last imported file. A debit that failed in an earlier import stays in staging and fails again on every run. Therefore, the log can show an error for an invoice or access key that isn't in the file that you just imported.

To run the batch job sooner than its normal cycle, open the batch job, and select **Change status** \> **Waiting**.

### Partial extinction: repeat steps 4 and 5 for each file

Several credit portions can extinguish a single CBS debit. Each portion is in a separate assessment result file. The system processes the portions sequentially, so you must import the files one at a time.

**Example:** A CBS debit of 2.48 is extinguished in three portions: 1.02, 0.80, and 0.68. You receive three files and import them one after the other.

<!-- SME REVIEW: As in the PDF, 1.02 + 0.80 + 0.68 = 2.50, not 2.48. Confirm the values. -->

1. Confirm that the invoice is posted. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Posted sales tax**, and confirm the CBS amount of the invoice.
1. Download the assessment result file for each portion. All files refer to the same debit invoice. Each file except the last one shows the debit as partially extinguished.
1. Import the first file as described in [Import the assessment result into Finance](#step-4-import-the-assessment-result-into-finance).
1. Refresh the **Batch jobs** page, and wait until the **Process Brazil tax debit staging** batch job has the **Ended** status, as described in [Monitor the batch job](#step-5-monitor-the-batch-job).
1. Repeat the import and wait for the batch job for each remaining file.

> [!IMPORTANT]
> Don't import all portions at the same time. Import one portion, wait until the batch job finishes processing it, and then import the next portion.

After each portion is processed, the extinguished amount of the debit increases, and a new extinction matching is created. After the last portion is processed, the debit is fully extinguished. The extinguished amount equals the total debit amount, and the amount that isn't extinguished is **0**.

### Optional: Test with a sample payload

> [!NOTE]
> This section applies only to test environments. In production, always import the file that you downloaded from the Receita Federal, and don't edit it.

In a test environment, you can test steps 4 and 5 without a downloaded file. Start from a sample payload, and edit it so that it matches an invoice that you posted. Then import it as described in [Step 4](#step-4-import-the-assessment-result-into-finance).

You can use a sample payload for a fully extinguished, partially extinguished, or not extinguished debit.

#### Link the sample debit to your invoice

The sample payload contains the access key and invoice number of another company's invoice. Replace them with the values of an invoice that you posted in Finance. Otherwise, Finance can't find the invoice, and the debit isn't processed.

1. Go to **Accounts receivable** \> **Fiscal documents** \> **All fiscal documents**, and select the fiscal document of the posted invoice.
1. Copy the value in the **Access key** column (44 digits). In the payload, paste it into **chaveDfe**.
1. Select **Original document**, and copy the **Invoice** value exactly, including any leading zeros and prefix. In the payload, paste it into **numeroDfe**.

**Example** (fictitious values):

```json
"chaveDfe": "35260812345678000195550010000000091876543210",
"numeroDfe": "001000000009",
```

<!-- SME REVIEW: Confirm the menu path and the "Original document" > "Invoice" field (from the CBS debit import fix steps guide). -->

Replace these two values only in the debit. Don't replace the access key and invoice number of the credits under **formasExtincao**. They refer to the documents that generated the credits.

#### Set the amounts

- Set **valorCBSTotal** to the total CBS amount of the debit.
- Set **valorCBSExtinto** to the amount that's extinguished.
- Set **valorCBSNaoExtinto** to the amount that remains.
- Set **situacaoDebito** to **Totalmente Extinto** for a full extinction or **Parcialmente Extinto** for a partial extinction.

#### Set the extinction forms

Under **formasExtincao**, list the ways that the debit is extinguished.

**Example:** To offset the debit with CBS credits, add the credits under **creditosCBS**.

- The invoice number and access key of a credit refer to the document that generated the credit. They don't have to match the debit invoice.
- If an extinction form isn't used, leave it as an empty list.

#### Keep the JSON valid

- For an empty list, use empty square brackets (`[]`). Otherwise, the import fails with a JSON error.
- Don't put a comma after the last value.
- Make sure that every bracket is matched.

For a description of each field, see [Payload field reference](#payload-field-reference).

### Payload field reference

The following table describes the key fields in the CBS debit calculation result payload (**apuracaoCorrente** \> **debitos**). Fields that you edit when you [test with a sample payload](#optional-test-with-a-sample-payload) are marked **Yes** in the **Edit** column. Don't edit the files that you download from the Receita Federal.

| Field | Description | Edit |
|---|---|---|
| modeloDfe | The DF-e model. **Example:** **55** for NF-e. | |
| numeroDfe | The DF-e (invoice) number. Must match the posted invoice. | Yes |
| chaveDfe | The 44-digit DF-e access key. Must match the posted invoice. | Yes |
| dataDfeEmissao, dataDfeAutorizacao, dataDfeRegistro | The DF-e issue, authorization, and registration timestamps. | |
| dataApuracao | The assessment period, in **YYYYMM** format. **Example:** **202605**. | |
| niEmitente, niAdquirente | The tax registration numbers (CNPJ or CPF) of the issuer and the acquirer. | |
| valorCBSTotal | The total CBS amount of the debit. | Yes |
| valorCBSExtinto | The CBS amount that's extinguished (offset). | Yes |
| valorCBSNaoExtinto | The CBS amount that isn't extinguished (remaining). | Yes |
| situacaoDebito | The debit situation. **Example:** **Totalmente Extinto** (fully extinguished) or **Parcialmente Extinto** (partially extinguished). | Yes |
| formasExtincao \> creditosCBS | The CBS credits that are used to extinguish the debit: **cClassCred**, **numeroDfe**, **chaveDfe**, **valorCreditoUtilizadoPrincipal**, **valorCreditoUtilizadoMulta**, and **valorCreditoUtilizadoJuros**. The document number and access key refer to the credit document. | Yes |
| formasExtincao \> debitos and other forms | Other extinction forms. Use `[]` for an empty list. | |
| eventos | The events object. Usually empty (`{}`). | |

## Next steps

After the assessment results are processed, continue with [Phase C: Tax assessment](brazil-reform-tax-assessment.md#phase-c-tax-assessment).

## Related information

- [Tax assessment in Brazil Reformed Tax](brazil-reform-tax-assessment.md)
- [Brazil tax reform setup](brazil-reform-setup.md)
- [Batch processing overview](/dynamics365/fin-ops-core/dev-itpro/sysadmin/batch-processing-overview)
