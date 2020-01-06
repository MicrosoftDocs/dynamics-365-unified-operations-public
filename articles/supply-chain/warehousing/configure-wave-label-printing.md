---

# required metadata

title: Configure wave label printing
description: This topic provides an overview of functionality that provides wave label printing.
author: GarmMSFT
manager: PJacobse
ms.date: 12/31/2019
ms.topic: configure-wave-label-printing
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSWaveLabel, WHSWaveLabelTemplate
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: PJacobse
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: v-olbara
ms.search.validFrom: yyyy-mm-dd
ms.dyn365.ops.version: 10.0.0

---

# Configure wave label printing

[!include [banner](../includes/banner.md)]

# Released in version 10.0.0, upgraded in version 10.0.2

# About

This functionality offers alternative approach to label printing in Microsoft Dynamics D365 by introducing new wave step method. The new method enables creating and printing of the labels directly from the wave template during wave execution process. Therefore, the labels will be available before the work order is executed on the mobile device. This handles scenarios where different approach to label handling is desirable, enabling the worker to use and attach the required labels during picking and not only after picking.

The feature introduces new Label layout form where ZPL label layouts are created to be used for every label that is printed via the new functionality. The new label layout is broken into three sections, header, body, and footer, to allow labels with repeating structure to be printed. Label templates, which tell the system what label layout to use, is the second form introduced. Here, the user can also specify which printer to print the label at, or if needed, to print labels at multiple printers at once. To further extend the overview of printed labels, Label history form is introduced where records of all labels created via this setup are shown.

With this setup you can print and collate labels based on work headers, print break labels per work header, container content labels, case labels, and other similar labels.

NOTE: This functionality does not replace existing label printing functionality via Document routing.

This functionality has been enhanced in 10.0.2 release with the following functionalities:
- Allow for labels to be printed according to a number of cartons on a single work line – without using containerization feature (“carton” meaning designated unit from Unit sequence group lines); use of multiple different label sequences (for example, carton and pallet labels) is covered by “repeatable” check box.
- Include an enumeration of the labels (1/124, 2/124…124/124) and configuration of how to define the range of enumeration (work line, load line, shipment, etc.)
- Allow for BOL (Bill of lading) ID to be created and printed on label
- Allow unique SSCC (Serial Shipping Container Code) to be created per carton and included on label
- Allow for creation of GS1 compliant number sequence for BOL and SSCC numbers
- Allow for HAZMAT code to be include if relevant on label
- Support for reprint of labels (from handhelds and from rich client)
- Support for voiding of labels (a.o. for short pick scenarios) and reprint
- Support for clean-up of wave label history

These amendments will make it more efficient to support labelling of cartons prior palletizing. It especially supports companies shipping to large retailers that perform order receipt confirmation on an automatic fashion using scanning of each individual carton.

# Example scenario

For this scenario, you must have demo data installed, and you must use the **USMF** demo data company.

## Setup

### Wave process methods

You may need to regenerate the wave process methods for the wave label printing method to become available.

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave process methods** and check if **waveLabelPrinting** is present in the list.
2. If it isn&#39;t, click on **Regenerate methods** in the action bar to add it.

### Wave templates

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave templates**.
2. Select a template, such as **62 Shipping Default**.
3. In the **Methods** FastTab, add the **Wave label printing** method to the **Selected methods**.
4. Assign a wave step code to the method, such as **Printlabel**.

### Wave label layout

The label layout control what information is printed on the label, and how it is laid out. Here is where you write the ZPL code that is sent to the printer.

1. Go to **Warehouse management** \> **Setup** \> **Document routing** \> **Wave Label Layout**.
2. Create a new record.
  - **Label layout ID**: **Carton**
  - **Description**: **Carton (SSCC)**
3. Save the **Carton** record.
4. Click on **Row Settings** in the ribbon. Row settings allow you to configure the dynamic part of the label.
5. Create a new row:
  - **Row Id**: **WaveLabel**
  - **Row table**: **WHSWaveLabel**
  - **Row start position** – Where the row will begin on the label (vertically): **0**
  - **Row height** – The height of each row: **0**. The row height is positive if the label is horizontal, negative if vertical
  - **Rows per page** – How many rows can be printed on one label: **1**<br>
  > [!NOTE]
  > The above setup results in 1 separate ZPL label to be printed per record in Wave labels table.
6. Click on **Edit query** in the ribbon, and in the range section, add a record for **Work lines** with criterion **Pick** set on **Work type** field. This is so that only the Pick-type work lines are printed on the label, and not the put.
7. You need to add the **Shipments** table to the query to be able to print out **Bill of lading ID**. Join it to the **Work lines** table.
8. In the **ZPL Layout** FastTab, there are three sections in which you can write ZPL: Header, Body, and Footer.
  - Put the required text in the **Header**, such as the following:
