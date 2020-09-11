---
# required metadata

title: Run the process
description: This topic describes how to run processes for the process automation framework.
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

# Run the process

For a process to run in the process automation framework, the process must implement the **ProcessAutomationTask** interface. The framework, by using this interface, provides an instance of **ProcessScheduleWorkItem**. The instance contains information about the series, the occurrence (if applicable) that is being run, and the execution ID. You must create the batch task that needs to be run and provide the task to the framework. The framework creates the batch header and the tasks provided.

Polled processes don't have occurrences because they might be frequently run and that would create far more occurrences than you want to track. Instead, you use a unique execution ID to track every run of the polled process. Scheduled processes are also assigned an execution ID.

The **getListOfWorkToBePerformed** method determines if there is work to be done. If there is, it returns a list of batch enabled classes inheriting from **SysOperationServiceController**. This method must be efficient and fast because it's run in the context of the polling process. Therefore you shouldn't do any work in this method beyond checking if work to be done and, if there is, creating batch tasks. It's ok to return an empty list as that signifies no work to be done. In this case, the framework doesn't create any batch processes.

The framework supports a list for those processes that do parallel processing and want multiple batch tasks. If the process being run is an older process that implements **RunBaseBatch**, then it can’t be returned through the list. Two options exist in this case:

- Convert the process to **SysOperationServiceController**. For more information, see [SysOperations Framework](https://docs.microsoft.com/dynamicsax-2012/developer/sysoperation-framework-overview). This option is preferred, if it's feasible.
- Wrap the legacy **RunBaseBatch** class with a new class inheriting from **SysOperationServiceController**. For an example, check the **LedgerCovTotalProcessAutomationProcessor** in the AOT.

Here is an example of implementing the **ProcessAutomationTask** interface.

```xpp
using System.ComponentModel.Composition;

// The test class to test the process automation task engine.
[ExportMetadataAttribute(classStr(ProcessAutomationTask), classStr(ProcessAutomationTaskTestImplementation))]
[ExportAttribute(identifierStr('Microsoft.Dynamics.AX.Application.ProcessAutomationTask'))]
internal final class ProcessAutomationTaskTestImplementation extends ProcessAutomationTask
{

    protected boolean isProcessAutomationEnabledForThisTask()
    {
        return true;
    }

    protected List getListOfWorkToBePerformed()
    {
        ProcessScheduleWorkItem scheduleWorkItemToExecute = this.parmProcessScheduleWorkItem();
        List taskList = new List(Types::Class);
        ProcessAutomationTestProcess testProcess = ProcessAutomationTestProcess::construct(scheduleWorkItemToExecute);
        taskList.addEnd(testProcess);
        return taskList;
    }

    // Gets and sets the batch job caption that will be used by the batch job scheduled to run this process.
    // Returns the batch caption that will be used for the batch job that will perform the task.
    protected BatchCaption batchJobCaption()
    {
        return "@ProcessAutomationFramework:ProcessScheduleExplodeProcessLabel";
    }
}
```

## ProcessScheduleWorkItem class

This class has many pieces of information and is designed to represent a process that is to be run. The intent of this class is to provide uptake teams with this information.

Method | Description
---|---
`public ProcessExecutionId parmExecutionId(ProcessExecutionId _executionId = executionId)` | A polled process gets a new unique Execution ID every time it is run. Scheduled processes are only ever run once for each occurrence so each occurrence will only ever have one execution ID. The execution ID is used for logging errors.
`public RefRecId parmProcessScheduleOccurrenceRecId(RefRecId _scheduleOccurrenceRecId = scheduleOccurrenceRecId)` | The occurrence that is being run. Use this method to reference occurrence-specific parameter information in parameter tables. Polled processes won't have an occurrence RecId.
`public RefRecId parmProcessScheduleSeriesPatternRecId(RefRecId _scheduleSeriesPatternRecId = scheduleSeriesPatternRecId)` | The series pattern this process is associated with. Series currently can have only one pattern. All parameter records typically have a foreign key to this pattern.
`public ProcessScheduleProcessType parmProcessScheduleType(ProcessScheduleProcessType _scheduleType = scheduleType)` | The schedule type of this process - polled or scheduled.
`public ProcessScheduleTypeName parmProcessScheduleTypeName(ProcessScheduleTypeName _scheduleTypeName = scheduleTypeName)` | The type name that this process and series is associated with. This name is an internal developer name and it isn't displayed to the user. For example, **VendPaymentProposal**.
`public List parmLegalEntityList(List _legalEntityList = legalEntityList)` | The list of legal entities this process will be run against. If the process is a global process, then this list will be **null**. If single company then this list will contain a single company. Multi-company isn't supported, but might be in the future.
`public Name getName()` | Returns the occurrence name. If a type is polled, it returns the series name.
`public ProcessScheduleSeriesName parmSeriesName(ProcessScheduleSeriesName _seriesName = seriesName)` | Gets the name of the series.
`public Name parmOccurrenceName(Name _occurrenceName = occurrenceName)` | Gets the occurrence name. This value will be empty if the process is a polled process.
`public List parmTaskList(List _taskList = taskList)` | The list of batch tasks for the framework to add to batch. If this list is **null**, then it will be assumed  no work to be done and nothing will be created in batch.
`public ProcessScheduleDateTime parmScheduledDateTime(ProcessScheduleDateTime _scheduledDateTime = scheduledDateTime)` | The date and time the process was scheduled to run. The date and time might differ from the actual date and time the process runs.
`public UserGroupId parmOwnerId(UserGroupId _ownerId = ownerId)` | The owner of the occurrence being run.
`public void initializeFromScheduleWorkItem(ProcessScheduleWorkItem _item)` | Initializes an instance of **ProcessScheduleWorkItem** from another instance.
