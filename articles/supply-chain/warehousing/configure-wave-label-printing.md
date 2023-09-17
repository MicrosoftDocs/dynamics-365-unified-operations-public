---
title: Wave label printing
description: This article describes wave label printing and explains how to set it up.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSWaveLabel, WHSWaveLabelTemplate, WHSWaveLabelLayoutRow, WHSDocumentRouting, WHSWaveTableListPage, WHSPostMethod, WHSMobileDisplayWaveLabelListLookup, WHSWaveLabelType, WHSWaveLabelTemplateGroup, WHSDocumentRoutingLayout
ms.topic: how-to
ms.date: 12/02/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Wave label printing

[!include [banner](../includes/banner.md)]

Wave label printing offers an alternative approach to label printing by introducing a new wave step method that lets you create and print labels directly from the wave template during wave execution. Therefore, the labels will already be available before workers run the work order on a mobile device. Workers can then attach the required labels during picking instead of after picking.

Wave label printing uses Zebra Programming Language (ZPL) to create label layouts. A label layout is divided into three sections (header, body, and footer) to allow for labels that have repeating structure. Wave label templates tell the system which label layout to use. Users can specify which printer is used. They can also print labels on several printers at the same time, as they require. The **Wave label history** page shows a record of all labels that have been created by using this setup.

You can print and collate labels based on work headers, you can print break labels per work header, and you can print container content labels, case labels, and other similar labels.

> [!NOTE]
> This functionality doesn't replace existing label printing functionality that is based on document routing.

Wave label printing offers the following enhancements:

- Print labels according to the number of cartons on a single work line, without using containerization. (A "carton" is a unit that is designated on unit sequence group lines.)
- Print several different label sequences (for example, carton and pallet labels).
- Include label enumeration (for example, 1/124, 2/124, ... 124/124), and define the range of enumeration (for example, work line, load line, or shipment).
- Create and print a bill of lading ID on labels before the bill of lading is generated.
- Create a unique serial shipping container code (SSCC) for each carton, and include it on each label.
- Create GS1-compliant number sequences for bill of lading IDs and SSCCs.
- Reprint labels from both mobile devices and the rich client.
- Void labels (for example, in short pick scenarios), and reprint them.
- Clean up the wave label history.
- Improvements to document routing layouts are shared between document routing layouts and wave label layouts. (For more information, see [Document routing label layouts](../warehousing/document-routing-layout-for-license-plates.md).)

These enhancements make it more efficient to label cartons before palletization. They especially benefit companies that ship to large retailers that automatically confirm order receipts by scanning each carton separately.

> [!NOTE]
> You can implement the configuration scenarios that are described in this article either separately or in combination, depending on your business requirements. You can design several wave label templates that work in sequence (as illustrated in scenario 3). For example, you can use scenario 1 to print carton labels and scenario 2 to print pallet labels (if pallets in stock vary in size and composition).

## Scenario 1: Wave label printing where a single wave label is generated

This scenario shows how a company can print shipping labels for a large retailer that automatically confirms order receipts by scanning each carton separately.

This scenario shows the end-to-end flow.

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Make sure that the wave label method is available

You might have to regenerate the wave process methods to make the wave label printing method available.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Confirm that **waveLabelPrinting** is in the list. If it isn't, select **Regenerate methods** on the Action Pane to add it.

### Configure a wave template

Wave templates let you link specific instances of wave methods to a corresponding wave label template.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select a template, such as **62 Shipping Default**.
1. On the **Methods** FastTab, move the **Wave label printing** method to the **Selected methods** column.
1. In the **Selected methods** column, select the **Wave label printing** method, and set its **Wave step code** field to *PrintLabel*. For more information about wave step codes, see [Wave step codes](wave-step-codes.md).

### Create a wave label layout

The label layout controls what information is printed on the label and how it's laid out. Here, you enter the ZPL code that is sent to the printer.

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label layouts**.
1. Create a record that has the following settings:

    - **Label layout ID:** *Carton*
    - **Description:** *Carton (SSCC)*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Wave label row settings**.

    The **Wave label row settings** page appears. Here, you can configure the dynamic part of the label.

1. Add a row that has the following settings:

    - **Row Id:** *WaveLabel*
    - **Row table name:** *WHSWaveLabel*
    - **Row start position:** *0*

        This field defines the vertical position where the row will begin on the label.

    - **Row height:** *0*

        This field defines the height of each row (in points), according to the ZPL standard. The row height is positive for horizontal labels and negative for vertical labels. Because there's just one row in this example, you can set the value to *0* (zero).

    - **Rows per page:** *1*

        This field defines the number of rows that can be printed on each label.

        > [!NOTE]
        > This setup will cause a separate ZPL label to be printed for each record in the wave labels table.

1. Close the page.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work type*
    - **Criteria:** *Pick*

    This query ensures that only pick-type work lines will be printed on the label, not put-type work lines.

