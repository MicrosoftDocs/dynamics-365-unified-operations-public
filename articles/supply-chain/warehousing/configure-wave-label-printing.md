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

# Setup

## Wave process methods

You may need to regenerate the wave process methods for the wave label printing method to become available. Navigate to _Warehouse management - Setup - Waves -  Wave process methods_ and check if waveLabelPrinting is present in the list. If it isn&#39;t, click on &#39;Regenerate methods&#39; in the action bar to add it.

## Wave templates

Navigate to _Warehouse management - Setup -  Waves - Wave templates._ Select the template &#39;62 Shipping Default&#39;. In the Methods FastTab, add the Wave label printing method to the Selected Methods. Assign the &#39;Printlabel&#39; wave step code to the method.

## Wave label layout

The label layout control what information is printed on the label, and how it is laid out. Here is where you write the ZPL code that is sent to the printer.

Navigate to _Warehouse Management - Setup - Document routing - Wave Label Layout_. Create a new record.

- Label Layout ID: Carton
- Description: Carton (SSCC)

Save the Carton record and click on ‘Row Settings’ in the Ribbon. Click on ‘Row Settings’ in the Ribbon. Row settings allow you to configure the dynamic part of the label. Create a new row:

- Row Id: WaveLabel
- Row Table: WHSWaveLabel
- Row start position – Where the row will begin on the label (vertically): 0
- Row Height – The height of each row: 0. The row height is positive if the label is horizontal, negative if vertical
- Rows Per Page – How many rows can be printed on one label: 1

The above setup results in 1 separate ZPL label to be printed per record in Wave labels table.

Click on Edit Query in the ribbon, and in the range section, add a record for Work lines – Work type = Pick. This is so that only the Pick-type work lines are printed on the label, and not the put.

You need to add the Shipments table to the query to be able to print out Bill of lading ID. Join it to the table Work lines.

In the ZPL Layout FastTab there are three sections in which you can write ZPL: Header, Body, and Footer.

Put the following text in the header:

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

In the body, put:

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

In the footer put:

```text
^PQ1^XZ
```

This ends the label.

## Wave label types

Navigate to _Warehouse Management - Setup - Document Routing - Wave Label Types_ and create a new record.

- Label type: Carton
- Description: Carton

## Unit sequence groups

Navigate to _Warehouse Management - Setup - Warehouse - Unit Sequence Groups_.

- Select or create ‘Ea Box PL’ group.
- Set the ‘Carton’ wave label type to Box line.

## Wave label templates

Navigate to _Warehouse Management - Setup - Document Routing - Wave Label Templates_ and create a new record.

- Label Template Name: Carton labels
- Description: Carton labels
- Wave step code: PrintLabel
- Warehouse: 62

In the Label Template General FastTab, select a Wave label type:

- Wave label type: Carton

In the Label Template Details FastTab, add a new record:

- Label Layout Id: Carton
- Printer name: Whatever ZPL printer you have setup.
- Run query: Yes (optional)
- Click on Edit query and add a filter on Shipment -> Account number (optional)

As we are setting up a customer-specific label design, it should be necessary to create a query for that account specifically.

Click on **Edit Query** in the Ribbon, and in the sorting tab, add sorting on Load line ref rec ID (Reference load line id (Record-ID). Click OK and Yes on Grouping reset suggestion.

Click on Wave Label Template Grouping, and check the box to Label build by Load line ref rec ID. This will create one label sequence (“Carton 1 of X” on a label layout) per Load line that is created through the wave.

## Number sequence extensions

Number sequence extension controls GS1 compliance of specific number sequences:

- A new column was added to the “Number sequences” Tab in Warehouse management parameters where you can select the extension. Out of the box it is available only for the following references:
- License plate ID
- Wave label ID
- Container ID
- Bill of lading ID
- GS1 prefix is not a constant but always comes from the Parameters. So, updating this setup will impact all number sequences using extensions with it included
- License plate ID rules will remain As Is if no extension is configured, and overridden with new rules if some extension is configured there
- Extension segments description:
- GS1 prefix: GS1 prefix in Warehouse management parameters
- Application identifier: 00 for SSCC, for example, 420 for BOL, numeric value
- New number for the Number sequence specified
- Packing type: field from Unit sequence group lines or 0 as default (current LP logic)
- Check digit: Modulo 10 calculation

Navigate to _Warehouse Management - Setup - Warehouse Management Parameters_ and enter a value in GS1 company prefix (your company’s GS1-prefix).

Navigate to _Warehouse Management - Setup - Warehouse Management Parameters - Reports_ and activate checkbox “Generate Bill of lading number when printing wave labels”.

Navigate to _Warehouse Management - Setup - Number Sequence Extensions_ and click “Create default setup”. It covers 3 variants of SSCC number generation and 1 variant of GS1-compliant BOL number sequence. You can also create the following setups manually:

Create a new record.

- Number sequence extension: SSCC-18
- Description: SSCC without application identifier

In the Segments FastTab, add new segments:

-	Packing type
- GS1 prefix
- Number sequence (make sure the length is 16 minus GS1 prefix length)
- Check digit

Create a new record:

- Number sequence extension: BOL
- Description: Bill of lading ID

In the Segments FastTab, add new segments:

-	GS1 prefix
-	Number sequence (make sure the length is 16 minus GS1 prefix length)
-	Check digit

Navigate to _Warehouse Management - Setup - Warehouse Management Parameters - Number Sequences_ and select extension ID on Wave label ID (SSCC-18) and Bill of lading ID (BOL).

# Process

1. Navigate to _Sales and Marketing_ _-_ _Common - Sales order - All sales orders_ and create a new sales order. Select customer US-001 and warehouse 62.

2. Add two lines to the sales order, one for item A0001, quantity 9024, and one for item A0002, quantity 9016 (items are given as example, they must have the Unit sequence group defined above, have unit conversions from ea to Box to PL, and have stock in Warehouse 62).

3. Reserve the order and release it to the warehouse.

- The system will process the created shipment through the wave, using the template that includes the label printing step. The label layout will be used to define the format of the label, and the end result will be a label printed at the printer setup in the label template.

- Wave labels will be generated and printed in the amount equal to the number of cartons.

- The new Bill of lading ID will be generated for the shipments, and the wave label IDs will be following SSCC-18 number format from GS-1.

Labels can be viewed and re-printed from the following forms (Related information section):

-	All shipments/shipment details
-	All loads/load details
-	All waves
-	Wave labels
-	Wave label history