```text
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
^FD>:(420)>53153>63^FS
^FT526,315^A0N,28,28^FH\^FD ^FS
^FT437,248^A0N,28,28^FH\^FDCARR: $WHSShipmentTable.SCAC$^FS
^FT425,201^A0N,23,24^FH\^FDCARRIER:^FS
^FT17,68^A0N,20,19^FH\^FDCRC INDUSTRIES, INC.^FS
^FT15,99^A0N,20,19^FH\^FD83 RAILROAD DRIVE^FS
^FT16,158^A0N,20,19^FH\^FD ^FS
^FT438,368^A0N,28,28^FH\^FDB/L#^FS
^FT15,128^A0N,20,19^FH\^FDIVYLAND PA 18974^FS
^FT19,203^A0N,23,24^FH\^FD(420) SHIP TO POSTAL CODE^FS
^FT331,39^A0N,28,28^FH\^FDShip To:^FS
^FT14,39^A0N,28,28^FH\^FDShip From:^FS
^FT331,67^A0N,23,24^FH\^FDWAL-MART DC 6010A-ASM DIS^FS
^FT330,98^A0N,23,24^FH\^FDDEPT 10^FS
^FT329,166^A0N,23,24^FH\^FDDOUGLAS GA 31533^FS
^FT330,134^A0N,23,24^FH\^FD690 HWY 206^FS
^FT19,504^A0N,28,28^FH\^FDPO#:^FS
^FT437,316^A0N,28,28^FH\^FDPRO#^FS
^FT105,371^A0N,28,28^FB130,1,0,C^FH\^FD(420)31533^FS
```
  - Put the required text in the **Body**, such as the following:
```text
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
  - Put the required text in the **Footer**, such as the following:
```text
^PQ1^XZ
```
  This ends the label.
  > [!NOTE]
  > The above setup results in 1 copy for each ZPL label to be printed. If more copies are needed (for example, to put on each side of the pallet), change the **n** value in **^PQn** section, such as **^PQ4**.

### Wave label types

1. Go to **Warehouse management** \> **Setup** \> **Document routing** \> **Wave label types**.
2. Create a new record:
  - **Label type**: **Carton**
  - **Description**: **Carton**

### Unit sequence groups

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Unit Sequence Groups**.
2. Select or create a **Ea Box PL** group.
3. Set the **Carton** wave label type to the **Box** line.

### Wave label templates

1. Go to **Warehouse management** \> **Setup** \> **Document routing** \> **Wave label templates**
2. Create a new record:
  - **Label template name**: **Carton labels**
  - **Description**: **Carton labels**
  - **Wave step code**: **PrintLabel**
  - **Warehouse**: **62**
3. In the **General** FastTab of the label template, select a **Wave label type**, such as **Carton**.
4. In the **Details** FastTab of the label template, add a new record:
  - **Label layout Id**: **Carton**
  - **Printer name**: Whatever ZPL printer you have setup.
  - **Run query**: **Yes** (optional)
  - Click on **Edit query** in **Details** and add a filter on table **Shipments**, field **Account number** (optional)
    > [!NOTE]
    > If we are setting up a customer-specific label design, it is necessary to create a query for that account specifically.
5. Click on **Edit Query** in the Ribbon (for the entire record), and in the **Sorting** tab, add sorting on **Load line ref rec ID (Reference load line id (Record-ID))**. Click **OK** and Yes on Grouping reset suggestion.
6. Click on **Wave label template grouping**, and enable the **Label build** parameter next to the **Load line ref rec ID** field.
  > [!NOTE]
  > This will create one label sequence (“Carton 1 of X” as can be printed on a label layout) per Load line that is created through the wave regardless of work grouping setup.

### Number sequence extensions

Number sequence extension controls GS1 compliance of specific number sequences (optional for the current scenario; more details and configuration instruction can be found here: [Configure number sequence extensions](../warehousing/configure-number-sequence-extensions.md)).

## Process

1. Go to **Sales and marketing** \> **Common** \> **Sales order** \> **All sales orders**.
2. Create a new sales order.
3. Select a customer account, such as **US-001**, and a warehouse, such as **62**.
4. Add two lines to the sales order:
  - One for an item, such as **A0001**, enter quantity, such as **9024**,
  - One for another item, such as **A0002**, enter quantity, such as **9016**
  > [!NOTE]
  > Items and quantities are provided as an example only, they must have the **Unit sequence group** defined above, have unit conversions defined from **ea** to **Box** to **PL**, and have stock in Warehouse **62**).
3. Reserve the order and release it to the warehouse.
  - The system will process the created shipment through the wave, using the template that includes the label printing step. The label layout will be used to define the format of the label, and the end result will be a label printed at the printer setup in the label template.
  - Wave labels will be generated and printed in the amount equal to the number of cartons.
  - The new **Bill of lading ID** will be generated for the shipments, and the wave label IDs will be following **SSCC-18** number format if the number sequence extensions have been configured.

Wave labels can be viewed and re-printed from the following forms (**Related information** field group in the ribbon):

-	**All shipments/Shipment details**
-	All loads/Load details
-	All waves
-	Wave labels
-	Wave label history
