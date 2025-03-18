| **title** | **description** | **author** | **ms.author** | **ms.topic** | **ms.date** | **ms.reviewer** | **audience** | **ms.search.region** | **ms.search.validFrom** | **ms.dyn365.ops.version** |
|------|-------|-----|------|------|------|-------|------|--------|---------|---------|
| Exchange difference invoicing | Access links to Microsoft Dynamics 365 Finance documentation resources for Türkiye , including links to resources about exchange difference invoicing. | kfend | kfend | overview | 07/25/2019 | johnmichalak | Application User | Türkiye | 2016-02-28 | AX 7.0.0 |

# Exchange difference invoicing

\[!include [banner](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/main/articles/finance/includes/banner.md)\]

This article provides information on how to create and process exchange difference invoices in Türkiye due to the floating exchange rate system. 

Exchange difference invoices must reflect the difference between the exchange rate at the time of invoicing and the exchange rate at the time of payment. In Türkiye, the requirement to create an exchange rate invoice arises due to the floating exchange rate system, where the exchange rate at the time of invoice may differ from the exchange rate at the time of payment. This results in a difference in the amount in Turkish Lira, even if the foreign exchange amount remains the same.
Companies must issue invoices for exchange rate differences, and these invoices must reflect the equivalent amount in Turkish Lira using the foreign exchange buying rate of the Central Bank of the Republic of Türkiye.

## Tax in exchange difference invoicing

The tax rate applied to the exchange rate difference is crucial. The exchange rate difference invoice must be issued with the same tax rate as the product or service in question. For the specific product or service being invoiced, the same tax rate should be applied to the exchange rate difference. If the invoice is exempt from tax or is subject to withholding, the exchange rate difference invoice should be issued accordingly.

## Configuring exchange difference invoicing

### Setup exchange difference invoicing

Exchange difference invoicing can be configured according to the parameters in **Accounts payable** or **Accounts receivable > Setup > Exchange difference invoicing > Exchange difference invoicing parameters** form.

Here is an explanation for each field in the **General** tab:

| **Field** | **Description**                   |
|-----------|-----------------------------------|
| **Require same posting profile in settlement** | Specifies whether the same posting profile must be used when settling transactions.   |
| **Require same currency in settlement** |  Indicates whether transactions must be in the same currency to be settled. |
| **Require invoice approval** | Indicates whether invoice approval is required before processing. |
| **Exchange rate adjustment** | Specifies whether the invoice should be printed.  |
| **Exchange adjustment statement** |  Creates an invoice template invoices that involve exchange rate differences. |

Here are the details for each field in the **Invoice** tab:

| **Field** | **Description**                   |
|-----------|-----------------------------------|
| **Separate exchange difference invoice for each invoice** | Specifies whether a separate exchange difference invoice should be created for each individual invoice.    |
| **Include only fully settled invoices** |  Indicates whether only fully settled invoices should be included in the exchange difference invoice update. |
| **Group by dimension** | Specifies whether invoices should be grouped by dimension. |
| **Group by tax group** | Specifies whether invoices should be grouped by tax group.       |
| **Group by profit and loss** |  Specifies whether invoices should be grouped by profit and loss.    |
| **Default invoice prefix** |  Indicates whether a default prefix should be used for the invoice number.   |
| **Copy description to voucher transaction** | Specifies whether the description should be copied to the voucher transaction.           |
| **Copy description to journal line** |  Specifies whether the description should be copied to the journal line.      |

Here are the details for each field in the **Number sequence** tab:

| **Field** | **Description**                   |
|-----------|-----------------------------------|
| **Exchange difference invoice** | Unique key for exchange difference invoice.    |
| **Exchange difference invoice voucher** |  Unique key for exchange difference invoice voucher. |


When you want to create an exchange difference invoice, there must be defined the Realized gain or loss accounts in **Currency revaluation posting profile** form for **Accounts payable** and **Accounts receivable**. 
Learn more about how to define a currency revaluation posting profile in [Currency revaluation posting profile](currency-revalue-posting-profile.md).

