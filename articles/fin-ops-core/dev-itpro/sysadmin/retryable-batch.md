---
title: Enable batch retries
description: Learn about how to enable automatic retries on batch jobs and tasks when failures occur, including an overview on retrying mechanisms for batch tasks.
author: matapg007
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/18/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-05-31
---

# Enable batch retries

[!include [banner](../includes/banner.md)]

Implementation of a retry mechanism in Finance and Operations Batch is vital for maintaining robust data processing. A retry mechanism provides fault tolerance by automatically handling transient errors. Therefore, it ensures uninterrupted operation without requiring manual intervention. In addition, it enhances data integrity by reprocessing incomplete or failed transactions. Therefore, it reduces the risk of data loss. By minimizing downtime and manual intervention, a retry mechanism improves operational efficiency, so that batch processing can proceed smoothly, despite intermittent errors or disruptions.

## Retry mechanisms for batch tasks

Two types of retries can be used for batch tasks:

- **Retry for any error or batch server restart** – To configure this type of retry, adjust the retry count on the batch task through the **Batch job** page.
- **Retry for SQL transient connection errors** – You can achieve this type of retry through code, either by implementing the **BatchRetryable** interface on the batch class or by using **BatchInfo** to set the **Idempotent** attribute for the batch class.

### Retry for any error or batch server restart

You can configure this functionality through the batch job setup, by adjusting the retry count on the batch task. The **Maximum retries** parameter determines the number of retries that are attempted for a task, regardless of the error type or batch server restart. If a task fails, the batch platform evaluates the number of retries that have been performed. If the count is less than the **Maximum retries** value, the task is reset to a ready state for reprocessing. The highest allowed value for the **Maximum retries** parameter is **5**.

To set the **Maximum retries** value via the Batch user interface, follow these steps.

1. On the **Batch jobs** page, select **Batch task details**.
2. On the **General** tab, adjust the value of the **Maximum retries** field for the batch task.

> [!NOTE]
> Setting the retry count on a runtime batch task isn't supported. If you try to define this value programmatically, the platform overrides it to **0** (zero), and the runtime task isn't retried.

If your batch tasks are dynamically generated (for example, if the job is a runtime job), you can configure the **Maximum retries** value programmatically by using the **BatchInfo** or **BatchHeader** class. Here's an example.

```X++
class SampleBatchClass extends RunBaseBatch
{
    void scheduleMyBatchClass()
    {
        BatchInfo info = this.batchInfo();
        info.parmRetriesOnFailure(5);
        ...
    }
    ...
}
```

```X++
class SampleBatchClass extends RunBaseBatch
{
    void scheduleMyBatchClass()
    {
        BatchInfo info = this.batchInfo();
        BatchHeader header = batchInfo.parmBatchHeader(); 
        header.parmRetriesOnFailure(5);
        ...
    }
}
```

A **Maximum retries** value that's set by using **BatchHeader** overrides the value that's set in the batch task by using **BatchInfo**. If the **Maximum retries** parameter is set to **0** (zero), the batch task isn't retried.

### Retry for SQL transient connection errors

Currently, if finance and operations apps experience a brief loss of connection to Microsoft SQL Server, all batch tasks that are running fail. This behavior disrupts business processes. Because connection loss is inevitable in a cloud service, Microsoft enables automated retries when failures of this type occur.

> [!NOTE]
> Runtime tasks can be designated as retryable or idempotent. In the event of a SQL transient connection error, the platform automatically retries them.

There are three ways to indicate that a batch class is retryable for SQL transient connection errors:

- **Implement the BatchRetryable interface on the batch class.** The **BatchRetryable** interface has a single method, **isRetryable**, that returns a Boolean value. If the value is **True**, the batch class is retryable. If the value is **False**, the batch class isn't retryable. The **BatchRetryable** interface is available as of version 10.0.18 (with Platform update 40). The following example shows how to set **isRetryable** for a batch class.

    ```X++
    //RunBaseBatch
    class SampleBatchClass extends RunBaseBatch implements BatchRetryable
    {
        [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
        public boolean isRetryable() // Use final if you want to prevent overriding
        {
            return true; // You can also use false if you do not want to enforce retryable behavior using isRetryable
        }
        ...
    } 
    ```

    ```X++
    //SysOperationServiceController 
    class SampleBatchClass extends SysOperationServiceController implements BatchRetryable
    {
        [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
        public boolean isRetryable() // Use final if you want to prevent overriding
        {
            return true; // You can also use false if you do not want to enforce retryable behavior using isRetryable
        }
    }
    ```

- **Set an override of isRetryable in the Batch user interface.** Go to **System Administration** \> **Setup** \> **Batch class configuration overrides**, add the batch class, and set the desired value for **Is Retryable**. The value that you enter here overrides the value that's provided in code through the previous option.
- **Set the isIdempotent flag in the code of your batch class.** The following example shows how to set the **Idempotent** attribute for a batch class. The default value of **Idempotent** is **False**.

    ```X++
    //RunBaseBatch
    class SampleBatchClass extends RunBaseBatch
    {
        public void run()
        {
            this.batchInfo().parmIdempotent(true); // You can also use false if you do not want to enforce retryable behavior using Idempotent
            .....
        }
        ...
    } 
    ```

    ```X++
    //SysOperationServiceController 
    class SampleBatchClass extends SysOperationServiceController
    {
        public static SampleBatchClass construct(Args _args)
        {
            SampleBatchClass controller = new SampleBatchClass();
            controller.batchInfo().parmIdempotent(true); // You can also use false if you do not want to enforce retryable behavior using Idempotent
            ....
            return controller;
        }
        ...
    }
    ```

