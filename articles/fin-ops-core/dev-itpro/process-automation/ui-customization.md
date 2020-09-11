---
# required metadata

title: Customize the user interface
description: This topic describes how to customize the user interface using the process automation framework.
author: RyanCCarlson2
manager: AnnBe
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Customize the user interface

The process automation framework supports some UI customizations. Most of this section is optional since the framework provides defaults for everything. The only exception is the **ProcessScheduleSeries** form. If you intend to display the **ProcessScheduleSeries** form for a specific product area, then customizations are required so that the framework can display data specific to the product area.

## Weekly Calendar View

### ProcessScheduleIBuildOccurrenceCard interface

This interface lets you customize the appearance of occurrence cards on the weekly calendar view. There is a static method on the interface for each status of an occurrence: **Scheduled**, **Waiting**, **Running**, **Successful**, **Failed**, and **Disabled**. You can create a customized occurrence card for each status value. Each of these methods returns an instance of **ProcessScheduleOccurrenceCard**.

The framework provides a default implementation in the class **ProcessScheduleOccurrenceCardBuilder**. You inherit from this class and override the functionality as needed. Then register your derived class via sys-plugin for your specific type in a similar manner to many of the plug-ins in the framework docs.

An instance of **ProcessScheduleOccurrenceCardBuilderContract** is passed into each of the methods and can be used to retrieve information about the occurrence. The derived class can invoke the default implementation for each of the static methods that returns the **ProcessScheduleOccurrenceCard** instance and then modify whatever is needed and return it.

### ProcessScheduleOccurrenceCard class

This class lets you customize the appearance of an occurrence card which is shown on the calendar view. The first two lines are controlled by the framework and can't be modified. The subheader is the **Completed at** phrase. The message is the status word **Completed** with the blue background.

![Default occurrence card with status and time.](media/uptake-schedule.png)

Method | Description
---|---
`public str parmSubHeader(str _subHeader = cardSubHeader)` | The subheader is the third line of the occurrence card shown in the screenshot.
`public str parmStatusMessage(str _statusMessage = statusMessage)` | The status message represents the status of the process and has a colored background.
`public ProcessExecutionOccurrenceCardStatusColor parmStatusColor(ProcessExecutionOccurrenceCardStatusColor _statusColor = statusColor)` | The color of the background which contains the status message.

### ProcessScheduleIShowOccurrenceCalendarView interface

This interface must be implemented by forms which will display the weekly calendar view. The **ProcessScheduleSeries** form is an example of a form that implements this interface.

Method | Description
---|---
`ProcessScheduleOccurrenceCalendarViewContract getProcessScheduleOccurrenceCalendarViewContract()` | Return the contract the weekly view will use to determine which types should be displayed.
`void refreshAfterChangeToCalendarView()` | This value is a callback from the weekly view indicating the parent form should refresh because of changes on the weekly calendar view.

### ProcessScheduleOccurrenceCalendarViewContract class

Use this class to restrict which series the weekly calendar view should display. For an example, see **ProcessScheduleSeries.getProcessScheduleOccurrenceCalendarViewcontract** in the AOT.

Method | Description
---|---
`public static ProcessScheduleOccurrenceCalendarViewContract construct()` | Use this constructor if the intention is to display occurrences for one to many types.
`internal static ProcessScheduleOccurrenceCalendarViewContract newFromScheduleSeries(ProcessScheduleSeries _scheduleSeries)` | Use this constructor if the intention is to display occurrences for a single series.
`public void AddScheduleType(ProcessScheduleTypeName _scheduleTypeName)` | If not displaying a single series then use this to add the types to be displayed.

### ProcessScheduleOccurrenceCalendarViewRenderer class

Use this class to render the weekly calendar view onto an existing form. A form part will be created and initialized properly. An example of this class is in use on the **ProcessScheduleSeries** form.

Method | Description
---|---
`public static ProcessScheduleICalendarView renderCalendarViewInFormControl(FormGroupControl _containingGroupControl)` | This will render the weekly calendar view within the specified form group control.

### Render interfaces

There are several interfaces that allow customization of how occurrences processes are rendered in the calendar view. One exists for each status of a process:

- **ProcessScheduleIRenderDisabledOccurrenceCard**
- **ProcessScheduleIRenderFailedOccurrenceCard**
- **ProcessScheduleIRenderRunningOccurrenceCard**
- **ProcessScheduleIRenderScheduledOccurrenceCard**
- **ProcessScheduleIRenderSuccessfulOccurrenceCard**
- **ProcessScheduleIRenderWaitingOccurrenceCard**

These interfaces all follow the same pattern. An instance of **ProcessScheduleOccurrenceCardRendering** is sent into these interfaces. This instance is used to manipulate how the occurrence card is rendered.

For an example, see the **CustVendPaymProposalAutomationOccurrenceCardRenderer** class in the AOT.

### ProcessScheduleOccurrenceCardRendering

Method | Description
---|---
`public ProcessScheduleOccurrence getOccurrenceBeingRendered()` | This method returns the occurrence being rendered in the occurrence card.
`public ProcessExecutionExecutingInformation getOccurrenceExecutionInformation()` | This method returns the running information for this occurrence. The information typically includes the results of the batch job, the start time, and the end time.
`public void makeCardSubHeaderInvisible()` | Makes the card's subheader invisible. See the screenshot above and documentation underneath it to determine which line is the subheader.
`public void makeCardButtonsInvisible()` | This value specifies whether the **Disable** and **Edit** buttons on the occurrence card invisible or not.
`public void setColumnsOnOccurrenceCardDetailGroup(int _numberOfColumns)` | Allows the number of columns on the occurrence card to be customized. The default is 2 columns.
`public FormButtonControl addButtonControl(FormControlName _buttonControlName)` | Allows a new button to be added to the occurrence card.
`public FormStaticTextControl addStaticTextControl(FormControlName _staticTextControlName)` | Allows a static text control to be added to the occurrence card.
`public FormStringControl addStringControl(FormControlName _stringControlName, LabelId _stringControlLabel)` | Adds a string control to the occurrence card.

