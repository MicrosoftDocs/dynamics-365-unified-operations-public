---
title: Customs declaration numbers
---

Customs declaration numbers
===========================

You can track customs declarations (CDs) from the time when goods arrive at the
customs terminal through the time when they are shipped to the end customer.

The CD number is one of the inventory dimensions that is manually entered when
goods are received. For example, you enter it when you register the invoice with
the facture from the vendor and then provide the appropriate field expenditure
documents, such as the facture for a sales order, to the customer. In this way,
the customer can trace the CD number. The specified CD number is also shown in
the purchase book.

To do CD accounting, you must activate the corresponding tracking dimension in
the item's tracking dimension group.

The receipt and sale of goods can be done in various ways. For example, goods
can be received through purchase orders from the vendor, and they can be sold to
the customer.

When goods are received, their CD numbers are manually entered. When goods are
sold, their CD numbers are automatically determined, based on the item lot. The
CD number that was used when the goods were purchased is shown on the documents
that are created when the goods are sold.

Set up CD numbers in tracking dimensions
----------------------------------------

1.  Go to **Product information management \> Setup \> Dimension and variant
    groups \> Tracking dimension groups**.

2.  Select **New** to create a dimension group.

3.  In the **Name** field, enter the name of the dimension group.

4.  In the **Description** field, enter a description.

5.  On the **Tracking dimensions** FastTab, in the row for **GTD number**,
    select the **Active** check box.

6.  Select **Save**.

![A screenshot of a cell phone Description automatically generated](media/f74eac0b5870ed35e1bcdf45cafe062a.jpg)

A screenshot of a cell phone Description automatically generated

Create a CD number
------------------

Before you can register CD numbers for newly received goods, you must enter them
in a corresponding database. You must also enter item names, and the country or
region of origin.

1.  Go to **Inventory management** \> **Inquiries and reports** \> **Tracking
    dimensions** \> **Custom decl. numbers**.

2.  Select **New** to create a CD number.

3.  In the **GTD number** field, enter the CD number.

4.  In the **Item number** field, select the item number.

>   **Note:** The item should have the tracking dimension group that you created
>   earlier, where the **GTD number** tracking dimension is activated.

1.  In the **Country/region** field, select the country or region.

2.  Select **Save**.

![](media/b30fa5cead3b35f783ecc2d7d07b9c12.jpg)

Specify the CD number in a purchase order
-----------------------------------------

1.  Create a purchase order, and on the purchase order line, select the item
    number.

-   **Note:** The item should have the tracking dimension group that you created
    earlier, where the **GTD number** tracking dimension is activated.

1.  On the **Line details** FastTab, on the **Product** tab, in the **Tracking
    dimensions** section, in the **GTD number** field, select the CD number that
    you created earlier.

![](media/1fb458bff4ea9ab011c4d9f16c8cd08a.jpg)

>   A screenshot of a social media post Description automatically generated

1.  Set other purchase order parameters, and create a facture in the usual way.
    Column 11 of the facture shows the information about the CD number.

![](media/52455bb181aa98e5175f8fb87b1eacae.jpg)

>   A close up of text on a white background Description automatically generated

View the CD number in the purchase book
---------------------------------------

1.  After the **Incoming VAT processing** procedure is completed, on the
    **Purchase books journal** page, on the Action Pane, select **Update** to
    update the purchase book.

2.  On the Action Pane, select **Lines**, and select the invoice that you just
    created. On the **General** tab, the **Custom decl. numbers** field shows
    the information about the facture and the CD number.

![](media/fef71bab707d96b35c148a32af7da99b.jpg)

>   A screenshot of a cell phone Description automatically generated

Ship goods that have CD numbers
-------------------------------

1.  Create a sales order, and on the sales order line, select the same item
    number that you used in the previous procedures in this topic.

2.  On the **Line details** FastTab, on the **Setup** tab, in the
    **Reservation** field, select **Automatic**, so that the item is
    automatically reserved from existing receipts when you create a sales order
    line.

3.  On the **Product** tab, in the **Tracking dimensions** section, in the **GTD
    number** field, select the CD number that you created earlier.

![](media/9b3fd51ea7866d56344bcd3fb563e90d.jpg)

>   A screenshot of a social media post Description automatically generated

1.  Set other sales order parameters, and create a facture in the usual way.
    Column 11 of the facture shows the information about the CD number.

![](media/f9a4aa90ad6707a5650247d0f4a6d7ee.jpg)

>   A close up of text on a white background Description automatically generated
