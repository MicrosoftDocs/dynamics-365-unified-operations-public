---
title: Use exchange difference invoicing
description: Learn how to configure and use exchange difference invoicing for the Republic of Türkiye in Microsoft Dynamics 365 Finance.
author: v-omerorhan 
ms.author: v-omerorhan
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/30/2025
ms.reviewer: johnmichalak
ms.search.region: Türkiye
ms.search.validFrom: 2020-02-03
ms.search.form: ExchangeDifferenceInvoicing
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Use exchange difference invoicing

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure and use exchange difference invoicing for the Republic of Türkiye in Microsoft Dynamics 365 Finance.

Exchange difference invoices must reflect the difference between the exchange rate at the time of invoicing and the exchange rate at the time of payment. In Türkiye, the requirement to create an exchange difference invoice comes from the behavior of the floating exchange rate system. In that system, the exchange rate at the time of invoicing might differ from the exchange rate at the time of payment. As a result, the amount in Turkish lira differs, even if the foreign exchange amount remains the same.

Companies must issue invoices for exchange rate differences. Those invoices must reflect the equivalent amount in Turkish lira, based on the foreign exchange buying rate of the Central Bank of the Republic of Türkiye.

According to the legislation, the tax rate that is applied to the exchange rate difference is crucial. The tax rate that is applied to the invoiced product or service must also be applied to the exchange difference invoice. If the invoice is exempt from tax or subject to withholding tax, the exchange difference invoice should be issued accordingly.

## Configure exchange difference invoicing

This section explains how to configure the system so that you can create exchange difference invoices.

### Exchange difference invoicing parameters

To configure exchange difference invoicing in Dynamics 365 Finance, go to the **Exchange difference invoicing parameters** page (**Accounts payable** or **Accounts receivable** \> **Setup** \> **Exchange difference invoicing** \> **Exchange difference invoicing parameters**). The fields that you must set are divided among several tabs.

The following table describes the fields on the **General** tab.

| Field | Description |
|-------|-------------|
| Require same posting profile in settlement | Specify whether the same posting profile must be used when transactions are settled. |
| Require same currency in settlement | Specify whether transactions can be settled only if they are in the same currency. |
| Require invoice approval | Specify whether the invoice must be approved before it can be processed. |
| Exchange difference invoice | Select the report format to use to print the exchange difference invoice after it's posted to the ledger. |
| Exchange difference invoice voucher | Select the report format to use for exchange difference invoice reconciliation. |

The following table describes the fields on the **Invoice** tab.

| Field | Description |
|-------|-------------|
| Separate exchange difference invoice for each invoice | Specify whether a separate exchange difference invoice should be created for each invoice. |
| Include only fully settled invoices | Specify whether only fully settled invoices should be included in the exchange difference invoice update. |
| Group by dimension | Specify whether invoices should be grouped by financial dimension. |
| Group by tax group | Specify whether invoices should be grouped by tax group. |
| Group by profit and loss | Specify whether invoices should be grouped by profit and loss. |
| Default invoice prefix | Specify whether the default serial prefix for the invoice number should be assigned automatically to exchange difference invoices. |
| Copy description to voucher transaction | Specify whether the description should be copied to the voucher transaction. |
| Copy description to journal line | Specify whether the description should be copied to the journal line. |

The following table describes the fields on the **Number sequence** tab.

| Field | Description |
|-------|-------------|
| Exchange difference invoice | Define the unique key for exchange difference invoices. |
| Exchange difference invoice voucher | Define the unique key for vouchers of exchange difference invoices. |
| Exchange difference pending invoice voucher | Define the unique key for vouchers of exchange difference pending invoices. | 
| Exchange difference revaluate and close voucher | Define the unique key for vouchers of exchange difference revaluate and close. |

> [!NOTE]
> Separate number sequences are used for each exchange difference type to ensure correct document type mapping in e-Ledger.

### Realized gain and realized loss accounts

Before you create an exchange difference invoice, the realized gain and realized loss accounts must be defined on the **Currency revaluation posting profile** page in Accounts payable and Accounts receivable.

Learn how to define a currency revaluation posting profile in [Currency revaluation posting profiles](../../general-ledger/currency-revalue-posting-profile.md).

### Exchange difference invoice formats

This section explains how to configure Excel reports for the exchange difference invoicing process.

The reports are implemented as Electronic reporting (ER) configurations. You must import the latest versions of the following ER configurations:

- **Exchange difference invoice (TR) (Excel)** – This configuration provides an Excel report that you can use to get a printout of exchange difference invoicing.
- **Exchange adjustment statement (TR) (Excel)** – This configuration provides an Excel report that you can use to get an exchange difference reconciliation report. The report includes information about the exchange difference invoice, and the invoice and payment transactions that generated the exchange difference amount.
- **Model mapping (TR)** – This configuration sets the structure and data mapping for exchange difference invoice data. It ensures that data is correctly formatted for ER.

