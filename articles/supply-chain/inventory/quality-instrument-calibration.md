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

# Instrument Calibration

Certain test instruments that are used during quality control processes need to be regularly calibrated. Calibration is the process of evaluating and adjusting the precision and accuracy of measurement equipment and is usually defined as a performance comparison against a standard of known accuracy. Proper calibration of an instrument allows people to have a safe working environment and produces valid data for future reference. Instruments that are not calibrated regularly can result in product which has incorrectly passed or failed quality control tests. This new feature adds capability around tracking individual test instrument tags, supports an on-going calibration process for the instrument tag and tracks usage of given tags against the quality order tests.

The Instrument Calibration feature found within Supply Chain Management offers enhanced quality management capability by providing robust functionality around test instrument tracking and calibration. The added functionality will give users the ability to:

- Track additional quality details related to Test instrument tags, such as Calibration groups, Test departments and Test owners.

- Track additional information on the Test instrument tag and support new actions triggered from the Test instrument tag.

- Track Test instrument type and Tag number on the quality order line and automatically assign Tag number if desired. The user can also be notified if the selected tool is not available.

- Define whether the Test instrument tag requires calibration and if so, to track additional details about the calibration such as Calibration users, Calibration dates, Calibration tools, Calibration procedure and Calibration history.

- Specify whether the Test instrument tag is to be calibrated based on Usage or Periodic schedule.

    - If the calibration takes place based on Usage, then the user can define the usage triggers. A periodic utility will evaluate if the current usage is equal to or greater than the trigger usage count and then mark the instrument for calibration and create a calibration record.

    - If the calibration takes place based on Periodic schedule, then the user can define the frequency of calibrations based on daily, monthly or yearly buckets. A schedule will be generated based on these frequencies and will populate the next calibration date field. A periodic utility will create calibration records for those instruments where the Next calibration date has been met.

- Support calibration reporting such as Calibration Certificate and Calibration Schedule Report.

- Support the ability to print Calibration labels as needed.

## Setting up Instrument Calibration

Parameters drive several components for instrument calibration. The following are the Inventory management parameters found under Quality management used by the Instrument calibration feature. The first three checks are used when processing a quality order that uses a calibrated test instrument. The system can optionally check with an error or a warning if the selected test instrument tag is currently being calibrated, if the maximum usage for the instrument tag has been exceeded and/or if the lifetime maximum usage for the instrument tag has been exceeded. If configured to do so, the system can automatically attempt to assign available test instrument tags to quality order lines when created. If not assigned automatically, they will need to be assigned manual for tests that use test instrument tags. The last four fields for the Test instrument calibration parameters are used as defaults for printing calibration labels. Calibration labels can be printed from a given test instrument tag or a given calibration record. The Calibration label will use a layout that is set as a parameter and defaulted to the test instrument type. The label can be printed to a file or to a ZPL printer. These parameters set up the default values for this data that can be overridden at printing time.

To accommodate the added functionality, the **Test instrument** form has been modified to allow the user to specify if the instrument type requires a Tag. On this standard form, there are three new fields used with instrument calibration. *Tag number required* needs to be selected to trigger additional functionality around tracking test instrument tags.*Used for calibration* indicates that this type of instrument is a tool used when calibrating. The*Calibration label layout* identifies what the Calibration label should look like when printed. To add tags to the instrument, the user will have to select the *Tag number required* field. To add tags to the instrument, the user can either click the Test instrument tags ribbon action or go to Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags.

For additional tracking of test instrument tags, **test locations** can optionally be defined and subsequently associated to a test instrument tag. Test locations can be used to identify the location where this test instrument tag is tested.

