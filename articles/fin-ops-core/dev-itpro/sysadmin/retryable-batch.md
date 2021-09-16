---
# required metadata

title: Enable automatic retries on batch jobs
description: This topic describes how to enable automatic retries on batch jobs when transient failures occur.
author: matapg007
ms.date: 09/09/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2021-05-31

---

# Enable automatic retries on batch jobs

[!include [banner](../includes/banner.md)]

This topic describes how retries are implemented on batch jobs in Finance and Operations apps, and how you can enable automatic retries on batch jobs when transient failures occur. Currently, if Finance and Operations apps experience a brief loss of connection to Microsoft SQL Server, all batch jobs that are running fail. This behavior disrupts business processes. Because connection loss is inevitable in a cloud service, Microsoft is enabling automated retries when failures of this type occur.

> [!IMPORTANT]
> This feature is available with version 10.0.18 and later.

## Metadata

Because not all batch jobs might be idempotent (for example, when a batch runs credit card transactions), retries can't be enabled equally across all batch jobs. To help ensure that retries can safely be enabled, Microsoft has added metadata to the batch jobs to indicate whether they can automatically be retried. Between versions 10.0.18 and 10.0.19, more than 90 percent of the Microsoft batch jobs have explicitly implemented the **BatchRetryable** interface, and the **isRetryable** value has been set appropriately. For any jobs where the **BatchRetryable** interface isn't implemented, the default value of **isRetryable** is **false**.

## Retries

Retries are enabled only for jobs where the **BatchRetryable** interface is implemented and **isRetryable** is set to **true**. In this new functionality, retries occur on any interruption of the SQL Server connection. Microsoft will continue to add retries on other exceptions.

## Frequently asked questions

### How do retries work for my custom batch jobs?

There is no change to the custom batch jobs. To take advantage of automated retries, explicitly implement the **BatchRetryable** interface on the custom batch jobs, and set **isRetryable** to **true**. Note that you might have to modify the batch jobs to ensure that they are safe to retry.

### How do I implement the retryable interface?

Add the following code to your batch class.

For more information, see [Final methods and the Wrappable attribute](../extensibility/method-wrapping-coc.md).

```
//RunBaseBatch
class TestBatchJob extends RunBaseBatch implements BatchRetryable
{
    [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
    public boolean isRetryable() // Use final if you want to prevent overriding
    {
        return false; // You can also use true if you want to enforce retryable behavior
    }
    ...
} 

//SysOperationServiceController 
class TestBatchJob extends SysOperationServiceController implements BatchRetryable
{
    [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
    public boolean isRetryable() // Use final if you want to prevent overriding
    {
        return false; // You can also use true if you want to enforce retryable behavior
    }
    ...
}
```

### I am extending a Microsoft batch that is retryable, but my batch job isn't retryable. Will the retry be triggered?

Provided that **isRetryable** is set to **false** for the extended job, the job won't be retried.

### I mistakenly marked my custom job as retryable. Can I override without taking another code change?

Yes. You can go to **System administration \> Setup \> Batch class configuration overrides** to unregister your class from being retried when SQL Server connection failures occur, without having to go through a code change. On the **Batch class configuration overrides** page, you must create a new record and add the batch class that you want to unregister. You can use this feature to react quickly to changes that are required. The best practice recommendation is to make sure that the code is updated.

### My batch jobs are designed to run multithreaded. How do I implement retries?

If your custom batch process is designed to run in multithreading (that is, if you're creating multiple tasks and adding runtime tasks), you must implement the **BatchRetryable** interface in both the main controller and the task controller.

### What is the best practice for the execution time for a batch job?

A batch job that has a shorter execution time is more likely to be successfully completed. Therefore, the need for a retry is avoided.
 
### What is the best practice for the transaction size for a batch job?

A batch job that has a smaller transaction size reduces the amount of work that can be lost because of a transient failure. Therefore, the need for a retry won't drastically increase the total execution time.

### What does idempotent mean for a batch job?

In this context, *idempotent* means that a retry won't change or affect the overall result. For example, something should be done only one time and won't be done more than one time. Therefore, something that is done in the original run won't be done again during the retry.

### What is the maximum number of retries that BatchRetryable supports, and what is the retry interval?

**MaxRetryCount** specifies the number of retries that will be applied to a task, regardless of the type of exception that occurs. If a task fails, the batch platform evaluates the number of times that it has been retried. If the number is less than the value of **MaxRetryCount**, the task is put back into a ready state so that it can be picked up again.

The **BatchRetryable** interface starts after five seconds and stops retrying after the interval time reaches five minutes. (Interval time increases in the following way: 5, 8, 16, 32, and so on.)

### Can I change the maximum number of retries and the retry interval?

The **BatchRetryable** interface enables transient SQL connection issues to be handled. It's mainly controlled by the framework. Customers can't update setting for **BatchRetryable**, such as the maximum number of retries and the retry interval.