Learn how to import ER formats in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Before you can generate the reports, the relevant formats must be selected in the **Exchange difference invoice** and the **Exchange difference invoice voucher** fields on the **General** tab of the **Exchange difference invoicing parameters** page.

## Process exchange difference invoicing

This section provides general information about the fields and functions that are available on the **Exchange difference invoicing** page.

The exchange difference invoicing feature retrieves settled invoice and payment transactions for customers and vendors that are specified during the process. When you select **New** on the Action Pane to create exchange difference invoice records, two options are presented:

- **Exchange difference invoices for vendors** – Generate exchange difference invoices that are based on settled vendor invoice and payment transactions.
- **Exchange difference invoices for customers** – Generate exchange difference invoices that are based on settled customer invoice and payment transactions.

The **Date** field determines which settled transactions are considered for customers and vendors. It's used to ensure that no exchange differences are created from payment transactions that are dated after the specified invoice date.

> [!NOTE]
> The values set on the **Invoice** tab of the **Exchange difference invoicing parameters** page are used as default values when a new exchange difference invoice is created.
>
> - Separate exchange difference invoice for each invoice
> - Group by dimension
> - Group by tax group
> - Group by profit and loss

After exchange difference invoices are created, various functions are available for them on the **Exchange difference invoicing** page. The following table describes the buttons on the **Invoice** tab of the Action Pane.

| Button | Description |
|-------|-------------|
| Create return quotation | Copy the exchange difference invoice for return invoices that come after invoicing or that the company must issue. |
| Reverse | Reverse the registration of the transactions that occurred. In exchange difference reversal, automatic marking is done for customer and vendor invoice transactions, customer and vendor transactions, and voucher transactions. |
| Transactions | Go to the customer or vendor transactions for exchange difference invoices. |
| Exchange rate adjustment | Get a printout of exchange difference invoicing. |
| Exchange adjustment statement | Get an exchange difference reconciliation report. |

> [!NOTE]
> After the vendor or customer exchange difference invoice is created, settled transactions for the customer or vendor can't be reversed.

The **Exchange difference invoice** section provides general information about the generated exchange difference invoices. The following table describes the fields in the **Exchange difference invoice** section.

| Field | Description |
|-------|-------------|
| Exchange difference invoice | The unique number of the exchange difference invoice. |
| Exchange difference type | The type of exchange difference invoice. |
| Account type | The type of account that is involved (for example, customer or vendor). |
| Account number | The unique identifier of the account. |
| Account name | The name that is associated with the account number. |
| Currency | The currency that the transaction is conducted in. |
| Exchange difference amount | The amount of the exchange difference in the transaction currency. |
| Exchange difference reporting amount | The amount of the exchange difference in the reporting currency. |
| Date | The posting date of the transaction. |
| Invoice serial | The serial prefix of the exchange difference invoice. |
| Invoice | The invoice number. |
| Invoice description | A brief description of the exchange difference invoice. |
| Sales tax group | The sales tax group of the exchange difference invoice. |
| Item sales tax group | The item sales tax group of the exchange difference invoice. |
| Sales tax amount | The sales tax amount that is applied to the exchange difference invoice. |
| Adjusted tax amount | The adjusted sales tax amount after any corrections. |
| Posted | A value that specifies whether the transaction was posted. |
| Exchange difference invoice voucher | The voucher number that is associated with the exchange difference invoice. |
| Description | A brief description of the exchange difference invoice voucher. |
| Reference voucher | The voucher of the new exchange difference invoice generated after revaluation to the next day in the **Pending invoice** type. It also displays the voucher of the reversed exchange difference invoice.|
| Reference voucher date | The date of the new exchange difference invoice generated after revaluation to the next day in the **Pending invoice** type. It also displays the revere date of the reversed exchange difference invoice.|
| Posting profile | The posting profile that is used to post the exchange difference invoice. |
| Exchange difference account | The account that is used to post the realized gain or realized loss exchange difference amount. |
| Reconciliation statement sent | A value that specifies whether the **Exchange adjustment statement** report was generated. |
| Approved | A value that specifies whether the transaction was approved. |
| Approved date | The date when the transaction was approved. |

The **Exchange difference invoice line transactions** section contains information about the invoices that are related to the exchange difference invoice. If there are multiple invoice transactions, the grid is populated accordingly. Payments or collections that are made for multiple invoices might be invoiced as part of exchange difference invoicing.

The following table describes the fields in the **Exchange difference invoice line transactions** section.

