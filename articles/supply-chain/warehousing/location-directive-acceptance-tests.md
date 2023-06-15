---
title: Test location directives with acceptance tests
description: This article explains how to set up and run automated tests that validate whether your location directive setup is working as expected and help you troubleshoot if it isn't.
author: MichaelFruergaardPontoppidan
ms.author: mfp 
ms.reviewer: kmaybac
ms.search.form: WHSLocDirTable, WHSLocationDirectiveAcceptanceTest
ms.topic: how-to
ms.date: 09/29/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Test location directives with acceptance tests

[!include [banner](../includes/banner.md)]

Acceptance tests let you define a set of *given-when-then* tests to verify that location directives behave as expected. In this type of test, *given* a set of conditions, *when* something happens, *then* some specified result should occur. This terminology is known from quality assurance in engineering and can be traced back to the [scientific method](https://en.wikipedia.org/wiki/Scientific_method).

Acceptance tests provide two main benefits:

- **Faster initial setup:** You can verify the outcomes of your location directives without having to go through the regular warehouse processes and inspect the work creation history log.
- **Lower maintenance:** You'll be able to have more confidence when you modify your location directives later, because you can have the impact of each change automatically validated by running your defined acceptance tests.

Acceptance tests for location directives have no operational impact on the warehouse.

> [!NOTE]
> You can't create acceptance tests for location directives where the **Scope** option is set to *Multiple items* (or the **Multiple items** option is set to *Yes*). We recommend that, whenever possible, you use location directive scopes that can be tested with single items, such as *Single item or order* and *All*.

For more information about how to set up location directives, including how to use location directive scopes, see [Work with location directives](create-location-directive.md).

## Set up an acceptance test

Follow these steps to set up an acceptance test.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. On the Action Pane, select **Acceptance tests**.
1. On the **Location directive acceptance tests** page, follow one of these steps:

    - To create a new test, select **New** on the Action Pane.
    - To edit an existing test, select it in the list pane, and then select **Edit** on the Action Pane.
    - To copy an existing test, select the source test in the list pane, and then select **Copy** on the Action Pane. This step can be useful when you must create a new acceptance test that is a variation of an existing test.

1. On the header of the new or selected test, set the following fields:

    - **Name** – Enter a name for the test.
    - **Description** – Enter a short description of the test.
    - **Inactive** – Set this option to *Yes* to make the test inactive. Set it to *No* to make the test active. Inactive tests can't be run and will be skipped if you choose to run all tests.

1. On the **Given** FastTab, specify the starting conditions for the test. Set the following fields:

    - **Inventory levels** – Specify whether you want to run the test based on your actual inventory or simulate empty inventory. Select one of the following values:

        - *Current on-hand inventory* – Run the test by using whatever inventory is available when the test is run. This approach can make the test result less predictable and subject to arbitrary failures (for example, if the item that is used by the test isn't available).
        - *No inventory* – Simulate an empty warehouse. The simulation will clear inventory of the item that is used in the test, and for all locations that are specified under **Additional inventory**.

    - **Additional inventory** – Simulate on-hand quantities for one or more items. The test will add these quantities to the inventory that is specified by the **Inventory levels** field.

        - Select **New** on the toolbar to add a row to the grid.
        - Select **Delete** on the toolbar to remove a row from the grid.
        - Select **Display dimensions** to open a dialog box where you can add dimension columns to the grid, or remove them, as you require.
        - For each row, enter values to specify an item, dimension values, location, and quantity.

    > [!IMPORTANT]
    > The settings on the **Given** FastTab don't influence the actual inventory levels in the warehouse. Instead, they simulate conditions that are in effect only temporarily, during test execution.

1. On the **When** FastTab, specify what you want to test. The values that you enter are the inputs to the location directive engine. This approach is simpler than building manual tests by creating orders. Set the following fields:

    - **Work order type** – Specify the type of order to simulate (for example, *Sales orders* or *Purchase orders*).
    - **Work type** – Specify the work type to simulate. Typically, you'll select *Pick* or *Put*.
    - **Order number** – Specify the order number to use during the test. This information can be useful if the location directive query has ranges related to the order table.
    - **Disposition code** – Specify the disposition code that is used to handle return orders.
    - **Directive code** – Specify the directive code that drives the location directives.
    - **Item number** – Specify the item to locate.
    - **Quantity** – Specify the quantity to locate.
    - **Unit** – Specify the unit of measure for the **Quantity** field.
    - **Dimensions** – Specify the storage, product, and tracking dimensions for the item to locate.

1. On the **Then** FastTab, specify the expected outcome of the acceptance test. You **must** set one (and only one) of the following fields:

    - **Exact location** – Select a precise location. The test will be marked as passed if this location is the result of the location directive.
    - **Location matching regular expression** – Enter a regular expression that will be validated against the resulting location, even if the resulting location is blank (no result). The test will be marked as passed if the regular expression matches the name of the resulting location. For more information about regular expressions, see [.NET regular expressions](https://aka.ms/regex).
    - **Location with profile** – Select a location profile. The test will be marked as passed if the resulting location has this profile.
    - **Location in zone** – Select a location zone. The test will be marked as passed if the resulting location has this zone.

1. Select **Save** to save your test. The **Results** FastTab stores a record of any test results for each test. For information about how to run tests and interpret the results, see the next section.

## Run acceptance tests

After you set up your tests, you can run them, either one by one or all at once. To run one or more tests, follow these steps.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. On the Action Pane, select **Acceptance tests**.
1. On the **Location directive acceptance tests** page, follow one of these steps:

    - To run a single, specific test, select it in the list pane, and then select **Run** on the Action Pane.
    - To run all active tests, select **Run all** on the Action Pane.

1. After the tests have been run, the list pane is updated to indicate the most recent result of each test. To inspect the results of a test, select the test in the list pane, and then select the **Results** FastTab. The grid shows the result of each run of the test. For each result, the following information is provided:

    - **Result** – The result of the test: *Passed*, *Failed* or *Skipped*.
    - **Resulting location** – The location that was found by the test. If no location was found, this field is blank.
    - **Duration (ms)** – The duration of the test in milliseconds (ms). This field also indicates how quickly the system will be able to process your directives during daily operation. For efficient warehouse operations, you should design your location directives so that they can be processed as quickly as possible. One typical cause of a slow response is the use of location directive queries where the defined ranges or sort orders don't match an index on the table. (The system will warn you if you try to save a query that is configured in this way.)
    - **Locations evaluated** – The number of locations that were evaluated during the test. For efficient warehouse operations, you should try to have as few locations as possible evaluated. One way to minimize the number of evaluated locations is to have many location directives, the first of which are the most specific and the last of which are the most general. You can also segment your warehouse by keeping certain types of items in dedicated zones. This approach can help you avoid scanning the whole warehouse every time.
    - **Created date and time** – The date and time when the test was run.
    - **Created by** – The name of the person who ran the test.

1. To view more information about any test run, select it in the grid, and then review the **Log** field. The log includes a work creation history that will help you understand the outcome.

    > [!IMPORTANT]
    > To determine the result of the test, the system compares the **Resulting location** value with the **Then** condition. The log for a failing test might indicate that a location directive did find a location, but that location didn't match the expected location that is defined in the **Then** condition.

## Troubleshoot location directives and acceptance tests

Definition of acceptance tests is typically an iterative process. If a test fails, you should find out why it failed. Perhaps the test isn't set up correctly, or perhaps a location directive must be adjusted so that it better meets your requirements.

To troubleshoot your location directives and acceptance tests, follow these steps.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the list pane, select a location directive that you've designed an acceptance test for.
1. Expand the FactBox pane. This pane is on the right side of the page and is labeled **Related information**.
1. In the FactBox pane, expand the **Acceptance tests** FactBox. The grid in this FactBox lists the acceptance tests that are relevant to the selected location directive. It also shows the most recent result for each of those tests. From this FactBox, you can perform the following actions:

    - Select **Run all** to run all the listed tests.
    - Select **Coverage** to switch to and from the coverage view. The coverage view uses colored highlighting to indicate which location directives, lines, and actions were used to determine the result of a selected test. Records that are marked yellow were evaluated but didn't find a location. Records that are marked green did find a location. To change the test that coverage is shown for, select the symbol in the **Result** column for the relevant test.
    - Hover over a test to view more information about it, including the log.
    - In the **Name** column, select the name of a test to open that test on the **Location directive acceptance tests** page. There, you can inspect and adjust the test as you require.
    - Select **Run tests after change** to turn on and off the setting that will automatically run all tests each time that you change a location directive. Use this functionality to provide immediate feedback about the impact of changes as you make them.

1. Based on the results indicated by the coverage view and test log, adjust your tests and/or location directives until they produce the expected results for each test.
