---
title: Process parameters
description: Learn about how to implement custom parameters in the process automation framework, including overviews and code examples for various interfaces.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/10/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Process parameters

[!include [banner](../includes/banner.md)]

In most cases, a process must store custom parameters that are specific to its processes. For example, a process might require a date range or a customer number. You must create your own user interface (UI) and custom tables to show and store these parameters. If a type doesn't have any parameters, you can skip this task.

When a user creates a series in the UI, the **Create series** wizard hosts multiple form parts, each of which contains a related set of parameters. The form parts for the process contain the UI that the user uses to enter the parameters. These form parts are built by the developer of the process and provided through type registration. A form part implements interfaces that let you initialize, validate, and write the custom parameters.

The custom parameter tables typically have two types of records:

- A template record that is bound to the series that serves as a template for all occurrences.
- A record that is specific to an occurrence and contains the parameters that will be used when that occurrence runs. Users can override the parameters for each occurrence as they require.

Parameter tables typically have one foreign key (**RecId**) to the **ProcessScheduleSeries** table and another foreign key (**RecId**) to the **ProcessScheduleOccurrence** table. The template record has a series foreign key, but it doesn't have a foreign key to the occurrence. All other records have both foreign keys.

The following interfaces are used to maintain these parameters.

## ProcessScheduleParametersIInitialize interface

The **ProcessScheduleParametersIInitialize** interface lets you initialize parameters when the user interacts with the UI of the process automation framework. The form part that is built for the wizard that shows process-specific parameters implements this interface.

## ProcessScheduleParametersIValidate interface

The **ProcessScheduleParametersIValidate** interface lets you validate the parameters that the user enters in the form part.

## ProcessScheduleParametersIWrite interface

The **ProcessScheduleParametersIWrite** interface lets you write the parameters to their custom parameter tables.

## Example

In the following example, the three interfaces that were just described are used for a sample test process. In this example, the form part contains a single string that is known as a *message*.

```xpp
[Form]
public class ProcessScheduleSampleUptakeFirstFormPart
extends ProcessScheduleParametersFormPart
implements ProcessScheduleParametersIWrite, ProcessScheduleParametersIValidate, ProcessScheduleParametersIInitialize
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
            parameters.Message = ProcessScheduleSampleUptakeParameters_Message.valueStr();
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

        if (parameters.RecId != 0)
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

Implement the **ProcessScheduleIDeleteOccurrence** interface to receive an event that indicates that a user or the system has deleted occurrences. The parameters that are related to that occurrence should be deleted.

This interface is invoked via **SysPlugIn** for a specific type. Use the type name that was created when the type was registered.

Note that a Microsoft Azure SQL Database temp table is passed in so that you can do set-based deletes.

```xpp
using System.ComponentModel.Composition;

// The VendPaymProposalAutomationOccurrenceDeleteProvider class is designed to handle
// deleting the appropriate VendPaymProposalAutomationCriteria records when ProcessScheduleOccurrence records are deleted.
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName), 'VendPaymProposalAutomation')]
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

The **ProcessScheduleIDeleteSeries** interface resembles **ProcessScheduleIDeleteOccurrence**. The event is invoked whenever a series is deleted. You should delete all parameter records for all occurrences. These records include the series template record.

A SQL Database temp table is passed in so that you can do set-based deletes.

```xpp
using System.ComponentModel.Composition;

// The VendPaymProposalAutomationSeriesDeleteProvider class is designed to handle
// deleting the appropriate VendPaymProposalAutomationCriteria records when ProcessScheduleSeries records are deleted.
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

When a user creates a new series through the UI, all the future occurrences are generated. Therefore, if the series runs every day, the process automation framework creates an occurrence for every day. This action is known as *generating the series*. The **ProcessScheduleIExplodeOccurrences** event is fired when the series is generated. The series template record should be used as a template to create parameter records for each occurrence in the parameter tables.

A SQL Database temp table is passed in so that you can do set-based creation of parameter records for optimal performance.

In the following example, a parameter table stores a single parameter that is named **Type**. This parameter isn't related to the process automation framework type but is specific to cash flow forecasting.

```xpp
using System.ComponentModel.Composition;

// Provider for cash flow forecast automation generate occurrences.
[Export(identifierStr(Dynamics.AX.Application.ProcessScheduleIExplodeOccurrences))]
[ExportMetadata(extendedTypeStr(ProcessScheduleTypeName), 'LedgerCovTotalProcessAutomation')]
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