| Field | Description |
|-------|-------------|
| Source | The origin of the transaction. |
| Date | The date of the transaction. |
| Voucher | The voucher number that is associated with the transaction. |
| Invoice | The invoice number. |
| Currency | The currency of the source transaction. |
| Exchange rate | The exchange rate that was applied to the transaction. |
| Amount in transaction currency | The amount of the transaction in the original currency. |
| Amount | The amount of the transaction. |
| Amount in reporting currency | The amount of the transaction in the reporting currency. |
| Calculated exchange difference amount | The exchange difference amount that is calculated based on the transaction and reporting currencies. |
| Calculated exchange difference reporting amount | The exchange difference amount in the reporting currency. |
| Adjusted exchange difference amount | The adjusted exchange difference amount after any corrections. |
| Adjusted exchange difference reporting amount | The adjusted exchange difference amount in the reporting currency. |
| Sales tax group | The sales tax group that is applicable to the transaction. |
| Item sales tax group | The item sales tax group. |
| Closed | A value that specifies whether the transaction is closed. |

The **Settled transactions** section lists payment transactions. If multiple payments are made for a single invoice, each payment appears as a separate record. The **Calculated exchange difference** field shows the exchange difference amount for the settled transactions. The **Exchange difference amount** field on the **Overview** tab summarizes the total exchange difference amount from all invoice transactions.

The following table describes the fields in the **Settled transactions** section.

| Field | Description |
|-------|-------------|
| Source | The origin of the transaction. |
| Date | The date of the transaction. |
| Voucher | The voucher number that is associated with the transaction. |
| Invoice | The invoice number. |
| Currency | The currency that the transaction is conducted in. |
| Exchange rate | The exchange rate that is applied to the transaction. |
| Settled currency | The currency that the amount is settled in. |
| Amount settled | The settled amount in the transaction currency. |
| Amount in reporting currency | The settled amount in the reporting currency. |
| Calculated exchange difference amount | The exchange difference amount that is calculated based on the transaction and reporting currencies. |
| Calculated exchange difference reporting amount | The exchange difference amount in the reporting currency. |
| Adjusted exchange difference amount | The adjusted exchange difference amount after any corrections. |
| Adjusted exchange difference reporting amount | The adjusted exchange difference amount in the reporting currency. |
| Payment date | The date when the payment was made. |
| Offset voucher | The voucher number that is used to offset the transaction. |
| Payment currency | The currency that the payment was made in. |
| Payment exchange rate | The exchange rate that is applied to the payment. |
| Closed | A value that specifies whether the transaction is closed. |

## Create an exchange difference invoice

To create a new exchange difference invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** or **Accounts receivable** \> **Periodic tasks** \> **Exchange difference invoicing**.
1. Select **New**, and then select either **Exchange difference invoices for vendors** or **Exchange difference invoices for customers**.
1. In the **Date** field, select a date.
1. Set the **Default invoice prefix** option to **Yes** or **No**.
    - If you set it to **Yes**, the serial prefix is automatically selected in the **Invoice serial** field, based on the **Default prefix** value that is selected on the **Preprinted serial numbers** page.
    - If you set it to **No**, you must manually select the serial prefix in the **Invoice serial** field. Learn more in [Use serial numbering](emea-tur-serial-numbering.md).
1. Select or change the other filtering parameters.
1. Select **OK**.
1. After the exchange difference invoices are listed on the **Exchange difference invoicing** page, select the **Edit** button to update the fields.
1. In the **Exchange difference type** field, select one of the following values:
    - **Pending invoice** – Delay invoicing until the following months. However, perform regular revaluation, and generate vouchers and vendor transactions for the next day. Corrections are made at the end of the period.
    - **Exchange difference invoice** – Create an invoice transaction that can be invoiced either immediately or later. The vendor and customer are reconciled with the invoice, based on these records. When the customer or vendor invoices or advance payments are transferred to other periods, the transfer date of the exchange rate should match the invoice date. The standard foreign currency revaluation should then be run on the transfer date.
    - **Revaluate and close** – No invoice is issued if the other party doesn't accept it, or if you don't want to invoice. Settlement is done by using the standard currency revaluation function. When **Revaluate and close** is selected, the penny differences are closed again by posting again. The amount that remains when the settled transactions are listed for the customer or the vendor doesn't come for exchange difference invoicing.
1. In the **Invoice serial** field, select a serial prefix. If a serial prefix was automatically selected, you can manually change it.
1. In the **Invoice description** field, enter a description as required.
1. In the **Sales tax group** field, select a value.
1. In the **Item sales tax group** field, select a value.
1. In the **Description** field, enter a description as required.
1. Select **Post**.
1. Select **OK**.

## Edit an exchange difference invoice

You can use the **Date** field to manually change the posting date of exchange difference invoices. To calculate the tax amount for the exchange difference invoice, you must select a sales tax group and an item sales tax group.

