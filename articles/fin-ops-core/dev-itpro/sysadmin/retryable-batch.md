---
# required metadata

title: Enabling automatic retries on batch jobs
description: This topic provides information about enabling automatic retries on batch jobs
author: sarvanisathish
ms.date: 06/10/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sarvanis
ms.search.validFrom: 2021-05-31

---

# Enabling automatic retries on batch jobs

[!include [banner](../includes/banner.md)]

## Overview
This article describes how to enable automatic retries on batch jobs on transient failures. Currently, if Finance and Operations apps experience a brief connection loss to SQL 
Server, all executing batch jobs fail. This is very disruptive to business processes. Given that connection loss is inevitable in a cloud service, Microsoft is enabling automated retries on failures of this type. This article describes how retries are implemented in Finance and Operations apps batch jobs.

## Metadata
Given that all batch jobs may not be idempotent (for e.g a batch runs credit card transaction), the retries cannot be enabled across all batch jobs equally. In order to safely enable retries, we have added metadata to the batch jobs to indicate if they are automatically retryable. Between versions 10.0.18 and 10.0.19, more than 90% of the Microsoft batch jobs have implemented the BatchRetryable interface explicitly and set the isRetryable value appropriately. For any jobs the isRetryable interface is not implemented, the default value is false.

## Retries
The retries are enabled only for jobs that have implemented the BatchRetryable interface and have set isRetryable = true. With this new functionality, retries happen on any interruption to SQL connection. Microsoft will continue adding retries on other exceptions.

## Frequently asked questions

### How do retries work for my custom batch jobs?
There is no change to the custom batch jobs. In order to take advantage of the automated retries, implement the BatchRetryable interface explicitly and set isRetryable to true on custom batch jobs. Please note that the batch jobs may need to be modified to make sure the job is safe to retry.

### How do I implement the retryable interface?
Add the following code to your Batch class.

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
 
### I am extending a Microsoft batch that is retryable, but my batch job is not. Will the retry trigger?
As long as the extended job has the isRetryable set to false, the job will not be retried.

### I marked my custom job as Retryable by mistake. Is there a way I can override without taking another code change?
Yes, you can go to the **System administration > Setup > Batch class configuration overrides** page to unregister your class from being retried on SQL connection failures, without going through a code change. You need to create a new record in this page and add the batch class that you want to unregister. This feature can be used to react quickly to changes needed. Best practice recommendation is to make sure the code is updated.

### I have my batch jobs designed to run multithreaded. How do I implement retryable. 
If your custom batch process designed to run in multi-threading i.e., you are creating multiple tasks and adding runtime tasks, you must implement BatchRetryable interface in both the main controller and the task controller.

### What is the best practice for the execution time for a batch job?
A batch job that has a shorter execution time will have a greater chance of completing successfully which will avoid the need for a retry.
 
### What is the best practice for the transaction size for a batch job?
A batch job that has a smaller transaction size will reduce the amount of work that could be lost due to a transient failure and that will ensure the need for a retry will not drastically increase the total execution time.


### What does idempotent mean for a batch job?
It means that a retry will not change or affect the overall result. For example, it means that something should only be done once won't be done more than once, such as once in the original run and again in the retry.
