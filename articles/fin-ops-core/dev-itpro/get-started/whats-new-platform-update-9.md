---
title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 9 (July 2017)
description: Learn about the new or changed features in Dynamics 365 for Finance and Operations, Enterprise edition platform update 9. This version was released in July 2017.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 9 
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 9 (July 2017)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 9. This version was released in July 2017 and has a build number of 7.0.4612.35162.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 9, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=853624).

## Batch job history clean-up

Functionality to clean up the history of batch jobs has been added (this functionality was available in Dynamics AX 2012). This feature allows you to delete all or any subset of batch job history by clicking a button. Using a specific form, you can filter the batch job history by different criteria, such as batch job name, company, status, or finished time, and then delete the filtered subset. In addition to keeping the history notes clean and relevant, this feature also provides performance enhancements by eliminating the negative performance impact of having a large volume of entries in history tables, if left unmonitored for long periods of time. Before Platform update 9, you needed to delete the history on a job-by-job basis, which required extra time to cover all the wanted jobs.

Two new forms have been added to the **System Administration** workspace – **Batch job history clean-up** (regular and custom version).

The regular version of batch job history clean-up allows you to quickly clean all history entries older than a specified timeframe (in days). Any entry that was created prior to \<Today\> - \<History limit\> will be deleted from the **BatchJobHistory** table, as well as from linked tables with related records (**BatchHistory** and **BatchConstraintsHistory**). This form has improved performance optimization because it doesn't have to execute any filtering.

The custom batch job clean-up form should be used only when specific entries need to be deleted. This form allows you to clean up selected types of batch job history records, based on criteria such as status, job description, company, or user. Other criteria can be added using the **Filter** button.

## Change of usage data serialization format

The usage data that is typically stored in the **SysLastValue** table will no longer be serialized in binary format, and instead will be serialized in string format. This format change increases the scale, ability to debug the code, and overall reliability of the system, which allows for changes from the application layer to not have an effect on caches. However, due to technical reasons it is not possible to ensure the integrity of the data during the upgrade process and ensure system integrity and reliability.

Usage data is automatically reset upon moving to Platform update 9. Users will lose their usage data as part of this platform update process. This mostly includes data used for custom queries and saved dialog posting selections. Personalization is not affected.

The new data format is versioned, backward compatible, and always preserved from Platform update 9 onward for future application and platform releases.

## Method wrapping and chain of command

### Overview

The functionality of extension classes (also known as class augmentation) has been improved to allow developers to wrap logic around methods defined in a base class. This allows extending the logic of public and protected methods without the need to use event handlers. When you wrap a method, you can also access other public and protected methods and variables of the class. This way, you can start transactions and easily manage state variables associated with your class.

Consider the following situation. A model contains the following code.

```
class BaseClass1
{
    str method1(int arg) {
        …
    }
}
```

It is now possible to extend the functionality of method1 using an extension class by reusing the same name to add pre-and post-logic to it.

```
[ExtensionOf(ClassStr(BaseClass1))]
class BaseClass1_Extension
{
    str method1(int arg) {
        // Part 1
        var s = next method1(arg + 4);
        // Part 2
        return s;
    }
}
```

Wrapping method1 and the required use of the next keyword creates a Chain of Command (CoC) for the method. Here is what happens when the following code executes.

```
BaseClass1 c = new BaseClass1();
Print c.method1(33);
```

The system will find any method that wraps method1. It will randomly execute one of these methods, such as method1 of the BaseClass1\_Extension class. When the call to next method1() occurs, the system will randomly pick another method in the CoC or call the original implementation if none exist.

### Supported versions

The functionality described in this article is available as of Platform update 9 (CoC and access to protected methods and variables).

However, this functionality requires the class being augmented to be compiled on Platform update 9. Because the current releases of the Dynamics 365 for Finance and Operations, Enterprise edition applications have been compiled on Platform update 8 or earlier, you will need to recompile a base package (like Application Suite) on Platform update 9 or newer in order to wrap a method that is defined in that package.

## OData batch request size configuration

The default OData batch request size is 1,000 records. Microsoft can now change the size of OData batch requests for customers. Customers must log a support request through LCS to the Dynamics Service Engineering team (DSE) to increase the batch size up to a maximum value of 5,000 records. For more information, see [Submit service requests to the Dynamics Service Engineering team](../lifecycle-services/submit-request-dynamics-service-engineering-team.md)

## System startup performance for virtual machines

Performance issues with loading metadata have been addressed, so you should no longer experience a system freeze when a virtual machine starts.

> [!NOTE]
> This issue will still occur on virtual machines that are used as build machines (VMs that have enlistments and compile code).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
