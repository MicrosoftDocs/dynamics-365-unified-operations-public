---
# required metadata

title: Automatic retries in batch jobs
description: This topic provides information about enabling automatic retries on batch jobs
author: sarvanis
ms.date: 06/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 62333
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.search.region: Global
# ms.search.industry: 
ms.author: hasaid
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform update 42

---

# Enabling automatic retries on batch jobs

[!include [banner](../includes/banner.md)]

## Overview
This article describes how to enable automatic retries on batch jobs on transient failures. Currently, if Finance & Operations apps experience a brief connection loss to SQL, the executing batch jobs fail. This is very disruptive to business processes. Given that connection loss is inevitable in a cloud service, Microsoft is enabling automated retries on failures of this type. This article describes how retries are implemented in Finance & Operations apps batch jobs.

## Metadata
Given that all batch jobs may not be idempotent (for e.g a batch runs credit card transaction), the retries cannot be enabled across all batch jobs equally. In order to safely enable retries, we have added metadata to the batch jobs to indicate if they automatically retryable. Between 10.0.18 and 10.0.19, more than 90% of the Microsoft batch jobs have implemented the Retryable interface explicitly. For any jobs the retryable interface is not implemented, the default value is false.

## Retries
The retries are enabled for jobs that have implemented the BatchRetryable interface and have set isRetryable = true. Currently the retries happen on any interruption to SQL connection. Microsoft will continue adding retries on other exceptions.

## Frequently asked questions

### How do retries work for my custom batch jobs?
There is no change to the custom batch jobs. In order to take advantage of the automated retries, implement the retryable interface explicitly on every custom batch job.

### How do I implement the retryable interface?
Add the following code to your Batch class
```
  class TestBatchJob extends RunBaseBatch implements BatchRetryable
  {
    [Wrappable(true), Replaceable(true)] // Change to meet your customizability requirements
    public boolean isRetryable() // Use final if you want to prevent overriding
    {
        return false; // You can also use true if you want to enforce retryable behavior
    }
 ```
 
 ### I am extending a Microsoft batch that is retryable, but my batch job is not. Will the retry trigger?
 As long as the extended job has the isRetryable set to false, the job will not be retried.
 
 ### I marked my custom job as Retryable by mistake. Is there a way I can override without taking another code change?
 Yes, you can go to the system administration -> batch -> override form and override the retryable value to false. This will prevent further executions from being retried.
 
 ### I have 100s of batch jobs? How do I discover all my batch jobs to implement the interface?
 Plug in Peter's github repo here.