| **Path: Inventory management** \> **Setup** \> **Quality control** \> **Calibration groups** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **General** |  |  |
| Calibration group | Name of the group, used to group tags together with similar calibration details. | Monthly, Annually, Manually, 1000Usages |
| Calibration method | Select the method that determines when the instrument is calibrated. | Manual - Select this option to manually calibrate the instrument.</br>Usage - Select this option to base calibration on the use of the instrument on Quality tests.</br>Periodic - Select this option to base calibration on a specific time frame. |
| Calibration period | Select the calibration periodic frequency for the instrument.</br>Note: This field will only be active and is required when the Calibration method is Periodic | Day - Select this option to specify that the frequency specified will be based on days.</br>Month - Select this option to specify that the frequency specified will be based on months.</br>Year - Select this option to specify that the frequency specified will be based on years. |
| Calibration period frequency | The numeric frequency of when the instrument is to be calibrated.</br>Note: This field will only be active and is required when the Calibration method is Periodic. | For example, if Calibration period is Month, than a 3 in this field represents the fact that the instrument tag should be calibrated every 3 months. |
| Calibration usage update method | The usage method to be used when updating current usage of the test instrument based on the usage of the quality order test line.</br>Note: This field is only active and is required when the Calibration method is Usage. | Fixed increment - Select this option to update the usage count by the specified Usage increment each time a Quality order with the Instrument tag is validated.</br>Test quantity - Select this option to update the usage count by the specified test quantity of a Quality order test each time a Quality order with the Instrument tag is validated. |
| Usage increment | The increment by which to increase the usage count of an instrument each time it is used.</br>Note: This field is only active and is required when the Calibration method is Usage and the Calibration usage update method is Fixed increment. | For example, with a usage increment of 2, you can indicate that with every validated quality order, no matter how many units are tested, the usage count should be updated twice. |
| Usage count trigger for calibration | The numeric value used to trigger a calibration for a given instrument. The instrument can still be used until the Maximum usage before calibration is met.</br>Note: This field is only active and is required when the Calibration method is Usage. | For example, if the usage count trigger is 100, then after a given test instrument tag reaches 100 usages, when run, the periodic job to create calibration records will create one for this test instrument tag. |
| Maximum usage before calibration | The maximum number of times the instrument tag should be used before it is calibrated.</br>Note: This field is only active and is required when the Calibration method is Usage. | For example, the usage count trigger could be 100 but the maximum usage before calibration could be 125. This means that calibration could be triggered after 100 but the tag can still be used, until it reaches 125 usages. Inventory management parameter is used to determine if the quality order checks for maximum usage before calibration. |
| Lifetime usage maximum | The maximum time the instrument should be used over its lifetime.</br>Note: This field is only active when the Calibration method is Usage. | For example, the lifetime usage maximum could be 10000, which means even after it has been calibrated, the instrument tag should only be used 10000 times and then it should be marked as out of service. Inventory management parameter is used to determine if the quality order checks for lifetime usage maximum. |

When a given test instrument tag is identified as one that is calibrated, then a **calibration procedure** may be attached to the test instrument tag. The procedure provides details on exactly how the tag should be calibrated. The calibration procedure also can track if an external vendor is involved in the calibration process. This data is stored for informational purposes. Attachments can also be added to the Calibration procedure. If attachments are available, they will be transferred from the procedure to the test instrument tag to associated calibration records.

The main element of this feature revolves around the test instrument tag. A given test instrument type can have many tags, which uniquely defines the instrument. This form supports many details about the test instrument tag. For example, the tag will specify data such as the Manufacturer, Warranty number, Acquisition date and Specifications. The instrument tag can also be designated for Calibration. When calibration is required, a Calibration group defines the method and calibration details regarding the test instrument tag.

