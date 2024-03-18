---
# required metadata

title: Enable batch retries
description: This article describes how to enable automatic retries on batch jobs & tasks when failures occur.
author: matapg007
ms.date: 06/16/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2021-05-31

---

# Enable batch retries

[!include [banner](../includes/banner.md)]

Implementing a retry mechanism in Finance and Operations Batch is vital for maintaining robust data processing. It provides fault tolerance by automatically handling transient errors, ensuring uninterrupted operation without manual intervention. It enhances data integrity by reprocessing incomplete or failed transactions, reducing the risk of data loss. By minimizing downtime and manual intervention, retry mechanisms improve operational efficiency, enabling batch processing to proceed smoothly despite intermittent errors or disruptions.

## Retry Mechanisms for Batch Tasks

There are two distinct types of retries that can be used for batch tasks:

- **Retry for any error or Batch Server restart**: It can be configured via the Batch Job form by adjusting the retry count on the Batch Task.
- **Retry for SQL transient connection errors**: It can be achieved through code either by implementing the **BatchRetryable** interface on the Batch class or by setting the Batch Class **Idempotent** attribute using **BatchInfo**.

### Retry for any error or Batch Server restart 
 
This functionality is configurable through the Batch Job Setup by adjusting the retry count on the Batch Task. The **Maximum retries** parameter determines the number of retries that would be attempted for a task, irrespective of the error type or Batch Server restart. If a task fails, the batch platform evaluates the number of retries performed. If the count is below the specified "Maximum retries," the task is reset to a ready state for reprocessing. The highest allowed value for **Maximum retries** is 5.

   To set this value via the Batch user interface, follow these steps:
   1. From **Batch jobs** page and select **Batch task details**.
   2. Go to the **General** tab, and adjust the **Maximum retries** field for the batch task.

> [!NOTE]
> Setting the retry count on a Runtime Batch Task is not supported. If you attempt to define this value programmatically, the platform will override it to zero, and the runtime task will not be retried. 

   If your batch tasks are dynamically generated, such as if it's a runtime job, you can configure this value programmatically using the **BatchInfo** class or **BatchHeader** class. For example:

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

When you set the **Maximum retries** parameter, using **BatchHeader** then it overrides the value set in the Batch Task using **BatchInfo**. If the **Maximum retries** parameter is set to 0, the batch task shall not be retried.

### Retry for SQL transient connection errors

Currently, if finance and operations apps experience a brief loss of connection to Microsoft SQL Server, all batch tasks that are running fail. This behavior disrupts business processes. Because connection loss is inevitable in a cloud service, Microsoft enables automated retries when failures of this type occur.

> [!NOTE]
> Runtime tasks can be designated as retryable or idempotent. In the event of a SQL transient connection error, the platform will automatically retry them.


There are three ways to indicate that a batch class is retryable for SQL transient connection errors:

1. By implementing the **BatchRetryable** interface on the batch class. This interface has a single method, **isRetryable**, which returns a Boolean value. If the value is **True**, the batch class is retryable. If the value is **False**, the batch class isn't retryable. The **BatchRetryable** interface is available from version 10.0.18 (with Platform update 40). Here's code sample to set isRetryable to a Batch Class. 
```X++
//RunBaseBatch
class SampleBatchClass extends RunBaseBatch implements BatchRetryable
{
    [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
    public boolean isRetryable() // Use final if you want to prevent overriding
    {
        return true; // You can also use fasle if you do not want to enforce retryable behavior using isRetryable
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
        return true; // You can also use fasle if you do not want to enforce retryable behavior using isRetryable
    }
}
```

2. By setting override of **isRetryable** in Batch user interface. To do it, you have to navigate to **System Administration > Setup > Batch class configuration overrides** and add the batch class and desired value of Is Retryable. The value entered here shall override for the value provided in code by option 1.

3. By setting **isIdempotent** flag in code of your batch class. Here's code sample to set idempotent to a Batch Class. The default value of idempotent is **False**. 

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

Either batch class is marked Retryable or Idempotent, we retry it for SQL Transient connection error and it has no relation to Batch retry count on Batch Task. 

The batch platform governs the maximum number of retries and the retry interval for SQL transient connection errors. Initially, retries begin after five seconds and cease when the interval reaches five minutes. The interval time increases exponentially with each retry: starting at 5 seconds, then 8 seconds, 16 seconds, 32 seconds, and so forth.

