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
This article describes how to enable automatic retries on batch jobs on transient failures. Currently, if F&O experiences a brief connection loss to SQL, the executing batch jobs fail. This is very disruptive to business processes. Given that connection loss is inevitable in a cloud service, Microsoft is enabling automated retries on failures of this type. This article describes how retries are enabled in Finance & Operations apps batch jobs.

## Metadata
Given that all batch jobs may not be idempotent (for e.g a batch runs credit card transaction), the retries cannot be enabled across all batch jobs equally. In order to safely enable retries, we are have added metadata to the batch jobs to indicate if it is automatically retryable. Between 10.0.18 and 10.0.19, more than 90% of the Microsoft batch jobs have implemented the Retryable interface explicitly. For any jobs the retryable interface is not implemented, the default value is false.

## Retries
The retries are enabled for jobs that have implemented the Retryable interface and have set Retryable = true. Currently the retries happen on any interruption to SQL connection. Microsoft will continue adding retries on other exceptions.