| **Path: Inventory management** \> **Setup** \> **Quality control** \> **Test instrument tags** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Main** |  |  |
| Tag number | The Test instrument tag identification. | Uniquely identifies the specific instrument. |
| Tag description | A brief description of the Test instrument tag. | This field describes the unique tag number of the instrument type. |
| Test instrument type | The Test instrument for which the tag is associated with. | Examples could include Scale, Thermometer, Oximeter, etc. |
| Instrument description | The description of the Test instrument. | The description of the type of instrument. |
| Instrument usage status | The current status of the selected Test instrument tag. | Valid values are Available, Calibration and Out of service. |
| Check if test instrument is being calibrated | The action to take on a quality order when the Instrument usage status of the selected tag is Calibration. Defaults from the Quality management tab of the Inventory and warehouse management parameters to new Test instrument tags but can be changed by test instrument tag. | The available options are:</br><ul></br><li>Not allowed - When selected, if the selected tag is being calibrated, it will not be allowed to be used on a Quality order test.<li>Warning only - When selected, if the selected tag is being calibrated, it will be allowed to be used on a Quality order test with a warning message.<li>No check - When selected, if the selected tag is being calibrated, it will be allowed to be used on a Quality order test.</ul> |
| Restricted use | Indicates if the selected test instrument is for restricted use. | Informational purposes only. |
| Used for calibration | Indicates if the selected test instrument is used in a calibration process.</br>Note: Field is not editable; defaults from the Test instrument form. | If used for calibration, then it can be entered as a Calibration tool while calibrating an instrument. |
| **FastTabs** |  |  |
| General | Contains general information about the tag of the test instrument. |  |
| Calibration details | Contains information specific to the calibration of the test instrument tag. |  |
| Manufacturer data | Contains information specific to the manufacturer of the test instrument tag. |  |
| Test procedures | Contains additional procedural information for the selected test instrument tag. |  |
| Specifications | Contains additional specifics for the selected test instrument tag. |  |
| Notes | Contains additional notes applicable to the selected test instrument tag. |  |
| **General FastTab** |  |  |
| Serial number | The serial number of the test instrument tag manufacturer. |  |
| Owner | The owner of the test instrument tag. |  |
| Acquisition date | The date on which the test instrument tag was acquired. |  |
| Fixed asset number | Unique key for identification of fixed assets; used if the test instrument tag is tied to a fixed asset number. | Informational purposes only. Could be used with reporting if desired. |
| Customer account | The customer account that this test instrument tag is related to. | The specific test instrument tag can belong to and/or be assigned to a specific customer. |
| Vendor account | The vendor account that this test instrument tag is related to. | The specific test instrument tag can belong to and/or be assigned to a specific vendor. |
| Test area | The test area that the test instrument is associated with. | This field is a standard Supply Chain Management field that is being reused on this form based on standard logic. |
| Test department | The department that is responsible for the test instrument. | A new setup table created for this feature. |
| Test location | The location for the specific test instrument. | A new setup table created for this feature. |
| Unit | The Unit of measure associated with the values recorded from this test instrument. | Defined on the test instrument type. |
| Precision | The precision of a measurement (value describes the number of digits that are used to express that value) that can be used when recording results from this test instrument. | Defined on the test instrument type. |
| **Calibration details FastTab** |  |  |
| Calibration required | Indicates if calibration is required for the test instrument. | If not selected, then the entire FastTab is not editable. |
| Calibration procedure name | The name of the procedure used for calibration of the test instrument. |  |
| External calibrating vendor | The account number of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form. |
| External vendor name | The name of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| Calibration start date | The date that calibration calculations should be driven from for the first calibration. | For example, if the Calibration method is periodic and performed every 3 months, this date represents the 3 months from what date. This date should default to the current date for a new record and can be changed up until the point that a calibration is performed on the instrument. |
| Usage count since last calibration | The number of times this instrument has been used since its last calibration. This field applies only when the Calibration method is Usage and is used to determine when the next calibration is due. | When the instrument is calibrated/ approved, this value shall be reset to zero. |
| Lifetime usage count | Represents the number of times the instrument tag has been used over its lifetime; used to determine when lifetime usage is reached. | If the associated Calibration method is Usage, then this field is populated by the system but can be overridden by the Override usage data Functions ribbon action. If the associated Calibration method is Manual or Periodic, then this field will not be populated by the system but can still be changed by using the Override usage data Functions ribbon action. |
| Calibration group | The method in which the test instrument is calibrated. Defaults in all the details related to how this test instrument tag should be calibrated. This field is mandatory when calibration is required. | Depending on the Calibration group selected, the corresponding Calibration group details will be displayed. For example, if a group with a method of Usage is selected then the Calibration group details will appear displaying the setup of the usage information |
| Completion assignee | The user who is generally assigned to complete the calibration of this instrument. |  |
| Approval assignee | The user who is generally assigned to approve the calibration of this instrument. |  |
| Started date | The date when the most recent instrument calibration was started. | These date fields represent a set of dates based on the last closed calibration. They are updated by the calibration process when the associated test instrument tag has a calibration that is closed. |
| Completion date | The date when the most recent instrument calibration was completed. |  |
| Calibration result | The result of the most recent instrument calibration. |  |
| Approval date | The date when the most recent instrument calibration was approved. |  |
| Next calibration date | The date when the next instrument calibration is scheduled.</br>Note: This field applies only when the Calibration Method is Periodic or Manual. For manual calibration method, then this field is editable. For periodic calibration method, this field is automatically calculated using the Calibration approved date, Calibration period and Calibration period frequency. | For example:</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Day(s), the Calibration Period Frequency is 10 then the Next Calibration Date will calculate to be 1/11/2013.</br>OR</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Month(s), the Calibration Period Frequency is 3 then the Next Calibration Date will calculate to be 4/1/2013.</br>OR</br>If the Last Calibration approved Date is 1/1/2013, the Calibration Period is Year(s), the Calibration Period Frequency is 1 then the Next Calibration Date will calculate to be 1/1/2014. |
| Date calibration certificate printed | The date when the Instrument calibration certificate was last printed. |  |
| **Manufacturer data FastTab** |  |  |
| Manufacturer | The name of the test instrument tag manufacturer. | Manufacturer data is all for informational purposes only. |
| Manufacturer part number | The manufacturer part number of the test instrument tag. |  |
| Model number | The model number of the test instrument tag. |  |
| Manufacture date | The date when the test instrument tag was manufactured. |  |
| Warranty number | The warranty number of the test instrument tag. |  |
| Warranty expiry | The date of the expiry of the warranty on the test instrument tag. |  |
| **Test procedures FastTab** |  |  |
| Test procedures | Used to add any additional test procedures to support the Calibration procedures. |  |
| **Specifications FastTab** |  |  |
| Specifications | Used to add any specifications to the test instrument. |  |
| **Notes FastTab** |  |  |
| Notes | Used to add any notes applicable to the test Instrument. | Specific instructions on use or other such comments could be entered here. |
| **Buttons** |  |  |
| New | Add a new Test instrument tag. |  |
| Delete | Delete a Test instrument tag. | You cannot delete a test instrument tag if it used on any quality orders in the system or if any calibrations have been done on it. |
| Functions | Use the Function options to modify the calibration information of the selected instrument tag:</br>Select Calibrate instrument to calibrate the selected test instrument tag.</br>Select Reschedule calibration to change/update the date of the next calibration of the selected instrument tag.</br>Select Override usage data to change/update the values in the Usage count since last calibration and Lifetime usage count fields of the selected instrument tag. |  |
| Inquiry | Select to see the calibration history of the selected instrument tag. |  |
| Update usage status | Use this option to update the status of the selected instrument tag:</br>Select Out of service to remove the instrument tag from commission. The instrument will have to be calibrated before it can become available.</br>Select Available to make the instrument active. This status may indicate that the instrument was recently calibrated. |  |
| Print | Select to print either a Calibration label or Calibration certificate. |  |
| Attachments | Select to add/view/modify documents attached to the selected instrument tag. |  |

