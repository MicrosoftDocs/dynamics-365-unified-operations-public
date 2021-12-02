---
title: Series registration
description: This topic describes how to create a series for the process automation framework.
author: RyanCCarlson2
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Series registration

[!include [banner](../includes/banner.md)]

Every process must have a *series*. The concept of a series in process automation resembles the concept of a meeting series in Microsoft Outlook. However, a series in process automation is a series of scheduled runs of a process. For most scheduled process types, users create the series in the user interface (UI), and series registration never has to be implemented. However, if the process that is being implemented is a schedule series, you can skip this task.

Background processes typically create a series via code, by using series registration, because background processes tend to be "under the hood" processes that don't allow for user interaction. To create a series via code, you implement the **ProcessScheduleISeriesRegistration** interface. This interface contains a single method that returns an instance of **ProcessScheduleSeriesRegistrationItem**.

The process automation framework lets system admins change the default polling interval and unit for background processes.

Here is an example of a test series that is used to test the process automation framework.

```xpp
using System.ComponentModel.Composition;
// Implements the ProcessScheduleISeriesRegistration to register the vendor invoice batch posting task 'Series' with the Process Automation.
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

| Method | Description |
|---|---|
| `public ProcessScheduleTypeName parmTypeName(ProcessScheduleTypeName _typeName = typeName)` | The name of the type. |
| `public ProcessScheduleSeriesName parmSeriesName(ProcessScheduleSeriesName _SeriesName = seriesName)` | The name of the series. Be descriptive, so that the purpose of the series is clear from the name. |
| `public Description parmDescription(Description _description = description)` | The description of the series. |
| `public UserGroupId parmOwnerId(UserGroupId _ownerId = ownerId)` | The user ID of the owner of the series. |
| `public List parmProcessScheduleSeriesPatternList(List _seriesPatternList = seriesPatternList)` | The list of patterns for the series. Currently, only one pattern per series is supported. However, this limitation might change in the future. Insert an instance of the **ProcessScheduleSeriesPatternItem** class into the list. |

## ProcessScheduleSeriesPatternItem class

When the pattern is configured, applicable fields are determined based on the unit. Not all methods that are defined in the following table work for all units. The methods that apply to units are defined in the tables later in this section. Other combinations will be ignored. For polled processes, only the unit and the polling interval are used. Other fields are ignored.

| Method | Description |
|---|---|
| `public ProcessScheduleUnit parmUnit(ProcessScheduleUnit _unit = unit)` | The unit of time that the series runs in. The unit can be minutes or hours. |
| `public ProcessScheduleInterval parmPollingInterval(ProcessScheduleInterval _pollingInterval = pollingInterval)` | For polled processes, this value is an integer that, together with the unit, defines how often the process runs. |
| `public ProcessScheduleDateTime parmStartDate(ProcessScheduleDateTime _startDate = startDate)` | The start date of the series. The time should be set to the [empty time](../dev-ref/xpp-variables-data-types.md#null-values-for-data-types). |
| `public ProcessScheduleDateTime parmEndDate(ProcessScheduleDateTime _endDate = endDate)` | The end date of the series. The time should be set to the [empty time](../dev-ref/xpp-variables-data-types.md#null-values-for-data-types). |
| `public ProcessScheduleDateTime parmTime(ProcessScheduleDateTime _time = time)` | The time when the series should run. The date should be set to the [empty date](../dev-ref/xpp-variables-data-types.md#null-values-for-data-types). |

### Methods that are applicable to the week unit

| Method | Description |
|---|---|
| `public NoYes parmOnSunday(NoYes _onSunday = onSunday)` | The days of the week that you want the process to run on by selecting the appropriate methods for the day of the week. For example, **parmOnMonday()** will run the job on a Monday. |

### Methods that are applicable to the day unit

| Method | Description |
|---|---|
| `public NoYes parmDoesRepeatEveryNumberOfDays(NoYes _doesRepeatEveryNumberOfDays = doesRepeatEveryNumberOfDays)` | Indicates whether the process should run every *X* number of days. |
| `public int parmDailyRepeatInterval(int _dailyRepeatInterval = dailyRepeatInterval)` | Indicates the number of days. |
| `public NoYes parmDoesRepeatEveryWeekDay(NoYes _doesRepeatEveryWeekDay = doesRepeatEveryWeekDay)` | Indicates whether the process should run every weekday. |

### Methods that are applicable to the month unit

| Method | Description |
|---|---|
| `public NoYes parmDoesRepeatOnDayOfMonth(NoYes _doesRepeatOnDayOfMonth = doesRepeatOnDayOfMonth)` | The process should run on a specific day of every month. |
| `public Day parmMonthlyRepeatDayOfMonth(Day _monthlyRepeatDayOfMonth = monthlyRepeatDayOfMonth)` | The day of month when the process should run. |

### Modifying background processes

System admins can modify the polling interval and unit in the process automation framework. However, many background processes that currently exist have their own specific UI that is built to manage these changes. Microsoft provides a way to programmatically modify these values via the following APIs.

| Method | Description |
|---|---|
| `public static ProcessScheduleSeriesPollingDetails getPollingDetailsForSeries(ProcessScheduleTypeName _typeName, ProcessScheduleSeriesName _seriesName)` | Gets the polling interval, the unit, and the next scheduled date/time for a polled process. |
| `public static void setPollingDetailsForSeries(ProcessScheduleTypeName _typeName, ProcessScheduleSeriesName _seriesName, ProcessScheduleSeriesPollingDetails _pollingDetails)` | Enables changes to the polling interval, the unit, and the next scheduled date/time for a polled process. |

## Validating background process settings

In version 10.0.13, the process automation framework lets system admins modify background process settings via the **Edit background process** section. Some background processes have restrictions on the frequency of their runs. Microsoft has introduced an interface that a background process can implement. When this interface is invoked, it enables the background process to ensure that the unit and polling interval are within their allowed range.

The following example prevents this process from ever being run every minute or every hour. The process can run a maximum of one time per day. However, a process can implement the rules in such a way that more frequent runs are required.

```xpp
using System.ComponentModel.Composition;