If a batch class is marked as either **Retryable** or **Idempotent**, it's retried in the event of a SQL transient connection error. This retry has no relation to the batch retry count on the batch task. 

The batch platform governs the maximum number of retries and the retry interval for SQL transient connection errors. Initially, retries begin after five seconds and end when the interval reaches five minutes. The interval time increases exponentially for each retry. It's five seconds for the first retry, eight seconds for the second, 16 seconds for the third, 32 seconds for the fourth, and so on.

> [!NOTE]
> For SQL transient errors, the batch platform retries the task if the exception that's thrown from the corresponding batch class is an exception of the **TransientSqlConnectionError** type, or if an exception of the **TransientSqlConnectionError** type can be wrapped as a nested exception inside a custom exception and thrown.

If there's an SQL transient connection error, the batch class is expected to throw the exact error. If the error isn't of the **TransientSqlConnectionError** type, the platform doesn't recognize the issue. Therefore, it doesn't retry the corresponding batch task.

In the following example, the batch platform can't attempt a retry.

```X++
class SampleBatchClass extends RunBaseBatch
{
    public void run()
    {
        try
        {
            this.batchInfo().parmIdempotent(true); 
            .....
        }
        catch(Exception::TransientSqlConnectionError)
        {
            error("Batch class failed to run.");
            throw Exception::Error; //Throwing a new exception
        }
    }
    ...
} 
```

Here's correct way to do it.

```X++
class SampleBatchClass extends RunBaseBatch
{
    public void run()
    {
        try
        {
            this.batchInfo().parmIdempotent(true); 
            .....
        }
        catch(Exception::TransientSqlConnectionError)
        {
            error("Batch class failed to run.");
            throw; //Throwing the same exception
        }
    }
    ...
} 
```

## Retry mechanisms for batch jobs

- All recurring batch jobs are automatically returned to the waiting state, regardless of whether they fail or succeed. This behavior ensures that recurring jobs can complete any pending work during the next run if the previous run failed. This functionality can be enabled only if the batch job's recurrence conditions are still valid. For example, the batch job must have a remaining recurrence count or a recurrence end date that hasn't passed.
- Unlike the previous option, this option isn't a direct execution retry for batch jobs themselves. It enables the customer to add custom logic before the job is retriggered. If job execution fails, this logic can listen to corresponding business events and determine whether the failure can be retried. The batch platform provides an Open Data Protocol (OData) action as of version 10.0.22 (with Platform update 46). When a batch job ID is provided in a call to the endpoint, the job is requeued for execution. For more information, see [Batch OData API](batch-odata-api.md).

## Frequently asked questions

### How can I prevent my batch task from sending multiple emails because of retries?

To prevent a batch task from sending multiple emails because of retries, you can implement a mechanism to ensure that the email is sent only once, regardless of the number of retries. Here are a few strategies that you can consider:

- **Use transactional email services.** Use transactional email services that provide features for ensuring message delivery and avoiding duplication. These services often include built-in mechanisms that prevent duplicate emails from being sent, even if the task is retried.
- **Check email status.** Before you send the email, review the status of previous email deliveries to ensure that the same email isn't sent multiple times. You can maintain a log or database table to track the status of email deliveries and prevent duplicate emails from being sent.
- **Implement idempotent email sending.** Make the email sending process idempotent, so that sending the same email multiple times has the same effect as sending it once. You can achieve this result by including a unique identifier (such as a message ID or transaction ID) in the email content. Then check for the existence of the identifier before you send the email.
- **Use a different runtime batch task to send email.** In your main batch task, initiate a new runtime batch task for sending emails. Confirm that the email was successfully sent by keeping track of the batch task's state. When the main task is retried, verify the runtime task's state to determine whether the email was already sent. If it was sent, bypass the sending process.

By implementing one or more of these strategies, you can ensure that your batch task reliably sends emails without the risk of duplicates, even if there are retries.

### I have a multi-threaded batch job where the main task is static and queues multiple runtime tasks to do the work. Because retries aren't done for runtime tasks, how can I ensure that my job is successfully completed?

The main task, which is often referred to as the controller or driver, shouldn't finish immediately after it queues the child tasks. Instead, it should continue to monitor (for example, in a loop that has a delay of 15 seconds) the progress of each child runtime task to ensure successful completion. If a runtime task fails, the controller should queue a new runtime task to try the operation again.

It's important that you manage the number of retries that the controller performs for each task. To achieve this goal, you can maintain a log of retries in a dedicated table. Alternatively, you can use the caption field to structure task identifiers so that they reflect the retry count. We recommend that you limit retries (for example, to a maximum of five attempts) to avoid excessive processing or potential issues.

### Why doesn't the batch platform retry runtime tasks for errors other than SQL transient connection errors?

The batch platform doesn't retry runtime tasks for two primary reasons:

- Runtime tasks are designed to be temporary and in-memory, and are cleared when server restart events occur. The primary reason for this design is that the driver or controller class, which is always static, handles child task retries upon restart by queuing new runtime tasks for the ones that failed. If the runtime tasks are retried, duplicate tasks might be created. As a result, mutation issues might occur, and the system might become overloaded by excessive duplicate batch tasks.
- If runtime tasks are retried, they might complicate system management and lead to unexpected behavior. The risk is especially high because the creation of extra tasks by runtime tasks can have a cascading effect.