## Electronic reporting in Türkiye localization

During the exchange difference invoicing process, the following documents can be obtained via electronic reporting:

- **Exchange difference invoice (TR) (Excel)**: Provides a data mapping to get the exchange difference invoicing printout. This data mapping provides a resource for users to create their desired invoice print format using Electronic Reporting.
- After invoice design was created by using data mapping, the report can be access as below:
    - Go to **Accounts payable** or **Accounts receivable > Periodic tasks > Exchange difference invoicing**.
    - Select an exchange difference invoice which is **Posted**.
    - Click **Exchange difference invoice**.

Then, you will be able to generate an invoice printout created using data mapping.
The **Exchange difference invoice (TR) (Excel)** will be able to print after the exchange difference invoice is posted.

- **Exchange adjustment statement (TR) (Excel)**: Provides a data mapping to get exchange difference reconciliation report. This data mapping includes information about exchange difference invoice and provides a resource for users to create their desired report format using Electronic reporting. After reconciliation report design was created by using data mapping, the report can be access as below:
    - Go to **Accounts payable** or **Accounts receivable > Periodic tasks > Exchange difference invoicing**.
    - Select an exchange difference invoice which is **Not posted**.
    - Click **Exchange adjustment statement invoice**.

Then, you will be able to generate an Statement printout created using data mapping.

- **Model mapping (TR)**: Sets the structure and data mapping for exchange difference invoice data mapping, ensuring data is correctly formatted for Electronic reporting.

To enable synchronized electronic reporting tools in the Exchange difference invoicing, you must configure the necessary electronic reporting parameters:
- Go to **Organization administration > Workspaces > Electronic reporting**, which will redirect you to the **Localization Configurations** section. 


In this section, import the required **Reporting Configurations** listed below:
- Exchange adjustment statement (TR) (Excel)
- Exchange difference invoice (TR) (Excel)
- Model Mapping (TR) 

For more information about electronic reporting, see [Electronic reporting overview](general-electronic-reporting.md).

Then the **Exchange difference invoice** and the **Exchange adjustment statement** parameters must be selected to get report in creating exchange difference invoicing process.
When the **Exchange adjustment statement** is printed, The **Reconciliation statement sent** field is marked and **Approve** will be active. If you click **Approve**, the **Approved** and the **Approved date** fields will be filled. 

>[!NOTE]
>If the **Require invoice approval** parameter is active in **Exchange difference invoicing parameters**:
>- You must click **Approve** the exchange difference invoice before posting or you can use **Reset approval** to rollback. Then, the exchange difference invoice will be able to post.


# Processing exchange difference invoicing

Exchange difference invoicing feature retrieves settled transactions for customers and vendors specified in the process. 
The **Date** field determines which settled transactions are considered for customer and vendors, ensuring that no exchange differences are created from payment transactions dated after the specified invoice date. 

You can click **New** to create exchange difference invoice records. There are two options:  
- **Exchange difference invoices for vendors** -  it provides the exchange difference invoices from vendor settled invoice -- payment transactions.
- **Exchange difference invoices for customers** - it provides the exchange difference invoices from settled customer invoice -- payment transactions.


>[!NOTE]
>In **Exchange difference parameters \> Invoice** tab, you can configure various parameters permanently, such as: 
>- Generating a separate exchange difference invoice for each invoice, 
>- Grouping based on financial dimensions, 
>- Grouping by tax group, 
>- Grouping by profit and loss 

After exchange difference invoices are created, you will see the functions for exchange difference invoices. Here are the details of functions:

| **Field** | **Description**                   |
|-----------|-----------------------------------|
| **Create return quotation** | Copies the exchange difference invoice for return invoices that come after invoicing or to be issued by the company.                                                            |
| **Reverse** | Performs reverse registration of the transactions that have occurred. In exchange difference reversal; automatic marking of customer and vendor invoice transactions, customer and vendor transactions and voucher transactions.|
| **Transactions** | Reaches customer or vendor transaction of exchange difference invoice.   |
| **Exchange rate adjustment** | Provides the exchange difference invoicing print.       |
| **Exchange adjustment statement** | Provides an electronic report model to get statement report.       |


#### Exchange difference invoice

This section provides general information regarding the exchange difference invoices created. 

The **Delete** button permits the removal of the selected record. If the invoice must re-creation, the function must be re-executed using the **New**.
After exchange difference invoices listed in the form, you can click the **Exclude** to exclude any record, and information about the excluded records can be accessed from the **Excluded records** tab. If you want to include any record again, it can be done by clicking **Include**. 

When you create Exchange adjustment statement report, **Reconciliation statement in sent** field will be marked. Then relevant exchange difference invoice will be able to approve by **Approve**. Also, you can reset approval with **Reset approval**.
It provides details on various fields related to exchange difference invoice transactions. The key fields include the source and date of the transaction, account type and number, currency, exchange difference amounts, tax details, and invoice information. 
It also covers approval status, posting profile, and reconciliation statements.

>[!NOTE]
>- To delete a transaction in the **Excluded records** tab, first include the record by **Include**, then delete it.
>- If the **Default invoice prefix** parameter is selected as **No**, the **Invoice serial** field will be mandatory, and a serial prefix must be chosen.

Here are the details for each field in the **Exchange difference invoice** section:

| **Field**                            | **Description**                                                                                                     |
|-----------|-----------------------------------|
| **Exchange difference type**              | Specifies the type of exchange difference                                                                            |
| **Account type**                          | Indicates the type of account involved (e.g., customer, vendor)                                                      |
| **Account number**                        | The unique identifier for the account                                                                                |
| **Account name**                          | The name associated with the account number                                                                          |
| **Currency**                              | The currency in which the transaction is conducted                                                                   |
| **Exchange difference amount**            | The amount of the exchange difference in the transaction currency                                                    |
| **Exchange difference reporting amount**  | The amount of the exchange difference in the reporting currency                                                      |
| **Date**                                  | The date of the transaction                                                                                          |
| **Invoice serial**                        | A unique serial number for the invoice                                                                               |
| **Invoice**                               | The invoice number                                                                                                   |
| **Invoice description**                   | A brief description of the invoice                                                                                   |
| **Sales tax group**                       | The field where sales tax group is specified.                                                                        |
| **Item sales tax group**                  | The field where item sales tax group is specified.                                                                   |
| **Sales tax amount**                      | The amount of sales tax applied to the transaction                                                                   |
| **Adjusted tax amount**                   | The adjusted amount of sales tax after any corrections                                                               |
| **Posted**                                | Indicates whether the transaction has been posted                                                                    |
| **Exchange difference invoice voucher**   | The voucher number associated with the transaction                                                                   |
| **Description**                           | A description of the transaction                                                                                     |
| **Reference voucher**                     | The voucher number of the waiting invoice type to the following day after the posting or the reverse voucher number. |
| **Reference voucher date**                | The date of the waiting invoice type to the following day after the posting or the reverse voucher date.             |
| **Posting profile**                       | The profile used for posting the transaction                                                                         |
| **Exchange difference account**           | The account used for posting exchange differences                                                                    |
| **Reconciliation statement sent**         | Indicates whether a reconciliation statement has been sent                                                           |
| **Approved**                              | Indicates whether the transaction has been approved                                                                  |
| **Approved date**                         | The date when the transaction was approved                                                                           |


After you created the exchange difference invoice, you must select exchange difference type. The details of each type are as below;
- **Pending invoice -** This option delays invoicing to the following months, performing normal revaluation and generating vouchers and vendor transactions for the next day. Corrections are made at the end of the period.
- **Exchange difference invoice -** This option creates an invoice record, which can be invoiced immediately or later. Vendor and customer are reconciled with the invoice based on these records.
- **Revaluate and close -** If selected, no invoice is issued if not accepted by the other party or if we do not want to invoice. Settlement is done using standard currency revaluation function.

