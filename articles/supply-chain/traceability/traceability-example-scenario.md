---
title: 
description: 
ms.date: 07/09/2024
ms.topic: how-to
ms.service: 
author: banluo-ms
ms.author: banluo
manager: 
---

# Example scenario: Track products manufactured using Supply Chain Management

## Integrate Traceability with Supply Chain Management

## Set up workers for the production floor execution interface

| Steps | Path | Expectation Results |
|-------------------------|-------------------------|-------------------------|
| Assign PFE (Product Floor Execution) roles | System administration -&gt; Users</br>Assign "Production supervisor" and "Shop supervisor" to shop floor operator user account. |  |
| Enable "Badge ID" for shop floor operator | Time and attendance -&gt; Setup -&gt; Time registration workers</br>Activate on registration terminals with Badge ID, example "admin", assigned. | Shop floor operator can access Production floor execution with badge ID. |


## Set up master data

| Steps | Path | Expectation Results |
|-------------------------|-------------------------|-------------------------|
| Create raw material | Product information management -&gt; Products -&gt; Released products</br>Create raw materials.</br>Item = cmp-01-serial</br>Storage dimension group = SiteWH</br>Tracking dimension group = SerialProd</br>Serial number group = SerialAuto</br>Item price = 10.00</br>Item = cmp-03-batch</br>Storage dimension group = SiteWH</br>Tracking dimension group = Batch-Phy</br>Batch number group = BatchAuto</br>Item price = 10.00 | Raw material cmp-01-serial and cmp-03-batch are created. |
| Create semi-finished goods | Product information management -&gt; Products -&gt; Released products</br>Create semi-finished goods.</br>Item = sfg-02-batch</br>Storage dimension group = SiteWH</br>Tracking dimension group = Batch-Phy</br>Batch number group = BatchAuto</br>Item price = 100.00</br>Production type = Formula | Semi-finished goods sfg-02-batch is created. |
| Create co/by product | Product information management -&gt; Products -&gt; Released products</br>Create co/by product.</br>Item = co-02-batch</br>Storage dimension group = SiteWH</br>Tracking dimension group = Batch-Phy</br>Batch number group = BatchAuto</br>Item price = 10.00</br>Production type = Co-product</br>Item = by-02-batch</br>Storage dimension group = SiteWH</br>Tracking dimension group = Batch-Phy</br>Batch number group = BatchAuto</br>Item price = 0.01</br>Production type = By-product | Co product co-02-batch and by product by-02-batch are created. |
| Create finished goods | Product information management -&gt; Products -&gt; Released products</br>Create finished goods.</br>Item = fg-01-serial</br>Storage dimension group = SiteWH</br>Tracking dimension group = SerialProd</br>Batch number group = SerialAuto</br>Item price = 1500.00</br>Production type = BOM | Finished goods fg-01-serial are created. |
| Create formula for semi-finished goods | Product information management -&gt; Bills of materials and formulas -&gt; Formulas</br>Formula = sfg-02-batch</br>Formula lines = cmp-03-batch/Site = 1/Warehouse = 11/Quantity = 1 ea/Oper. No. = 10</br>Add Co/By product to formula header:</br>Co product = co-02-batch/Site = 1/Warehouse = 11/Quantity = 1 ea</br>By product = by-02-batch/Site = 1/Warehouse = 11/Quantity = 1 ea</br>Approve and activate formula. | Formula of semi-finished goods is created and approved and activated. |
| Create BOM for finished goods | Product information management -&gt; Bills of materials and formulas -&gt; BOM</br>BOM version item number = fg-01-serial/Site = 1</br>BOM line = cmp-01-serial/Site = 1/Warehouse = 11/Quantity = 1 ea/Oper. No. = 10</br>BOM line = sfg-02-batch/Site = 1/Warehouse = 11/Quantity = 1 ea/Oper. No. = 20</br>Approve and activate BOM | New action "Tracked components" can be found in Production Floor Execution UI. |
| Create route for semi-finished goods | Production control -&gt; Operations -&gt; All routes</br>Route version item number = sfg-02-batch</br>Site = 1</br>Route details:</br>Oper. No. = 10/Operation = Assembly/Next = 20</br>Oper. No. = 20/Operation = Packing</br>Approve and activate route. |  |
| Create route for finished goods | Production control -&gt; Operations -&gt; All routes</br>Route version item number = fg-01-serial</br>Site = 1</br>Route details:</br>Oper. No. = 10/Operation = Assembly/Next = 20</br>Oper. No. = 20/Operation = Assembly/Next = 30</br>Oper. No. = 30/Operation = Packing</br>Approve and activate route. |  |

## Process a batch order in the production floor execution interface