// Provider to validate background settings.
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

The **ProcessScheduleISeriesValidateBackgroundDialog** interface enables background processes to validate user input when users edit background settings via **ProcessScheduleSeriesBackgroundDialog**.

| Method | Description |
|---|---|
| `boolean validateBackgroundProcessParameters(ProcessScheduleSeriesBackgroundValidationParameters _validationParameters)` | Implements any validation rules that you have for the process. |

## ProcessScheduleSeriesBackgroundValidationParameters class

The **ProcessScheduleSeriesBackgroundValidationParameters** class contains the validation parameters that are validated for the background processes that are being edited.

| Method | Description |
|---|---|
| `public UserId parmOwnerId(UserId _ownerId = ownerId)` | The owner of the process. It will be used when batch jobs are created, because batch jobs will be created under this user's context. |
| `public ProcessScheduleUnit parmUnit(ProcessScheduleUnit _unit = unit)` | The unit of time. |
| `public ProcessScheduleInterval parmPollingInterval(ProcessScheduleInterval _pollingInterval = pollingInterval)` | The polling interval. It defines the number of units of time (as specified by **parmUnit()**) that the process should be run. |
| `public ProcessScheduleDateTime parmPolledNextScheduledDateTime(ProcessScheduleDateTime _polledNextScheduledDateTime = polledNextScheduledDateTime)` | The next scheduled run of the process in Coordinated Universal Time (UTC). |
| `public ProcessScheduleDateTime parmSleepFromTime(ProcessScheduleDateTime _polledSleepFromTime = polledSleepFromTime)` | Specifies when the sleep should start. The process automation framework lets system admins put a process to sleep for a time range. The process isn't run during this time range, regardless of the setting of **parmPolledNextScheduleDateTime()**. This time range is a maximum of 16 hours and can span the date boundary. |
| `public ProcessScheduleDateTime parmSleepToTime(ProcessScheduleDateTime _polledSleepToTime = polledSleepToTime)` | Specifies when the sleep should end. The process automation framework lets system admins put a process to sleep for a time range. The process isn't run during this time range, regardless of the setting of **parmPolledNextScheduleDateTime()**. This time range is a maximum of 16 hours and can span the date boundary.  |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]