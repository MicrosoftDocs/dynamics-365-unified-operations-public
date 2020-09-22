---
# required metadata

title: Set up demo data for Payment predictions 
description: This topic lists the steps for setting up demo data that you can use with Customer payment predictions.  
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
# Set up demo data for Payment predictions (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

If you're using the Payment predictions capability in Finance Insights, you'll need to set up demo data in addition to the demo data that's included by default with Dynamics 365 Finance. This topic lists the steps for setting up demo data that you can use with Customer payment predictions.  

> [!Note]
> All demo data is set up for the USMF demo data company. Switch to the USMF company when setting up or using this data. 

### Create customer records and invoices

1. Be sure that your entity list has been loaded. One way to refresh the entity list is to go **Data management > Framework parameters > Entity settings**, and then click **Refresh**. This process can run in the background and can take several minutes to complete. 

2. Create customers and invoices. Open **Data Management** and import the package from the zip file. The package assumes that system has initial demo data containing things like cash discounts, customers groups, among others. This step adds 10 new customers, as well as approximately 900 invoices across these customers. 

3. Post invoices for the customers that were added. The invoices that were imported in the previous steps must be posted. To do so, open the **Free Text Invoice batch invoicing** page.

   In the opened panel click **Records To Include > Filter**. Add the list of customers from step 2, separated by commas, into the **Invoice account** field (you can also find the customers entity in the package and obtain the customer IDs from there):
   US-SM1,US-SM2,US-SM3,US-SM4,US-SM5,US-MD6,US-MD7,US-MD8,US-LG9,US-LG10

   Post the invoices in the background by opening the **Run in background** tab on the **Batch Invoicing** page, and setting **Batch processing** to **Yes**. When you click **OK**, the batch posting job will start.

   This process might take several minutes to complete. When processing is finished, go to to **All Free Text Invoices** to verify that imported invoices are no longer marked as **"Not posted**. You can also determine their status by viewing the progress of the bath posting job in the batch jobs list. 

5. Pay the invoices. Settle 90% or so of the invoices that were imported and posted in the preceding steps (the number doesn't have to exact). The easiest way to settle these invoices is per customer.

   > [!IMPORTANT]
   > Be sure that settle date is the one specified in the file for each customer in the data folder provided above. For this particular data set, the settle date for all customers is 2020-04-22. It's important to pay and settle approximately 90% of the invoices, but it doesn't matter which invoices are paid and which ones aren't.

### Pay invoices
1. Open the **Customer Payment Journal**. Create a new entry, and enter the **CustPay** in the **Name** field. Then click **Journal Batch number**.

2. In opened window put the CUSTOMERACCOUNT value from step 3. In the first column, enter the date for settling from step 4 in the **Date** field that corresponds to this customer. It's important to enter the correct date. When the date is entered, you can settle transactions. To do so, complete the following steps. 

   - Click **Checkmark** in the first column, select the **Selected** button to mark all the records, and then clear the section of a couple of records randomly (this will become what you will predict). Click **OK** and go back to the payment journal.

   - Click **OK** and return to the payment journal. To post this journal, the balance must be zero. (The balance is displayed at the bottom of the page.) Depending on the data that's in your system, the balance might already be zero, However, if it's not, scroll to the right and enter values in the **Offset Account** and **Method of Payment** fields, using the values that are in their drop-down menus. When you've finished, click **Post**.
 
   - Click **OK** and go back to the payment journal. To post this journal the **Balance** must be zero. Depending on the data in your system it might already be zero, but if not, scroll all the way to the right and fill in **Offset Account** and method of **Payment** with any values from their drop-down menus. When you've finished, click **Post**.
 
3. The demo data setup process is now complete and you are ready to use Customer payment predictions.

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