1. If you want to be able to print the bill of lading ID, on the **Joins** tab, select the **Work lines** table, and join the **Shipments** table to it.
1. Close the query editor dialog box.
1. The **Printer text Layout** FastTab has three sections where you can write printer code: **Header section**, **Body section**, and **Footer section**. In the **Header section** section, in the **Label header** field, enter code for the required header. For example, if you're using Zebra printers, you can use the following code.

    ```plaintext
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNW^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI0^XZ
    ^XA
    ^MMT
    ^PW812
    ^LL1218
    ^LS0
    ^FT85,505^A0N,28,28^FH\^FD$WHSShipmentTable.CustomerReq$^FS
    ^FO1,173^GB809,0,1^FS
    ^FO0,391^GB809,0,1^FS
    ^FO3,599^GB809,0,2^FS
    ^FO420,176^GB0,216,1^FS
    ^FO313,3^GB0,169,1^FS
    ^FO0,807^GB809,0,1^FS
    ^FT529,370^A0N,28,26^FH\^FD$WHSShipmentTable.BillOfLadingId$^FS
    ^BY2,3,132^FT25,344^BCN,,N,N
    ^FD>:(420)>38102>63^FS
    ^FT526,315^A0N,28,28^FH\^FD ^FS
    ^FT437,248^A0N,28,28^FH\^FDCARR: $WHSShipmentTable.SCAC$^FS
    ^FT425,201^A0N,23,24^FH\^FDCARRIER:^FS
    ^FT17,68^A0N,20,19^FH\^FDIntershipping, Inc.^FS
    ^FT15,99^A0N,20,19^FH\^FD1000 Shipping Lane^FS
    ^FT16,158^A0N,20,19^FH\^FD ^FS
    ^FT438,368^A0N,28,28^FH\^FDB/L#^FS
    ^FT15,128^A0N,20,19^FH\^FDShelbyville TN 38102^FS
    ^FT19,203^A0N,23,24^FH\^FD(420) SHIP TO POSTAL CODE^FS
    ^FT331,39^A0N,28,28^FH\^FDShip To:^FS
    ^FT14,39^A0N,28,28^FH\^FDShip From:^FS
    ^FT331,67^A0N,23,24^FH\^FDWAL-MART DC 1111A-ABC DIS^FS
    ^FT330,98^A0N,23,24^FH\^FDDEPT 10^FS
    ^FT329,166^A0N,23,24^FH\^FDSpringfield TN 39021^FS
    ^FT330,134^A0N,23,24^FH\^FD100 Main Street^FS
    ^FT19,504^A0N,28,28^FH\^FDPO#:^FS
    ^FT437,316^A0N,28,28^FH\^FDPRO#^FS
    ^FT105,371^A0N,28,28^FB130,1,0,C^FH\^FD(420)39021^FS
    ```

1. In the **Body section** section, in the **Label body** field, enter ZPL code for the required body. Here's an example.

    ```plaintext
    <Row name="WaveLabel">
    ^FT127,439^A0N,28,28^FH\^FD$WHSWaveLabel.SeqNum$^FS
    ^FT256,439^A0N,28,28^FH\^FD$WHSWaveLabel.NumberOfLabels$^FS
    ^FT17,439^A0N,28,28^FH\^FDCARTON^FS
    ^FT522,422^A0N,23,24^FH\^FDVPN:^FS
    ^FT74,1156^A0N,28,28^FH\^FDSSCC-18^FS
    ^FT21,579^A0N,28,28^FH\^FDItem name:^FS
    ^FT107,580^A0N,28,28^FH\^FD$WHSWaveLabel.LabelItemName$^FS
    ^FT576,423^A0N,23,21^FH\^FD$WHSWaveLabel.LabelItemId$^FS
    ^FT252,1155^A0N,32,31^FH\^FD(00)$WHSWaveLabel.WaveLabelId$^FS
    ^BY4,3,283^FT66,1115^BCN,,N,N
    ^FD>;>800$WHSWaveLabel.WaveLabelId$^FS
    ^FT194,439^A0N,28,28^FH\^FDof^FS
    </Row>
    ```

1. In the **Body section** section, in the **Label footer** field, enter ZPL code for the required footer. Here's an example.

    ```plaintext
    ^PQ1^XZ
    ```

    > [!NOTE]
    > This setup will print one copy of each label. If you require more copies (for example, one copy for each side of the pallet), set the **n** value for the **\^PQn** section in the footer to the required number of copies. For example, to print four copies of each label, specify **\^PQ4**.

Your label is now ready to use.

### Create a wave label type

Wave label types are used to link wave label templates to a unit on unit sequence group lines.

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label types**.
1. Add a wave label type that has the following settings:

    - **Label type:** *Carton*
    - **Description:** *Carton*

### Set up unit sequence groups

Next, set up the unit sequence group for the wave label type.

