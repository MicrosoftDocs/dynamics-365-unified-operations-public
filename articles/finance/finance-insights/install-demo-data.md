---
# required metadata

title: Set up demo data for Payment predictions 
description:  
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

If you're using the Payment predictions capability in Finance Insights, you'll need to install additional demo data in addition to what's included in Dynamics 365 Finance by default. Complete the following steps to set up demo data for Payment predictions. 

1. All data is for USMF legal entity so you have to be using this legal entity.

2. Make sure that your entity list has been loaded in. One way to refresh entity list is to go Data management -> Framework parameters -> Entity settings -> click Refresh. This takes somewhere around 10 min to run in the background.

3. Create Customers and Invoices: Open Data Management and import the package from the zip file. The package assumes that system has initial demo data containing things like cash discounts, customers groups, etc.
This step adds 10 new customers and about 900 invoices total across these new customers. 

4. Post invoice to customer: We need to post all of the invoices we just imported. To do so navigate to or search for "Free Text Invoice" batch invoicing.

In the opened panel click on Records To Include -> Filter. Add list of customers from step 3 separated by comma into "Invoice account" field (you can also find the customers entity in the package and grab customer ids from there):
US-SM1,US-SM2,US-SM3,US-SM4,US-SM5,US-MD6,US-MD7,US-MD8,US-LG9,US-LG10

You need to run posting in the background: do so by going into 'Run in background' tab of Batch Invoicing and enable Batch processing to yes. Once you click OK it will kick off a job.

This process might take a while (~10-20 min). After process is complete you can again navigate to All Free Text Invoices to verify that imported invoices are no longer marked as "Not posted".  Or you can look at the job progress in batch jobs as well. 

5. Pay these invoices: Settle about 90% of invoices that was imported and posted in the previous steps. The easiest way to do that is to settle these invoices per customer.

IMPORTANT NOTE: you need to make sure that settle date is the one specified in the file for each customer in the data folder provided above. For this particular data set the settle date for all customers is the same: 2020-04-22. Which invoices you settle and which ones you keep open is not really important, just make sure you have about 90% if them paid.

## To pay invoices
Navigate to Customer Payment Journal. Create new entry and set Name to be CustPay. After that click on Journal Batch number

In opened window put the CUSTOMERACCOUNT value from step 4. In the first column, enter the date for settling from step 5 in the **Date** field that corresponds to this customer.  It's important to enter the correct date. When the date is entered, you can settle transactions. To do so, complete the following steps. 

 - Click on **Checkmark** in the first column, Mark Selected button, and clear the section of a couple of records randomly (this would become what you will predict). Click **OK** and go back to the payment journal.

 - Click **OK** and get back to the payment journal. In order to be able to post this journal the Balance (bottom of the page) has to be zero. Depending on the data you have in the system it might already be zero but if not, scroll all the way to the right and fill in Offset Account and method of Payment with any values from their drop down menus. After that you can click "Post":
 
 - Click **OK** and get back to the payment journal. In order to be able to post this journal the Balance (bottom of the page) has to be zero. Depending on the data you have in the system it might already be zero but if not, scroll all the way to the right and fill in Offset Account and method of Payment with any values from their drop down menus. After that, click **Post**.
 
6. The demo data setup process is complete! You can use Payment Predictor now.