## Using Instrument calibration process

To automatically create a record of the calibration of a test instrument, there is a batch job called Create calibration record that is available for the user to execute as needed. The user will have the ability to run the job based on a specific Approval date, Calibration method, Tag number or several other options.

Additionally, calibration records can be created manually from the Test instrument tag or from the Calibration test instrument list page directly.

On the Calibrate test instrument list page, the user will be able to Start, Complete and Approve the calibration of a test instrument. As the test instrument tag is being calibrated, the calibration record can be updated with all the resulting details. When completing a calibration, there are three available result possibilities: Pass, Limited pass (the instrument can still be used but within a limited scope) or Fail. For failed calibrations, the user has the option to make the instrument out of service or leave it as being calibrated. For passed calibrations, the calibration record needs to be approved. E-signature can optionally be set up for the approval of the calibration record.

A completed or approved calibration can be reopened at any point and there will be a history of all reopened calibrations.

To create calibration records in batch, the **Create calibration record** job can be utilized. The job has many options available to base the calibration record creation on such as by calibration method, next calibration date, and test instrument type or usage status.

Additionally, instrument calibration records can be created manually from the Instrument **calibration list page** by using the New Calibrate instrument ribbon action. This list page also shows all calibration records already created and supports a filter that can show All, Open or Closed calibration records. The Calibrate instrument list page shows the test instrument type, tag number, who started the calibration and when, who completed the calibration and when and who approved the calibration and when. It also shows the Calibration result which will be either Open, Pass, Limited pass or Fail.