1. Go to **Warehouse management \> Setup \> Warehouse \> Unit sequence groups**.
1. Select the **Ea Box PL** group.
1. For the **Box** line, set the **Wave level type** field to *Carton*.

### Create a wave label template

Next, create the wave label template for the wave label type.

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label templates**.
1. Add a wave level template, and set the following values in the header:

    - **Label template name:** *Carton labels*
    - **Description:** *Carton labels*
    - **Wave step code:** *PrintLabel*
    - **Warehouse:** *62*

1. On the **General** FastTab, set the **Wave label type** field to *Carton*.
1. On the **Wave label template details** FastTab, add a new row that has the following settings:

    - **Label layout ID:** *Carton*
    - **Printer name:** Select an appropriate ZPL printer.
    - **Run query:** *Yes* (This setting is optional, but it's recommended for optimal performance.)

1. On the Action Pane, select **Save**.
1. Optional: If you're setting up a customer-specific label design, you must create a query to find the customer's account. On the **Wave label template details** FastTab, select **Edit query**. Then, in the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Account number*
    - **Criteria:** Enter the relevant customer account number.

    When you've finished, select **OK** to close the query editor dialog box.

1. On the Action Pane, select **Edit query** to open the query editor dialog box for the whole label template.
1. In the query editor dialog box, on the **Sorting** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Reference load line id (Record-ID)*
    - **Search direction:** *Ascending*

1. Select **OK** to close the query editor dialog box.
1. A message box prompts you to confirm the grouping reset operation. Select **Yes** to continue.
1. On the Action Pane, select **Wave label template group**.
1. In the **Wave label template group** dialog box, select the row where the **Reference field name** field is set to *Reference load line id*, and then select the **Label build ID** check box for this row.

    > [!NOTE]
    > This setup will create one label sequence ("Carton 1 of X") per load line throughout the wave, regardless of the work grouping setup. This label sequence can be printed on the label layout.

### Configure number sequence extensions

Number sequence extensions control the GS1 compliance of specific number sequences. This configuration is optional for the current scenario. For more information and configuration instructions, see [Configure number sequence extensions](../warehousing/configure-number-sequence-extensions.md).

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Warehouse:** *62*

1. Add two sales order lines that have the following settings:

    - Sales order line 1:

        - **Item number:** *A0001*
        - **Quantity:** *9024*
        - **Unit:** *ea* (9024 ea = 376 Box = 47 PL)

    - Sales order line 2:

        - **Item number:** *A0002*
        - **Quantity:** *9016*
        - **Unit:** *ea* (9016 ea = 322 Box = 46 PL)

    > [!NOTE]
    > The items and quantities that are provided here are only examples. They must use the unit sequence group that you defined earlier, appropriate unit conversions from *ea* to *Box* to *PL* must be defined for them, and they must have stock in warehouse *62*. For more information, see [Unit of measure and stocking policies](unit-measure-stocking-policies.md).

1. Select sales order line 1. Then, in the **Sales order line** section, on the **Inventory** menu, select **Reservations**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**, and then close the page.
1. Repeat steps 4 and 5 for sales order line 2.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    The following events occur:

    - The system processes the created shipment by using the template that includes the label printing step. The label layout will be used to define the format of the label, and the result will be a label that is printed on the printer that is selected in the label template.
    - Wave labels are generated and printed. The number of labels will equal the number of cartons (in this example, 376 Box labels for line 1 and 322 Box labels for line 2).
    - A new bill of lading ID is generated for the shipments. If you configured the number sequence extensions, the wave label IDs will follow the **SSCC-18** number format. 

You can view and reprint wave labels from the following pages. On the Action Pane of each page, on the **Shipments** tab, in the **Related information** group, select **Wave labels**.

- All shipments \> Shipment details
- All loads \> Load details
- All waves
- Wave labels
- Wave label history

## Scenario 2: Wave label printing for containerization (without wave label records)

This scenario lets you print wave labels when you use containerization to automatically split items into cartons and therefore don't require a wave label record. In this case, the container ID acts as a placeholder for the SSCC.

Here are the main differences between this scenario and scenario 1:

- **Wave label templates:** You won't select a wave label type on the wave label template, and you won't require a label build grouping. Otherwise, you'll configure the wave label template and link to the wave template in the same way that is described in scenario 1. You must leave the wave label type blank to prevent wave labels from being generated.
- **Wave label layouts:** You'll configure the wave label layout row settings for work lines instead of wave label records. You must configure the row setting for the label layout by using the **WHSWorkLine** table instead of the **WHSWaveLabel** table. The **Rows per page** setting controls the number of rows that the body section will have. 

This configuration is also suitable for business scenarios where multiple different items are packed into one labeled box or into a pallet, and this packing process can be defined by work creation (for example, work that is grouped by shipment).

This scenario shows the end-to-end flow.

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Make sure that the wave label method is available

You might have to regenerate the wave process methods to make the wave label printing method available.

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Confirm that **waveLabelPrinting** is in the list. If it isn't, select **Regenerate methods** on the Action Pane to add it.

### Set up a wave template

Wave templates let you link specific instances of wave methods to a corresponding wave label template.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Select a template, such as **63 Containerization**.
1. On the **Methods** FastTab, move the **Wave label printing** method to the **Selected methods** column.
1. In the **Selected methods** column, select the **Wave label printing** method, and set its **Wave step code** field to *PrintLabel*. For more information about wave step codes, see [Wave step codes](wave-step-codes.md).

### Create a wave label layout

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label layouts**.
1. Create a record that has the following settings:

    - **Label layout ID:** *Carton*
    - **Description:** *Carton (SSCC)*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Wave label row settings**.

    The **Wave label row settings** page appears. Here, you can configure the dynamic part of the label.

1. Add a row that has the following settings:

    - **Row Id:** *WorkLine*
    - **Row table name:** *WHSWorkLine*
    - **Row start position:** *500*

        This field defines the vertical position where the row will begin on the label.

    - **Row height:** *-50*

        This field defines the height of each row. The row height is positive for horizontal labels and negative for vertical labels.

    - **Rows per page:** *5*

        This field defines the number of rows that can be printed on each label.

        > [!NOTE]
        > This setup will print several ZPL labels per work, where each page can hold up to five work lines. For example, if a label is printed for a container that has 12 lines, three labels will be printed. If you want to print a separate label for each pick line, set this value to *1*.

1. Close the page.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work type*
    - **Criteria:** *Pick*

1. If you want to be able to print the bill of lading ID, on the **Joins** tab, select the **Work lines** table, and join the **Shipments** table to it.
1. Close the query editor dialog box.
1. The **Printer text Layout** FastTab has three sections where you can write printer code: **Header section**, **Body section**, and **Footer section**. In the **Header section** section, in the **Label header** field, enter code for the required header. For example, if you're using Zebra printers, you can use the following code.

    ```plaintext
    CT~~CD,~CC^~CT~
    ^XA
    ^LH10,10
    ^FO0,0 ^AT ^FD$WHSWorkTable.ContainerId$ ^FS
    ^FO0,75 ^AT ^FD$WHSWorkLine.ShipmentId$ ^FS
    ^FO0,150 ^AT ^FD$WHSShipmentTable.BillOfLadingId$ ^FS
    ```

1. In the **Body section** section, in the **Label body** field, enter ZPL code for the required body. Here's an example.

    ```plaintext
    <Row name="WorkLine">
    <Heading>
    //Optional heading for section of rows
    </Heading>
    ^FO0,450 ^AT ^FDItem ^FS
    ^FO200,450 ^AT ^FDQuantity ^FS
    ^FO0,[[YPos]] ^AT ^FD$WHSWorkLine.ItemId$ ^FS
    ^FO200,[[YPos]] ^AT ^FD$WHSWorkLine.QtyWork$ ^FS
    </Row>
    ```

1. In the **Body section** section, in the **Label footer** field, enter ZPL code for the required footer. Here's an example.

    ```plaintext
    ^PQ1^XZ
    ```

    > [!NOTE]
    > This setup will print one copy of each label. If you require more copies (for example, one copy for each side of the pallet), set the **n** value for the **\^PQn** section in the footer to the required number of copies. For example, to print four copies of each label, specify **\^PQ4**.

Your label is now ready to use.

### Create a wave label template

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label templates**.
1. Add a wave level template, and set the following values in the header:

    - **Label template name:** *Container labels*
    - **Description:** *Container labels*
    - **Wave step code:** *PrintLabel*
    - **Warehouse:** *63*

1. On the **Wave label template details** FastTab, add a row that has the following settings:

    - **Label layout ID:** *Container*
    - **Printer name:** Select an appropriate ZPL printer.
    - **Run query:** *Yes* (This setting is optional, but it's recommended for optimal performance.)

1. On the Action Pane, select **Save**.
1. Optional: If you're setting up a customer-specific label design, you must create a query to find the customer's account. On the **Wave label template details** FastTab, select **Edit query**. Then, in the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Account number*
    - **Criteria:** Enter the relevant customer account number.

    When you've finished, select **OK** to close the query editor dialog box.

### Configure number sequence extensions

Number sequence extensions control the GS1 compliance of specific number sequences. This configuration is optional for the current scenario. For more information and configuration instructions, see [Configure number sequence extensions](../warehousing/configure-number-sequence-extensions.md).

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Warehouse:** *63*

1. Add five sales order lines:

    - Sales order line 1:

        - **Item number:** *A0001*
        - **Quantity:** *10*

    - Sales order line 2:

        - **Item number:** *A0002*
        - **Quantity:** *20*

    - Sales order line 3:

        - **Item number:** *L0006*
        - **Quantity:** *20*

    - Sales order line 4:

        - **Item number:** *L0100*
        - **Quantity:** *40*

    - Sales order line 5:

        - **Item number:** *L0101*
        - **Quantity:** *50*

    > [!NOTE]
    > The items and quantities that are provided here are only examples. They must have stock in the specified warehouse.

1. Select sales order line 1. Then, in the **Sales order line** section, on the **Inventory** menu, select **Reservations**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**, and then close the page.
1. Repeat steps 4 and 5 for each additional sales order line.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    The following events occur:

    - The system processes the created shipment using the template that includes the label printing step. The label layout will be used to define the format of the label, and the end result will be a label that has five lines and that is printed on the printer that is selected in the label template.
    - A new bill of lading ID is generated for the shipments. If you configured the number sequence extensions, the wave label IDs will follow the **SSCC-18** number format. 

You can reprint these wave labels by going to **Warehouse management \> Enquiries and reports \> Wave label history**.

## Scenario 3: Wave label printing for multi-tiered labels

This scenario shows how to use the wave label printing functionality when the warehousing processes require several tiers of shipping labels. For example, separate labels might have to be printed for cartons and pallets, and a break label might have to be printed for a whole shipment. Break labels are a separate type of label that can be used as a divider between rolls and containers, such as labels for the shipment ID and a bar code, so that the labels can easily be sorted after they're printed.

The main difference between the configuration of this scenario and the configuration of scenario 1, besides the fact that break labels are enabled, is that multiple wave label types must be associated with wave label templates and unit sequence group lines. To accomplish this configuration, you set up the following elements for this scenario:

- **Wave processing methods:** You'll mark the wave label method as "repeatable," add it two (or more) times to the wave template, and set different wave step codes.
- **Wave label templates:** You'll configure the wave label templates and link them to the wave template. Each wave label template has its own wave label type.
- **Wave label layouts:** You'll create multiple wave label layouts. There will be a separate label layout for each "tier" of labels, and there will also be a break label layout.

This scenario shows the end-to-end flow.

### Make demo data available

To follow this scenario, you must have demo data installed, and you must select the **USMF** legal entity.

### Set up a wave process method

1. Go to **Warehouse management \> Setup \> Waves \> Wave process methods**.
1. Confirm that **waveLabelPrinting** is in the list. If it isn't, select **Regenerate methods** on the Action Pane to add it.
1. For the **waveLabelPrinting** method, select the **Make method repeatable** check box.

### Set up a wave template

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
2. Select a template, such as **62 Shipping Default**.
3. On the **Methods** FastTab, move the **Wave label printing** method to the **Selected methods** column.
4. In the **Selected methods** column, assign a **Wave step code** value, such as *Carton*, to the **Wave label printing** method. For more information about wave step codes, see [Wave step codes](wave-step-codes.md).
5. Move the **Wave label printing** method to the **Selected methods** column a second time.
6. In the **Selected methods** column, assign a different **Wave step code** value, such as *Pallet*, to the second **Wave label printing** method. For more information about wave step codes, see [Wave step codes](wave-step-codes.md).

### Create three wave label layouts

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label layouts**.
1. Create a record that has the following settings:

    - **Label layout ID:** *Carton*
    - **Description:** *Carton (SSCC)*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Wave label row settings**.

    The **Wave label row settings** page appears. Here, you can configure the dynamic part of the label.

1. Add a row that has the following settings:

    - **Row Id:** *WaveLabel*
    - **Row table name:** *WHSWaveLabel*
    - **Row start position:** *0*

        This field defines the vertical position where the row will begin on the label.

    - **Row height:** *0*

        This field defines the height of each row (in points), according to the ZPL standard. The row height is positive for horizontal labels and negative for vertical labels. Because there's just one row in this example, you can set the value to *0* (zero).

    - **Rows per page:** *1*

        This field defines the number of rows that can be printed on each label.

        > [!NOTE]
        > This setup will cause a separate ZPL label to be printed for each record in the wave labels table.

1. Close the page.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work type*
    - **Criteria:** *Pick*

    This query ensures that only pick-type work lines will be printed on the label, not put-type work lines.

1. If you want to be able to print the bill of lading ID, on the **Joins** tab, select the **Work lines** table, and join the **Shipments** table to it. 
1. Close the query editor dialog box.
1. The **Printer text Layout** FastTab has three sections where you can write printer code: **Header section**, **Body section**, and **Footer section**. In the **Header section** section, in the **Label header** field, enter code for the required header. For example, if you're using Zebra printers, you can use the following code.


    ```plaintext
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNW^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI0^XZ
    ^XA
    ^MMT
    ^PW812
    ^LL1218
    ^LS0
    ^FT85,505^A0N,28,28^FH\^FD$WHSShipmentTable.CustomerReq$^FS
    ^FO1,173^GB809,0,1^FS
    ^FO0,391^GB809,0,1^FS
    ^FO3,599^GB809,0,2^FS
    ^FO420,176^GB0,216,1^FS
    ^FO313,3^GB0,169,1^FS
    ^FO0,807^GB809,0,1^FS
    ^FT529,370^A0N,28,26^FH\^FD$WHSShipmentTable.BillOfLadingId$^FS
    ^BY2,3,132^FT25,344^BCN,,N,N
    ^FD>:(420)>38102>63^FS
    ^FT526,315^A0N,28,28^FH\^FD ^FS
    ^FT437,248^A0N,28,28^FH\^FDCARR: $WHSShipmentTable.SCAC$^FS
    ^FT425,201^A0N,23,24^FH\^FDCARRIER:^FS
    ^FT17,68^A0N,20,19^FH\^FDIntershipping, Inc.^FS
    ^FT15,99^A0N,20,19^FH\^FD1000 Shipping Lane^FS
    ^FT16,158^A0N,20,19^FH\^FD ^FS
    ^FT438,368^A0N,28,28^FH\^FDB/L#^FS
    ^FT15,128^A0N,20,19^FH\^FDShelbyville TN 38102^FS
    ^FT19,203^A0N,23,24^FH\^FD(420) SHIP TO POSTAL CODE^FS
    ^FT331,39^A0N,28,28^FH\^FDShip To:^FS
    ^FT14,39^A0N,28,28^FH\^FDShip From:^FS
    ^FT331,67^A0N,23,24^FH\^FDWAL-MART DC 1111A-ABC DIS^FS
    ^FT330,98^A0N,23,24^FH\^FDDEPT 10^FS
    ^FT329,166^A0N,23,24^FH\^FDSpringfield TN 39021^FS
    ^FT330,134^A0N,23,24^FH\^FD100 Main Street^FS
    ^FT19,504^A0N,28,28^FH\^FDPO#:^FS
    ^FT437,316^A0N,28,28^FH\^FDPRO#^FS
    ^FT105,371^A0N,28,28^FB130,1,0,C^FH\^FD(420)39021^FS
    ```

1. In the **Body section** section, in the **Label body** field, enter ZPL code for the required body. Here's an example.

    ```plaintext
    <Row name="WaveLabel">
    ^FT127,439^A0N,28,28^FH\^FD$WHSWaveLabel.SeqNum$^FS
    ^FT256,439^A0N,28,28^FH\^FD$WHSWaveLabel.NumberOfLabels$^FS
    ^FT17,439^A0N,28,28^FH\^FDCARTON^FS
    ^FT522,422^A0N,23,24^FH\^FDVPN:^FS
    ^FT74,1156^A0N,28,28^FH\^FDSSCC-18^FS
    ^FT21,579^A0N,28,28^FH\^FDItem name:^FS
    ^FT107,580^A0N,28,28^FH\^FD$WHSWaveLabel.LabelItemName$^FS
    ^FT576,423^A0N,23,21^FH\^FD$WHSWaveLabel.LabelItemId$^FS
    ^FT252,1155^A0N,32,31^FH\^FD(00)$WHSWaveLabel.WaveLabelId$^FS
    ^BY4,3,283^FT66,1115^BCN,,N,N
    ^FD>;>800$WHSWaveLabel.WaveLabelId$^FS
    ^FT194,439^A0N,28,28^FH\^FDof^FS
    </Row>
    ```

1. In the **Body section** section, in the **Label footer** field, enter ZPL code for the required footer. Here's an example.

    ```plaintext
    ^PQ1^XZ
    ```

    > [!NOTE]
    > This setup will print one copy of each label. If you require more copies (for example, one copy for each side of the pallet), set the **n** value for the **\^PQn** section in the footer to the required number of copies. For example, to print four copies of each label, specify **\^PQ4**.

1. The first label is now ready to use.
1. Create a second layout record that has the following settings:

    - **Label layout ID:** *Pallet*
    - **Description:** *Pallet*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Wave label row settings**.

    The **Wave label row settings** page appears. Here, you can configure the dynamic part of the label.

1. Add a row that has the following settings:

    - **Row Id:** *WaveLabel*
    - **Row table name:** *WHSWaveLabel*
    - **Row start position:** *0*

        This field defines the vertical position where the row will begin on the label.

    - **Row height:** *0*

        This field defines the height of each row (in points), according to the ZPL standard. The row height is positive for horizontal labels and negative for vertical labels. Because there's just one row in this example, you can set the value to *0* (zero).

    - **Rows per page:** *1*

        This field defines the number of rows that can be printed on each label.

        > [!NOTE]
        > This setup causes a separate ZPL label to be printed for each record in the wave labels table.

1. Close the page.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Work type*
    - **Criteria:** *Pick*

    This query ensures that only pick-type work lines will be printed on the label, not put-type work lines.

1. If you want to be able to print the bill of lading ID, on the **Joins** tab, select the **Work lines** table, and join the **Shipments** table to it.
1. Close the query editor dialog box.
1. The **Printer text Layout** FastTab has three sections where you can write printer code: **Header section**, **Body section**, and **Footer section**. In the **Header section** section, in the **Label header** field, enter code for the required header. For example, if you're using Zebra printers, you can use the following code.

    ```plaintext
    CT~~CD,~CC^~CT~
    ^XA
    ^LH10,10
    ^FO0,0 ^AT ^FD$WHSWaveLabel.WaveLabelId$ ^FS
    ^FO0,75 ^AT ^FD$WHSWorkLine.ShipmentId$ ^FS
    ^FO0,150 ^AT ^FD$WHSShipmentTable.BillOfLadingId$ ^FS
    ```

1. In the **Body section** section, in the **Label body** field, enter ZPL code for the required body. Here's an example.

    ```plaintext
    <Row name="WaveLabel">
    ^FO0,450 ^AT ^FDItem ^FS
    ^FO200,450 ^AT ^FDQuantity ^FS
    ^FO0,[[YPos]] ^AT ^FD$WHSWaveLabel.LabelItemId$ ^FS
    ^FO200,[[YPos]] ^AT ^FD$WHSWaveLabel.QtyWork$ ^FS
    </Row>
    ```

1. In the **Body section** section, in the **Label footer** field, enter ZPL code for the required footer. Here's an example.

    ```plaintext
    ^PQ1^XZ
    ```

    > [!NOTE]
    > This setup will print one copy of each label. If you require more copies (for example, one copy for each side of the pallet), set the **n** value for the **\^PQn** section in the footer to the required number of copies. For example, to print four copies of each label, specify **\^PQ4**.

1. The second label is now ready to use.
1. Create a third layout record that has the following settings:

    - **Label layout ID:** *Break*
    - **Description:** *Break label*

1. On the Action Pane, select **Save**.
1. The **Printer text Layout** FastTab has three sections where you can write printer code: **Header section**, **Body section**, and **Footer section**. In the **Header section** section, in the **Label header** field, enter ZPL code for the required header. Here's an example.

    ```plaintext
    CT~~CD,~CC^~CT~
    ^XA
    ^LH10,10
    ^FO0,0 ^AT ^FD$WHSWorkLine.ShipmentId$ ^FS
    ```

1. This time, no body is required. Therefore, just enter the required text in the **Footer section** section. Here's an example.

    ```plaintext
    ^XZ
    ```

    The third label is now ready to use.

    > [!NOTE]
    > This third label is a break label that will be used as a divider between label rolls.

### Create two wave label types

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label types**.
1. Create a record that has the following settings:

    - **Label type:** *Carton*
    - **Description:** *Carton*

1. Create a second record that has the following settings:

    - **Label type:** *Pallet*
    - **Description:** *Pallet*

### Set up unit sequence groups

1. Go to **Warehouse management \> Setup \> Warehouse \> Unit sequence groups**.
1. Select or create an **Ea Box PL** group.
1. For the **Box** line, set the **Wave level type** field to *Carton*.
1. For the **PL** line, set the **Wave level type** field to *Pallet*.

### Create wave label templates

1. Go to **Warehouse management \> Setup \> Document routing \> Wave label templates**.
1. Create a label template that has the following settings:

    - **Label template name:** *Carton labels*
    - **Description:** *Carton labels*
    - **Wave step code:** *Carton*
    - **Warehouse:** *62*

1. On the **General** FastTab, in the **Wave label type** field, select a value, such as *Carton*.
1. On the **Wave label template details** FastTab, add a row that has the following settings:

    - **Label layout ID:** *Carton*
    - **Printer name:** Select an appropriate ZPL printer.
    - **Run query:** *Yes* (This setting is optional, but it's recommended for optimal performance.)

1. On the Action Pane, select **Save**.
1. Optional: If you're setting up a customer-specific label design, you must create a query to find the customer's account. On the **Wave label template details** FastTab, select **Edit query**. Then, in the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Account number*
    - **Criteria:** Enter the relevant customer account number.

    When you've finished, select **OK** to close the query editor dialog box.

1. On the Action Pane, select **Edit query** to open the query editor dialog box for the whole label template.
1. In the query editor dialog box, on the **Sorting** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Reference load line id (Record-ID)*
    - **Search direction:** *Ascending*

1. Add a second row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to close the query editor dialog box.
1. A message box prompts you to confirm the grouping reset operation. Select **Yes** to continue.
1. On the Action Pane, select **Wave label template group**.
1. In the **Wave label template group** dialog box, for the row where the **Reference field name** field is set to *Shipment ID*, set the following values:

    - **Print break label:** Select this check box.
    - **Label layout ID:** Select a break label. (For example, select the *Break* label layout that you created earlier in this scenario.)
    - **Printer name:** Select the printer for the break label. (Typically, when splitting label rolls, you would select the same printer that is selected on the **Wave label template details** FastTab. However, other scenarios are possible.)

1. For the row where the **Reference field name** field is set to *Reference load line id*, select the **Label build ID** check box.

    > [!NOTE]
    > This setup will create one label sequence ("Carton 1 of X") per load line throughout the wave, regardless of the work grouping setup. This label sequence can be printed on a label layout. Additionally, labels for different shipments will be separated by the selected break label.

1. Select **OK** to close the **Wave label template group** dialog box.
1. Create a second label template that has the following settings:

    - **Label template name:** *Pallet labels*
    - **Description:** *Pallet labels*
    - **Wave step code:** *Pallet*
    - **Warehouse:** *62*

1. On the **General** FastTab, in the **Wave label type** field, select a value, such as *Pallet*.
1. On the **Wave label template details** FastTab, add a row that has the following settings:

    - **Label layout ID:** *Pallet*
    - **Printer name:** Select an appropriate ZPL printer.
    - **Run query:** *Yes* (This setting is optional, but it's recommended for optimal performance.)

1. On the Action Pane, select **Save**.
1. Optional: If you're setting up a customer-specific label design, you must create a query to find the customer's account. On the **Wave label template details** FastTab, select **Edit query**. Then, in the query editor dialog box, on the **Range** tab, add a row that has the following settings:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Account number*
    - **Criteria:** Enter the relevant customer account number.

    When you've finished, select **OK** to close the query editor dialog box. 

1. On the Action Pane, select **Edit query** to open the query editor dialog box for the whole label template.
1. In the query editor dialog box, on the **Sorting** tab, add a row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Reference load line id (Record-ID)*
    - **Search direction:** *Ascending*

1. Add a second row that has the following settings:

    - **Table:** *Work lines*
    - **Derived table:** *Work lines*
    - **Field:** *Shipment ID*
    - **Search direction:** *Ascending*

1. Select **OK** to close the query editor dialog box.
1. A message box prompts you to confirm the grouping reset operation. Select **Yes** to continue.
1. On the Action Pane, select **Wave label template group**.
1. In the **Wave label template group** dialog box, for the row where the **Reference field name** field is set to *Shipment ID*, set the following values:

    - **Print break label:** Select this check box.
    - **Label layout ID:** Select a break label. (For example, select the *Break* label layout that you created earlier in this scenario.)
    - **Printer name:** Select the printer for the break label. (Typically, when splitting label rolls, you would select the same printer that is selected on the **Wave label template details** FastTab. However, other scenarios are possible.)

1. For the row where the **Reference field name** field is set to *Reference load line id*, select the **Label build ID** check box.

    > [!NOTE]
    > This setup will create one label sequence ("Carton 1 of X") per load line throughout the wave, regardless of the work grouping setup. This label sequence can be printed on a label layout. Additionally, labels for different shipments will be separated by the selected break label.

### Configure number sequence extensions

Number sequence extensions control the GS1 compliance of specific number sequences. This configuration is optional for the current scenario. For more information and configuration instructions, see [Configure number sequence extensions](../warehousing/configure-number-sequence-extensions.md).

### Create a sales order and release it to the warehouse

1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Warehouse:** *62*

1. Add two sales order lines:

    - Sales order line 1:

        - **Item number:** *A0001*
        - **Quantity:** *9024*
        - **Unit:** *ea* (9024 ea = 376 Box = 47 PL)

    - Sales order line 2:

        - **Item number:** *A0002*
        - **Quantity:** *9016*
        - **Unit:** *ea* (9016 ea = 322 Box = 46 PL)

    > [!NOTE]
    > The items and quantities that are provided here are only examples. They must use the unit sequence group that you defined earlier, appropriate unit conversions from *ea* to *Box* to *PL* must be defined for them, and they must have stock in warehouse *62*. For more information, see [Unit of measure and stocking policies](unit-measure-stocking-policies.md).

1. Select sales order line 1. Then, in the **Sales order line** section, on the **Inventory** menu, select **Reservations**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**, and then close the page.
1. Repeat steps 4 and 5 for sales order line 2.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    The following events occur: 

    - The system processes the created shipment by using the template that includes the label printing step. The label layout will be used to define the format of the label, and the result will be a label that is printed on the printer that is selected in the label template.
    - Wave labels are generated and printed. The number of labels will equal the number of cartons (in this example, 376 Box labels for line 1, 322 Box labels for line 2, 47 PL labels for line 1, 47 PL labels for line 2, and two break labels that have the shipment ID).
    - A new bill of lading ID is generated for the shipments. If you configured the number sequence extensions, the wave label IDs will follow the **SSCC-18** number format. 

You can view and reprint wave labels from the following pages:

- All shipments \> Shipment details
- All loads \> Load details
- All waves
- Wave labels
- Wave label history

For most of these pages, you can find the relevant function by selecting **Wave labels** in the **Related information** group on the **Shipments** tab of the Action Pane.

## Additional resources

- [Reprint and void wave labels](reprint-and-void-wave-labels.md)
- [Schedule wave label printing during wave](configure-task-based-wave-label-printing.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
