---
title: Test instrument calibration
description: Learn how to track the calibration schedule and history of individual test instruments, run an ongoing calibration process, and track the use and calibration status of each test instrument.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventParameters, QMSInventTestLocation, InventTestInstrument, QMSInventTestDepartment, QMSInventCalibrationProcedure, QMSInventCalibrationGroup, QMSInventTestInstrumentTag, QMSInventInstrumentCalibrationDetail, QMSInventTestCalibrationReopenHistory, InventTestGroup, InventQualityOrderTable, QMSInventCalibrationLabelLayout
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Test instrument calibration

[!include [banner](../../includes/banner.md)]

*Calibration* is the process of evaluating and adjusting the precision and accuracy of measurement equipment. It's usually defined as a performance comparison against a standard of known accuracy. Proper calibration of test instruments helps ensure a safe working environment. It also helps ensure that valid data is produced for future reference. Test instruments that aren't regularly calibrated can lead to false-positive and/or false-negative quality control tests.

The instrument calibration feature in Microsoft Dynamics 365 Supply Chain Management supports an ongoing calibration process. You can use it to track the calibration schedule and history of individual test instruments. You can also track the use of each test instrument based on the completion of quality order tests.

Instrument calibration is managed primarily through *test instrument tags*. Each test instrument tag is a digital record that represents a specific physical test instrument. This record holds settings for the test instrument and information about it.

Each test instrument tag includes a calibration history for the test instrument, indicates whether the instrument requires calibration. Each tag also provides a calibration procedure (which might include attached documents) and manages other calibration details.

Test instrument tags are assigned to a *calibration group*, which defines the calibration schedule. There are two ways to define the calibration schedule for the test instrument tags in a calibration group:

- **Based on usage** – The system tracks the numbers of times that the test instrument tag is used (that is, assigned to a quality order). It automatically creates calibration records when the usage count reaches a specified threshold. For example, calibration records might be created after every 1,000 uses.
- **Based on a periodic schedule** – The system tracks the date of the last calibration. It automatically creates a calibration record when the next scheduled calibration date is reached. For example, calibration records might be created monthly.

The feature also lets you generate and print calibration reports, such as calibration certificates and calibration schedule reports. In addition, you can design calibration label layouts that you print and attach to individual test instruments as required.

## Prerequisites

Before you can use test instrument calibration features in Supply Chain Management, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="parameters"></a>Set up instrument calibration parameters

