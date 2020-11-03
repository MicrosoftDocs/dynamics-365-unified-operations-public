---
# required metadata

title: Set up demo data for payment predictions (preview)
description: This topic explains how to set up demo data that you can use with the Customer payment predictions feature.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-23
ms.dyn365.ops.version: AX 10.0.13

---
# Set up demo data for payment predictions (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

If you're using the payment predictions functionality in Finance Insights, you must set up demo data in addition to the default demo data that is included with Microsoft Dynamics 365 Finance. This topic explains how to set up demo data that you can use with the Customer payment predictions feature.

> [!NOTE]
> All demo data is set up for the USMF demo data company. Therefore, if you want to set up or use this data, you must switch to the **USMF** company.

## Create customer records and invoices

1. Make sure that your entity list has been loaded. Refresh the entity as required. One way to refresh the entity list is to go **Data management \> Framework parameters \> Entity settings**, and then select **Refresh**. This process can run in the background. It might take several minutes.
2. Create customers and invoices. Open the **Data management** workspace, and import the package from the zip file. For this package, it's assumed that the system has initial demo data that contains items such as cash discounts and customers groups. This step adds 10 new customers and approximately 900 invoices across those customers.
3. Post the invoices that were imported for the new customers in the previous step:

    1. In the **Free text invoice batch invoicing** dialog box, on the **Records to include** FastTab, select **Filter**.
    2. In the **Invoice account** field, enter a comma-separated list of customer IDs for the customers that were imported:

        US-SM1,US-SM2,US-SM3,US-SM4,US-SM5,US-MD6,US-MD7,US-MD8,US-LG9,US-LG10

        > [!TIP]
        > You can find the Customers entity in the package and get the customer IDs from there.

    3. In the **Batch invoicing** dialog box, on the **Run in background** tab, set the **Batch processing** option to **Yes**, and then select **OK**. The batch posting job is started, and the invoices are posted in the background. This process might take several minutes.
    4. When the processing is completed, open the **All free text invoices** page, and verify that the imported invoices are no longer marked as **Not posted**. You can also determine the status of the invoices by viewing the progress of the bath posting job in the batch jobs list.

4. Pay and settle approximately 90 percent of the invoices that were imported and posted in the preceding steps. The easiest way to settle these invoices is per customer.

    > [!IMPORTANT]
    > Make sure that the settlement date is the date that is specified in the file for each customer in the data folder that was imported. For this data set, the settlement date for all customers is **2020-04-22** (April 22, 2020). It's important that you pay and settle approximately 90 percent of the invoices. However, it doesn't matter which invoices are paid.

## Pay invoices

1. On the **Customer payment journal** page, create an entry. In the **Name** field, enter **CustPay**. Then select the link in the **Journal batch number** field.
2. Enter the **CUSTOMERACCOUNT** value from step 3 of the previous procedure. In the **Date** field, enter the settlement date that you specified for the customer in step 4. It's important that you enter the correct date. After the date is entered, you can settle transactions by following these steps:

    1. In the first column, select the check mark, select **Selected** to mark all the records in the grid, and then clear the selection of a couple of records at random. (This will become what you predict.)
    2. Select **OK** to return to the payment journal.
    3. Before you can post this journal, the balance must be 0 (zero). (The balance is shown at the bottom of the page.) Depending on the data that is loaded in your system, the balance might already be 0 (zero). However, if it isn't, scroll to the right, and then select values in the **Offset Account** and **Method of Payment** fields. When you've finished, select **Post**.

The setup for the demo data has been completed, and you can now use customer payment predictions.

## Privacy notice

Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
