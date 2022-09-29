---
title: Test location directives with acceptance tests
description: This article explains how to set up and run automated tests that verify whether your location directive setup is working as expected and help you troubleshoot if it isn't.
author: MichaelFruergaardPontoppidan
ms.author: mfp 
ms.reviewer: kmaybac
ms.search.form: WHSLocDirTable, WHSLocationDirectiveAcceptanceTest
ms.service: dynamics-365
ms.topic: how-to
ms.date: 09/29/2022
ms.custom: bap-template
---

# Test location directives with acceptance tests

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.31 GA -->

Acceptance tests enable you to define a set of *given-when-then* tests to verify the location directives behaves as expected (*given* a set of conditions, *when* something happens, *then* the following should happen). This is terminology known from quality assurance in engineering, and can be traced back to the [scientific method](https://en.wikipedia.org/wiki/Scientific_method).

Acceptance tests provide two main benefits:

- **Faster initial setup**: You can verify the outcomes of your location directives without having to go through the regular warehouse processes and inspect the work creation history log.
- **Lower maintenance**: Going forward, you'll be able to modify your location directives with higher confidence because the impact of each change can automatically be verified by running your defined acceptance tests.

Acceptance tests for location directives have no operational impact on the warehouse.

> [!NOTE]
> It isn't possible to create acceptance tests for location directives with **Scope** set to *Multiple items* (or with **Multiple items** set to *Yes*). We recommend using location directive scopes that can be tested with single items whenever possible, such as *Single item or order* and *All*.

For more information about how to set up location directives, including how to use location directive scopes, see [Work with location directives](create-location-directive.md).

## Set up an acceptance test

Follow these steps to set up an acceptance test:

1. Go to **Warehouse management \> Setup \> Location directives**.
1. On the Action Pane, select **Acceptance tests**.
1. The **Location directive acceptance tests** page opens. Do one of the following:
    - To create a new test, select **New** on the Action Pane.
    - To edit an existing text, select it on the list pane and then select **Edit** on the Action Pane.
    - To copy an existing test, select the source test on the list pane and then select **Copy** on the Action Pane. This can be handy for when you need to create a new test that is a variation of an existing acceptance test.

1. Make the following settings in the header of your new or selected test:
    - **Name** – Enter a name for the test.
    - **Description** – Enter a short description for the test.
    - **Inactive** – Set to *Yes* to make the test inactive. Set to*No* to make it active. Inactive tests can't be run and will be skipped if you choose to run all tests.

1. Expand the **Given** FastTab. This is where you specify the starting conditions for the test. Make the following settings:
    - **Inventory levels** – Choose whether to run the test based on your actual inventory or to simulate empty inventory. Select one of the following values:
        - *Current on-hand inventory* – Run the test using whatever inventory is available at the time the test is run. This can make the test result less predictable and subject to arbitrary failures, for example when the item used by the test is not available.
        - *No inventory* – Simulate an empty warehouse. The simulation will clear inventory of the item used in the test, and for all locations specified under **Additional inventory**.
    - **Additional inventory** – Simulate on-hand quantities for one or more items. The test will add these quantities to the inventory selected for the **Inventory levels** field.
        - Select **New** on the toolbar to add a row to the grid.
        - Select **Delete** on the toolbar to remove a row from the grid.
        - Select **Display dimensions** to open a dialog where you can add or remove dimension columns in the grid as needed.
        - For each row, enter values to specify an item, dimension values, location, and quantity.

    > [!IMPORTANT]
    > The settings on the **Given** FastTab won't influence the actual inventory levels in the warehouse. Rather they will simulate conditions that are only in effect temporarily during the test execution.

1. Expand the **When** FastTab. This is where you specify what you want to test. These are the inputs to the location directive engine. This is much simpler than building manual tests by creating orders. Make the following settings:
    - **Work order type** – Specify the type of order to simulate, for example *Sales orders* or*Purchase orders*.
    - **Work type** – Specify the work type to simulate, typically *Pick* or*Put*.
    - **Disposition code** – Specify the disposition code used for handling return orders.
    - **Directive code** – Specify the directive code to drive the location directives.
    - **Item number** – Specify the item to locate.
    - **Quantity** – Specify the quantity to locate.
    - **Unit** – Specify the unit of measure for the **Quantity**.
    - **Dimensions** – Specify the storage, product, and tracking dimensions for the item to locate.

1. Expand the **When** FastTab. This is where you specify the expected outcome of the acceptance test. You *must* specify one (and only one) of the following settings:
    - **Exact location** – Select a precise location. The test will pass if the location directive results in this location.
    - **Location matching regular expression** – Enter a regular expression that will be validated against the resulting location (including if the resulting location is blank (no result)). The test will be marked as passed if the regular expression matches the name of the resulting location. For more information about regular expressions, see [.NET regular expressions](https://aka.ms/regex).
    - **Location with profile** – Select a location profile. The test will be marked as passed if the resulting location has this profile.

1. Select **Save** to save your test. (The **Results** FastTab stores a record of test results for each test (if any). See the next section for details about how to run tests and interpret these results.)

## Run acceptance tests

Once you have set up your tests, you can run them, either one-by-one or all at once. To run one or more tests, follow these steps:

1. Go to **Warehouse management \> Setup \> Location directives**.
1. On the Action Pane, select **Acceptance tests**.
1. The **Location directive acceptance tests** page opens. Do one of the following:
    - To run a single, specific test, select the test on the list pane and then select **Run** on the Action Pane.
    - To run all active tests, select **Run all** on the Action Pane.

1. After all tests have run, the list pane updates to indicate the most recent result of each test. To inspect the results of a test, select the test on the list pane and then expand the **Results** FastTab. The grid here shows the result each time the test was run, with each result providing the following information:
    - **Result** – The result of the test. Can be *Passed*, *Failed* or*Skipped*.
    - **Resulting location** – The location found by the test (or blank if no location was found).
    - **Duration (ms)** – The duration of the test. This also indicates how quickly the system will be able to process your directives during daily operation. For efficient warehouse operations, you should design your location directives so they can be processed as quickly as possible. One typical cause for a slow response is using location directive queries defined with ranges or sort orders that don't match an index on the table (the system will warn you if you try to save a query that does this).
    - **Locations evaluated** – The number of locations evaluated during the test. For efficient warehouse operations, aim for as few locations being evaluated as possible. One way to minimize the number of evaluated locations is to have many location directives, where the first ones are very specific and the most general ones come last. You could also segment your warehouse by keeping certain types of items in dedicated zones, which can help avoid scanning the entire warehouse every time.
    - **Created date and time** – The date and time when the test was run.
    - **Created by** – The name of the person that ran the test.

1. To get more information about any test run, select it in the grid and then inspect the **Log** field. The log includes a work creation history that will help you to understand the outcome.

    > [!IMPORTANT]
    > The result of the test is determined by comparing the **Resulting location** with the **Then** condition. The log for a failing test may indicate that a location directive did find a location, but that location didn't match the expected location established by the **Then** condition.

## Troubleshoot location directives and acceptance tests

Defining acceptance tests is typically an iterative process. If a test fails, you should find out why. Perhaps the test isn't set up correctly, or perhaps a location directive needs to be adjusted to better meet your requirements.

To troubleshoot your location directives and acceptance tests, follow these steps:

1. Go to **Warehouse management \> Setup \> Location directives**.
1. On the list pane, select a location directive for which you have designed an acceptance test.
1. Expand the FactBox pane, which is on the right side of the page and is labeled **Related information**.
1. On the FactBox pane, expand the **Acceptance tests** FactBox, which shows a grid that lists the acceptance tests that are relevant for the selected location directive and the most recent result for each of them. From here, you can do the following:
    - Select **Run all** to run all the listed tests.
    - Select **Coverage** to toggle the coverage view. When enabled, the coverage view uses colored highlighting to indicate which location directives, lines and actions were used in determining the result of a selected test. Records marked yellow were evaluated but didn't find a location. Records marked green did find a location. You can change which test to show coverage for by selecting the icon in the **Result** column for the relevant test.
    - Hover over a test to see more information about it (including the log).
    - Select a name in the **Name** column to open that test on the **Location directive acceptance tests** page, where you can inspect and adjust it as needed.
    - Select **Run tests after change** to toggle the setting that will run all tests automatically each time you change a location directive. Use this to provide immediate feedback on the impact of changes as you make them.

1. Based on the results indicated by the coverage view and test log, adjust your tests and/or location directives until they produce the expected results for each test.
