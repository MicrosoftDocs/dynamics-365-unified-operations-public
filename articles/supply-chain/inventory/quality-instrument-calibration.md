---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Instrument calibration

Some of the test instruments that you use during quality control processes probably need to be regularly calibrated. Calibration is the process of evaluating and adjusting the precision and accuracy of measurement equipment and is usually defined as a performance comparison against a standard of known accuracy. Proper calibration helps ensure a safe working environment and produces valid data for future reference. Using test instruments that aren't calibrated regularly can result in false-positive and/or false-negative quality control tests. The instrument calibration feature in Supply Chain Management makes it possible to track the calibration schedule and history of individual test instruments, supports an ongoing calibration process, and can track the usage of each test instrument based on the completion quality order tests.

Instrument calibration is primarily managed through *test instrument tags*, each of which represents a specific physical test instrument. Each tag holds settings for and information about its test instrument, such as as the manufacturer, warranty number, acquisition date, and specifications. Test instrument tags also indicate weather an instrument requires calibration and, if so, assign it to a calibration group (which defines the calibration schedule), a calibration procedure (which provides instructions, possibly with attached documents), and other calibration details.

You can define the calibration schedule for each test instrument tag in one of two ways:

- Based on usage – The system tracks how many times the test instrument tag has been used and automatically creates calibration records when the usage count reaches a specified threshold.
- Based on a periodic schedule – The system tracks the date of the last calibration and automatically creates calibration records when the next scheduled calibration date is reached.

The feature also lets you generate and print calibration reports such as calibration certificates and calibration schedule reports.

You can design calibration labels layouts that you can print out as attach to each individual test instrument as needed.

## Prerequisites

To use instrument calibration features in Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM: more here? right FM? -->

## Set up instrument calibration parameters

To set options that affect the way instruction calibration works across the system, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. Open the **Quality management** tab.
1. Make the following settings in the **Test instrument calibration** field group.
    - **Automatically assign test instrument tag number on quality order line** – Set this option to *Yes* if the system should attempt to automatically assign the best available test instrument tag to new quality order test lines. If you set this to *No*, then test instrument tags must be assigned manually when needed.
    - If not assigned automatically, they will need to be assigned manual for tests that use test instrument tags
    - **Check if test instrument is being calibrated** – Select the action to take from a quality order when the test instrument tag assigned to a line result currently has a usage status of *Calibration* (which indicates that the instrument is being calibrated and might therefore not be available for use). This is a default for new test instrument tags. Choose one of the following values.
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

## Set up test instruments

Use the **Test instruments** page to define and view details about the devices that are used to perform calibration and tests on quality orders. Test instruments help quality workers know which device or tool they should use to calibrate instructions and perform other types of tests. For each test instrument that you define, you can choose whether the instrument is used for calibration, whether a test instrument tag is required, and which layout to use when printing calibration labels. Learn more in [Quality management test instruments](quality-test-instruments.md).

<!-- KFM: The original doc mentions test locations here, but never mentions them again. Should we document these?  "For additional tracking of test instrument tags, **test locations** can optionally be defined and subsequently associated to a test instrument tag. Test locations can be used to identify the location where this test instrument tag is tested." -->

## Set up calibration procedures

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

## Set up calibration groups