To calculate tax amount for exchange difference invoice, **Sales tax group** and **Item sales tax** **group** must be selected.
You can update or change the exchange difference invoice date in **Date** field manually.
According to legal requirements, an exchange difference invoice must be created when the exchange difference amount is in the debit balance. 
In this case, the serial prefix is mandatory and must be selected. When the exchange difference amount is in the credit balance, the document number of the incoming exchange difference invoice must be filled into this field.

#### Exchange difference invoice line transactions

This is the section where invoice transactions are recorded. If there are multiple invoice transactions, the grid will populate accordingly. Payments or collections made for multiple invoices may be invoiced as part of an exchange difference invoicing.

**Delete** is used to remove invoice transactions during the reconciliation process between the vendors and the customers. Once an invoice is deleted, the exchange difference amount displayed in the overview is automatically updated to reflect the deletion.

**Transactions** open the voucher transactions that are linked to the relevant invoice. This provides a detailed view of all the transactions associated with that specific invoice.

**Move** is utilized to transfer an exchange difference invoice to another invoice transaction within the same customer or vendor account. This helps in managing and organizing multiple invoice transactions efficiently.


| **Field**                                           | **Description**                                                                                 |
|-----------|-----------------------------------|
| **Source**                                          | The origin of the transaction                                                               |
| **Date**                                            | The date of the transaction                                                                 |
| **Voucher**                                         | The voucher number associated with the transaction                                          |
| **Invoice**                                         | The invoice number                                                                          |
| **Currency**                                        | The currency of the source transaction                                                      |
| **Exchange rate**                                   | The exchange rate applied to the transaction                                                |
| **Amount in transaction currency**                  | The amount of the transaction in the original currency                                      |
| **Amount**                                          | The amount of the transaction                                                               |
| **Amount in reporting currency**                    | The amount of the transaction in the reporting currency                                     |
| **Calculated exchange difference amount**           | The exchange difference amount calculated based on the transaction and reporting currencies |
| **Calculated exchange difference reporting amount** | The exchange difference amount in the reporting currency                                    |
| **Adjusted exchange difference amount**             | The adjusted exchange difference amount after any corrections                               |
| **Adjusted exchange difference reporting amount**   | The adjusted exchange difference amount in the reporting currency                           |
| **Sales tax group**                                 | The group of sales tax codes applicable to the transaction                                  |
| **Item sales tax group**                            | The group of item-specific sales tax codes                                                  |
| **Closed**                                          | Indicates whether the transaction is closed                                                 |

The functions in this section are explained as below:

| **Field**         | **Description**   |
|-----------|-----------------------------------|
| **Delete**        | When **Reconciliation statement is sent** is marked, deletion is done according to the records that come. After the deleted invoice transaction, the exchange difference amount in the overview is also automatically updated. |
| **Transactions**  | It opens the voucher transactions of the relevant invoice.                                                                                                                                                                     |
| **Move**          | It used to move an exchange difference invoice to another invoice transaction for same customer or vendor account.                                                                                                             |


#### Settled transactions

Settlement transactions are listed in the invoice settlement transactions tab. If more than one payment is done in response to one invoice, multiple records are displayed here. The value in the **Calculated exchange difference** field shows the exchange difference value that occurred for the settled transactions. Exchange differences amount arising from all invoice transactions are collected in the **Exchange difference amount** in the overview tab.


