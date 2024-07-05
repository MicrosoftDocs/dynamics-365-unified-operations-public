---
title: Write extensible forms
description: Learn about how to write extensible forms, including overviews on methods on forms, field groups, and form controls.
author: smithanataraj
ms.author: smnatara
ms.topic: article
ms.date: 09/09/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible forms

[!include [banner](../includes/banner.md)]

## Methods on forms
+ In general, the guidelines for writing extensible methods also apply to form methods.
+ Chain of Command (CoC) gives access to the form's non-private members, which are the same as the non-private members for classes.
+ CoC is enabled for nested classes. Therefore, methods that are defined in various levels on the form are extensible.

> [!NOTE]
> One limitation of methods on forms, that for form data source methods only methods that are defined in the kernel are enabled for extensions, i.e. methods defined on the form data source are not extensible. This will be available in an upcoming Platform Update.

## Field groups
Consider using field groups whenever possible. In this way, independent software vendors (ISVs) can add their fields for free when they extend a field group.

## Form controls
Moving around form controls could potentially cause a break if the controls are made non-extensible by moving.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
