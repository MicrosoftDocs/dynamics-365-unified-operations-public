---
# required metadata

title: Fixed asset inquiries and reports
description: This topic provides information about the inquiries and reports for fixed asset acquisitions for Russia.
author: v-oloski
ms.date: 08/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Inquiries, Reports
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2021-07-26
ms.dyn365.ops.version: 8.1

---
# Fixed asset inquiries and reports

There are three types of inquiries that are available from a Fixed asset value model. To work with these inquiries, go to **Fixed assets (Russia)** > **Fixed asset record** and select **Value model**:

- **Transactions**
- **Budget transactions**
- **Balance**

The following inquiries are available by going to **Fixed assets (Russia)** > **Inquiries**.

- **Transactions**
- **Budget transactions**
- **Voucher transactions**
- **Documents**
- **Working clothes/Special riggings on-hand**

## Transactions

To access all transactions, go to **Fixed assets (Russia)** > **Inquiries** > **Transactions**. The **Transactions** page shows all transactions regardless which module they
were posted in. Transactions can be posted from the following modules:

- **Fixed assets (Russia)**
- **General ledger**
- **Accounts payable**
- **Accounts receivable**

Transaction details are provided on the **General** tab. Select **Voucher** for an overview of the voucher transactions that are related to the fixed asset transaction, the source, and the original document for the fixed asset transaction.

## Budget transactions

To view budget transactions, go to **Fixed assets (Russia)** > **Inquiries** > **Budget transactions**. The **Budget transactions** page list displays the details of fixed asset budget records.

To review the budget transaction in the **General ledger** module, select **Budget account entries**.

## Voucher transactions

To view voucher transactions, go to **Fixed assets (Russia)** > **Inquiries** > **Voucher transactions**.

This page shows all voucher transactions that are related to the fixed asset transactions. Before you run this inquiry, you can apply a filter. For example, you can filter based on the fixed asset inventory number or value model.

## Documents

To view fixed asset documents, go to **Fixed assets** > **Inquiries** > **Documents**. The **Documents** page displays all of the different types of local documents. For example, the Acceptance report (\#FA-1) and the Statement about fixed assets object acceptance-transference (\#FA-1) etc.). For more information, see [Unified printing forms for fixed assets (Russia)](printing-forms-fixed-assets.md).

## Working clothes/Special riggings on-hand

You can go to **Fixed assets** > **Inquiries** > **Working clothes/Special riggings on-hand** to view all of the selected Working clothes/Special riggings cards by workers with information on lifetime, issued and disposal date on a specified date. You can select the cards based on the value model, the type of cards (Working clothes or Special riggings), or the department. You can group data by division, issue rate, item group, and item. 

## Reports

There are many reports in the **Fixed assets (Russia)** module. The following sections list the reports and provide a short description.

### FA list

Go to **Fixed asset (Russia)** > **Reports** > **FA list**.

This report displays the fixed asset list with the net book value on the report date.

### Inventory FA list

Go to **Fixed asset (Russia)** > **Reports** > **Inventory FA list**.

This report displays the fixed asset data that is required for the legal form, \#FA-6.

### FA movement report

Go to **Fixed asset (Russia)** > **Reports** > **FA movement report**.

You can view the total data by fixed asset groups for specified period.

The report displays the netbook value at start date of period, operations (putting in operation, depreciation, changing of cost, disposal) in the period, and the net book value on the last day of the period.

### Inventory FA list

Go to **Fixed asset (Russia)** > **Reports** > **Inventory FA list**.

This report displays a list of fixed assets with an indication of the acquisition cost and net book value, and data on the disposal of fixed assets.

### FA putting into operation

Go to **Fixed asset (Russia)** > **Reports** > **FA putting into operation**.

This report displays information about the acquisition of fixed assets, including the acquisition date and price.

### FA disposal

Go to **Fixed asset (Russia)** > **Reports** > **FA disposal**.

This report displays information about the disposal of fixed assets, including the date of disposal, the net book value, and profit and loss information.

### FA barcodes

Go to **Fixed asset (Russia)** > **Reports** > **FA barcodes**.

This report provides a list of barcodes on the base of fixed asset records.

### Balance by FA

Go to **Fixed asset (Russia)** > **Reports** > **Balance by FA**.

This report displays the acquisition amount and the net book value of fixed assets with a total amount by transaction type. Transaction types include:

   - Revaluation
   - Major repair 
   - Depreciation revaluation 
   - Partial dismantlement 
   - Disposal (sales)
   - Disposal (dismantlement) 
   - Writing-off

### FA transactions

Go to **Fixed asset (Russia)** > **Reports** > **FA transactions**.

This report displays a list of operations by fixed asset with transaction amounts and other data.

### History of lease

Go to **Fixed asset (Russia)** > **Reports** > **History of lease**.

This report displays a history of fixed asset leasing with date of lease, the expected return date, the actual return date, and other data from the **FA leased** page which you can find by going to **Fixed asset** > **History** > **Lease** from the fixed asset record.

### Lease (report)

Go to **Fixed asset (Russia)** > **Reports** > **Lease (report)**.

This report displays data about leased fixed assets that weren't returned from lease, and for which a lease was posted.

### Sheet of FA and depreciation charges

Go to **Fixed asset (Russia)** > **Reports** > **Sheet of FA and depreciation charges**.

This report displays data for the selected fixed assets in a selected date range.

![Sheet of FA and depreciation charges](media/RUS-sheet-of-FA-and-depreciation.png)

### Insurance

Go to **Fixed asset (Russia)** > **Reports** > **Insurance**.

This report displays data about fixed asset insurance including policy number, insurance amount, and date.

### NVFA accounting card (No. MB-2)

Go to **Fixed asset (Russia)** > **Reports** > **NVFA accounting card (No. MB-2)**.

This report displays the MB-2 forms for all net value fixed assets as of a specified date.
