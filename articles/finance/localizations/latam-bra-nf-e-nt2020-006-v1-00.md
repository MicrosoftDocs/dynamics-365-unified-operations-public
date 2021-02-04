# NT2020.006 – Intermediary sales digital platform for NF-e

In the scenarios where the sale was accomplished without the physical
presence of the consumer, and where the transaction has been
intermediated by a sale digital platform or marketplace, the XML of electronic fiscal document model 55 (NF-e) issued from this sale,
must contain a new tag to indicate the participation of such intermediary in the operation.

## How to enable the technical note in Finance and Supply Chain Management

1.  Log in Finance and Supply Chain Management.

2.  Go to **Organization administration &gt; Organizations &gt; Fiscal
    establishments &gt; Fiscal establishments.**

3.  Mark the Fiscal establishment.

4.  Select **Edit**.

5.  On fast tab **NF-e and NFC-e federal**, on field group **NF-e
    technical notes**, select **Enable NF-e technical note**.

6.  On field **NF-e technical notes**, select **2020.006 v1.00 technical
    note**.

## How to enable the technical note in Microsoft Dynamics AX2012 R3

Apply KB 4598546.

## Sale intermediated by own sales digital platform

When the sale is intermediated by a sale digital platform owned by the
Tax payer, in the header of the sales order created for this sales, on
the fast tab **Fiscal information**, if in the field **Presence type**
one of the options below are selected:

-   Internet or

-   Telesales or

-   Others

The tag **&lt;indintermed&gt;** is added to the XML of the NF-e with value 0.

## Out of scope of the feature

-   The NF-e issued from **Free Text Invoices** from sale without the presence of
    the consumer and intermediated by a sale digital platform is not in the scope of this feature.

-   The NF-e issued from Returns, Transfer order, Complementary and Tax
    Credit scenarios are not in scope of this feature.