## Series List Page

### ProcessScheduleISeriesFormController interface

The series list page uses this controller to determine which types will have their series displayed on the **ProcessScheduleSeries** list page. This class uses the **SysPlugIn** class. The menu item which the uptake teams use to launch the **ProcessScheduleSeries** form is used as the key to invoking the specified plugin. This key allows each usage of this form to customize what types are displayed.

```xpp
// Implementation of the ProcessScheduleISeriesFormController for the admin view of the process schedule series form.
// This implementation will show series for all process types, both scheduled and polled, on the series form.
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleISeriesFormController))]
[ExportMetadata(classStr(ProcessScheduleISeriesFormController), menuItemDisplayStr(ProcessScheduleSeriesAdmin))]
internal class ProcessScheduleSeriesFormAdminController implements ProcessScheduleISeriesFormController
{
    [Hookable(false)]
    public ProcessScheduleSeriesFormContract getSeriesFormContract()
    {
        return ProcessScheduleSeriesFormContract::newForAllScheduleTypes();
    }
}
```

### ProcessScheduleSeriesFormContract

This class is a contract that is used by the series list page to determine which **ProcessScheduleType** is displayed on the series list page. This could be used on a workspace to show only those series for specific types related to the work space.

Method | Description
---|---
`public void addScheduledScheduleType(ProcessScheduleTypeName _scheduleTypeName)` | Add a specific scheduled type.
`public void addPolledScheduleType(ProcessScheduleTypeName _scheduleTypeName)` | Add a specific polled type.

## Results and Messages

### ProcessExecutionIResultsController interface

This interface lets you customize the results window to our process. It lets you set the column header label for the **Header** field on the results grid and lets you make the value of the header column a hyperlink. This interface should be implemented by a class that is a plug-in. Here is a sample plug-in.

```xpp
using System.ComponentModel.Composition;

[Export(identifierStr(Dynamics.AX.Application.ProcessExecutionIResultsController))]
[ExportMetadata(classStr(ProcessExecutionIResultsController), 'TestScheduledType')]
public final class ProcessExecutionSampleUptakeExecutionResultsController implements ProcessExecutionIResultsController
{
    [Hookable(false)]
    public ProcessExecutionResultsDialogContract getResultsDialogContract()
    {
        ProcessExecutionResultsDialogContract contract = ProcessExecutionResultsDialogContract::construct();
        contract.parmSourceLinkHeaderLabel('Sample Header');
        contract.parmShouldSourceLinkHeaderBeLinkToSourceLinkDetails(true);
        return contract;
    }

    [Hookable(false)]
    public void openSourceLinkDetails(RefTableId _refTableId, RefRecId
    _refRecId)
    {
        if (_refTableId == tableNum(SystemParameters))
        {
            Args args = new Args();
            MenuFunction systemParametersMenuFunction = new MenuFunction(menuItemDisplayStr(SystemParameters), MenuItemType::Display);
            systemParametersMenuFunction.run(args);
        }
    }
}
```

Method | Description
---|---
`ProcessExecutionResultsDialogContract getResultsDialogContract()` | Return an instance of **ProcessExecutionResultsDialogContract**.
`void openSourceLinkDetails(RefTableId _refTableId, RefRecId _refRecId)` | Implement the logic to open the appropriate menu item that can display the record passed in.

### ProcessExecutionResultsDialogContract class

This class lets you customize the header column label and specify if the data in the header column should render as a hyperlink.

Method | Description
---|---
`public static ProcessExecutionResultsDialogContract newForSourceLinkHeader(LabelId _sourceLinkHeaderLabel, boolean _shouldSourceLinkHeaderBeLinkToSourceLinkDetails)` | Provide the label that will be used as a column title for the header column. Provide a Boolean value that indicates if the UI should render the value of the header column as a hyperlink.
`public LabelId parmExecutionResultsDialogCaption(LabelId _executionResultsDialogCaption = executionResultsDialogCaption)` | Sets the caption for the results dialog.

### ProcessExecutionMessageLogDialog

This interface allows the message log to be opened in the context of something from the source domain. For example, the message log could be opened from a posted vendor invoice window to show what message were logged while it was posted by a process automation framework enabled process. The posted vendor invoice window would need to implement this interface. Useing this interface saves uptake teams from having to have their own private results/messaging subsystems.

Method | Description
---|---
`ProcessExecutionMessageLogContract getContractForMessageLog()` | Returns an instance of **ProcessExecutionMessageLogContract**.

### ProcessExecutionMessageLogContract class

This contract lets you restrict the message log to a specific item from the source domain. There must be a record in **ProcessExecutionSourceLink** that has a **RefRecId** and **RefTableId** that matches what this contract sends.

Method | Description
---|---
`public static ProcessExecutionMessageLogContract newForSourceRecord(ProcessScheduleTypeName _typeName, RefTableId _refTableId, RefRecId _refRecId, guid _executionId = emptyGuid())` | Initializes the contract using the given type name, **RefTableId**, and **RefRecId**. There should be a record in **ProcessExecutionSourceLink** that matches. Background processes will have multiple execution IDs so the optional execution ID parameter should be provided for background processes. For more information, see [Type registration](type-registration.md).