The **Test instrument calibration record detail** form allows recording of all activity to calibrate the specific test instrument tag. Use this form to set up and maintain the calibration of test instrument tags when using the Test instrument calibration functionality.

| **Path: Inventory management** \> **Periodic** \> **Quality management** \> **Calibrate test instruments (Detail form)** |  |  |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **FastTabs** |  |  |
| General | Contains general information about the Test instrument/tag for which the calibration record is created. |  |
| Test procedures | Contains additional procedural information for calibrating the Test instrument/tag for which the calibration record is created. |  |
| Specifications | Contains additional specifics for calibrating the Test instrument/tag for which the calibration record is created. |  |
| Notes | Contains additional notes for calibrating the Test instrument/tag for which the calibration record is created. |  |
| **General FastTab** |  |  |
| Test instrument type | The Test instrument that is being calibrated. |  |
| Description | The description of the Test instrument. |  |
| Tag number | The tag number of the Test instrument being calibrated. |  |
| Description | The description of the Test instrument tag. |  |
| Instrument usage status | Indicates the current status of the Test instrument tag. | From this form, it is a display field and will display as Available, Calibration or Out of Service. |
| Calibration procedure name | The calibration procedure used on the selected calibration record. | This will default from the test instrument tag but can be changed on the calibration record. |
| Description | The description of the calibration procedure. |  |
| External calibrating vendor | The account number of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| External vendor name | The name of the external vendor used with the associated Calibration procedure. | Field is not editable; defaults from the Calibration procedures form |
| Calibration procedure | The procedures as specified on the Calibration procedure form. | Field is not editable; defaults from the Calibration procedures form |
| Started by | The user that started the calibration. | This field is updated by the Start calibration action. |
| Started date | The date the calibration was started. | This field is updated by the Start calibration action. |
| Completion assignee | The user responsible for assigning the user that will complete the calibration. | This field defaults from the test instrument tag but can be modified. |
| Completion by | The user that completed the calibration. | This field is updated by the Complete calibration action. |
| Completion date | The date the calibration was completed. | This field is updated by the Complete calibration action. |
| Calibration result | The result of the calibration of the test instrument. | This field is updated by the Complete calibration action. Valid options for this field are Open, Pass, Limited pass and Fail. |
| Approval assignee | The user responsible for assigning the user that will approve the calibration. | This field defaults from the test instrument tag but can be modified. |
| Approval by | The user that approved the calibration. | This field is updated by the Approve calibration action. |
| Approval date | The date the calibration was approved. | This field is updated by the Approve calibration action. |
| **Test procedures FastTab** |  |  |
| Test procedures | Used to add any additional test procedures to support the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Specifications FastTab** |  |  |
| Specifications | Used to add any specifications for the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Notes FastTab** |  |  |
| Notes | Used to add any notes applicable to the calibration of the test instrument. | Will default from the test instrument tag but can be updated during calibration. |
| **Buttons** |  |  |
| New – Calibrate instrument | Create a new calibration record. | Can only create one open calibration record at a time for a given test instrument tag. |
| New – CAPA Case | Create a new CAPA case for the selected calibration record. | Automatically creates associations on the CAPA case to the test instrument tag and the calibration record. |
| Maintain – Edit | Edit the selected calibration record. | Cannot be edited once it is approved unless it is reopened. |
| Maintain – Delete | Delete the selected calibration record. |  |
| Functions - Assign calibration tools | Select to add instruments that are used in the calibration process of the test instrument for which the calibration record is created. | In order for the tool to be available to assign to a calibration record, it must be marked as Use for calibration. If it requires tags, then tags will also need to be specified. |
| Functions – Start calibration | Select to start the calibration of the test instrument for which the calibration record is created. | Updates the Started by and Started Date fields on the calibration record. |
| Functions – Complete calibration | Select to complete the calibration of the test instrument for which the calibration record is created. | Updates the Completed by and Completed Date fields on the calibration record. |
| Functions – Approve calibration | Select to approve the calibration of the test instrument for which the calibration record is created. | Updates the Approved by and Approved Date fields on the calibration record. |
| Functions – Reopen calibration | Select to reopen a completed or approved calibration record. | Clears out completed and approved fields and writes a reopen calibration history record. |
| Inquiry – Calibration reopen history log | Select to view a history of the calibration records reopened of the test instrument for which the calibration record is created. |  |
| Print – Calibration label | Select to print the calibration label for the selected calibration record. | The Calibration record has to either be completed or approved in order to print a Calibration label. |
| Print – Calibration certificate | Select to print the calibration certificate for the selected calibration record. | The Calibration record has to either be completed or approved in order to print a Calibration certificate |
| Attachments | Select to add/view/modify documents attached to the selected calibration record. |  |