| Steps | Path | Expectation Results |
|-------------------------|-------------------------|-------------------------|
| Create purchase order | Accounts payable -&gt; Purchase orders -&gt; All purchase orders</br>Vendor account = 1001</br>Item number = cmp-03-batch</br>Site = 1</br>Warehouse = 11</br>Quantity = 100 ea | Purchase order is created |
| Register purchase order line to generate batch number | Purchase order lines -&gt; Update line -&gt; PROCESS -&gt; Registration | A batch number is created and assigned to the purchased item. |
| Post product receipt | Receive -&gt; Generate -&gt; Product receipt | A product receipt is post with journals created. |
| Wait 5 minutes |  |  |
| Verify product receipt result in Traceability | Traceability -&gt; Genealogy trace</br>Input the batch number of purchased item. | The purchased item is found in Traceability with purchase information collected. |
| Create batch order for semi-finished goods | Production control -&gt; Production orders -&gt; All production orders -&gt; New batch order</br>Item number = sfg-02-batch</br>Site = 1</br>Warehouse = 11</br>Quantity = 10</br>Formula number = sfg-02-batch</br>Route number = &lt;the one of sfg-02-batch&gt; | A batch order is created. |
| Estimate batch order | Production order -&gt; Process -&gt; Estimate | Batch order status is "Estimated". |
| Schedule batch order | Schedule -&gt; Production order -&gt; Schedule jobs</br>Scheduling direction = Forward from today | Batch order status is "Scheduled". |
| Release batch order | Production order -&gt; Process -&gt; Release | Batch order status is "Released". |
| Verify batch number of semi-finished goods and co/by product | Inventory management -&gt; Inquiries and reports -&gt; Tracking dimensions -&gt; Batches | New batch number of semi-finished goods and co/by product can be found. |
| Access Production floor execution | Production control -&gt; Manufacturing execution -&gt; Production floor execution</br>Badge ID = admin</br>Search batch order. | The batch order can be found with 2 operation lines. |
| Start Operation 10 of batch order | Pick Operation 10</br>Click "Start job"</br>Quantity = 10</br>Click "Start" | There is active job under "Active jobs" tag. |
| Associate raw material consumption to semi-finished goods | Pick active job</br>Click "Tracked component" (or "Link")</br>Select semi-finished goods line</br>Scan/input the batch number of sfg-02-batch</br>Select component line</br>Scan/input the batch number of cmp-03-batch</br>Select co-product line</br>Scan/input the batch number of co-02-batch</br>Select component line</br>Scan/input the batch number of cmp-03-batch</br>Select by-product line</br>Scan/input the batch number of by-02-batch</br>Select component line</br>Scan/input the batch number of cmp-03-batch</br>Click "OK" |  |
| Report progress of Operation 10 | Pick active job</br>Click "Report progress"</br>Good quality quantity = 10 ea</br>Job status = complete | The picking list is posted and integrated to Traceability. |
| Wait 5 minutes |  |  |
| Verify product consumption in Traceability | Traceability -&gt; Genealogy trace</br>Input the batch number of sfg-02-batch. | Semi-finished goods have cmp-03-batch as component.</br>Product picking list can be found under "Activities" tag of semi-finished goods. |
| Start Operation 20 of batch order | Pick Operation 20</br>Click "Start job"</br>Quantity = 10</br>Click "Start" | There is active job under "Active jobs" tag. |
| Report progress of Operation 20 | Pick active job</br>Click "Report progress"</br>Select all lines and click "Report progress"</br>Select by-02-batch</br>Select batch ID</br>Good quantity = 10 ea</br>Click "Next"</br>Select co-02-batch</br>Select batch ID</br>Good quantity = 10 ea</br>Click "Next"</br>Select sfg-02-batch</br>Select batch ID</br>Good quantity = 10 ea</br>Click "Next"</br>Change job status = Complete</br>Click "Report progress" | ProductionReportFinished transactions are integrated to Traceability. |
| Wait 5 minutes |  |  |
| Verify product consumption in Traceability | Traceability -&gt; Genealogy trace</br>Input the batch number of sfg-02-batch, co-02-batch, and by-02-batch. | ProductionReportFinished activity is inserted for sfg-02-batch, co-02-batch, and by-02-batch. |


## Execute production order in web client

