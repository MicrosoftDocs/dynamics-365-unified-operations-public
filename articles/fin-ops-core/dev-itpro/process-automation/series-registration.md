---
# required metadata

title: Series registration
description: This topic describes how to create a series for the process automation framework.
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

# Series registration

Every process must have a series. A series is similar in concept to a meeting series in outlook only our series are series of scheduled executions of a process. Most Scheduled process types have their series created in the UI by end users and never need to implement series registration. If the process being implemented is a schedule series then skip this section.

Background processes typically create a series via code using series registration as background processes tend to be “under the hood” processes that don’t allow user interaction. To create a series via code implement the ProcessScheduleISeriesRegistration interface. This contains a single method returning an instance of ProcessScheduleSeriesRegistrationItem.

The process automation framework allows system administrators to change the default polling interval and unit for background processes.

Here is an example of a test series used to test the framework:

```xpp
using System.ComponentModel.Composition;
/// <summary>
/// Implements the <c>ProcessScheduleISeriesRegistration</c> to
register the vendor invoice batch posting task 'Series' with the Process
Automation.
/// </summary>
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleISeriesRegistration))]
[ExportMetadata(classStr(ProcessScheduleISeriesRegistration), classStr(VendInvoicePostProcessScheduleSeriesRegistration))]
internal final class VendInvoicePostProcessScheduleSeriesRegistration implements ProcessScheduleISeriesRegistration
{

    [Hookable(false)]
    public ProcessScheduleSeriesRegistrationItem
    getProcessScheduleSeriesRegistrationItem()
    {
        ProcessScheduleSeriesRegistrationItem
        processScheduleSeriesRegistrationItem =
        ProcessScheduleSeriesRegistrationItem::construct();
        processScheduleSeriesRegistrationItem.parmDescription("@AccountsPayable:VendInvoicePostTaskFeatureSummary");
        processScheduleSeriesRegistrationItem.parmOwnerId(curUserId());
        processScheduleSeriesRegistrationItem.parmProcessScheduleSeriesPatternList(this.getSeriesPatternList());
        processScheduleSeriesRegistrationItem.parmSeriesName("@AccountsPayable:VendInvoicePostTaskFeatureLabel");
        processScheduleSeriesRegistrationItem.parmTypeName(VendInvoicePostTaskConstants::VendorInvoiceBatchPosting);
        return processScheduleSeriesRegistrationItem;
        }

    private List getSeriesPatternList()
    {
        ProcessScheduleSeriesPatternItem processScheduleSeriesPatternItem =
        ProcessScheduleSeriesPatternItem::construct();
        processScheduleSeriesPatternItem.parmUnit(ProcessScheduleUnit::Minute);
        processScheduleSeriesPatternItem.parmPollingInterval(VendParameters::pollingIntervalMinutes());
        List list = new List(Types::Class);
        list.addEnd(processScheduleSeriesPatternItem);
        return list;
    }
}
```

## ProcessScheduleSeriesRegistrationItem class

Method | Description
---|---
`public ProcessScheduleTypeName parmTypeName(ProcessScheduleTypeName _typeName = typeName)` | This is the name of the type.
`public ProcessScheduleSeriesName parmSeriesName(ProcessScheduleSeriesName _SeriesName = seriesName)` |This is the name of the series. Be descriptive so it's easy to understand the purpose of the series from the name.
`public Description parmDescription(Description _description = description)` | This is a description of the series.
`public UserGroupId parmOwnerId(UserGroupId _ownerId = ownerId)` | This is the user ID that is the owner of the series.
`public List parmProcessScheduleSeriesPatternList(List _seriesPatternList = seriesPatternList)` | This is the list of patterns for this series. Note: At present we only support one pattern per series. This may change in the future. Insert into the list an instance of the class ProcessScheduleSeriesPatternItem.

## ProcessScheduleSeriesPatternItem class

When configuring the pattern applicable fields are determined based on the Unit. Not all methods defined below work for all units. The methods that apply to units are defined below. Other combinations will be ignored. For polled processes only unit and the polling interval are used. All other fields are ignored.

Method | Description
---|---
`public ProcessScheduleUnit parmUnit(ProcessScheduleUnit _unit = unit)` | The unit of time this series runs which maybe in minutes, or hours.
`public ProcessScheduleInterval parmPollingInterval(ProcessScheduleInterval _pollingInterval = pollingInterval)` | For polled processes this is the how often the process gets run within the context of the unit. It's an integer which combined with the unit will define how often the process runs.
`public ProcessScheduleDateTime parmStartDate(ProcessScheduleDateTime _startDate = startDate)` |  Indicates the start date of the series. The time should be the empty time.
`public ProcessScheduleDateTime parmEndDate(ProcessScheduleDateTime _endDate = endDate)` | Indicates the end date of the series. The time should be the empty time.
`public ProcessScheduleDateTime parmTime(ProcessScheduleDateTime _time = time)` | Indicates the time the series should run. The date should be set to the empty date.

### Methods applicable to the unit week

