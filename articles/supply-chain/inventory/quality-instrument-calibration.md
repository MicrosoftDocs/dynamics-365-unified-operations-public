---
title: Test instrument calibration (preview)
description: Learn how to track the calibration schedule and history of individual test instruments, run an ongoing calibration process, and track the usage and calibration status of each test instrument.
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Test instrument calibration (preview)

Calibration is the process of evaluating and adjusting the precision and accuracy of measurement equipment and is usually defined as a performance comparison against a standard of known accuracy. Proper calibration of test instruments helps ensure a safe working environment and produces valid data for future reference. Using test instruments that aren't calibrated regularly can result in false-positive and/or false-negative quality control tests. The instrument calibration feature in Supply Chain Management makes it possible to track the calibration schedule and history of individual test instruments, supports an ongoing calibration process, and can track the usage of each test instrument based on the completion of quality order tests.

Instrument calibration is primarily managed through *test instrument tags*, each of which is a digital record that represents a specific physical test instrument. Each tag holds settings for and information about its test instrument. Each test instrument tag also includes a calibration history, indicates weather an instrument requires calibration, assigns a calibration group (which defines the calibration schedule), provides a calibration procedure (possibly including attached documents), and manages other calibration details.

You can define the calibration schedule for the tags in each calibration group in one of two ways:

- Based on usage (such as every 1,000 uses) – The system tracks how many times the test instrument tag has been used (assigned to a quality order) and automatically creates calibration records when the usage count reaches a specified threshold.
- Based on a periodic schedule (such as monthly) – The system tracks the date of the last calibration and automatically creates a calibration record when the next scheduled calibration date is reached.

The feature also lets you generate and print calibration reports such as calibration certificates and calibration schedule reports.

You can design calibration labels layouts that you can print and attach each individual test instruments as needed.

## Prerequisites

To use test instrument calibration features in Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM: more here? right FM? -->

## <a name="parameters"></a>Set up instrument calibration parameters

