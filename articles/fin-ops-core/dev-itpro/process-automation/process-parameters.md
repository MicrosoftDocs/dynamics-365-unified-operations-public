---
# required metadata

title: Process parameters
description: This topic describes how to implement custom parameters in the process automation framework.
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

# Process parameters

Most processes have custom parameters they need to store that are specific to their processes. For example, perhaps a process needs a date range, or a customer number, etc… Teams implementing the Process Automation Framework create their own UI and custom tables to display and store these parameters. If a type doesn’t have any parameters then this section can be skipped.

When a series is created by the user in the UI, the series wizard will host N form parts for the process which contain the UI the user uses to enter the parameters. These form parts are built by the developer of the process and provided via type registration. The form part will implement interfaces which allow the developer to initialize, validate, and write their custom parameters.

These tables typically have 2 types of records. A template record that is bound to the series which serves as a template for all occurrences. The second type of record is specific to an occurrence and contains the parameters to use when executing that specific occurrence. Users can override the parameters for each occurrence as needed.

Parameter tables typically have a foreign key (RecId) to the ProcessScheduleSeries table and a foreign key (RecId) to the ProcessScheduleOccurrence table. The template record will have a series FK without a FK to the occurrence. All other records will have both.

The following interfaces are used to maintain these parameters.

## ProcessScheduleParametersIInitialize interface

This interface allows the opportunity to initialize any parameters when the user is interacting with the Process Automation Framework UI. The form part built for the wizard which displays process specific parameters implements this interface.

## ProcessScheduleParametersIValidate interface

This interface allows the developer the chance to validate the parameters the user enters on the form part.

## ProcessScheduleParametersIWrite interface

This interface allows the developer the chance to write the parameters to their custom parameter tables.

The following code sample shows the above 3 interfaces used on a sample test process. This sample form part contains a single string called a message.

```xpp
[Form]
public class ProcessScheduleSampleUptakeFirstFormPart
extends ProcessScheduleParametersFormPart
implements ProcessScheduleParametersIWrite, ProcessScheduleParametersIValidate,  ProcessScheduleParametersIInitialize
{

    private ProcessScheduleSchedulingContract schedulingContract;

    public void setSchedulingContract(ProcessScheduleSchedulingContract _schedulingContract)
    {
    schedulingContract = _schedulingContract;
    }

    public void initializeForSeriesCreate()
    {
        str text = strFmt("@ProcessAutomationFramework:ProcessScheduleSeriesTestTypeInitSeriesCreate", curExt());
        ProcessScheduleSampleUptakeParameters_Message.text(text);
    }

    public void initializeForSeriesUpdate()
    {
        ProcessScheduleSampleUptakeParameters parameters =
            ProcessScheduleSampleUptakeParameters::findForProcessScheduleSeries(schedulingContract.processScheduleSeries, true);
        ProcessScheduleSampleUptakeParameters_Message.text(parameters.Message);
    }

    public void initializeForOccurrenceCreate()
    {
        str text = strFmt("@ProcessAutomationFramework:ProcessScheduleSeriesTestTypeInitOccurrenceCreate", curExt());
        ProcessScheduleSampleUptakeParameters_Message.text(text);
    }

    public void initializeForOccurrenceUpdate()
    {
        ProcessScheduleSampleUptakeParameters parameters =
            ProcessScheduleSampleUptakeParameters::findForProcessScheduleOccurrence(schedulingContract.processScheduleOccurrence);
        ProcessScheduleSampleUptakeParameters_Message.text(parameters.Message);
    }

    public void createScheduleSeries(ProcessScheduleSchedulingContract
    _schedulingContract)
    {
        ProcessScheduleSampleUptakeParameters sampleParameters;
        sampleParameters.Message = ProcessScheduleSampleUptakeParameters_Message.valueStr();
        sampleParameters.ProcessScheduleSeries = _schedulingContract.processScheduleSeries.RecId;
        sampleParameters.insert();
    }

    public void updateScheduleSeries(ProcessScheduleSchedulingContract
    _schedulingContract)
    {
        ProcessScheduleSampleUptakeParameters parameters =
            ProcessScheduleSampleUptakeParameters::findForProcessScheduleSeries(_schedulingContract.processScheduleSeries, true);

        if (parameters)
        {
            ttsbegin;
            parameters.Message =
            ProcessScheduleSampleUptakeParameters_Message.valueStr();
            parameters.update();
            ttscommit;
        }
    }

    public void createScheduledOccurrence(ProcessScheduleSchedulingContract _schedulingContract)
    {
        ProcessScheduleSampleUptakeParameters occurrenceParameters;
        occurrenceParameters.ProcessScheduleOccurrence = _schedulingContract.processScheduleOccurrence.RecId;
        occurrenceParameters.Message = ProcessScheduleSampleUptakeParameters_Message.valueStr();
        occurrenceParameters.insert();
    }

    public void updateScheduledOccurrence(ProcessScheduleSchedulingContract
    _schedulingContract)
    {
        ProcessScheduleSampleUptakeParameters parameters =
            ProcessScheduleSampleUptakeParameters::findForProcessScheduleOccurrence(_schedulingContract.processScheduleOccurrence,
            true);

        ttsbegin;

        parameters.ProcessScheduleSeries = _schedulingContract.processScheduleSeries.RecId;
        parameters.ProcessScheduleOccurrence = _schedulingContract.processScheduleOccurrence.RecId;
        parameters.Message = ProcessScheduleSampleUptakeParameters_Message.valueStr();

        if (parameters.RecId \!= 0)
        {
            parameters.update();
        }
        else
        {
            parameters.insert();
        }

        ttscommit;
    }

    public boolean validate()
    {
      boolean isValid = true;
      if (ProcessScheduleSampleUptakeParameters_Message.valueStr() == '')
      {
          isValid = checkFailed("@ProcessAutomationFramework:ProcessScheduleSeriesTestTypeMessageWarning");
      }
      return isValid;
    }
}
```