Use calibration groups to group test instrument tags that have similar calibration details. For example, you could have groups based on calibration schedule (monthly, bimonthly, biannually, yearly, and so on). <!-- KFM: Do the schedule settings have any actual effect, or are they just for information? -->

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
> Use the **Inventory and warehouse management parameters** page to configure how the system reacts when **Maximum usage before calibration** and **Lifetime usage maximum** values are met (you can choose to do nothing, show a warning but still allow the instrument to be used, or show an error and block the instrument from being used). Learn more in [Set up instrument calibration parameters](#set-up-instrument-calibration-parameters).

## Set up test instrument tags

The main element of this feature is the *test instrument tag*. A given test instrument type can have many test instrument tags, which uniquely defines the instrument. This form supports many details about the test instrument tag. For example, the test instrument tag will specify data such as the manufacturer, warranty number, acquisition date and specifications. The test instrument tag can also be designated for Calibration. When calibration is required, a Calibration group defines the method and calibration details regarding the test instrument tag.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags**.
1. Create or edit a test instrument tag.
1. Make the following settings for your new or selected test instrument tag.

    - **Tag number** – The Test instrument tag identification. Uniquely identifies the specific instrument.
    - **Tag description** – A brief description of the Test instrument tag. This field describes the unique test instrument tag number of the instrument type.
    - **Test instrument type** – The Test instrument for which the test instrument tag is associated with. Examples could include Scale, Thermometer, Oximeter, etc.
    - **Instrument description** – The description of the Test instrument. The description of the type of instrument.
    - **Instrument usage status** – The current status of the selected Test instrument tag. Valid values are Available, Calibration and Out of service.
    - **Check if test instrument is being calibrated** – The action to take on a quality order when the Instrument usage status of the selected test instrument tag is Calibration. Defaults from the Quality management tab of the Inventory and warehouse management parameters to new Test instrument tags but can be changed by test instrument tag. The available options are:
        - *Not allowed* – When selected, if the selected test instrument tag is being calibrated, it will not be allowed to be used on a quality order test.
        - *Warning only* – When selected, if the selected test instrument tag is being calibrated, it will be allowed to be used on a quality order test with a warning message.
        - *No check* – When selected, if the selected test instrument tag is being calibrated, it will be allowed to be used on a quality order test.
    - **Restricted use** – Indicates if the selected test instrument is for restricted use. Informational purposes only.
    - **Used for calibration** – Indicates if the selected test instrument is used in a calibration process. Note: Field is not editable; defaults from the Test instrument form. If used for calibration, then it can be entered as a Calibration tool while calibrating an instrument.

1. The **General** FastTab contains general information about the test instrument tag of the test instrument. Make the following settings here.

    - **Serial number** – The serial number of the test instrument tag manufacturer.
    - **Owner** – The owner of the test instrument tag.
    - **Acquisition date** – The date on which the test instrument tag was acquired.
    - **Fixed asset number** – Unique key for identification of fixed assets; used if the test instrument tag is tied to a fixed asset number. Informational purposes only. Could be used with reporting if desired.
    - **Customer account** – The customer account that this test instrument tag is related to. The specific test instrument tag can belong to and/or be assigned to a specific customer.
    - **Vendor account** – The vendor account that this test instrument tag is related to. The specific test instrument tag can belong to and/or be assigned to a specific vendor.
    - **Test area** – The test area that the test instrument is associated with. This field is a standard Supply Chain Management field that is being reused on this form based on standard logic.
    - **Test department** – The department that is responsible for the test instrument. A new setup table created for this feature.
    - **Test location** – The location for the specific test instrument. A new setup table created for this feature.
    - **Unit** – The Unit of measure associated with the values recorded from this test instrument. Defined on the test instrument type.
    - **Precision** – The precision of a measurement (value describes the number of digits that are used to express that value) that can be used when recording results from this test instrument. Defined on the test instrument type.

1. The **Calibration details** FastTab contains information specific to the calibration of the test instrument tag. Make the following settings here.

    - **Calibration required** – Indicates if calibration is required for the test instrument. If not selected, then the entire FastTab is not editable.
    - **Calibration procedure name** – The name of the procedure used for calibration of the test instrument.
    - **External calibrating vendor** – The account number of the external vendor used with the associated Calibration procedure. Field is not editable; defaults from the **Calibration procedures** page.
    - **External vendor name** – The name of the external vendor used with the associated Calibration procedure. Field is not editable; defaults from the **Calibration procedures** page.
    - **Calibration start date** – The date that calibration calculations should be driven from for the first calibration. For example, if the Calibration method is periodic and performed every 3 months, this date represents the 3 months from what date. This date should default to the current date for a new record and can be changed up until the point that a calibration is performed on the instrument.
    - **Usage count since last calibration** – The number of times this instrument has been used since its last calibration. This field applies only when the Calibration method is Usage and is used to determine when the next calibration is due. When the instrument is calibrated/approved, this value shall be reset to zero.
    - **Lifetime usage count** – Represents the number of times the test instrument tag has been used over its lifetime; used to determine when lifetime usage is reached. If the associated Calibration method is Usage, then this field is populated by the system but can be overridden by the Override usage data Functions ribbon action. If the associated Calibration method is Manual or Periodic, then this field will not be populated by the system but can still be changed by using the Override usage data Functions ribbon action.
    - **Calibration group** – The method in which the test instrument is calibrated. Defaults in all the details related to how this test instrument tag should be calibrated. This field is mandatory when calibration is required. Depending on the Calibration group selected, the corresponding Calibration group details will be displayed. For example, if a group with a method of Usage is selected then the Calibration group details will appear displaying the setup of the usage information.
    - **Completion assignee** – The user who is generally assigned to complete the calibration of this instrument.
    - **Approval assignee** – The user who is generally assigned to approve the calibration of this instrument.
    - **Started date** – The date when the most recent instrument calibration was started. These date fields represent a set of dates based on the last closed calibration. They are updated by the calibration process when the associated test instrument tag has a calibration that is closed.
    - **Completion date** – The date when the most recent instrument calibration was completed.
    - **Calibration result** – The result of the most recent instrument calibration.
    - **Approval date** – The date when the most recent instrument calibration was approved.
    - **Next calibration date** – The date when the next instrument calibration is scheduled. Note: This field applies only when the Calibration Method is Periodic or Manual. For manual calibration method, then this field is editable. For periodic calibration method, this field is automatically calculated using the Calibration approved date, Calibration period and Calibration period frequency. Here are a few examples:
        - If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Day(s), the Calibration Period Frequency is 10 then the Next Calibration Date will calculate to be 1/11/2013.
        - If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Month(s), the Calibration Period Frequency is 3 then the Next Calibration Date will calculate to be 4/1/2013.
        - If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Year(s), the Calibration Period Frequency is 1 then the Next Calibration Date will calculate to be 1/1/2014.
    - **Date calibration certificate printed** – The date when the Instrument calibration certificate was last printed.

1. The **Manufacturer data** FastTab contains information specific to the manufacturer of the test instrument tag. Make the following settings here.

    - **Manufacturer** – The name of the test instrument tag manufacturer. Manufacturer data is all for informational purposes only.
    - **Manufacturer part number** – The manufacturer part number of the test instrument tag.
    - **Model number** – The model number of the test instrument tag.
    - **Manufacture date** – The date when the test instrument tag was manufactured.
    - **Warranty number** – The warranty number of the test instrument tag.
    - **Warranty expiry** – The date of the expiry of the warranty on the test instrument tag.

1. The **Test procedures** FastTab contains additional specifics for the selected test instrument tag. Add additional test procedures here to support the calibration procedures as needed.

1. The **Specifications** FastTab contains additional specifications for the selected test instrument tag. Add specifications here as needed.

1. The **Notes** FastTab contains additional notes applicable to the selected test instrument tag. Add notes and other comments as needed.

The **Test instrument tags** page provides the following buttons on its Action Pane.

- **New** – Add a new Test instrument tag.
- **Delete** – Delete a Test instrument tag. You cannot delete a test instrument tag if it used on any quality orders in the system or if any calibrations have been done on it.
- **Functions** – Use the Function options to modify the calibration information of the selected test instrument tag:
    - Select **Calibrate instrument** to calibrate the selected test instrument tag.
    - Select **Reschedule calibration** to change/update the date of the next calibration of the selected test instrument tag.
    - Select **Override usage data** to change/update the values in the Usage count since last calibration and Lifetime usage count fields of the selected test instrument tag.
- **Inquiry** – Select to see the calibration history of the selected test instrument tag.
- **Update usage status** – Use this option to update the status of the selected test instrument tag:
    - Select Out of service to remove the test instrument tag from commission. The instrument will have to be calibrated before it can become available.
    - Select Available to make the instrument active. This status may indicate that the instrument was recently calibrated.
- **Print** – Select to print either a Calibration label or Calibration certificate.
- **Attachments** – Select to add/view/modify documents attached to the selected test instrument tag.

## Calibrate an instrument

To automatically create a record of the calibration of a test instrument, there is a batch job called Create calibration record that is available for the user to execute as needed. The user will have the ability to run the job based on a specific Approval date, Calibration method, test instrument tag number or several other options.

Additionally, calibration records can be created manually from the Test instrument tag or from the Calibration test instrument list page directly.

On the Calibrate test instrument list page, the user will be able to Start, Complete and Approve the calibration of a test instrument. As the test instrument tag is being calibrated, the calibration record can be updated with all the resulting details. When completing a calibration, there are three available result possibilities: Pass, Limited pass (the instrument can still be used but within a limited scope) or Fail. For failed calibrations, the user has the option to make the instrument out of service or leave it as being calibrated. For passed calibrations, the calibration record needs to be approved. E-signature can optionally be set up for the approval of the calibration record.

A completed or approved calibration can be reopened at any point and there will be a history of all reopened calibrations.

To create calibration records in batch, the **Create calibration record** job can be utilized. The job has many options available to base the calibration record creation on such as by calibration method, next calibration date, and test instrument type or usage status.

Additionally, instrument calibration records can be created manually from the Instrument **calibration list page** by using the New Calibrate instrument ribbon action. This list page also shows all calibration records already created and supports a filter that can show All, Open or Closed calibration records. The Calibrate instrument list page shows the test instrument type, test instrument tag number, who started the calibration and when, who completed the calibration and when and who approved the calibration and when. It also shows the Calibration result which will be either Open, Pass, Limited pass or Fail.

The **Test instrument calibration record detail** form allows recording of all activity to calibrate the specific test instrument tag. Use this form to set up and maintain the calibration of test instrument tags when using the Test instrument calibration functionality.

1. Go to **Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments (Detail form)**.
1. Create a new record or open an existing one for editing.
1. Make the following settings for your new or selected record.
1. The **General** FastTab contains general information about the test instrument tag for which the calibration record is created. Make the following settings here.
    - **Test instrument type** – The Test instrument that is being calibrated.
    - **Description** – The description of the Test instrument.
    - **Tag number** – The test instrument tag number of the Test instrument being calibrated.
    - **Description** – The description of the Test instrument tag.
    - **Instrument usage status** – Indicates the current status of the Test instrument tag. From this form, it is a display field and will display as Available, Calibration or Out of Service.
    - **Calibration procedure name** – The calibration procedure used on the selected calibration record. This will default from the test instrument tag but can be changed on the calibration record.
    - **Description** – The description of the calibration procedure.
    - **External calibrating vendor** – The account number of the external vendor used with the associated calibration procedure. Field is not editable; defaults from the **Calibration procedures** page.
    - **External vendor name** – The name of the external vendor used with the associated Calibration procedure. Field is not editable; defaults from the **Calibration procedures** page.
    - **Calibration procedure** – The procedures as specified on the Calibration procedure form. Field is not editable; defaults from the **Calibration procedures** page.
    - **Started by** – The user that started the calibration. This field is updated by the Start calibration action.
    - **Started date** – The date the calibration was started. This field is updated by the Start calibration action.
    - **Completion assignee** – The user responsible for assigning the user that will complete the calibration. This field defaults from the test instrument tag but can be modified.
    - **Completion by** – The user that completed the calibration. This field is updated by the Complete calibration action.
    - **Completion date** – The date the calibration was completed. This field is updated by the Complete calibration action.
    - **Calibration result** – The result of the calibration of the test instrument. This field is updated by the Complete calibration action. Valid options for this field are Open, Pass, Limited pass and Fail.
    - **Approval assignee** – The user responsible for assigning the user that will approve the calibration. This field defaults from the test instrument tag but can be modified.
    - **Approval by** – The user that approved the calibration. This field is updated by the Approve calibration action.
    - **Approval date** – The date the calibration was approved. This field is updated by the Approve calibration action.

1. The **Test procedures** FastTab contains additional procedural information for calibrating the test instrument tag for which the calibration record is created. Add additional test procedures to support the calibration of the test instrument as needed. The default information comes from the test instrument tag but can be updated during calibration.

1. The **Specifications** FastTab contains additional specifics for calibrating the test instrument tag for which the calibration record is created. Add specifications for the calibration of the test instrument as needed. The default information comes from the test instrument tag but can be updated during calibration.

1. The **Notes** FastTab contains additional notes for calibrating the test instrument tag for which the calibration record is created. Add notes for the calibration of the test instrument as needed. The default information comes from the test instrument tag but can be updated during calibration.

The **Calibrate test instruments** page provides the following buttons on its Action Pane.
  
- **New – Calibrate instrument** – Create a new calibration record. Can only create one open calibration record at a time for a given test instrument tag.
- **New – CAPA Case** – Create a new CAPA case for the selected calibration record. Automatically creates associations on the CAPA case to the test instrument tag and the calibration record.
- **Maintain – Edit** – Edit the selected calibration record. Cannot be edited once it is approved unless it is reopened.
- **Maintain – Delete** – Delete the selected calibration record.
- **Functions - Assign calibration tools** – Select to add instruments that are used in the calibration process of the test instrument for which the calibration record is created. In order for the tool to be available to assign to a calibration record, it must be marked as Use for calibration. If it requires test instrument tags, then test instrument tags will also need to be specified.
- **Functions – Start calibration** – Select to start the calibration of the test instrument for which the calibration record is created. Updates the Started by and Started Date fields on the calibration record.
- **Functions – Complete calibration** – Select to complete the calibration of the test instrument for which the calibration record is created. Updates the Completed by and Completed Date fields on the calibration record.
- **Functions – Approve calibration** – Select to approve the calibration of the test instrument for which the calibration record is created. Updates the Approved by and Approved Date fields on the calibration record.
- **Functions – Reopen calibration** – Select to reopen a completed or approved calibration record. Clears out completed and approved fields and writes a reopen calibration history record.
- **Inquiry – Calibration reopen history log** – Select to view a history of the calibration records reopened of the test instrument for which the calibration record is created.
- **Print – Calibration label** – Select to print the calibration label for the selected calibration record. The Calibration record has to either be completed or approved in order to print a Calibration label.
- **Print – Calibration certificate** – Select to print the calibration certificate for the selected calibration record. The Calibration record has to either be completed or approved in order to print a Calibration certificate.
- **Attachments** – Select to add/view/modify documents attached to the selected calibration record.

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

Test instrument calibration labels assume the use of a label printer. The calibration label layout uses ZPL code to generate the label. When printing a Calibration label, it generates ZPL code that can be immediately recognized and printed by a ZPL Printer in a specified layout or a ZPL reader can be used to view it. When choosing the ribbon action to Print Calibration label, the default destination will come from the Inventory parameters but can be modified at printing time and it supports the option to print the code to a file or to send it directly to a ZPL printer for immediate printing. This layout can be defined using the Calibration label layout setup and can support different layouts for different test instrument types. Test instrument Calibration schedule report can be printed directly from the menu path: **Inventory management** \> **Reports** \> **Quality management** \> **Test instrument calibration schedule**. The print destination supports the option to print the report to the screen or directly to a printer of your choice. This report is designed to provide a list of test instruments that need to be calibrated. However, the selection criteria provided supports many options such as by Owner or Calibration method. By using the Show all due today option, it will create a list of test instrument tags where the Next calibration due date is before today