The settings on the **Inventory and warehouse management parameters** page affect the way that instrument calibration works across the system. Follow these steps to set up the instrument calibration parameters.

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. On the **Quality management** tab, in the **Test instrument calibration** section, set the following fields:

    - **Automatically assign test instrument tag number on quality order line** – Set this option to *Yes* if the system should try to automatically assign the best available test instrument tag to new quality order test lines. If you set this option to *No*, test instrument tags must be manually assigned when they are needed.
    - **Check if test instrument is being calibrated** – Select one of the following values to specify what action the system takes if the test instrument tag that is assigned to a quality order line has a usage status of *Calibration*. (This status indicates that the instrument is being calibrated and therefore can't be used.) The value that you select is used as the default setting for new test instrument tags.

        - *No check* – Skip this check.
        - *Warning only* – If the instrument is being calibrated, show a warning message, but allow the instrument to be used.
        - *Not allowed* – If the instrument is being calibrated, show an error message that states that the instrument can't be used.

    - **Check for maximum usage before calibration when assigning tag numbers** – Select one of the following values to specify what action the system takes if the maximum usage count for a test instrument tag is exceeded. (When the maximum usage count is exceeded, the instrument is due for calibration.)

        - *No check* – Skip this check.
        - *Warning only* – If the instrument is due for calibration, show a warning message, but allow the instrument to be used.
        - *Not allowed* – If the instrument is due for calibration, show an error message that states that the instrument can't be used.

    - **Check for lifetime usage maximum when assigning tag numbers** – Select one of the following values to specify what action the system takes if the lifetime usage maximum for a test instrument tag is exceeded.

        - *No check* – Skip this check.
        - *Warning only* – If the instrument exceeds its lifetime usage maximum, show a warning message, but allow the instrument to be used.
        - *Not allowed* – If the instrument exceeds its lifetime usage maximum, show an error message that states that the instrument can't be used.

    - **Skip check for test instrument on open quality order** – Set this option to *No* to prevent test instrument tags that are already assigned to open quality orders from being assigned to new quality orders. Set it to *Yes* to skip this check. In this case, a test instrument tag might be assigned to more than one open quality order at a time.
    - **Label layout** – Select the default calibration label layout to assign to new test instrument type records. Learn more in the [Design and print calibration labels](#calibration-labels) section.
    - **Print destination** – Select one of the following values to specify the default destination for calibration labels that are printed:

        - *Printer* – Print physical labels to a printer.
        - *File* – Download and save labels as a ZPL file.

    - **Printer name** – If you set the **Print destination** field to *Printer*, select the name of the default printer to use to print calibration labels.

## <a name="instrument-types"></a>Set up test instrument types

Use the **Test instruments** page to define and view details about the types of devices that are used to perform tests on quality orders and calibrate other test instruments. *Test instrument types* help quality workers determine which type of device or tool they should use to run tests for a quality order and calibrate test instruments. For each test instrument type, you can specify the following details:

- Whether the instrument is used for calibration
- Whether a test instrument tag is required to identify the specific physical instrument that must be used
- What layout should be used when calibration labels are printed

Learn more in [Quality management test instruments](quality-test-instruments.md).

## <a name="locations"></a>Set up test locations

Use the **Test locations** page to establish a list of locations where test instruments can be kept. In this way, workers who perform tests on quality orders can find the test instruments that they need. Later, you can assign locations to each test instrument tag as required.

To set up test locations, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test locations**.
1. Use the buttons on the Action Pane to create new test locations or edit existing ones as required. (You can also delete existing test locations.)
1. For each test location, set the following fields:

    - **Test location** – Enter a unique name or number that identifies the test location.
    - **Description** – Enter a short description of the test location.

## <a name="departments"></a>Set up test departments

Use the **Test departments** page to establish a list of departments that use test instruments. In this way, users can find a test instrument and/or the people who work with it. Later, you can assign departments to each test instrument tag as required.

To set up test departments, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test departments**.
1. Use the buttons on the Action Pane to create new test departments or edit existing ones as required. (You can also delete existing test departments.)
1. For each test department, set the following fields:

    - **Test departments** – Enter a unique name or number that identifies the test department.
    - **Description** – Enter a short description of the test department.

## <a name="procedures"></a>Set up calibration procedures

For each type of instrument calibration that you perform, you can define a *calibration procedure* in Supply Chain Management. Calibration procedures help you track the steps that are required to calibrate a specific type of instrument. You can also use them to track the external vendors that you use to calibrate instruments. Later, when you set up a test instrument tag, you can assign a calibration procedure to it.

To set up a calibration procedure, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Calibration procedures**.
1. Create a new calibration procedure, or select an existing one that you want to edit.
1. On the header of the new or selected procedure, set the following fields:

    - **Calibration procedure name** – Enter a name for the calibration procedure.
    - **Description** – Enter a short description of the calibration procedure.
    - **External calibrating vendor** – Enter or select the account number of the external vendor that you use to calibrate instruments. Leave this field blank for calibration procedures that you perform in-house. After you select a value in this field, the read-only **External vendor name** field shows the name of the selected external vendor.

1. On the **Procedure** FastTab, enter details about the steps that are required to calibrate instruments where this procedure must be used.
1. Optional: If you want to attach a document that provides even more details about the calibration procedure, select the **Attachments** button (paperclip symbol) on the right side of the Action Pane. The **Attachments for Calibration procedures** page shows all the documents that are attached to the calibration procedure. Use the **New** menu on the Action Pane to upload a file as a new attachment. Attachments can be viewed from instrument and calibration records that use this procedure.

## <a name="groups"></a>Set up calibration groups

Use calibration groups to group test instrument tags and assign calibration schedules to them. All test instrument tags that are assigned to a given calibration group share the same calibration method, calibration schedule, and other settings.

To set up a calibration group, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Calibration groups**.
1. Create a new calibration group, or select an existing one that you want to edit.
1. On the header of the new or selected group, set the following fields:

    - **Calibration group** – Enter the name of the group.
    - **Description** – Enter a short description of the group.

1. On the **General** FastTab, set the following fields:

    - **Calibration method** – Select one of the following values to specify the method that determines when the instrument is calibrated:

      - *Manual* – Manually calibrate the instrument as it's required.
      - *Usage* – Calibrate the instrument based on the number of times that it's used.
      - *Periodic* – Calibrate the instrument on a regular schedule, based on calendar days, months, or years.

    - **Calibration period** – This field is available only when the **Calibration method** field is set to *Periodic*. Select one of the following values to specify the unit for the amount of time between calibrations:

      - *Day* – Specify the period in days.
      - *Month* – Specify the period in months.
      - *Year* – Specify the period in years.

    - **Calibration period frequency** – This field is available only when the **Calibration method** field is set to *Periodic*. Enter the amount of time between calibrations, in the unit that is selected in the **Calibration period** field. For example, if test instrument tags for this group are assigned to instruments that should be calibrated every three months, set the **Calibration period** field to *Month* and the **Calibration period frequency** field to *3*.
    - **Calibration usage update method** – This field is available only when the **Calibration method** field is set to *Usage*. Select one of the following values to specify the method that is used to update the current usage of the test instrument:

      - *Fixed increment* – Each time a quality order that has a test instrument tag in this group is validated, update the test instrument tag's usage count by the value that is specified in the **Usage increment** field.
      - *Test quantity* – Each time a quality order that has a test instrument tag in this group is validated, update the test instrument tag's usage count by the test quantity that is specified on the quality order.

    - **Usage increment** – This field is available only when the **Calibration method** field is set to *Usage* and the **Calibration usage update method** field is set to *Fixed increment*. Specify the increment by which to increase the usage count of a test instrument tag each time an instrument is used. For example, if the **Usage increment** field is set to *2*, the usage count for a test instrument tag in this group is increased by two for every validated quality order that includes the test instrument tag, regardless of the number of units that are tested.
    - **Usage count trigger for calibration** – This field is available only when the **Calibration method** field is set to *Usage*. Enter the usage value that triggers a calibration for test instrument tags in this group. The instrument can still be used until the usage count that is specified in the **Maximum usage before calibration** field is reached. For example, if the **Usage count trigger for calibration** field is set to *100*, and a test instrument tag in this group reaches 100 uses, the periodic job that creates calibration records creates a record for that test instrument tag the next time the job runs.
    - **Maximum usage before calibration** – This field is available only when the **Calibration method** field is set to *Usage*. Enter the maximum number of times that a test instrument tag in this group can be used before it must be calibrated. For example, the **Usage count trigger for calibration** field might be set to *100*, whereas the **Maximum usage before calibration** field might be set to *125*. In this case, calibration is triggered after 100 uses, but the instrument can continue to be used until it reaches 125 uses.
    - **Lifetime usage maximum** – This field is available only when the **Calibration method** field is set to *Usage*. Enter the maximum number of times that an instrument can be used before it's taken out of service. For example, if the **Lifetime usage maximum** field is set to *10,000*, test instrument tags in this group that reach 10,000 uses are marked as out of service and can no longer be calibrated.

> [!NOTE]
> Use the **Inventory and warehouse management parameters** page to configure how the system reacts when the **Maximum usage before calibration** and **Lifetime usage maximum** values are reached. You can choose to have the system do nothing, show a warning but still allow the instrument to be used, or show an error and block the instrument from being used. Learn more in the [Set up instrument calibration parameters](#parameters) section.

## <a name="tags"></a>Set up test instrument tags

Each physical test instrument is represented in Supply Chain Management by a test instrument tag record. This record specifies data such as the manufacturer, warranty number, acquisition date, and specifications. The test instrument tag is used to track the calibration schedule and history of the test instrument, and it can be assigned to quality order tests.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Create a new test instrument tag, or select an existing one that you want to edit.
1. On the header of the new or selected test instrument tag, review or set the following fields:

    - **Tag number** – Enter a unique name, number, or code for the instrument.
    - **Test instrument type** – Select the type or category of test instrument that the test instrument tag is associated with. Examples include *Scale*, *Thermometer*, and *Oximeter*. The test instrument type defines options such as whether the instrument is used for calibration, whether a test instrument tag is required to identify the specific physical instrument that must be used, and what layout should be used when calibration labels are printed. Learn more in the [Set up test instrument types](#instrument-types) section.
    - **Instrument usage status** – The current usage status of the test instrument. Although the field is read-only, you can manually change the status to *Out of service* or *Available* by using the buttons on the **Update usage status** tab of the Action Pane. The following status values are used:

        - *Available* – The test instrument is ready to be assigned to a new quality order.
        - *Calibration* – The test instrument is currently being calibrated. This status is automatically set when an open (in-progress) calibration record exists for this test instrument tag.
        - *Out of service* – The test instrument is out of service and can't be used for quality order tests. This status is automatically set when the lifetime usage maximum is reached.

1. On the **General** FastTab, review or set the following fields. These fields provide general information about the test instrument tag of the test instrument.

    - **Description** – Enter a brief description of the test instrument.
    - **Instrument description** – A description of the test instrument type that is selected in the **Test instrument type** field on the header.
    - **Used for calibration** – A value that indicates whether the test instrument is used to calibrate other instruments. The value is inherited from the selected test instrument type.
    - **Skip check for test instrument on open quality order** – Set this option to *No* to prevent test instrument tags that are already assigned to open quality orders from being assigned to new quality orders. Set it to *Yes* to skip this check. In this case, a test instrument tag might be assigned to more than one open quality order at a time.
    - **Restricted use** – Set this option to *Yes* if this test instrument is restricted. This option is for information only.
    - **Check if test instrument is being calibrated** – Select the action that is taken on a quality order when the **Instrument usage status** value of the instrument is *Calibration*. The default value for new tags is defined in [Inventory and warehouse management parameters](#parameters), but you can change it for individual test instrument tags. The following values are available:

        - *Not allowed* – If the **Instrument usage status** value is *Calibration*, don't allow the instrument to be used for new or existing quality orders.
        - *Warning only* – If the **Instrument usage status** value is *Calibration*, show a warning, but still allow the instrument to be used for new or existing quality orders.
        - *No check* – Always allow the instrument to be used for new or existing quality orders, regardless of its calibration status.

    - **Serial number** – Enter the serial number of the test instrument.
    - **Owner** – Enter the owner of the test instrument.
    - **Acquisition date** – Enter the date when the test instrument was acquired.
    - **Fixed asset number** – If the test instrument is linked to a fixed asset number, select that number. This field is for information only.
    - **Customer account** – Select the customer account that the test instrument is related to. For example, the test instrument might belong to and/or be assigned to a specific customer.
    - **Vendor account** – Select the vendor account that the test instrument is related to. For example, the test instrument might belong to and/or be assigned to a specific vendor.
    - **Test area** – Select the test area that the test instrument is associated with. This field is a standard Supply Chain Management field. It's reused on this page based on standard logic.
    - **Test department** – Select the department that is responsible for the test instrument. Learn more in the [Set up test departments](#departments) section.
    - **Test location** – Select the location where the test instrument can be found. Learn more in the [Set up test locations](#locations) section.
    - **Unit** – The unit that the test instrument measures in (such as grams or milliliters). The value is inherited from the selected test instrument type.
    - **Precision** – The precision of measurement that can be used when results from the test instrument are recorded. Precision refers to the number of digits that are used to express a value. The value of this field is inherited from the selected test instrument type.

1. On the **Calibration details** FastTab, review or set the following fields. These fields provide information that is specific to the calibration of the test instrument.

    - **Calibration required** – Specify whether calibration is required for the test instrument. The other fields on this FastTab can be edited only when this option is set to *Yes*.
    - **Calibration procedure name** – Select the name of the procedure that is used to calibrate the test instrument. The procedure provides instructions for calibrating the instrument. To read the procedure, select the link. If the selected procedure includes attached documents, select the **Attachments** button (paperclip symbol) on the right side of the Action Pane to view them. Learn more in the [Set up calibration procedures](#procedures) section.
    - **External calibrating vendor** – If an external vendor is used to calibrate the test instrument, the account number of the vendor. The value of this read-only field is inherited from the calibration procedure that is selected in the **Calibration procedure name** field.
    - **External vendor name** – If an external vendor is used to calibrate the test instrument, the name of the vendor. The value of this read-only field is inherited from the selected calibration procedure.
    - **Calibration start date** – The date of the first calibration. Other calibration dates are calculated relative to this date.
    - **Usage count since last calibration** – The number of times that the test instrument has been used since its last calibration. This field applies only when the **Calibration method** field is set to *Usage*. It's used to determine when the next calibration is due. Each time the instrument is calibrated and approved, the value of this field is reset to *0* (zero). Although this field is usually read-only, you can make it editable by selecting **Override usage data** on the **Functions** tab of the Action Pane.
    - **Lifetime usage count** – The number of times that the test instrument has been used during its lifetime. Although this field is usually read-only, you can make it editable by selecting **Override usage data** on the **Functions** tab of the Action Pane.
    - **Calibration group** – Select the calibration group that the test instrument belongs to. The calibration group establishes the calibration method (manual, periodic, or usage) and related settings that define the calibration schedule. Settings from the selected group are shown nearby in read-only form. They depend on the calibration method that the group uses. Learn more in the [Set up calibration groups](#groups) section.
    - **Completion assignee** – Select the user who is usually assigned to complete the calibration of the test instrument.
    - **Approval assignee** – Select the user who is usually assigned to approve the calibration of the test instrument.
    - **Started date** – The date when the most recent calibration of the test instrument was started.
    - **Completion date** – The date when the most recent calibration of the test instrument was completed.
    - **Calibration result** – The result of the most recent calibration of the test instrument.
    - **Approval date** – The date when the most recent calibration of the test instrument was approved.
    - **Next calibration date** – The date when the next calibration of the test instrument is scheduled. This field applies only when the **Calibration method** field is set to *Periodic* or *Manual*. If you're using the *Manual* calibration method, this field is editable. If you're using the *Periodic* calibration method, the value is automatically calculated by using the approval date of the most recent calibration and the settings of the calibration group schedule. If you must reschedule the date that is automatically calculated for the next calibration, select **Reschedule calculations** on the **Functions** tab of the Action Pane.

        Here are some examples that show how dates are calculated:

        - The **Approval date** value of the last closed calibration is *January 1, 2025*, the **Calibration period** value is *Day*, and the **Calibration period frequency** value is *10*. In this case, the **Next calibration date** value is calculated as *January 11, 2025*.
        - The **Approval date** value of the last closed calibration is *January 1, 2025*, the **Calibration period** value is *Month*, and the **Calibration period frequency** value is *3*. In this case, the **Next calibration date** value is calculated as *April 1, 2025*.
        - The **Approval date** value of the last closed calibration is *January 1, 2025*, the **Calibration period** value is *Year*, and the **Calibration period frequency** value is *1*. In this case, the **Next calibration date** value is calculated as *January 1, 2026*.

    - **Date calibration certificate printed** – The date when the instrument calibration certificate was last printed.

1. Enter information on the following FastTabs as required. The fields on these FastTabs are for information only. They aren't used in any calculations or processes.

    - **Manufacturer data** – Enter information that is specific to the test instrument and its manufacturer.
    - **Test procedures** – Add more test procedures to support the calibration procedures.
    - **Specifications** – Add more specifications.
    - **Notes** – Add notes and other comments.

## Create calibration records

When a test instrument requires calibration, a *calibration record* must be created. The calibration record is used to track the details of the calibration process, including the date and time when the calibration was started, completed, and approved, the person who performed each step, and the results of the calibration. To review the full calibration history, open the calibration record list. You can filter the list so that it shows the calibration history of a specific physical instrument, for example.

While a calibration record is open, its related test instrument tag shows an **Instrument usage status** value of *Calibration*. This status usually indicates that the instrument isn't available for use.

### Manually create a calibration record

You can manually create a calibration record for a test instrument tag at any time by following these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Select the test instrument tag that you want to create a calibration record for.
1. On the Action Pane, on the **Functions** tab, select **Calibrate instrument**.
1. On the **Test instrument calibration record detail** page, most of the fields are preset so that the values match the settings of the selected test instrument tag. However, you can adjust the values as you require.
1. On the Action Pane, select **Save**.

### Schedule a batch job to automatically create calibration records as required

The *Create calibration records* batch job automatically creates calibration records for test instrument tags that are due for calibration. The batch job can be scheduled to run regularly (for example, daily or weekly), or it can be manually run as required. Each time the batch job runs, it checks every test instrument tag and uses the following method to determine whether it should create an open calibration record:

- If the **Calibration method** value is *Usage*, the job checks the **Usage count since last calibration** and **Maximum usage before calibration** fields to determine whether a calibration record should be created.
- If the **Calibration method** value is *Periodic*, the job checks the **Next calibration date** field to determine whether a calibration record should be created.

To run or schedule the batch job, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Create calibration records**.
1. On the **Records to include** FastTab, set up filters and constraints to define which test instrument tags are checked. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often the job runs. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog.

## Calibrate an instrument

Calibration work is created and traced by using calibration records. Each calibration record is associated with a specific test instrument tag. It contains information about the calibration process, including the date and time when the calibration was started, completed, and approved, the person who performed each step, and the results of the calibration.

Calibration records are listed on the **Calibrate test instruments** page. There, you can view, start, take notes about, complete, and approve the calibration of a test instrument.

The three possible calibration results are *Pass*, *Limited pass*, and *Fail*. For failed calibrations, you can mark the instrument as out of service or have it continue to show up as being calibrated. Calibrations that pass must also be approved. Electronic signatures can optionally be required for approval of a completed calibration record.

A completed or approved calibration can be reopened at any time. You can view a history of all reopened calibrations.

To perform a calibration, follow these steps:

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments**.
1. All the open records that are listed on the page represent calibrations that are due. Either select one of these records or select **New** on the Action Pane to create a new one.
1. Review and set the following fields as required:

    - **Test instrument type** – The test instrument that is being calibrated.
    - **Description** – A description of the test instrument.
    - **Tag number** – The test instrument tag number of the test instrument that is being calibrated.
    - **Description** – A description of the test instrument tag.
    - **Instrument usage status** – The current status of the test instrument tag (*Available*, *Calibration*, or *Out of Service*).
    - **Calibration procedure name** – The calibration procedure to use. By default, this field is set to the procedure that is selected for test instrument tag. However, you can select a different procedure. Learn more in the [Set up calibration procedures](#procedures) section.
    - **Description** – A description of the calibration procedure.
    - **External calibrating vendor** – If an external vendor is used to calibrate the test instrument, the account number of the vendor. This value of this read-only field is inherited from the calibration procedure that is selected in the **Calibration procedure name** field.
    - **External vendor name** – If an external vendor is used to calibrate the test instrument, the name of the vendor. This value of this read-only field is inherited from the selected calibration procedure.
    - **Calibration procedure** – The procedures as they are specified on the **Calibration procedure** page. The value of this read-only field is inherited from the selected calibration procedure.
    - **Started by** – The user who started the calibration. This field is updated by the **Start calibration** action.
    - **Started date** – The date when the calibration was started. This field is updated by the **Start calibration** action.
    - **Completion assignee** – The user who is responsible for assigning the user who will perform the calibration. The default value comes from the test instrument tag, but you can modify it.
    - **Completion by** – The user who completed the calibration. This field is updated by the **Complete calibration** action.
    - **Completion date** – The date when the calibration was completed. This field is updated by the **Complete calibration** action.
    - **Calibration result** – The result of the calibration of the test instrument. This field is updated by the **Complete calibration** action.
    - **Approval assignee** – The user who is responsible for assigning the user who will approve the calibration. The default value comes from the test instrument tag, but you can modify it.
    - **Approval by** – The user who approved the calibration. This field is updated by the **Approve calibration** action.
    - **Approval date** – The date when the calibration was approved. This field is updated by the **Approve calibration** action.
    - **Test procedures** – More information about how to calibrate the test instrument that must be calibrated. The default information comes from the test instrument tag, but it can be updated during calibration.
    - **Specifications** – Further specifications for the test instrument that must be calibrated. The default information comes from the test instrument tag, but it can be updated during calibration.
    - **Calibration notes** – Further notes about the calibration. The default information comes from the test instrument tag, but it can be updated during calibration.

    > [!TIP]
    > If more calibration instructions are available as attached documents, the **Attachments** button (paperclip symbol) on the right side of the Action Pane includes a badge that shows the number of attachments. Select the **Attachments** button to open the **Attachments for Calibration procedures** page, where you can view, add, and describe documents that are attached to the calibration record.

1. If you want to record details about the specific instruments that are required or used to calibrate the test instrument, on the Action Pane, on the **Calibrate instruments** tab, select **Assign calibration tools**. Then use the **Calibration tools used** page to record each instrument. For each instrument that you add, set the following fields:

    - **Calibration tool** – Select the test instrument type for the instrument that is used. This field lists only test instrument types where the **Use for calibration** option is set to *Yes*. Learn more in [Quality management test instruments](quality-test-instruments.md).
    - **Calibration tool tag number** – To identify a specific physical test instrument, select its test instrument tag number. This field is required if the **Requires test instrument tag** option is set to *Yes* for test instrument type that is selected in the **Calibration tool** field.

1. To start the calibration, on the Action Pane, on the **Calibrate instruments** tab, select **Start calibration**. Then select **OK** in the dialog. The **Started by** and **Started date** fields on the calibration record are updated.
1. Do your calibration tests as required. When you're finished, on the Action Pane, on the **Calibrate instruments** tab, select **Complete calibration**. Then, in the **Calibration action** dialog, set the following fields:

    - **Calibration result** – Select one of the following values to specify the result of the calibration:

        - *Pass* – The instrument passed the calibration.
        - *Limited pass* – The instrument can still be used, but within a limited scope.
        - *Fail* – The instrument failed the calibration.

    - **Update associated test instrument tag status to 'Out of service'** – Set this option to *Yes* if the instrument failed the calibration, and you want to mark it as out of service. This option is available only when the **Calibration result** field is set to *Fail*.

1. The calibration must now be approved, either by you or by somebody else (such as a supervisor), depending on the setup of your system. The approver must open the calibration record, and then, on the Action Pane, on the **Calibrate instruments** tab, select **Approve calibration**. The instrument is now approved, and the **Approved by** and **Approved date** fields are updated. The related test instrument tag is updated with the test result, approval date, and next calibration date.
1. If you must print a calibration label and/or calibration certificate, on the Action Pane, on the **Calibration instruments** tab, in the **Print** group, select the appropriate button.

## Reopen an approved calibration record

If you must edit an approved calibration record, follow these steps:

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments**.
1. Find and select the relevant calibration record. The record must be in the *Fail* or *Approved* state.
1. On the Action Pane, on the **Calibrate instruments** tab, select **Reopen calibration**. The completed and approved fields are cleared, a *reopen calibration history* record is created, and the calibration record returns to the *Open* state. You can now edit and complete the calibration record in the usual way.

To view a history of reopened calibration records, follow these steps:

- Go to **Inventory management** \> **Inquiries and reports** \> **Quality management** \> **Calibration reopen history log**.
- Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments**. On the Action Pane, on the **Calibrate instruments** tab, select **Calibration reopen history log**.

## Apply test instrument types and tags to a quality order

You set up and manage quality tests by using [quality orders](quality-orders.md). A quality order defines what must be tested and how. A [test group](quality-test-groups.md) is assigned to each quality order. The test group defines which tests must be done, and which [test instrument type](quality-test-instruments.md) should be used for each test.

When you assign a test group to a quality order, each line from the selected test group becomes a line on the new quality order. The quality order also inherits the test instrument type from the test group. When you create a quality order, you can (and in some cases must) assign a specific test instrument tag to each line. In this way, you specify the physical instrument that must be used for the test.

To view and assign [test instrument types](quality-test-instruments.md) for a test group, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**.
1. Create a new test group, or select an existing one.
1. At the bottom of the page, on the **Overview** tab, create or select a test group line.
1. On the **Test** tab, in the **Test instrument** field, select the test instrument type.

To view and assign [test instrument tags](#tags) to a quality order, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Quality orders**.
1. Create a new quality order, or select an existing one.
1. At the bottom of the page, the **Overview** tab has a line for each test that the quality order requires. It includes lines that are inherited from the test group that is assigned to the quality order. You can manually add more lines as you require.
1. On the **Overview** tab, select a quality order line.
1. On the **Test** tab, in the **Tag number** field, review or set the test instrument tag for the selected quality order line.

Here are some guidelines for using test instrument types and tags on quality orders:

- If the **Automatically assign test instrument tag number on quality order line** option is set to *Yes* in [Inventory and warehouse management parameters](#parameters), when a quality order is created, the system sorts through the test instrument tags for each selected instrument type and selects the best available test instrument tag for the quality test. If the option is set to *No*, you must manually assign test instrument tags as required.
- If a test instrument type that is selected for use on a quality order line is set up to require a test instrument tag, the quality order can't be validated until a test instrument tag is selected on the quality order line.
- Test instrument tags that have an **Instrument usage status** value of *Out of service* aren't available for selection on the quality test.
- Test instrument tags that have an **Instrument usage status** value of *Calibration* might be available for selection on the quality test, depending on the setup of the test instrument tag.
- Depending on how you set up the system to validate test instrument tags, you might receive a warning or error if you select a test instrument tag that is already assigned to another open quality order, or if the selected tag has exceeded its maximum usage and/or its lifetime usage.
- When a quality order is validated, if a selected test instrument tag is calibrated based on usage, the usage counts on the tag are updated based on the quality order. The current usage count and the lifetime usage count are incremented by either the test quantity or the usage increment, depending on the details of the calibration group on the test instrument tag.

## <a name="calibration-labels"></a>Design and print calibration labels

Use calibration labels to attach calibration information directly to physical test instruments.

### Set up calibration label layouts

Calibration label layouts are designed and printed in Zebra Programming Language (ZPL) format, a standard format for printing labels on Zebra printers. Calibration labels can include information such as the test instrument tag number, the test instrument type, the calibration procedure name, and the next calibration date.

To get started quickly, you can generate a predesigned ZPL layout for a calibration label. This layout is designed to be used with Zebra printers and can be modified as required. To add the predesigned ZPL layout to your system, go to **Inventory management** \> **Setup** \> **Quality control** \> **Create sample calibration labels**. The system then generates a label layout that is named *SampleLabel_2X1*.

To customize the standard layout or create new ones, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Calibration label layout**.
1. Use the buttons on the Action Pane to create a new calibration label layout or edit an existing one as required. (You can also delete existing layouts.)
1. On the header of the new or selected layout, enter details such as the name, description, and dimensions.
1. On the **Label layout** FastTab, use the large field to design your label layout. For help, use a ZPL reference.
1. The page helps you find the codes that you need to insert field values. To add a field value to your layout, follow these steps:

    1. Set the **Use fields from** field to the type of database record that you want to use a field from (*Test instrument tags* or *Test instrument calibration records*).
    1. In the **Labels** list, select a field name.
    1. Select **Insert at end of text** to add the reference code to the end of the label layout text.
    1. Use a copy-and-paste operation to move the reference code to the desired location in the label layout text.

### Assign layouts to test instrument types

When you print a calibration label, the system uses the layout that is assigned to the test instrument type of the test instrument tag. Learn how to assign a layout to a test instrument type in [Quality management test instruments](quality-test-instruments.md).

### Print calibration labels

To print calibration labels for a physical test instrument, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Select the test instrument tag that you want to print a calibration label for.
1. On the Action Pane, on the **Print** tab, select **Calibration label**.
1. In the **Print calibration label** dialog, set the following fields:

    - **Print destination** – Select *Printer* to print the label directly to a printer. Select *File* to download and save the label locally as a ZPL file.
    - **Name** – If you selected *Printer* in the **Print destination** field, select the printer to use.

## Print calibration certificates

Calibration certificates can be printed for each calibration record. They document the calibration process and results for a test instrument, and are used to verify that the test instrument was calibrated according to the specified procedures and standards. Calibration certificates include information such as the test instrument tag number, the calibration procedure name, the calibration result, the name of the person who performed the calibration, and the next calibration date.

To print a certificate for the last closed calibration for a test instrument tag, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Select the test instrument tag that you want to print a calibration label for.
1. On the Action Pane, on the **Print** tab, select **Calibration certificate**.
1. The certificate is generated and shown on your screen. You can review, print, and/or export it.

To print a certificate for any selected calibration record, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Calibrate test instruments**.
1. Select the test calibration record that you want to print a calibration label for.
1. On the Action Pane, on the **Calibrate instruments** tab, in the **Print** group, select **Calibration certificate**.
1. The certificate is generated and shown on your screen. You can review, print, and/or export it.

## View or print the calibration schedule report

The calibration schedule report provides a list of test instruments that must be calibrated. However, you can customize the selection criteria to support many other uses. For example, you can filter by owner or calibration method. You can use the **Show all due today** option to create a list of test instrument tags where the due date of the next calibration is before the current date.

To print a calibration schedule report, follow these steps:

1. Go to **Inventory management** \> **Inquiries and reports** \> **Quality management** \> **Test instrument calibration schedule**.
1. In the **Test instrument calibration schedule** dialog, on the **Parameters** FastTab, set the **Show all due today** option to one of the following values:

    - *Yes* – Show only test instrument tags where the next calibration date is before the current date.
    - *No* – Show all test instruments tags, regardless of when they are due for calibration.

1. The **Destination** FastTab shows the current destination for the report. The possible destinations are *Screen*, *Printer*, *File*, and *Email*. (The default destination is *Screen*.) To change the destination, select **Change**, select a new destination, and then configure settings that are related to that destination.
1. On the **Records to include** FastTab, set up filters and constraints to define which test instrument tags are included. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often to run the job. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog.