You can use the **Delete** button to remove a selected record in the **Exchange difference invoice** section. When an exchange difference invoice is deleted, the invoice and payment transactions that led to its creation are also deleted. If a deleted exchange difference invoice must be re-created, select **New** on the **Exchange difference invoicing** page, and then select either **Exchange difference invoices for vendors** or **Exchange difference invoices for customers**. The relevant exchange difference invoice is then listed again, based on the selected parameters.

In some cases, the generated exchange difference invoice might have to be excluded before it's posted to the ledger. To exclude an exchange difference invoice, select **Exclude**. You can view information about excluded records on the **Excluded records** tab. To include a record again, select **Include**.

> [!NOTE]
> To delete an excluded exchange difference invoice that appears on the **Excluded records** tab, first include the record by selecting **Include**, and then delete it by selecting **Delete**.

According to legal requirements, if the exchange difference amount is a debit balance, an exchange difference invoice must be created for the relevant customer or vendor. In this case, the **Invoice serial** field is mandatory, and a serial prefix must be selected in it. If the exchange difference amount is a credit balance, the document number of the exchange difference invoice that is received from the relevant customer or vendor must be entered in the **Invoice serial** field.

> [!NOTE]
> - If the **Default invoice prefix** option is set to **No**, the **Invoice serial** field is mandatory, and a serial prefix must be manually selected in it.
> - If the **Default invoice prefix** option is set to **Yes**, the **Invoice serial** field is automatically set, based on the **Default prefix** value that is selected on the **Preprinted serial numbers** page. Learn more in [Use serial numbering](emea-tur-serial-numbering.md).

When you generate the **Exchange adjustment statement** report from the **Document** group on the **Invoice** tab of the Action Pane, the **Reconciliation statement sent** field in the **Exchange difference invoice** section is marked. The relevant exchange difference invoice can then be approved by using the **Approve** button. As required, approval can be reset by using the **Reset Approval** button.

If the **Require invoice approval** option is set to **Yes** on the **General** tab of the **Exchange difference invoicing parameters** page, the **Post** button becomes available only after the exchange difference invoice is approved. This button can be used to post the invoice to the ledger. If the **Require invoice approval** option is set to **No**, the exchange difference invoice can be posted to the ledger without approval.

Exchange difference invoices are indicated by the **Foreign currency revaluation** transaction type on the **General** tab of customer or vendor transactions after they are posted.

In the **Exchange difference invoice line transactions** section, you can use the **Delete** button to remove invoice transactions during the reconciliation process between vendors and customers. After an invoice is deleted, the exchange difference amount that is shown in the **Exchange difference amount** field in the **Exchange difference invoice** section is automatically updated to reflect the deletion. You can select **Transactions** to open a detailed view of all the voucher transactions that are associated with the relevant invoice. You can select **Move** to transfer an exchange difference invoice to another invoice transaction within the same customer or vendor account. This button helps efficiently manage and organize multiple invoice transactions.

When you reconcile invoices, payments, and collections with customers and vendors, timing differences in money transfers might cause exchange differences. You must review the value of the **Exchange difference amount** field and manually adjust it as required. Initially, the **Calculated exchange difference amount** and **Adjusted exchange difference amount** values are the same. However, you can make adjustments in the **Settled transactions** section. The reconciliation amount from customers and vendors must be manually entered.

## Print the exchange difference invoicing documents

This section explains how to print the Excel reports from the **Exchange difference invoicing** page.

### Print the exchange rate adjustment report

You can print the exchange rate adjustment report after the exchange difference invoice is posted.

To print the exchange rate adjustment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** or **Accounts receivable** \> **Periodic tasks** \> **Exchange difference invoicing**.
1. Select an exchange difference invoice that was posted.
1. On the Action Pane, on the **Invoice** tab, in the **Document** group, select **Exchange rate adjustment**.

### Print the exchange adjustment statement report

To print the exchange adjustment statement report, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** or **Accounts receivable** \> **Periodic tasks** \> **Exchange difference invoicing**.
1. Select an exchange difference invoice that wasn't posted.
1. On the Action Pane, on the **Invoice** tab, in the **Document** group, select **Exchange adjustment statement**.

When the **Exchange adjustment statement** report is printed, the **Reconciliation statement sent** field is marked, and the **Approve** button becomes available in the **Exchange difference invoice** section. If you select **Approve**, the **Approved** and **Approved date** fields are set.

> [!NOTE]
> If the **Require invoice approval** option is set to **Yes** on the **Exchange difference invoicing parameters** page, follow these steps:
>
> - Before you can post the exchange difference invoice, you must select **Approve** for it in the **Exchange difference invoice** section.
> - To roll back the exchange difference invoice, select **Reset approval**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