|  **Field** | **Details**            |
|-----------|-----------------------------------|
| **Source**                                          | The origin of the transaction                                                               |
| **Date**                                            | The date of the transaction                                                                 |
| **Voucher**                                         | The voucher number associated with the transaction                                          |
| **Invoice**                                         | The invoice number                                                                          |
| **Currency**                                        | The currency in which the transaction is conducted                                          |
| **Exchange rate**                                   | The exchange rate applied to the transaction                                                |
| **Settled currency**                                | The currency in which the amount is settled                                                 |
| **Amount settled**                                  | The amount settled in the transaction currency                                              |
| **Amount in reporting currency**                    | The amount settled in the reporting currency                                                |
| **Calculated exchange difference amount**           | The exchange difference amount calculated based on the transaction and reporting currencies |
| **Calculated exchange difference reporting amount** | The exchange difference amount in the reporting currency                                    |
| **Adjusted exchange difference amount**             | The adjusted exchange difference amount after any corrections                               |
| **Adjusted exchange difference reporting amount**   | The adjusted exchange difference amount in the reporting currency                           |
| **Payment date**                                    | The date when the payment was made                                                          |
| **Offset voucher**                                  | The voucher number used to offset the transaction                                           |
| **Payment currency**                                | The currency in which the payment was made                                                  |
| **Payment exchange rate**                           | The exchange rate applied to the payment                                                    |
| **Closed**                                          | Indicates whether the transaction is closed                                                 |

## Exchange rate adjustment on exchange difference reconciliation

When invoices, payments, and collections are reconciled with customers and vendors, exchange differences might arise due to timing differences in money transfers. 
The exchange rate difference must be re-evaluated for the customer or vendor, and the adjusted exchange difference can be manually updated. 
Initially, both calculated and adjusted exchange differences are the same, and manual adjustments can be made if needed.

If exchange rate type is selected as **Exchange difference invoicing**, the **Adjusted exchange difference amount** field will be editable for manual update.
When it is first run, both fields have the same values. The exchange difference field adjusted on the invoice settlement transactions form can be changed. 
The value from the customer and vendor reconciliation is entered here manually.

>[!NOTE]
>- The sign of the entered value should be considered.
>- The **Adjusted exchange difference amount** field on the **Exchange difference invoicing line transactions** section, updates the exchange difference amount field on the **Exchange difference invoice** section.
>- After the exchange difference on the above screen has been posted, the exchange difference must be re-run for the customer or the vendor.
>- When **Revaluate and close** is selected in **Exchange difference invoice type** field, these penny differences are closed again by posting again. The amount remaining when the settled transactions are listed for the customer or the vendor will not come for exchange difference invoicing.

>[!NOTE]
>- When the customer or vendor invoices or advance payments are transferred to other period, the transferring date of exchange rate should be as invoice date. Then, the **Foreign currency revaluation** in standard should be executed at the date of transfer.
>- If the vendor and customer invoice or advance payments are to be made within one voucher, the invoice numbers must be different. If this is not different, the amount of exchange difference calculated for them will be wrong.
>- Vendor or customer settled transactions cannot be reversed if the vendor or customer foreign exchange invoice has not been posted or has been posted.

## Creating an exchange difference invoice

To create a new exchange difference invoice;  
1. Go to **Accounts payable \> Periodic tasks \> Exchange difference invoicing** or **Accounts receivable \> Periodic tasks \> Exchange difference invoicing**.
2. Click **New**.
3. Select **Exchange difference invoices for vendors** or **Exchange difference invoices for customers**.
4. In the **Date** field, enter a date.
5. Select or change the relevant filtering parameters.
6. Click **OK**.
7. In **Exchange difference invoicing** form, click **Edit** to update the fields.
8. In the **Exchange difference type** field, select an option.
9. In the **Invoice** field, select a value or change the serial preifx manually.
10. In the **Invoice description** field, type a value if needed.
11. In the **Sales tax group** field, enter or select a value.
12. In the **Item sales tax group** field, enter or select a value.
13. In the **Description** field, type a value if needed.
14. Click **Post**.
15. Click **OK**.

Exchange difference invoices are specified by the **Foreign currency revaluation** transaction type in **General** tab in customer or vendor transactions.

\[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/main/articles/includes/footer-banner.md)\]