> [!NOTE]
> For SQL transient errors, the batch platform will retry the task if the exception that is thrown from the respective batch class is an exception of the **TransientSqlConnectionError** type, or if **TransientSqlConnectionError** can be wrapped as a nested exception inside a custom exception and thrown.

To ensure that if there's an SQL Transient connection error, we expect the batch class to throw the exact error. If the error isn't of type **TransientSqlConnectionError**, the platform wouldn't recognize the issue, and so, it shall not retry the corresponding batch task.

In this example platform shall not be able to retry:

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

Here's correct way to do it:

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

## Retry Mechanisms for Batch Jobs

- All recurring Batch Jobs are automatically returned to the waiting state, regardless of whether they fail or succeed. It ensures that recurring jobs can complete any pending work in the next run if the previous run failed. To enable this functionality, the Batch Job's recurrence conditions must still be valid. It includes having a remaining recurrence count or a recurrence end date that hasn't passed.

- This option isn't a direct execution retry for Batch Jobs themselves, like the previous option. It enables the customer to add custom logic before the job is retriggered. When job execution fails, one can listen to corresponding business events and decide whether the failure can be retried. The batch platform provides an Open Data Protocol (OData) action from version 10.0.22 (with Platform update 46). When a Batch Job ID is provided in a call to the endpoint, the job is requeued for execution. For more information, refer [Batch OData API](batch-odata-api.md).

## Frequently asked questions

### How can I prevent my batch task from sending multiple emails as a result of retries?

To prevent the batch task from sending multiple emails due to retries, you can implement a mechanism to ensure that the email is sent only once, regardless of the number of retries. Here are a few strategies you can consider:

1. **Use Transactional Email Services**: Utilize transactional email services that provide features for ensuring message delivery and avoiding duplication. These services often include built-in mechanisms to prevent duplicate emails from being sent, even if the task is retried.

2. **Check Email Status**: Before sending the email, check the status of previous email deliveries to ensure that the same email isn't sent multiple times. You can maintain a log or database table to track the status of email deliveries and prevent duplicate sends.

3. **Implement Idempotent Email Sending**: Make the email sending process idempotent, meaning that sending the same email multiple times has the same effect as sending it once. It can be achieved by including a unique identifier (such as a message ID or transaction ID) in the email content and checking for its existence before sending the email.

4. **Use different Runtime Batch Task to send email**: In your main batch task, initiate a new runtime batch task for sending emails. Confirm if the email was successfully sent, by keep track of the batch task's state. When the main task is retried, verify the runtime task's state to check if the email was already sent, and if so, bypass the sending process.

By implementing one or more of these strategies, you can ensure that your batch task sends emails reliably without the risk of duplicates, even if there are retries.

### I have a multi-threaded Batch Job, where the main task is static and it queues multiple runtime tasks to do the work. As runtime tasks don't undergo retries, how can I make sure my Job completes successfully.

The main task, often referred to as the controller or driver, shouldn't finish immediately after queuing the child tasks. Instead, it should keep monitoring, in a loop say with delay of 15 seconds, the progress of each child runtime task to ensure successful completion. If a runtime task failed, the controller should requeue a new runtime task to attempt the operation again. It's important to manage the number of retries performed by the controller for each task. This can be achieved by maintaining a log of retries in a dedicated table or by structuring task identifiers, by using caption field, to reflect the retry count. It's advisable to limit retries, perhaps to a maximum of Five attempts, to avoid excessive processing or potential issues.

### Why do Batch Platform doesn't retry Runtime Tasks on server restarts?

Batch platform doesn't retry Runtime tasks on Batch Server restart due to several reasons. 

- Runtime tasks are designed to be temporary and in-memory, and are cleared upon server restart events. It's primarily because the driver or controller class, which is always static, handles child task retries upon restart by requeuing new runtime tasks for the once which failed. Retrying the runtime tasks could lead to the creation of duplicate tasks, potentially causing mutation issues and system overload with excessive duplicate batch tasks. 

- Runtime tasks, if retried, could complicate system management and lead to unexpected behavior, especially considering the potential cascading effect of runtime tasks creating extra tasks.