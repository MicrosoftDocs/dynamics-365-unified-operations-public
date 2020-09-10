# Process execution

In order for the Process Automation Framework to execute the process we must implement the ProcessAutomationTask interface. This is mandatory. The Process Automation Framework via this interface will provide us with an instance of ProcessScheduleWorkItem which contains information concerning the series and an occurrence if applicable that is being
executed and the Execution Id. We will create the batch task that need to be run and provide them to the Process Automation Framework. The Process Automation Framework creates the batch header and the tasks provided.

Polled processes do not have occurrences because they may get executed very frequently and that would create far more occurrences then we want to track so we use a unique execution Id to track every execution of a polled process. Scheduled processes are also assigned an execution Id.

The method getListOfWorkToBePerformed() decides if there is work to be done. If there is, it returns a list of batch enabled classes inheriting from SysOperationServiceController. (Batch tasks). This method must be very efficient and very fast because it is executed in the context of the polling process therefore we should not do any work in this method beyond checking if there is work to be done and, if there is, creating batch tasks. It is ok to return an empty list as that signifies there is no work to be done. In this case we will not create any batch processes.

We support a list for those processes that do parallel processing and want multiple batch tasks. If the process being executed is an older process that implements RunBaseBatch then it can’t be returned via the list. Two options exist in this case:

1. Convert the process to SysOperationServiceController. See this link for more information regarding the [SysOperations Framework](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/sysoperation-framework-overview).
2. Wrap the legacy RunBaseBatch class with a new class inheriting from SysOperationServiceController. See the class LedgerCovTotalProcessAutomationProcessor as an example of how to do this.

It is preferrable to follow option 1 if feasible.

Here is an example of implementing the ProcessAutomationTask interface.

```xpp
using System.ComponentModel.Composition;

/// <summary>
/// The test class to test the process automation task engine.
/// </summary>
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

    /// <summary>
    /// Gets and sets the batch job caption that will be used by the batch job scheduled to execute this process.
    /// </summary>
    /// <returns>Batch caption that will be used for the batch job that will perform the task.</returns>
    protected BatchCaption batchJobCaption()
    {
        return "@ProcessAutomationFramework:ProcessScheduleExplodeProcessLabel";
    }
}
```

## ProcessScheduleWorkItem class

This class has many pieces of information and is designed to represent a process that is to be executed. The intent of this class is to provide uptake teams with this information.

Method | Description
---|---
`public ProcessExecutionId parmExecutionId(ProcessExecutionId _executionId = executionId)` | Polled process will get a new unique Execution Id every time they are executed. Scheduled processes are only ever run once for each occurrence so each occurrence will only ever have one execution Id. The execution Id is used for logging errors.
`public RefRecId parmProcessScheduleOccurrenceRecId(RefRecId _scheduleOccurrenceRecId = scheduleOccurrenceRecId)` | The occurrence that is being executed. Use this to reference occurrence specific parameter information in parameter tables. Polled processes will not have an occurrence RecId.
`public RefRecId parmProcessScheduleSeriesPatternRecId(RefRecId _scheduleSeriesPatternRecId = scheduleSeriesPatternRecId)` | The series pattern this process is associated with. Series currently can have only 1 pattern. All parameter records typically have a FK to this pattern.
`public ProcessScheduleProcessType parmProcessScheduleType(ProcessScheduleProcessType _scheduleType = scheduleType)` | The schedule type of this process – Polled or Scheduled.
`public ProcessScheduleTypeName parmProcessScheduleTypeName(ProcessScheduleTypeName _scheduleTypeName = scheduleTypeName)` | The type name this process and series is associated with. This is an internal developer name and not displayable to the user. (e.g. “VendPaymentProposal”)
`public List parmLegalEntityList(List _legalEntityList = legalEntityList)` | The list of legal entities this process will be run against. If the process is a global process then this list will be null. If single company then this list will contain a single company. We currently don’t support multi-company but plan to in the future.
`public Name getName()` | Returns the occurrence name or if a polled type then the series name.
`public ProcessScheduleSeriesName parmSeriesName(ProcessScheduleSeriesName _seriesName = seriesName)` | Gets the name of the series.
`public Name parmOccurrenceName(Name _occurrenceName = occurrenceName)` | Gets the occurrence name. This will be empty if the process is a polled process.
`public List parmTaskList(List _taskList = taskList)` | The list of batch tasks for the framework to add to batch. If this list is null then it will be assumed there is no work to be done and nothing will be created in batch.
`public ProcessScheduleDateTime parmScheduledDateTime(ProcessScheduleDateTime _scheduledDateTime = scheduledDateTime)` | The date and time the process was scheduled to run. This may differ from the actual date and time the process was run.
`public UserGroupId parmOwnerId(UserGroupId _ownerId = ownerId)` | The owner of the occurrence being executed.
`public void initializeFromScheduleWorkItem(ProcessScheduleWorkItem _item)` | Initializes an instance of ProcessScheduleWorkItem from another instance.
