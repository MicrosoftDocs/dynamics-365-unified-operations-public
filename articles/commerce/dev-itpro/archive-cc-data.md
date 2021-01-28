---
# required metadata

title: Archive credit card transaction data
description: This topic describes an archival job that can be used to free up database space by archiving credit card transactions.
author: rubendel
manager: annbe
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Archive credit card transaction data

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes an archival job that can be used to free up database space by archiving credit card transactions.

For every credit card authorization, the authentication binary large object ([auth blob](#key-terms)) is stored in the database. Auth blobs contain data related to the authorization and over time can grow to take up a significant amount of space in the database. The job described in this topic provides a way to archive auth blob data by exporting it to Azure Blob Storage and then deleting the data from the database. 

The parameters for the archival job are based on the age of the transaction in days. In other words, if the **Minimum transaction age in days** is set to **365**, then all credit authorization XML data older than 365 days will be subject to archiving when the job is run. 

When using the archival job, it is important to understand that the data cannot be easily restored. For this reason, transactions subject to [linked refunds](#key-terms) should not be archived. For example, if a merchant's returns policy allows for transactions to be returned to the same credit card for refund within two years, the parameter for the job should be set to 730 days (tw0 years). In this example, if a transaction is returned after 730 days, the XML required to perform a linked refund will not be found, so the customer will need to be refunded via a [standalone refund](#key-terms) to a credit card or to some other payment method such as a credit memo or gift card. 

## Key terms

| Term | Description |
|---|---|
| Auth blob | The response returned from a credit card processor as a result of a payment request. This response is stored in as an XML blob and can take up a large amount of database space over time. |
| Linked refund | A refund request that references a previous transaction. Linked refunds are viewed as lower risk by processors and have lower associated fees. |
| Standalone refund | A refund request that does not reference a previous transaction. Standalone refunds carry higher risk and have higher processing fees. |

## Document management dependency

When the archival job is run, aged credited card XML data is exported in a .zip file using document management. If document management is not set up in an environment, the credit card data archival job will not be able to run successfully. For more information, see [Configure document management](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-document-management).

The archival job will process all credit card payment data that meets the **Minimum transaction age in days** criteria. If the job is enabled and (according to the criteria) there is a large number of records that need to be processed, the job execution may take several days to complete. Once the backlog of payments has been archived, the job will not take as long to process. 

## Data in scope for archival

The archival job archives data in the `PaymentAuthorization`, `PaymentCaptureToken`, and `PaymentCardToken` fields of the `RetailTransactionPaymentTrans` table. Transactions that have been archived will not have associated data in these fields, but may still be returned without linked refunds. 

## Batch job setup

To access the archival job, in Commerce headquarters go to **Retail and commerce \> Retail and Commerce IT \> Clean up \> Archive credit card transaction data**. The **Archive credit card transaction data** dialog box for the batch job requires you to enter the age in days under **Minimum transaction age in days** for credit card authorizations that will be subject to archiving. This value should be set to the length of time that customers can have refunds linked to their original credit card authorization. If the age in days is set to 365 days, a return for a transaction 366 days old may still be eligible for refund based on the merchant's policies, but since the data required to perform a linked refund will not be available, any refund would need to be a standalone refund. 

In addition to the minimum transaction age in days, the **Archive credit card transaction data** dialog box includes options for job recurrence. Batch processing is enabled by default and cannot be changed. 

The following example image shows the **Archive credit card transaction data** dialog box parameters.

![Archive credit card transaction data dialog box parameters](media/PAYMENTS/Batch1.png)

Once the parameters and batch details have been established, select **Next** to view a sample of the data to be exported, as shown in the following image. The data in this view is limited, but all data subject to archiving can be exported. 

![View of sample of data to be exported](media/PAYMENTS/Batch2.png)

> [!NOTE]
> The data subject to archiving includes personally identifiable customer information such as the name of the cardholder. This sensitive data should be handled according to your local regulatory requirements.

After confirming the parameters for data to be archived, you will be prompted to confirm that the data being archived is not easily restored, as shown in the following image. 
 
![Confirmation prompt](media/PAYMENTS/Batch3.png)
 
After selecting **Yes**, the archival job will be active and authorization XML data older than the **Minimum transaction age in days** will be subject to archiving. 

## Additional resources

[Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md?tabs=8-1-3)

[Checkout module](../add-checkout-module.md)