The **Inventory and warehouse management parameters** page includes options that affect the way instruction calibration works across the system. Follow these steps to set them up.

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. Open the **Quality management** tab.
1. Make the following settings in the **Test instrument calibration** field group.
    - **Automatically assign test instrument tag number on quality order line** – Set this option to *Yes* if the system should attempt to automatically assign the best available test instrument tag to new quality order test lines. If you set this to *No*, then test instrument tags must be assigned manually when needed.
    - **Check if test instrument is being calibrated** – Select the action to take when the test instrument tag assigned to a quality order line has a usage status of *Calibration* (which indicates that the instrument is being calibrated and therefore can't be used). This establishes the default setting for new test instrument tags. Choose one of the following values.
        - *No check* – Skip this check.
        - *Warning only* – If the instrument is being calibrated, then show a warning message but allow the instruction to be used.
        - *Not allowed* – If the instrument is being calibrated, then show an error messages that says the instrument can't be used.
    - **Check for maximum usage before calibration when assigning tag numbers** – Select the action to take from a quality order when the maximum use count for a test instrument tag is exceeded (which means that the instrument needs to be calibrated). Choose one of the following values.
        - *No check* – Skip this check.
        - *Warning only* – If the instrument is due for calibration, then show a warning message but allow the instruction to be used.
        - *Not allowed* – If the instrument is due for calibration, then show an error messages that says the instrument can't be used.
    - **Check for lifetime usage maximum when assigning tag numbers** – Select the action to take from a quality order when the lifetime usage maximum is exceeded for a given test instrument tag. Choose one of the following values.
        - *No check* – Skip this check.
        - *Warning only* – If the instrument has exceeded it's lifetime usage maximum, then show a warning message but allow the instruction to be used.
        - *Not allowed* – If the instrument has exceeded it's lifetime usage maximum, then show an error messages that says the instrument can't be used.
    - **Skip check for test instrument on open quality order** – Set this option to *No* to prevent test instrument tags that are already assigned to open quality orders from being assigned to a new quality orders. Set to *Yes* to skip this check, which might allow a test instrument tag to be assigned to more than open quality order at a time.
    - **Label layout** – Select the label layout to use when printing calibration labels. <!-- KFM: We probably need a section or topic that explains how/where to create these layouts. Seems like we can generate a sample layout from the navigator. -->
    - **Print destination** – Choose where to print calibration labels.  Choose one of the following values.
        - *Printer* – Print physical labels to a printer.
        - *File* – Save labels to a file. <!-- KFM: Where can I find these? How do I use them? -->
    - **Printer name** – If you set **Print destination** to *Printer*, then select the name of the printer to use here.

## <a name="instrument-types"></a>Set up test instrument types

Use the **Test instruments** page to define and view details about the types of devices that are used to perform tests on quality orders and to calibrate other test instruments. Test instrument types help quality workers know which type of device or tool they should use when running test for a quality order and for calibrating test instruments. For each test instrument type, you can choose whether the instrument is used for calibration, whether a test instrument tag is required to identify which specific physical instrument to use, and which layout to use when printing calibration labels. Learn more in [Quality management test instruments](quality-test-instruments.md).

## <a name="locations"></a>Set up test locations

Use the **Test locations** page to establish a list of locations where test instruments can be located. This can help workers find the test instruments they need when performing tests on quality orders. Later, you'll be able to assign locations to each test instrument tag as needed.

To set up your test locations, go to **Inventory management** \> **Setup** \> **Quality control** \> **Test locations**. Use buttons on the Action Pane, to create, edit, and delete locations as needed. For each test location, enter the following information:

- **Test location** – Enter a unique name or number that identifies the test location.
- **Description** – Enter a short description of the test location.

## <a name="departments"></a>Set up test departments

Use the **Test departments** page to establish a list of departments that use test instruments. This can help users find the test instrument and/or the people who work with it. Later, you'll be able to assign departments to each test instrument tag as needed.

To set up your test locations, go to **Inventory management** \> **Setup** \> **Quality control** \> **Test departments**. Use buttons on the Action Pane, to create, edit, and delete locations as needed. For each test location, enter the following information:

- **Test departments** – Enter a unique name or number that identifies the test department.
- **Description** – Enter a short description of the test department.

## <a name="procedures"></a>Set up calibration procedures

For each type of instrument calibration you perform, you can define a *calibration procedure* in Supply Chain Management. Calibration procedures help you track the steps that are required to calibrate a specific type of instrument. You can also use calibration procedures to track the external vendors that you use to calibrate instruments. Later, when you're setting up a test instrument tag, you can assign a calibration procedure to the tag.

To set up a calibration procedure, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Calibration procedures**.
1. Create or edit a calibration procedure.
1. For your new or selected procedure, make the following settings in the header.
    - **Calibration procedure name** – Enter a name for the calibration procedure.
    - **Description** – Enter a short description of the calibration procedure.
    - **External calibrating vendor** – Enter or select the account number of the external vendor that you use to calibrate instruments. Leave this blank for calibration procedures that you perform in-house.
    - **External vendor name** – This read-only field shows the name of the external vendor whose account number you selected in the **External calibrating vendor** field.
1. On the **Procedure** FastTab, enter details for how to proceed when calibrating instruments where this procedure is to be used.
1. If you'd like to attach a document that provides even more detail about the calibration procedure, select the **Attachments** icon (paperclip) at the right side of the Action Pane to open the **Attachments for Calibration procedures** page, where you can view, add, and describe documents attached to your selected calibration procedure. Use the **New** menu in the Action Pane to upload a file as a new attachment. Attachments are available for viewing from instrument and calibration records that use this procedure.

## <a name="groups"></a>Set up calibration groups

Use calibration groups to group test instrument tags and assign their calibration schedules. All test instrument tags that are assigned to a given calibration group share the same calibration method, calibration schedule, and other settings.

To set up a calibration group, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Calibration groups**.
1. Create or edit a calibration group.
1. For your new or selected group, make the following settings in the header.
    - **Calibration group** – Enter the name of the group.
    - **Description** – Enter a short description of the group.

1. Make the following settings on the **General** FastTab.
    - **Calibration method** – Select the method that determines when the instrument is calibrated. Choose one of the following values:
      - *Manual* – Manually calibrate the instrument on an ad-hoc basis.
      - *Usage* – Calibrate the instrument based on how many times it's been used.
      - *Periodic* – Calibrate the instrument on a regular schedule based on calendar days, months, or years.
    - **Calibration period** – This field is only active when **Calibration method** is *Periodic*. Select the unit by which you will define number of days between calibrations.  Choose one of the following values:
      - *Day* – Specify the period using days.
      - *Month* – Specify the period using months.
      - *Year* – Specify the period using years.
    - **Calibration period frequency** – This field is only active when **Calibration method** is *Periodic*. Enter the amount of time to wait between calibrations, using the unit selected for **Calibration period**.  For example, if test instrument tags for this group are assigned to instruments that should be calibrated every three months, set **Calibration period** to *Month* and **Calibration period frequency** to *3*.
    - **Calibration usage update method** – This field is only active when **Calibration method** is *Usage*. The usage method to be used when updating current usage of the test instrument based on the usage of the quality order test line.
      - *Fixed increment* – Each time a quality order with a test instrument tag from this group is validated, update the test instrument tag's usage count by the specified **Usage increment**.
      - *Test quantity* – Each time a quality order with a test instrument tag from this group is validated, update the test instrument tag's usage count by the test quantity specified in that quality order.
    - **Usage increment** – This field is only active when **Calibration method** is *Usage* and **Calibration usage update method** is *Fixed increment*. Specify the increment by which to increase the usage count of a test instrument tag each time an instrument is used. For example, if **Usage increment** is set to *2*, the usage count for a test instrument tag in this group is increased by two for every validated quality order that includes that test instrument tag, no matter how many units are tested.
    - **Usage count trigger for calibration** – This field is only active when **Calibration method** is *Usage*. Enter the usage value that triggers a calibration for test instrument tags in this group. The instrument can still be used until the **Maximum usage before calibration** is met. For example, if **Usage count trigger for calibration** is *100*, and a test instrument tag from this group reaches 100 usages, then the periodic job that creates calibration records will create one for that test instrument tag the next time the job runs.
    - **Maximum usage before calibration** – This field is only active when **Calibration method** is *Usage*. Enter the maximum number of times a test instrument tag from this group can be used before it must be calibrated. For example, the **Usage count trigger for calibration** could be *100* while the **Maximum usage before calibration** is 125. This means that calibration is triggered after 100 uses but the instrument can still be used until it reaches 125 usages.
    - **Lifetime usage maximum** – This field is only active when **Calibration method** is *Usage*. Enter the maximum number of times an instrument can be used before being taken out of service.  For example, if **Lifetime usage maximum** is *10,000*, then test instrument tags in this group that reach 10,000 uses are marked as out of service and can no longer be calibrated.

> [!NOTE]
> Use the **Inventory and warehouse management parameters** page to configure how the system reacts when **Maximum usage before calibration** and **Lifetime usage maximum** values are met (you can choose to do nothing, show a warning but still allow the instrument to be used, or show an error and block the instrument from being used). Learn more in [Set up instrument calibration parameters](#parameters).

## Set up test instrument tags

Each physical test instrument is represented in Supply Chain Management by a *test instrument tag* record. The test instrument tag is used to track the calibration schedule and history of the test instrument, and it can be assigned to quality order tests. For example, the test instrument tag specifies data such as the manufacturer, warranty number, acquisition date, and specifications.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Create or edit a test instrument tag.
1. View and make the following settings in the header for your new or selected test instrument tag.

    - **Tag number** – Enter a unique identify name, number, or code for the instrument.
    - **Test instrument type** – Select the type or category of the test instrument. The test instrument for which the test instrument tag is associated with. Examples could include Scale, Thermometer, Oximeter, and so on.  The test instrument type establishes options such as whether the instrument is used for calibration, whether a test instrument tag is required to identify which specific physical instrument to use, and which layout to use when printing calibration labels. Learn more in [Set up test instrument types](#instrument-types).
    - **Instrument usage status** – Shows the current usage status of the test instrument. The field is read-only, but you can manually change the status to *Out of service* or *Available* using the buttons in the **Update usage status** tab of the Action Pane. The field shows one of the following values:
        - *Available* – The test instrument is ready to be assigned to a new quality order.
        - *Calibration* – The test instrument is currently being calibrated. This status is set automatically when an open (in-progress) calibration record exists for this test instrument tag.
        - *Out of service* – The test instrument is out of service and can't be used for quality order tests. This status is set automatically when the lifetime usage maximum is reached.

1. Expand the **General** FastTab, which contains general information about the test instrument tag of the test instrument. The following fields are available here.

    - **Description** – Enter a brief description of this instrument.
    - **Instrument description** – Shows the description of the instrument type that is selected in the **Test instrument type** field. This field is read-only.
    - **Used for calibration** – Indicates whether the selected test instrument is used to calibrate other instruments. This setting is read-only here and is inherited from the the selected **Test instrument type**.
    - **Skip check for test instrument on open quality order** – Set this option to *No* to prevent test instrument tags that are already assigned to open quality orders from being assigned to a new quality orders. Set to *Yes* to skip this check, which might allow a test instrument tag to be assigned to more than open quality order at a time.
    - **Restricted use** – Set to *Yes* if this test instrument is restricted. This is for information only.
    - **Check if test instrument is being calibrated** – Select the action to take on a quality order when the **Instrument usage status** of the instrument is *Calibration*. The default value for new tags is established on the [**Inventory and warehouse management parameters** page](#parameters), but you can change it for each individual test instrument tag. The available options are:
        - *Not allowed* – If the **Instrument usage status** is *Calibration*, then don't allow the instrument to be used for new or existing quality orders.
        - *Warning only* – If the **Instrument usage status** is *Calibration*, then show a warning but still allow it to be used for new or existing quality orders.
        - *No check* – ALways allow the instrument to be used for new or existing quality orders, regardless of its calibration status.
    - **Serial number** – Enter the serial number of this test instrument.
    - **Owner** – Enter the owner of this test instrument.
    - **Acquisition date** – Enter date on which the test instrument was acquired.
    - **Fixed asset number** – If the test instrument is tied to a fixed asset number, then select that number here. This is for information only.
    - **Customer account** – Select the customer account that this test instrument is related to. For example, the instrument might belong to and/or be assigned to a specific customer.
    - **Vendor account** – Select the vendor account that this test instrument tag is related to. The specific test instrument tag can belong to and/or be assigned to a specific vendor.
    - **Test area** – Select the test area that this test instrument is associated with. This field is a standard Supply Chain Management field that is being reused on this form based on standard logic.
    - **Test department** – Select the department that is responsible for this test instrument. Learn more in [Set up test departments](#departments).
    - **Test location** – Select the location where this test instrument can be found. Learn more in [Set up test locations](#locations).
    - **Unit** – Indicates the unit that this instrument measures in (such as grams or milliliters). This setting is read-only here and is inherited from the the selected **Test instrument type**.
    - **Precision** – Indicates the precision of a measurement (the number of digits that are used to express that value) that can be used when recording results from this test instrument. This setting is read-only here and is inherited from the the selected **Test instrument type**.

1. Expand the **Calibration details** FastTab, which contains information specific to the calibration of the test instrument tag. The following fields are available here.

    - **Calibration required** – Choose whether calibration is required for this test instrument. The other fields on this FastTab are only editable when this option is set to *Yes*.
    - **Calibration procedure name** – Select name of the procedure used for calibration of this test instrument. The procedure provides instructions for how to calibrate the instrument. To read the procedure, select this link. If the selected procedure includes attached documents, then select the **Attachments** icon (paperclip) at the right side of the Action Pane to see them. Learn more in [Set up calibration procedures](#procedures).
    - **External calibrating vendor** – If an external vendor is used for calibrating this instrument, then this field indicates the account number of that vendor. This setting is read-only here and is inherited from the the selected **Calibration procedure name**.
    - **External vendor name** – If an external vendor is used for calibrating this instrument, then this field indicates the name of that vendor. This setting is read-only here and is inherited from the the selected **Calibration procedure name**.
    - **Calibration start date** – The date of the first calibration. Other calibration dates are calculated relative to this date.
    - **Usage count since last calibration** – Indicates the number of times this instrument has been used since its last calibration. This field applies only when the **Calibration method** is *Usage* and is used to determine when the next calibration is due. When the instrument is calibrated and approved, this value is reset to zero. This field is usually read-only, but you can make it editable from the Action Pane by opening the **Functions** tab and selecting **Override usage data**.
    - **Lifetime usage count** – Indicates the number of times the test instrument tag has been used over its lifetime. This field is usually read-only, but you can make it editable from the Action Pane by opening the **Functions** tab and selecting **Override usage data**.
    - **Calibration group** – Select the calibration group that this instrument belongs to. The calibration group establishes the calibration method (manual, periodic, or usage) and related settings that establish the calibration schedule (how often the instrument should be calibrated). Settings from the selected group are shown nearby (read-only), which depend on which calibration method the group uses. Learn more in [Set up calibration groups](#groups).
    - **Completion assignee** – Select the user who is generally assigned to complete the calibration of this instrument.
    - **Approval assignee** – Select the user who is generally assigned to approve the calibration of this instrument.
    - **Started date** – Indicates the date when the most recent instrument calibration was started.
    - **Completion date** – Indicates the date when the most recent instrument calibration was completed.
    - **Calibration result** – Indicates the date result of the most recent instrument calibration.
    - **Approval date** – Indicates the date date when the most recent instrument calibration was approved.
    - **Next calibration date** – Indicates the date date when the next instrument calibration is scheduled. This field applies only when the **Calibration method** is *Periodic* or *Manual*. If you'r using the manual calibration method, this field is editable. For the periodic calibration method, this field is automatically calculated using the most recent calibration **Approval date** plus the calibration group schedule settings. If you need to reschedule the automatically calculated **Next calibration date**, then go to the Action Pane, open the **Functions** tab and select **Reschedule calculations**. Here are a few examples of how dates are calculated:
        - If the last closed calibration **Approval date** is *Jan 1, 2025*, the **Calibration period** is *Day*, and the **Calibration period frequency** is *10*, then the **Next calibration date** calculates to be *Jan 11, 2025*.
        - If the last closed calibration **Approval date** is *Jan 1, 2025*, the **Calibration period** is *Month*, and the **Calibration period frequency** is *3*, then the **Next calibration date** calculates to be *Apr 1, 2025*.
        - If the last closed calibration **Approval date** is *Jan 1, 2025*, the **Calibration period** is *Year*, and the **Calibration period frequency** is *1*, then the **Next calibration date** calculates to be *Jan 1, 2026*.
    - - **Date calibration certificate printed** – Indicates the date when the Instrument calibration certificate was last printed.

1. Expand each of the following FastTabs and enter information as needed. These fields are for information only and are not used in any calculations or processes.
    - **Manufacturer data** – Enter information specific to the instrument and its manufacturer.
    - **Test procedures** – Add additional test procedures here to support the calibration procedures.
    - **Specifications** – Add additional specifications.
    - **Notes** – Add notes and other comments.

## Create calibration records

When a test instrument requires calibration, a *calibration record* must be created. The calibration record is used to track the details of the calibration process, including the date and time when the calibration was started, completed, and approved, who performed each step, and the results of the calibration. You can see your full calibration history by viewing the calibration record list and you can filter that list to see, for example, the calibration history of a specific physical instrument.

While a calibration record is open, its related test instrument tag shows an **Instrument usage status** of *Calibration*, which usually means that the instrument isn't available for use.

## Manually create a calibration record

You can manually create a calibration record for a test instrument tag at any time. To do so, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Select the test instrument tag for which you want to create a calibration record.
1. In the Action Pane, on the **Functions** tab, select **Calibrate instrument**.
1. The **Test instrument calibration record detail** page opens. Most of the fields are prefilled to match the settings of your selected test instrument tag, but you can adjust them as needed.
1. On the Action Pane, select **Save**.

## Schedule a batch job to automatically create calibration records when needed

The *Create calibration records* batch job automatically creates calibration records for test instrument tags that are due for calibration. The batch job can be scheduled to run on a regular basis (for example, daily or weekly) or it can be run manually as needed. Each time the batch job runs, it checks each test instrument tag and creates an open calibration record for each tag that meets the following criteria:
    - If the **Calibration method** is *Usage*, then the job checks the **Usage count since last calibration** and **Maximum usage before calibration** fields to determine if a calibration record should be created.
    - If the **Calibration method** is *Periodic*, then the job checks the **Next calibration date** field to determine if a calibration record should be created.

To run or schedule the batch job, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Create calibration records**.
1. On the **Records to include** FastTab, set up filters and constraints to define which test instrument tags to check. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often to run the job. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box.

## Calibrate an instrument

Calibration work is created and traced using calibration records. Each calibration record is associated with a specific test instrument tag and contains information about the calibration process, including the date and time when the calibration was started, completed, and approved, who performed each step, and the results of the calibration.

Calibration records are listed on the **Calibrate test instruments** page, where you can view, start, take notes, complete, and approve the calibration of a test instrument. On completing a calibration, there are three available result possibilities: *Pass*, *Limited pass*, or *Fail*. For failed calibrations, you can choose to make the instrument out of service or leave it as being calibrated. Calibrations that pass must also be approved. Electronic signatures can optionally be required for approving a completed calibration record.

A completed or approved calibration can be reopened at any time, and you can view a history of all reopened calibrations.

To perform a calibration, follow these steps:

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments**.
1. All of the open records listed here represent calibrations that are due. Either select one of these or select **New** on the Action Pane to create a new one.
1. Read and enter information in the following fields as needed.
    - **Test instrument type** – The test instrument that is being calibrated.
    - **Description** – Describes the test instrument.
    - **Tag number** – The test instrument tag number of the test instrument being calibrated.
    - **Description** – Describes the test instrument tag.
    - **Instrument usage status** – Indicates the current status of the test instrument tag (*Available*, *Calibration* or *Out of Service*).
    - **Calibration procedure name** – The calibration procedure to use. By default, this matches the procedure selected for test instrument tag but you can change it here. Learn more in [Set up calibration procedures](#procedures).
    - **Description** – Describes the calibration procedure.
    - **External calibrating vendor** – If an external vendor is used for calibrating this instrument, then this field indicates the account number of that vendor. This setting is read-only here and is inherited from the the selected **Calibration procedure name**.
    - **External vendor name** – If an external vendor is used for calibrating this instrument, then this field indicates the name of that vendor. This setting is read-only here and is inherited from the the selected **Calibration procedure name**.
    - **Calibration procedure** – The procedures as specified on the Calibration procedure form. This setting is read-only here and is inherited from the the selected **Calibration procedure name**.
    - **Started by** – The user that started the calibration. This field is updated when you **Start calibration** action.
    - **Started date** – The date the calibration was started. This field is updated by the **Start calibration** action.
    - **Completion assignee** – The user responsible for assigning the user that will complete the calibration. This field defaults from the test instrument tag but can be modified.
    - **Completion by** – The user that completed the calibration. This field is updated by the **Complete calibration** action.
    - **Completion date** – The date the calibration was completed. This field is updated by the **Complete calibration** action.
    - **Calibration result** – The result of the calibration of the test instrument. This field is updated by the **Complete calibration** action.
    - **Approval assignee** – The user responsible for assigning the user that will approve the calibration. This field defaults from the test instrument tag but can be modified.
    - **Approval by** – The user that approved the calibration. This field is updated by the **Approve calibration** action.
    - **Approval date** – The date the calibration was approved. This field is updated by the **Approve calibration** action.
    - **Test procedures** – Additional information for how to calibrate the test instrument to be calibrated. The default information comes from the test instrument tag but can be updated during calibration.
    - **Specifications** – Additional specifications about the test instrument to be calibrated. The default information comes from the test instrument tag but can be updated during calibration.
    - **Calibration notes** – Additional notes about the calibration. The default information comes from the test instrument tag but can be updated during calibration.
    - **Attachments** – If additional calibration instructions are available as attached documents, then the **Attachments** icon (paperclip) at the right side of the Action Pane shows a badge with the number of attachments. Select this icon to open the **Attachments for Calibration procedures** page, where you can view, add, and describe documents attached to your calibration record.

1. If you'd like to record details about the specific instruments required or used to calibrate the test instrument, go to the Action Pane, open the **Calibrate instruments** tab and select **Assign calibration tools**. Then use the **Calibration tools used** page to record each instrument. Make the following settings for each instrument you add here: <!-- KFM: Does anything happen with this info? I can't see it listed anywhere after calibration is finished. -->
    - **Calibration tool** – Select the test instrument type for the instrument to be used. For a test instrument type to be listed here here, it must have **Use for calibration** set to *Yes*. Learn more in [Quality management test instruments](quality-test-instruments.md).
    - **Calibration tool tag number** – To identify a specific physical test instrument, then select its test instrument tag number here. This value is required if the selected **Calibration tool** has **Requires test instrument tag** set to *Yes*. <!-- KFM: will this result in incrementing the usage count of this tag when calibration is marked as complete? -->

1. To start the calibration, go to the Action Pane, open the **Calibrate instruments** tab and select **Start calibration**. Then select **OK** in the dialog. This updates the **Started by** and **Started date** fields on the calibration record.
1. Do your calibration tests as required. When you're done testing, go to the Action Pane, open the **Calibrate instruments** tab and select **Complete calibration**. Then make the following settings in the **Calibration action** dialog.
    - **Calibration result** – Select the result of the calibration. Choose one of the following values:
        - *Pass* – The instrument passed the calibration.
        - *Limited pass* – The instrument can still be used but within a limited scope.
        - *Fail* – The instrument failed the calibration.
    - **Update associated test instrument tag status to 'Out of service'** – Set to *Yes* if the instrument failed the calibration and you want to mark it as out of service. This option is only available when the **Calibration result** is set to *Fail*.

1. The calibration must now be approved, either by you or by somebody else (such as a supervisor), depending on how your system is set up. The approver must open the calibration record and then, on the Action Pane, open the **Calibrate instruments** tab and select **Approve calibration**. The instrument is now approved and the **Approved by** and **Approved date** fields are updated. The related test instrument tag is updated with the test result, approval date, and next calibration date.
1. If you need to print a calibration label and/or calibration certificate, then open the Calibration instruments tab on the Action pane and select the appropriate button in the **Print** group.

## Reopen an approved calibration record

If you need to edit an approved calibration record, open the record and, in the Action Pane, go to the **Calibrate instrument** tab and select **Reopen calibration**. This clears out the completed and approved fields and writes a reopen calibration history record. The calibration record returns to the *Open* state can now be edited and completed as usual.

To view a history of reopened calibration records, go to **Inventory management** \> **Inquiries and reports** \> **Quality management** \> **Calibration reopen history log**.

## Apply test instrument tags to a quality order

The specification of a test instrument on a quality order line has been expanded to include the selection of a test instrument tag. When a test instrument that is selected for use on a quality order requires a test instrument tag, the quality order cannot be validated without the selection of a test instrument tag on the quality order result line.

There is an added field in the Inventory and warehouse management parameters called Automatically assign test instrument tag number on quality order line that when selected, will sort through the test instrument tags for the instrument and select the best available test instrument tag for the quality test. If this parameter is not selected, the user will have to manually select a test instrument tag on the quality order line or the quality order results line when the quality order is updated.

If a test instrument tag has an Instrument usage status of Out of service, then it will not be available for selection. If the test instrument tag has an Instrument usage status of Calibration, depending on the specific of the test instrument tag, it may or may not be available for selection on the Quality test. Additionally, depending on parameter validations, the system might also optionally either warn or send an error to the user, if the chosen test instrument tag has exceeded its maximum usage and/or its lifetime usage. Also, if the chosen test instrument tag is currently being used on an open quality order, a warning message will also be provided to the user.

Once validated, if the chosen test instrument tag is calibrated based on Usage, then the usage counts on the test instrument tag are updated based on the quality order. The current usage count and the lifetime usage count will be incremented by either the test quantity or the usage increment depending on the details of the calibration group on the test instrument tag.

## Print calibration reports

There are three calibration related reports provided:

- Test instrument calibration certificates
- Test instrument calibration labels
- Test instrument calibration schedule

Calibration certificates can also be generated in mass directly from the menu path: **Inventory management** \> **Reports** \> **Quality management** \> **Test instrument calibration certificates**. The Calibration certificates and the Calibration labels can both be printed from a test instrument tag or from a specific calibration record. If printed from the test instrument tag, they include details from the last closed calibration. If printed from a specific calibration record, it will print details from that specific calibration.

Once generated, it can be saved to a file or printed directly to a printer of your choosing. Here is an example of a Calibration certificate:

Test instrument calibration labels assume the use of a label printer. The calibration label layout uses ZPL code to generate the label. When printing a Calibration label, it generates ZPL code that can be immediately recognized and printed by a ZPL Printer in a specified layout or a ZPL reader can be used to view it. When choosing the ribbon action to Print Calibration label, the default destination will come from the Inventory parameters but can be modified at printing time and it supports the option to print the code to a file or to send it directly to a ZPL printer for immediate printing. This layout can be defined using the Calibration label layout setup and can support different layouts for different test instrument types. Test instrument calibration schedule report can be printed directly from the menu path: **Inventory management** \> **Reports** \> **Quality management** \> **Test instrument calibration schedule**. The print destination supports the option to print the report to the screen or directly to a printer of your choice. This report is designed to provide a list of test instruments that need to be calibrated. However, the selection criteria provided supports many options such as by owner or calibration method. By using the Show all due today option, it will create a list of test instrument tags where the Next calibration due date is before today
