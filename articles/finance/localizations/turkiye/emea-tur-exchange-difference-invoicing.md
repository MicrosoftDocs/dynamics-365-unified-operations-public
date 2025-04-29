---
title: Exchange difference invoicing (preview)
description: Access links to documentation resources for Türkiye, including links to resources about exchange difference invoicing.
author: v-omerorhan 
ms.author: v-omerorhan
ms.topic: overview
ms.date: 04/24/2024
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Türkiye
ms.search.validFrom: 2020-02-03
ms.search.form: ExchangeDifferenceInvoicing
ms.dyn365.ops.version: 10.0.9
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Exchange difference invoicing (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides information on how to create and process exchange difference invoices in Türkiye due to the floating exchange rate system. 

Exchange difference invoices must reflect the difference between the exchange rate at the time of invoicing and the exchange rate at the time of payment. In Türkiye, the requirement to create an exchange rate invoice arises due to the floating exchange rate system, where the exchange rate at the time of invoice may differ from the exchange rate at the time of payment. This results in a difference in the amount in Turkish Lira, even if the foreign exchange amount remains the same.
Companies must issue invoices for exchange rate differences, and these invoices must reflect the equivalent amount in Turkish Lira using the foreign exchange buying rate of the Central Bank of the Republic of Türkiye.

According to the legislations, the tax rate applied to the exchange rate difference is crucial. The exchange difference invoice must be issued with the same tax rate as the related product or service. The tax rate applied to the invoiced product or service should also be applied to the exchange difference invoice. If the invoice is exempt from tax or subject to withholding tax, the exchange difference invoice should be issued accordingly.

## Configuring exchange difference invoicing

This section explains how to configure to create exchange difference invoices. 

Exchange difference invoicing can be configured according to the parameters in **Accounts payable** or **Accounts receivable > Setup > Exchange difference invoicing > Exchange difference invoicing parameters** page. 

Here is an explanation for each field in the **General** tab:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Require same posting profile in settlement** | Specify whether the same posting profile must be used when settling transactions.   |
| **Require same currency in settlement** |  Specify whether transactions must be in the same currency to be settled. |
| **Require invoice approval** | Specify whether invoice approval is required before processing. |
| **Exchange difference invoice** | Select the relevant report format for printing the exchange difference invoice that has been posted to the ledger.  |
| **Exchange difference inovice voucher** |  Select the relevant report format to be used for exchange difference invoice reconciliation. |

Here are the details for each field in the **Invoice** tab:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Separate exchange difference invoice for each invoice** | Specify whether a separate exchange difference invoice should be created for each individual invoice.|
| **Include only fully settled invoices** | Specify whether only fully settled invoices should be included in the exchange difference invoice update.|
| **Group by dimension** | Specify whether invoices should be grouped by dimension.|
| **Group by tax group** | Specify whether invoices should be grouped by tax group.|
| **Group by profit and loss** | Specify whether invoices should be grouped by profit and loss.|
| **Default invoice prefix** | Specify whether the default serial prefix for the invoice number is automatically assigned to exchange difference invoices.|
| **Copy description to voucher transaction** | Specify whether the description should be copied to the voucher transaction.|
| **Copy description to journal line** | Specify whether the description should be copied to the journal line.|

Here are the details for each field in the **Number sequence** tab:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Exchange difference invoice** | Define the unique key for exchange difference invoice.|
| **Exchange difference invoice voucher** |  Define the unique key for voucher of exchange difference invoice. |

When you want to create an exchange difference invoice, there must be defined the **Realized gain** and **Realized loss** accounts in **Currency revaluation posting profile** page for **Accounts payable** and **Accounts receivable**. 
Learn more about how to define a currency revaluation posting profile in [Currency revaluation posting profile](../../general-ledger/currency-revalue-posting-profile.md). 

### Set up exchange difference invoice formats

This section explains how to configure Excel reports for the exchange difference invoicing process. The reports are implemented as Electronic Reporting (ER) configurations. 
You must import the latest versions of the following ER configurations:

- **Exchange difference invoice (TR) (Excel):** Provides an excel report to get an exchange difference invoicing printout using Electronic reporting.
- **Exchange adjustment statement (TR) (Excel):** Provides an excel report to get an exchange difference reconciliation report. This report includes information about the exchange difference invoice and the invoice and payment transactions that generate the exchange difference amount.
- **Model mapping (TR):** Sets the structure and data mapping for exchange difference invoice data mapping, ensuring data is correctly formatted for Electronic reporting.

Fore more information about how to import the electronic reporting formats, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

To generate the reports, the relevant formats must be selected in the **Exchange difference invoice** and the **Exchange difference invoice voucher** parameters in **General** Tab on **Accounts payable** or **Accounts receivable > Setup > Exchange difference invoicing > Exchange difference invoicing parameters** page. 


## Processing exchange difference invoicing

This section provides general information of the fields and functions for **Exchange difference invoicing** page. 

Exchange difference invoicing feature retrieves settled invoice and payment transactions for customers and vendors specified in the process. 
When you click the **New** in ActionPane to create exchange difference invoice records, there are two options:  

- **Exchange difference invoices for vendors**: It generates exchange difference invoices based on settled vendor invoice and payment transactions.  
- **Exchange difference invoices for customers**: It generates exchange difference invoices based on settled customer invoice and payment transactions.

The **Date** field determines which settled transactions are considered for customer and vendors, ensuring that no exchange differences are created from payment transactions dated after the specified invoice date. 

> [!NOTE]
> In **Exchange difference parameters > Invoice** tab, you can configure various parameters permanently, such as: 
> - Generating a separate exchange difference invoice for each invoice, 
> - Grouping based on financial dimensions, 
> - Grouping by tax group, 
> - Grouping by profit and loss 

After exchange difference invoices are created, you see the functions for exchange difference invoices. Various functions are available for exchange difference invoices created on the exchange difference invoicing page. General information about these functions is provided below.
Here are the details of functions in the **Invoice** tab in ActionPane:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Create return quotation** | Copies the exchange difference invoice for return invoices that come after invoicing or to be issued by the company. |
| **Reverse** | Performs reverse registration of the transactions that have occurred. In exchange difference reversal; automatic marking of customer and vendor invoice transactions, customer and vendor transactions and voucher transactions.|
| **Transactions** | Reaches customer or vendor transaction of exchange difference invoice. |
| **Exchange rate adjustment** | Provides the exchange difference invoicing print. |
| **Exchange adjustment statement** | Provides an electronic report model to get statement report. |

> [!NOTE]
> Because the vendor or customer exchange difference invoice is created, the settled transactions of customer or vendor cannot be reversed. 

The **Exchange difference invoice** section provides general information about the generated exchange difference invoices.

Here are the details for each field in the **Exchange difference invoice** section:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Exchange difference invoice** | Specifies the unique number of the exchange difference invoice. |
| **Exchange difference type** | Specifies the type of exchange difference invoice. |
| **Account type** | Specifies the type of account involved (e.g., customer, vendor).|
| **Account number** | Specifies the unique identifier for the account. |
| **Account name** | Specifies the name associated with the account number. |
| **Currency** | Specifies the currency in which the transaction is conducted. |
| **Exchange difference amount** | Specifies the amount of the exchange difference in the transaction currency. |
| **Exchange difference reporting amount** | Specifies the amount of the exchange difference in the reporting currency. |
| **Date** | Specifies the posting date of the transaction. |
| **Invoice serial** | Specifies the serial prefix for the exchange difference invoice. |
| **Invoice** | Specifies the invoice number. |
| **Invoice description** | Specifies the brief description of the exchange difference invoice. |
| **Sales tax group**  | Specifies the sales tax group of exchange difference invoice.|
| **Item sales tax group** | Specifies the item sales tax group of exchange difference invoice.|
| **Sales tax amount** | Specifies the sales tax amount applied to the exchange difference invoice. |
| **Adjusted tax amount** | Specifies the adjusted sales tax amount after any corrections.|
| **Posted** | Specifies whether the transaction has been posted.|
| **Exchange difference invoice voucher** | Indicates the voucher number associated with the exchange difference invoice.|
| **Description** | Specifies the brief description of the exchange difference invoice voucher.|
| **Reference voucher** | Specifies the voucher number of the waiting invoice type to the following day after the posting or the reverse voucher number. |
| **Reference voucher date** | Specifies the date of the waiting invoice type to the following day after the posting or the reverse voucher date. |
| **Posting profile** | Specifies the posting profile used for posting the exchange difference invoice.|
| **Exchange difference account** | Specifies the account used for posting realized gain or realized loss exchange difference amount. |
| **Reconciliation statement sent** | Specifies whether the **Exchange adjustment statement** report has been generated. |
| **Approved** | Specifies whether the transaction has been approved. |
| **Approved date** | Specifies the date when the transaction was approved.|

The **Exchange difference invoice line transactions** section contains information about the invoices related to the exchange difference invoice. If there are multiple invoice transactions, the grid populates accordingly. Payments or collections made for multiple invoices may be invoiced as part of an exchange difference invoicing.

Here are the details for each field in the **Exchange difference invoice line transactions** section:

| **Field** | **Description** |
|-----------|-----------------------------------|
| **Source** | Specifies the origin of the transaction. |
| **Date** | Specifies the date of the transaction. |
| **Voucher** | Specifies the voucher number associated with the transaction. |
| **Invoice** | Specifies the invoice number. |
| **Currency** | Specifies the currency of the source transaction. |
| **Exchange rate** | Specifies the exchange rate applied to the transaction. |
| **Amount in transaction currency** | Specifies the amount of the transaction in the original currency. |
| **Amount** | Specifies the amount of the transaction. |
| **Amount in reporting currency** | Specifies the amount of the transaction in the reporting currency. |
| **Calculated exchange difference amount** | Specifies the exchange difference amount calculated based on the transaction and reporting currencies. |
| **Calculated exchange difference reporting amount** | Specifies the exchange difference amount in the reporting currency. |
| **Adjusted exchange difference amount** | Specifies the adjusted exchange difference amount after any corrections. |
| **Adjusted exchange difference reporting amount** | Specifies the adjusted exchange difference amount in the reporting currency. |
| **Sales tax group** | Specifies the sales tax group applicable to the transaction. |
| **Item sales tax group** | Specifies the item sales tax group. |
| **Closed** | Specifies whether the transaction is closed. |


In the **Settled transactions** section, payment transactions are listed. If multiple payments are made for a single invoice, each payment appears as a separate record. The **Calculated exchange difference** field displays the exchange difference amount for the settled transactions. The total exchange difference amount from all invoice transactions is summarized in the **Exchange difference amount** field on the **Overview** tab.

Here are the details for each field in the **Settled transactions** section:

| **Field** | **Details** |
|-----------|-----------------------------------|
| **Source** | Specifies the origin of the transaction. |
| **Date** | Specifies the date of the transaction.|
| **Voucher** | Specifies the voucher number associated with the transaction.|
| **Invoice** | Specifies the invoice number. |
| **Currency** | Specifies the currency in which the transaction is conducted. |
| **Exchange rate** | Specifies the exchange rate applied to the transaction. |
| **Settled currency** | SpecifiestThe currency in which the amount is settled. |
| **Amount settled** | Specifies the amount settled in the transaction currency. |
| **Amount in reporting currency** | Specifies the amount settled in the reporting currency. |
| **Calculated exchange difference amount** | Specifies the exchange difference amount calculated based on the transaction and reporting currencies. |
| **Calculated exchange difference reporting amount** | Specifies the exchange difference amount in the reporting currency. |
| **Adjusted exchange difference amount** | Specifies the adjusted exchange difference amount after any corrections. |
| **Adjusted exchange difference reporting amount** | Specifies the adjusted exchange difference amount in the reporting currency. |
| **Payment date** | Specifies the date when the payment was made. |
| **Offset voucher** | Specifies the voucher number used to offset the transaction. |
| **Payment currency** | Specifies the currency in which the payment was made. |
| **Payment exchange rate** | Specifies the exchange rate applied to the payment. |
| **Closed** | Specifies whether the transaction is closed. |

## Creating an exchange difference invoice

This section explains how to create an exchange difference invoice. 
To create a new exchange difference invoice; 

1. Navigate to **Accounts payable > Periodic tasks > Exchange difference invoicing** or **Accounts receivable > Periodic tasks > Exchange difference invoicing**.
2. Click **New**.
3. Select the **Exchange difference invoices for vendors** or the **Exchange difference invoices for customers**.
4. In the **Date** field, select a date.
5. In the **Default invoice prefix** parameter;

    - If it is set as **Yes**, the serial prefix is automatically selected in the **Invoice serial** field based on the **Default prefix** marked in **Preprinted serial numbers** page. .
    - If it is set as **No**, the serial prefix must be manually selected in the **Invoice serial** field. For more information, see [Serial numbering](emea-tur-serial-numbering.md).

6. Select or change the other filtering parameters.
7. Click **OK**.
8. Click the **Edit** button to update the fields on the **Exchange difference invoicing** page after the exchange difference invoices are listed.
9. Select an option in the **Exchange difference type** field.
11. Select a serial prefix or change the serial prefix manually in the **Invoice serial** field.
12. Type a description if needed in the **Invoice description** field.
13. Select a value in the **Sales tax group** field.
14. Select a value in the **Item sales tax group** field.
15. Type a description if needed in the **Description** field.
16. Click **Post**.
17. Click **OK**.


After the exchange difference invoices listed in the page, the **Exchange difference type** must be selected. 

The details of each type are as below;

- **Pending invoice -** This option delays invoicing to the following months, performing normal revaluation and generating vouchers and vendor transactions for the next day. Corrections are made at the end of the period.
- **Exchange difference invoice -** This option creates an invoice transaction which can be invoiced immediately or later. Vendor and customer are reconciled with the invoice based on these records. When the customer or vendor invoices or advance payments are transferred to other period, the transferring date of exchange rate should be as invoice date. Then, the **Foreign currency revaluation** in standard should be executed at the date of transfer.
- **Revaluate and close -** If it is selected, no invoice is issued if not accepted by the other party or if we do not want to invoice. Settlement is done using standard currency revaluation function. When **Revaluate and close** is selected in **Exchange difference invoice type** field, these penny differences are closed again by posting again. The amount remaining when the settled transactions are listed for the customer or the vendor doesn't come for exchange difference invoicing.

You can change the exchange difference invoice posting date in **Date** field manually. To calculate tax amount for exchange difference invoice, **Sales tax group** and **Item sales tax** **group** must be selected.

The **Delete** button permits the removal of the selected record in the **Exchange difference invoice** section. When an exchange difference invoice is deleted, the invoice and payment transactions that led to its creation are also deleted. If a deleted exchange difference invoice needs to be recreated, click the **New** button on the **Exchange difference invoicing** page, select the relevant option for customer or vendor transactions and the relevant exchange difference invoice is listed again based on the selected parameters.

In some cases, the generated exchange difference invoice may need to be excluded before being posted to the ledger. If you want to exclude any exchange difference invoice, you can click the **Exclude** to exclude any record and information about the excluded records can be accessed from the **Excluded records** tab. If you want to include any record again, it can be done by clicking **Include**. 

> [!NOTE]
> To delete an excluded exchange difference invoice in the **Excluded records** tab, first include the record by **Include**, then delete it.

According to legal requirements, when the **Exchange difference amount** is debit balance, an exchange difference invoice must be created for the relevant customer or vendor. In this case, the **Invoice serial** field is mandatory and a serial prefix must be selected in the **Invoice serial** field. 
When the **Exchange difference amount** is a credit balance, the document number of the exchange difference invoice received from the relevant customer or vendor must be entered in this field.

> [!NOTE]
> - If the **Default invoice prefix** parameter is set as **No**, the **Invoice serial** field is mandatory and a serial prefix must be chosen manually.
> - If the **Default invoice prefix** parameter is set as **Yes**, the **Invoice serial** value is selected automatically depending on the **Default prefix** field selected in the **Preprinted serial numbers** page. For more information, see [Serial numbering](emea-tur-serial-numbering.md).

When you generate the **Exchange adjustment statement** report from the **Document** group in the **Invoice** tab, the **Reconciliation statement sent** field in the **Exchange difference invoice** section is marked. Then, the relevant exchange difference invoice can be approved using **Approve**. If needed, approval can be reset using **Reset Approval**. 

If the **Require invoice approval** parameter is set to **Yes** in the **General** tab on the **Exchange difference invoicing parameters** page, the **Post** button activates after the exchange difference invoice is approved, allowing it to be posted to the ledger. If the parameter is set to **No**, the exchange difference invoice can be posted to the ledger without requiring approval.

Exchange difference invoices are specified by the **Foreign currency revaluation** transaction type in **General** tab in customer or vendor transactions after posted.

In the **Exchange difference invoice line transactions** section, **Delete** is used to remove invoice transactions during the reconciliation process between vendors and customers. Once an invoice is deleted, the exchange difference amount displayed in the **Exchange difference amount** in the **Exchange difference invoice section**, is automatically updated to reflect the deletion. **Transactions** open the voucher transactions that are linked to the relevant invoice. This provides a detailed view of all the transactions associated with that specific invoice. **Move** is utilized to transfer an exchange difference invoice to another invoice transaction within the same customer or vendor account. This helps in managing and organizing multiple invoice transactions efficiently.

When reconciling invoices, payments and collections with customers and vendors, exchange differences may arise due to timing differences in money transfers. The **Exchange difference amount** must be reviewed and can be manually adjusted if needed. Initially, the **Calculated exchange difference amount** and **Adjusted exchange difference amount** values are the same, but adjustments can be made in the **Settled transactions** section. The reconciliation amount from customers and vendors must be entered manually.


## How to print the exchange difference invoicing documents

This section explains how to print the excel reports in exchange difference invoicing page. 

- **Exchange rate adjustment**: The report can print after the exchange difference invoice is posted. The report can be access as below:

1. Navigate to **Accounts payable** or **Accounts receivable > Periodic tasks > Exchange difference invoicing**.
2. Select an exchange difference invoice which is **Posted**.
3. Click **Exchange rate adjustmet** in the **Document** group in **Invoice** tab.

- **Exchange adjustment statement**: The report can be access as below:

1. Navigate to **Accounts payable** or **Accounts receivable > Periodic tasks > Exchange difference invoicing**.
2. Select an exchange difference invoice which is **Not posted** .
3. Click **Exchange adjustment statement** in the **Document** group in the **Invoice** tab.

When the **Exchange adjustment statement** is printed, the **Reconciliation statement sent** field is marked and **Approve** actives in the **Exchange difference invoice** section. If you click **Approve**, the **Approved** and the **Approved date** fields is filled. 

> [!NOTE]
> If the **Require invoice approval** parameter is set to **Yes** in the **Exchange difference invoicing parameters** page:
> - You must click the **Approve** for the exchange difference invoice in the **Exchange difference invoice** section before posting. Then, the exchange difference invoice can post.
> - You can click the **Reset approval** to rollback the exchange difference invoice. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