Method | Description
---|---
`public NoYes parmOnSunday(NoYes _onSunday = onSunday)' | Indicate which day(s) of the week you would like the process to run on by selecting the appropriate methods for the day of the week. For example, parmOnMonday() will execute the job on a Monday.

### Methods applicable to the unit day

Method | Description
---|---
`public NoYes parmDoesRepeatEveryNumberOfDays(NoYes _doesRepeatEveryNumberOfDays = doesRepeatEveryNumberOfDays)` | Indicates if the process should be run every X number of days.
`public int parmDailyRepeatInterval(int _dailyRepeatInterval = dailyRepeatInterval)` | Indicate the number of days
`public NoYes parmDoesRepeatEveryWeekDay(NoYes _doesRepeatEveryWeekDay = doesRepeatEveryWeekDay)` |  Indicates if the process should be run every weekday.

### Methods applicable to unit month

Method | Description
---|---
`public NoYes parmDoesRepeatOnDayOfMonth(NoYes _doesRepeatOnDayOfMonth = doesRepeatOnDayOfMonth)` | Indicates the process should run on a specific day of every month.
`public Day parmMonthlyRepeatDayOfMonth(Day _monthlyRepeatDayOfMonth = monthlyRepeatDayOfMonth)` | The day of month the process should run on.

### Modifying Background Processes

The polling interval and unit can be modified in the process automation framework by system administrators. However, many background process that exist today have their own specific UI built to manage this. We provide away to update these values programmatically via these APIs:

Method | Description
---|---
`public static ProcessScheduleSeriesPollingDetails getPollingDetailsForSeries(ProcessScheduleTypeName _typeName, ProcessScheduleSeriesName _seriesName)` | Gets the polling interval, the unit, and the next scheduled date time for a polled process.
`public static void setPollingDetailsForSeries(ProcessScheduleTypeName _typeName, ProcessScheduleSeriesName _seriesName, ProcessScheduleSeriesPollingDetails _pollingDetails)` | Allows the polling interval, the unit, and the next scheduled date time for a polled process to be modified.

## Validating Background dialog 

The process automation framework in 10.0.13 allows system administrators to modify background process settings via the background dialog. Some background processes have restrictions on how often they want to run. We have introduced an interface a background process can implement which gets invoked and allows the background process to ensure that the unit and polling interval are within their allowed range.

Here is an example that prevents this process from ever being run every minute or every hour. Once a day is the most frequent this process allows. However, a process could implement the rules such that more frequent execution is required.

```xpp
using System.ComponentModel.Composition;
/// <summary>
/// Provider to validate background settings.
/// </summary>
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleISeriesValidateBackgroundDialog))]
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName), 'ProcessAutomationExploder')]
internal final class ProcessScheduleExplodeAutomationBackgroundDialogValidationProvider implements ProcessScheduleISeriesValidateBackgroundDialog
{

    public boolean
    validateBackgroundProcessParameters(ProcessScheduleSeriesBackgroundValidationParameters
    _validationParameters)
    {
        ProcessScheduleUnit currentUnit = _validationParameters.parmUnit();
        if (currentUnit == ProcessScheduleUnit::Minute || currentUnit == ProcessScheduleUnit::Hour)
        {
            SysDictEnum enum = new SysDictEnum(enumNum(ProcessScheduleUnit));
            throw Error(
                strFmt("@ProcessAutomationFramework:ProcessScheduleExplodeProcessInvalidUnit",
                enum.value2Label(ProcessScheduleUnit::Minute),
                enum.value2Label(ProcessScheduleUnit::Hour)));
        }
        return true;
    }
}
```

## ProcessScheduleISeriesValidateBackgroundDialog interface

This interface allows background processes to validate user input when background settings are edited by the user via the **ProcessScheduleSeriesBackgroundDialog**.

Method | Description
---|---
`boolean validateBackgroundProcessParameters(ProcessScheduleSeriesBackgroundValidationParameters _validationParameters)` | Implement any validation rules for the process in this method.

## ProcessScheduleSeriesBackgroundValidationParameters class

This class contains the validation parameters being validated for the background processes being edited.

Method | Description
---|---
`public UserId parmOwnerId(UserId _ownerId = ownerId)` | The owner of the process. This will be used when creating batch jobs as the batch jobs will be created under this users context.
`public ProcessScheduleUnit parmUnit(ProcessScheduleUnit _unit = unit)` | The unit of time.
`public ProcessScheduleInterval parmPollingInterval(ProcessScheduleInterval _pollingInterval = pollingInterval)` | The polling interval. This is how many units of time specified by parmUnit() above this processes should be executed.
`public ProcessScheduleDateTime parmPolledNextScheduledDateTime(ProcessScheduleDateTime _polledNextScheduledDateTime = polledNextScheduledDateTime)` | This is the next scheduled execution of the process in UTC.
`public ProcessScheduleDateTime parmSleepFromTime(ProcessScheduleDateTime _polledSleepFromTime = polledSleepFromTime)` | The framework allows system administrators to put a process to sleep for a time range. The process won't get executed during this time range regardless of what the parmPolledNextScheduleDateTime() is set to. This time range is a maximum of 16 hours. This 16 hour time range may span the date boundary. This is the from time.
`public ProcessScheduleDateTime parmSleepToTime(ProcessScheduleDateTime _polledSleepToTime = polledSleepToTime)` | The framework allows system administrators to put a process to sleep for a time range. The process won't get executed during this time range regardless of what the parmPolledNextScheduleDateTime() is set to. This time range is a maximum of 16 hours. This 16 hour time range may span the date boundary. This is the to time.
