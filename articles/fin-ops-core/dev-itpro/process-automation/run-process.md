---
title: Run processes
description: This topic describes how to run processes for the process automation framework.
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

# Run processes

[!include [banner](../includes/banner.md)]

To run in the process automation framework, a process must implement the **ProcessAutomationTask** interface. The framework uses this interface to provide an instance of **ProcessScheduleWorkItem**. That instance contains information about the series, the occurrence that is being run (if applicable), and the execution ID. You must create the batch task that has to be run, and you must provide the task to the framework. The framework then creates the batch header and the tasks that are provided.

Polled processes don't have occurrences, because they might be run frequently, and those frequent runs will create many more occurrences than you want to track. Instead, you use a unique execution ID to track every run of a polled process. An execution ID is also assigned to scheduled processes.

The **getListOfWorkToBePerformed** method determines whether there is work that must be done. If there is, the method returns a list of batch-enabled classes that inherit from **SysOperationServiceController**. This method must be efficient and fast, because it's run in the context of the polling process. Therefore, you should not do any work in this method except check whether work must be done and create batch tasks for any work that must be done. It's OK if the method returns an empty list, because an empty list indicates that no work must be done. In this case, the process automation framework doesn't create any batch processes.

The process automation framework supports a list for those processes that do parallel processing and that want multiple batch tasks. If the process that is being run is an older process that implements **RunBaseBatch**, it can't be returned through the list. In this case, you have two options:

- Convert the process to **SysOperationServiceController**. For more information, see [SysOperations Framework](/dynamicsax-2012/developer/sysoperation-framework-overview). This option is recommended, if it's feasible.
- Wrap the legacy **RunBaseBatch** class with a new class that inherits from **SysOperationServiceController**. For an example, see **LedgerCovTotalProcessAutomationProcessor** in the Application Object Tree (AOT).

The following example shows an implementation of the **ProcessAutomationTask** interface.

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

The **ProcessScheduleWorkItem** class has many pieces of information and is designed to represent a process that must be run.

| Method | Description |
|---|---|
| `public ProcessExecutionId parmExecutionId(ProcessExecutionId _executionId = executionId)` | The execution ID is used to log errors. A polled process gets a new, unique execution ID every time that it's run. Because scheduled processes are only ever run one time for each occurrence, each occurrence only ever has one execution ID. |
| `public RefRecId parmProcessScheduleOccurrenceRecId(RefRecId _scheduleOccurrenceRecId = scheduleOccurrenceRecId)` | The occurrence that is being run. Use this method to reference occurrence-specific parameter information in parameter tables. Polled processes don't have a **RecId** value for an occurrence. |
| `public RefRecId parmProcessScheduleSeriesPatternRecId(RefRecId _scheduleSeriesPatternRecId = scheduleSeriesPatternRecId)` | The series pattern that the process is associated with. Currently, series can have only one pattern. All parameter records typically have a foreign key to this pattern. |
| `public ProcessScheduleProcessType parmProcessScheduleType(ProcessScheduleProcessType _scheduleType = scheduleType)` | The schedule type of the process: polled or scheduled. |
| `public ProcessScheduleTypeName parmProcessScheduleTypeName(ProcessScheduleTypeName _scheduleTypeName = scheduleTypeName)` | The type name that the process and series are associated with, such as **VendPaymentProposal**. This name is an internal developer name and isn't shown to the user. |
| `public List parmLegalEntityList(List _legalEntityList = legalEntityList)` | The list of legal entities that the process will be run against. If the process is a global process, this list will be **null**. If the process is run against a single company, this list will contain a single company. Multiple companies aren't currently supported, but they might be supported in the future. |
| `public Name getName()` | Returns the occurrence name. If a type is polled, this method returns the series name. |
| `public ProcessScheduleSeriesName parmSeriesName(ProcessScheduleSeriesName _seriesName = seriesName)` | The name of the series. |
| `public Name parmOccurrenceName(Name _occurrenceName = occurrenceName)` | The occurrence name. If the process is a polled process, the value will be empty. |
| `public List parmTaskList(List _taskList = taskList)` | The list of batch tasks that the process automation framework should add to the batch. If this list is **null**, it's assumed that no work must be done, and nothing will be created in a batch. |
| `public ProcessScheduleDateTime parmScheduledDateTime(ProcessScheduleDateTime _scheduledDateTime = scheduledDateTime)` | The date and time when the process was scheduled to run. This date and time might differ from the actual date and time when the process runs. |
| `public UserGroupId parmOwnerId(UserGroupId _ownerId = ownerId)` | The owner of the occurrence that is being run. |
| `public void initializeFromScheduleWorkItem(ProcessScheduleWorkItem _item)` | Initializes an instance of **ProcessScheduleWorkItem** from another instance. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]