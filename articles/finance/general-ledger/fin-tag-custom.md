---
title: Financial tags development guidelines and FAQ 
description: Learn about customizing Financial tags.
author: leizi2015
ms.author: kweekley
ms.topic: article
ms.date: 09/15/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
ms.dyn365.ops.version: 10.0.16
---


# Financial tags development guidelines and FAQ 

Financial tags are a critical component of Microsoft Dynamics 365 finance and operations that enable organizations to categorize and track financial transactions with additional metadata. When developing 
customizations or extensions that interact with Financial tags, it's essential to follow specific guidelines to maintain data integrity and system functionality.

This article answers some FAQs and outlines guidelines for developers working with Financial tags to prevent data corruption and ensure proper system behavior.

### Can I delete from the FinTag table? 
Financial tags aren't meant to be deleted. There may be existing transactions across various tables and legal entities that refer to that Financial tag.
```x++
// NEVER DO THIS
delete_from finTag where finTag.RecId == someRecId;
```

### Can I update the FinTag table directly?
Direct updates bypass validation logic, trigger execution, and can lead to corrupt data. Other records in the system may be using this FinTag record as well. Changing your instance may also 
unintentionally change others.
```x++
// NEVER DO THIS
update_recordset finTag setting DisplayValue = "NewValue" where finTag.RecId == someRecId;
```

### Can I remove, disable, or update triggers? 
No, triggers maintain data integrity and enforce business rules. Disabling or updating them can lead to data corruption and system instability.

### Can I delete FinTagConfiguration records?
No, once a Financial tag is created, it can be deactivated but not deleted. This ensures that tag values remain available for reporting and auditing on posted transaction entries. Even if the tag is no longer
in use, its historical data must remain intact for compliance and traceability.
```x++
// NEVER DO THIS
delete_from finTagConfiguration where finTagConfiguration.RecId == someRecId;
```

### Why can't I search for Financial tags using display value?
DisplayValue isn't an indexed field. Use `FinTag.find()` to find by RecID. Otherwise, use the `FinTagResolver.resolve()` method to resolve a FinTag by display value. This provides better performance and caching.
```x++
// NEVER DO THIS - Display values can change
select finTag where finTag.DisplayValue == "SomeDisplayValue";
```

### What method should be used for inserts into the FinTag table?
The `save()` method ensures that all validation logic, business rules, and triggers are properly executed during the insertion process. It also checks if an existing record exists and creates a new record
only if necessary.


Following these guidelines is essential for maintaining system stability and data integrity when working with Financial tags. Not following these practices can lead to data corruption, system instability, and 
support issues.
