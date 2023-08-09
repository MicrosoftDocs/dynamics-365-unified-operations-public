---
title: Submit VAT return in XML to the Danish Tax Agency
description: This article describes how to set up, generate a value-added tax (VAT) declaration for Denmark in XML format and submit it to the Danish Tax Agency.
author: liza-golub
ms.date: 03/10/2022
ms.topic: article
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: egolub
ms.search.validFrom: 
---

# Submit VAT return in XML to the Danish Tax Agency

[!include [banner](../includes/banner.md)]

This article describes how to prepare your Finance to generate VAT return in XML format and submit it to the Danish Tax Agency.

## Prerequisites

To automatically generate the VAT declaration in Excel or XML format, first create enough sales tax codes to keep a separate VAT accounting for each box of VAT declaration. 
Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup results for the boxes on the VAT declaration.
For more information about structure of VAT declaration of Denmark and lookup results for boxes of VAT declaration, see [Overview of VAT declaration of Denmark](emea-dnk-vat-declaration-denmark.md) section.

Before you start to prepare your Finance for direct submission of VAT return in XML to the Danish Tax Agency, complete the setup necessary for [Preview VAT declaration in Excel format](emea-dnk-vat-declaration-preview.md).

To submit your VAT return directly to the Danish Tax Agency you need to contact the Danish Tax Agency (Skattestyrelsen) at `momsapi@sktst.dk` and provide your CVR number. You can also see more here: [skat.dk/momsapi](https://skat.dk/data.aspx?oid=2234574) (Danish). From the Danish Tax Agency you will get access the test environment (endpoints and certificates) and you will also get a short guide on what you need to do to get access to the production environment.

## Set up Azure Key Vault for certificate storage

certificates obtained from the Danish Tax Agency to submit your VAT return must be stored in your Azure Key Vault storage.

To set up Azure Key Vault for certificate storage, follow these steps:

1. Go to **System administration** > **Setup** > **System parameters**.
2. On the **General** tab, set the **Use advanced certificate store** option to **Yes**.
3. Upload the certificate to KeyVault.
4. Go to **System administration** > **Setup** > **Key Vault parameters**.
5. Select **New** and set the **Name** and **Description** fields.
6. On the **General** FastTab, set the following fields:

    - **Key Vault URL**: Enter the default Azure Key Vault URL.
    - **Key Vault client**: Enter the interactive client ID of the Azure Active Directory (Azure AD) application that is associated with Key Vault storage for authentication.
    - **Key Vault secret key**: Enter a secret key that is associated with the Azure AD application that's used for authentication to Key Vault storage.

7. On the **Secrets** FastTab, select **Add**, and create lines for Key Vault secrets for the the Danish Tax Agency server and client certificates.

    ![Key vault parameters.](media/Key-vault-parameters-dk.png)

For more information about how to set up Key Vault parameters, see [Set up the Azure Key Vault client](setting-up-azure-key-vault-client.md).

## Set up electronic messages

### Download and import the data package that has example settings for electronic messages

The data package contains settings of electronic message functionality that enables the following scenario in your Finance.

#### Preview VAT declaration in Excel without collecting Sales tax payments (for any open period with any From and To dates)

    ![Preview VAT declaration in Excel.](media/em-processing-preview-dk.png)

#### Request information about VAT obligation periods from Skattestyrelsen for the period specified in electronic message

    ![Request information about VAT obligation periods.](media/em-processing-calendar-dk.png)

#### Generate VAT return electronic file and submit it to Skattestyrelsen

    ![Generate VAT return electronic file and submit it to Skattestyrelsen.](media/em-processing-submission-dk.png)

For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).

To import the data package that contains settings of electronic message functionality that enable the listed scenario in your Microsoft Dynamics 365 Finance follow these steps.

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **EM Denmark VAT package**. The downloaded file is named **EM Denmark VAT package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.

    ![Import the data package that has example settings for electronic messages.](media/em-package-dk.png)

8. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and validate the electronic message processing that you imported (**DK VAT declaration**).

### Define a sales tax settlement period

1. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
2. Select the line for **DK VAT collect sales tax payment records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

### Save the executable class parameters for Electronic messaging



## Generate a VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#run-vat-declaration) section later in this article.

The following procedure applies to the electronic message processing example that you imported earlier from the LCS Shared asset library.

1. Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
2. In the left pane, select **DK VAT declaration**.
3. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.

   > [!NOTE]
   > Steps 5 through 7 are optional.

5. Optional: On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#settle-and-post-sales-tax) section earlier in this article. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
6. Optional: On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select **Ready to generate**, and then select **OK**. Verify that the message status is changed to **Ready to generate**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#preview-vat-excel) section earlier in this article, and then select **OK**.
11. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file. Review the amounts in the Excel document.

## <a name="run-vat-declaration"></a>Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** > **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
4. On the **Populate records action** page, select the line for **DK VAT collect sales tax payment records**.

   In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

    | Field                  | Description                                                                                                                   |
    |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | Name                   | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type      | Select **VAT return**. This value is the only value that is available for all the records.                                    |
    | Account type           | Select **All**.                                                                                                               |
    | Master table name      | Specify **TaxReportVoucher** for all the records.                                                                             |
    | Document number field  | Specify **Voucher** for all the records.                                                                                      |
    | Document date field    | Specify **TransDate** for all the records.                                                                                    |
    | Document account field | Specify **TaxPeriod** for all the records.                                                                                    |
    | Company                | Select the ID of the legal entity.                                                                                            |
    | User query             | This checkbox is automatically selected when you define criteria by selecting **Edit query**.                                 |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