## Using Instrument Calibration Tags on a Quality order

The specification of a test instrument on a Quality order line has been expanded to include the selection of a test instrument tag. When a test instrument that is selected for use on a Quality order requires a tag, the Quality order cannot be validated without the selection of a tag on the quality order result line.

There is an added field in the Inventory and warehouse management parameters called Automatically assign test instrument tag number on quality order line that when selected, will sort through the tags for the instrument and select the best available tag for the quality test. If this parameter is not selected, the user will have to manually select a tag on the Quality order line or the Quality order results line when the quality order is updated.

If a tag has an Instrument usage status of Out of service, then it will not be available for selection. If the tag has an Instrument usage status of Calibration, depending on the specific of the tag, it may or may not be available for selection on the Quality test. Additionally, depending on parameter validations, the system might also optionally either warn or send an error to the user, if the chosen test instrument tag has exceeded its maximum usage and/or its lifetime usage. Also, if the chosen test instrument tag is currently being used on an open quality order, a warning message will also be provided to the user.

Once validated, if the chosen test instrument tag is calibrated based on Usage, then the usage counts on the test instrument tag are updated based on the quality order. The current usage count and the lifetime usage count will be incremented by either the test quantity or the usage increment depending on the details of the calibration group on the test instrument tag.

## Printing Calibration Reports

There are three calibration related reports provided:

- Test instrument calibration certificates

- Test instrument calibration labels

- Test instrument calibration schedule

Calibration certificates can also be generated in mass directly from the menu path: Inventory management** \> **Reports** \> **Quality management** \> **Test instrument calibration certificates. The Calibration certificates and the Calibration labels can both be printed from a test instrument tag or from a specific calibration record. If printed from the test instrument tag, they include details from the last closed calibration. If printed from a specific calibration record, it will print details from that specific calibration.

Once generated, it can be saved to a file or printed directly to a printer of your choosing. Here is an example of a Calibration certificate:

Test instrument calibration labels assume the use of a label printer. The calibration label layout uses ZPL code to generate the label. When printing a Calibration label, it generates ZPL code that can be immediately recognized and printed by a ZPL Printer in a specified layout or a ZPL reader can be used to view it. When choosing the ribbon action to Print Calibration label, the default destination will come from the Inventory parameters but can be modified at printing time and it supports the option to print the code to a file or to send it directly to a ZPL printer for immediate printing. This layout can be defined using the Calibration label layout setup and can support different layouts for different test instrument types. Test instrument Calibration schedule report can be printed directly from the menu path: Inventory management** \> **Reports** \> **Quality management** \> **Test instrument calibration schedule. The print destination supports the option to print the report to the screen or directly to a printer of your choice. This report is designed to provide a list of test instruments that need to be calibrated. However, the selection criteria provided supports many options such as by Owner or Calibration method. By using the Show all due today option, it will create a list of test instrument tags where the Next calibration due date is before today