## ProcessScheduleIDeleteOccurrence interface

Implement this interface to receive an event indicating a user or the system has deleted occurrence(s). We should delete the parameters related to that occurrence.

This interface is invoked via SysPlugIn for a specific type. Use the Type Name created when the type was registered.

Note that a SQL Database Temp table is passed in so that we can do set based deletes.

```xpp
using System.ComponentModel.Composition;

/// <summary>
/// The VendPaymProposalAutomationOccurrenceDeleteProvider class is designed to handle
/// deleting the appropriate VendPaymProposalAutomationCriteria</c> records when ProcessScheduleOccurrence records are deleted.
/// </summary>
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName),
'VendPaymProposalAutomation')]
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleIDeleteOccurrence))]
internal final class VendPaymProposalAutomationOccurrenceDeleteProvider
implements ProcessScheduleIDeleteOccurrence
{
    private ProcessScheduleSeriesOccurrenceTmp occurrencesExplodedTmp;

    [Wrappable(false)]
    public void deleteOccurrences(ProcessScheduleSeriesOccurrenceTmp _occurrencesExplodedTmp)
    {
        this.initialize(_occurrencesExplodedTmp);
        this.deleteVendPaymProposalAutomationCriteria();
    }

    private void initialize(ProcessScheduleSeriesOccurrenceTmp _occurrencesExplodedTmp)
    {
        occurrencesExplodedTmp.linkPhysicalTableInstance(_occurrencesExplodedTmp);
    }

    private void deleteVendPaymProposalAutomationCriteria()
    {
        VendPaymProposalAutomationCriteria automationCriteria;
        automationCriteria.skipDeleteActions(true);
        automationCriteria.skipDataMethods(true);
        automationCriteria.skipAosValidation(true);
        automationCriteria.skipDatabaseLog(true);
        automationCriteria.skipEvents(true);

        delete_from automationCriteria
            exists join occurrencesExplodedTmp
            where automationCriteria.ProcessScheduleOccurrence == occurrencesExplodedTmp.ProcessScheduleOccurrence;
    }
}
```

## ProcessScheduleIDeleteSeries interface

Similar to ProcessScheduleIDeleteOccurrence only this event is invoked whenever a series is deleted. We should delete all parameter records for all occurrences including the series template record.

Note that a SQL Database Temp table is passed in so that we can do set based deletes.

```xpp
using System.ComponentModel.Composition;

/// <summary>
/// The VendPaymProposalAutomationSeriesDeleteProvider class is designed to handle
/// deleting the appropriate VendPaymProposalAutomationCriteria records when ProcessScheduleSeries records are deleted.
/// </summary>
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName), 'VendPaymProposalAutomation')]
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleIDeleteSeries))]
internal final class VendPaymProposalAutomationSeriesDeleteProvider
implements ProcessScheduleIDeleteSeries
{

    [Wrappable(false)]
    public void deleteSeries(RefRecId _seriesRecId)
    {
        this.deleteVendPaymProposalAutomationCriteria(_seriesRecId);
    }

    private void deleteVendPaymProposalAutomationCriteria(RefRecId _seriesRecId)
    {
        VendPaymProposalAutomationCriteria automationCriteria;
        automationCriteria.skipDeleteActions(true);
        automationCriteria.skipDataMethods(true);
        automationCriteria.skipAosValidation(true);
        automationCriteria.skipDatabaseLog(true);
        automationCriteria.skipEvents(true);

        delete_from automationCriteria
            where automationCriteria.ProcessScheduleSeries == _seriesRecId;
    }
}
```

## ProcessScheduleIExplodeOccurrences interface

When a user creates a new series via the UI we ‘explode’ all the future occurrences. This means that if the series is a series executing every day then under the hood we will create an occurrence for every day. This is called exploding the series. When we explode the series this event fires. Parameter records for each occurrence should be created in the parameter tables using the series template record as a template.

Note that a SQL Database Temp table is passed in so that we can do set creation of parameter records for optimal performance.

The example below has a parameter table storing a single parameter named Type which is not related to the process automation framework type but is instead specific to cash flow forecasting:

```xpp
using System.ComponentModel.Composition;

/// <summary>
/// Provider for cash flow forecast automation explode occurrences.
/// </summary>
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleIExplodeOccurrences))]
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName),
'LedgerCovTotalProcessAutomation')]
internal final class LedgerCovTotalProcessAutomationExplodeOccurrencesProvider 
implements ProcessScheduleIExplodeOccurrences
{
    private void new()
    {
    }

    [Wrappable(false)]
    public void explodeOccurrences(ProcessScheduleSeriesOccurrenceTmp _occurrencesExplodedTmp)
    {
        LedgerCovTotalProcessAutomationSchedulingParameters parameters;
        LedgerCovTotalProcessAutomationSchedulingParameters
        parametersSeriesRecord;

        insert_recordset parameters
        (
            Type,
            ProcessScheduleSeries,
            ProcessScheduleOccurrence
        )

        select Type, ProcessScheduleSeries from parametersSeriesRecord
            where parametersSeriesRecord.ProcessScheduleOccurrence == 0
            join ProcessScheduleOccurrence from _occurrencesExplodedTmp
            where _occurrencesExplodedTmp.ProcessScheduleSeries == parametersSeriesRecord.ProcessScheduleSeries
                && _occurrencesExplodedTmp.TypeName == LedgerCovTotalProcessAutomationConstants::RegisteredTypeName;
    }
}
```