| Steps | Path | Expectation Results |
|-------------------------|-------------------------|-------------------------|
| Create purchase order | Accounts payable -&gt; Purchase orders -&gt; All purchase orders</br>Vendor account = 1001</br>Item number = cmp-01-serial</br>Site = 1</br>Warehouse = 11</br>Quantity = 5 ea | Purchase order is created |
| Register purchase order line to generate batch number | Purchase order lines -&gt; Update line -&gt; PROCESS -&gt; Registration | 5 serial numbers are created and assigned to the purchased item. |
| Post product receipt | Receive -&gt; Generate -&gt; Product receipt | A product receipt is post with journals created. |
| Wait 5 minutes |  |  |
| Verify product receipt result in Traceability | Traceability -&gt; Genealogy trace</br>Input a serial number of purchased item. | The purchased item is found in Traceability with purchase information collected. |
| Create production order for semi-finished goods | Production control -&gt; Production orders -&gt; All production orders -&gt; New production order</br>Item number = fg-01-serial</br>Site = 1</br>Warehouse = 11</br>Quantity = 3</br>BOM number = &lt;the one of fg-01-serial&gt;</br>Route number = &lt;the one of sfg-02-batch&gt; | A production order is created. |
| Estimate production order | Production order -&gt; Process -&gt; Estimate | Production order status is "Estimated". |
| Schedule batch order | Schedule -&gt; Production order -&gt; Schedule jobs</br>Scheduling direction = Forward from today | Production order status is "Scheduled". |
| Release batch order | Production order -&gt; Process -&gt; Release | Production order is released with default parameters. |
| Verify serial number of finished good | Inventory management -&gt; Inquiries and reports -&gt; Tracking dimensions -&gt; Serial numbers | New serial number of finished goods can be found. |
| Access web client of Current operation | Production control -&gt; Operations -&gt; Current operation</br>Search the production order. | The production order can be found with 3 operation lines. |
| Start Operation 10 of production order | Pick Operation 10</br>Click Process -&gt; Start</br>Quantity = 3</br>Automatic route consumption = Route group dependent</br>Post route card now = No</br>Automatic BOM consumption = Never</br>Post picking list now = No | In Journals -&gt; Route card, a route card is created. |
| Associate raw material consumption to finished goods | Click route card journal</br>Click "Tracked components" button</br>Scan/input the serial number of fg-01-serial</br>Click "Submit"</br>Scan/input a serial number of cmp-01-serial</br>Click "Submit" | Click "View associations"</br>The raw material cmp-01-serial with serial number is linked to the serial number of fg-01-serial. |
| Post route card journal of Operation 10 | Check "BOM consumption" of route card.</br>Validate the route card from the menu bar.</br>Post the route card from the menu bar. | The picking list is posted and integrated to Traceability. |
| Wait 5 minutes |  |  |
| Verify product consumption in Traceability | Traceability -&gt; Genealogy trace</br>Input the serial number of fg-01-serial | Finished goods have cmp-01-serial as component.</br>Product picking list can be found under "Activities" tag of finished goods. |
| Start Operation 20 of production order | Pick Operation 20</br>Click Process -&gt; Start</br>Quantity = 3</br>Automatic route consumption = Route group dependent</br>Post route card now = No</br>Automatic BOM consumption = Never</br>Post picking list now = No | In Journals -&gt; Route card, a route card is created. |
| Associate raw material consumption to finished goods | Click route card journal</br>Click "Tracked components" button</br>Scan/input the serial number of fg-01-serial</br>Click "Submit"</br>Scan/input a batch number of sfg-02-batch</br>Click "Submit" | Click "View associations"</br>The semi-finished goods sfg-02-batch with batch number is linked to the serial number of fg-01-serial. |
| Post route card journal of Operation 20 | Check "BOM consumption" of route card.</br>Validate the route card from the menu bar.</br>Post the route card from the bar. | The picking list is posted and integrated to Traceability. |
| Wait 5 minutes |  |  |
| Verify product consumption in Traceability | Traceability -&gt; Genealogy trace</br>Input the serial number of fg-01-serial | Finished goods have sfg-02-batch as component.</br>Product picking list can be found under "Activities" tag of finished goods. |
| Start Operation 30 of production order | Pick Operation 30</br>Click Process -&gt; Start</br>Quantity = 3</br>Automatic route consumption = Route group dependent</br>Post route card now = No</br>Automatic BOM consumption = Never</br>Post picking list now = No | In Journals -&gt; Route card, a route card is created. |
| Associate raw material consumption to finished goods | Click route card journal</br>Click "Tracked components" button</br>Scan/input the serial number of fg-01-serial</br>Click "Submit" | Click "View associations"</br>The serial number of fg-01-serial can be found. |
| Post route card journal of Operation 30 | Check "BOM consumption", "Operation completed", "Production report as finished" of rout card.</br>Validate the route card from the menu bar.</br>Post the route card from the menu bar. | Report as finished journal is post and integrated to Traceability. |
| Wait 5 minutes |  |  |
| Verify product consumption in Traceability | Traceability -&gt; Genealogy trace</br>Input the serial number of fg-01-serial | ProductionReportFinished can be found under "Activities" tag of finished goods. |


#### Test result example

Activities of SFC-02-BATCH, Batch No. = 000063

![A screenshot of a computer Description automatically generated](media/image27.png)

Genealogy tree of FG-01-SERIAL, Serial No. = 000009

![A screenshot of a computer Description automatically generated](media/image28.png)

Activities of FG-01-SERIAL, Serial No. = 000009

![A screenshot of a computer Description automatically generated](media/image29.png)

