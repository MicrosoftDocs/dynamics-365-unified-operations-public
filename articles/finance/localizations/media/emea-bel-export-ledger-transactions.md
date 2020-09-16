**Export ledger transactions**

The feature described in this topic is used to export the total balance of each
ledger account for a specific period to a plain text (ASCII) file in .CED
format. You can then import the generated file into third-party software to
create an accounting report according to country/region-specific requirements.

This functionality is available for legal entities that have their primary
address in Belgium.

Prerequisites
=============

Create posting journals
-----------------------

1.  Go to **General ledger \> Journal setup \> Posting journals**.

2.  On the **Journal setup** page, select **Create**. Posting journals and
    corresponding number sequences are automatically created.

Export ledger transactions to a plain text file in CED format
=============================================================

1.  In Microsoft Dynamics Lifecycle Services (LCS), in the Shared asset library,
    download the latest versions of the Electronic reporting (ER) configurations
    for the following report format:

-   Ledger transaction export format (BE)

>   For more information, see Download Electronic reporting configurations from
>   Lifecycle Services.

1.  In Dynamics 365 Finance, go to **General ledger \> Periodic tasks \> Export
    ledger transactions**.

2.  In the **Export ledger transactions to an ASCII file in CED format** dialog
    box, in the **Format mapping** field, select the **Ledger transaction export
    format (BE)** format that you just downloaded, and then select **OK**.

3.  In the **Electronic report parameters** dialog box, set the following
    fields.

| **Field**          | **Description**                                                             |
|--------------------|-----------------------------------------------------------------------------|
| From date          | Enter the first day of the reporting period.                                |
| To date            | Enter the last day of the reporting period.                                 |
| Reporting in euros | Set this option to **Yes** if the company uses a currency other than euros. |

4.  Select **OK** to generate and download the .txt file.

    For example, you post the following ledger transactions in the DEMF company.

| **Date**        | **Transaction type** | **Main account**          | **Offset account**        | **Amount net** | **VAT amount** | **Sales tax code** |
|-----------------|----------------------|---------------------------|---------------------------|----------------|----------------|--------------------|
| January 1, 2020 | Customer invoice     | 110110 – Bank account USD |                           | 1,000          | 190            | VAT19              |
| January 1, 2020 | Vendor invoice       |                           | 110120 – Bank account CNY | 1,095          | 76.65          | EU7                |
| January 1, 2020 | Customer invoice     | 110115 – Bank account CAD |                           | 800            | 0              | EUS                |

In this case, the file that is generated contains the following data.

![](media/0b5bb919597459a03cf883ad3e58e0b8.png)

>   A screenshot of a cell phone Description automatically generated

>   Here is an explanation of the columns in this file:

-   The first column shows the ledger account code.

-   The second column shows the debit balance on the ledger account.

-   The third column shows the credit balance on the ledger account.

-   The fourth column shows the name of the ledger account.

Note: To post ledger transactions for customer invoices, go to **Accounts
receivable \> Invoices \> All free text invoices**. For vendor invoices, go to
**Accounts payable \> Invoices \> Invoice journal**.
