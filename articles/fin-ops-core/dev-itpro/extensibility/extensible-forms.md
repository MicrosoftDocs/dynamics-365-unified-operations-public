---
title: Write extensible forms
description: Learn about how to write extensible forms, including overviews on methods on forms, field groups, and form controls.
author: smithanataraj
ms.author: smnatara
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible forms

[!include [banner](../includes/banner.md)]

## Methods on forms

- Generally, the guidelines for writing extensible methods also apply to form methods.
- Chain of Command (CoC) gives access to the form's non-private members, which are the same as the non-private members for classes.
- CoC is enabled for nested classes. Therefore, methods that are defined in various levels on the form are extensible.

> [!NOTE]
> One limitation of methods on forms is that for form data source methods, only methods that the kernel defines are enabled for extensions. Methods defined on the form data source aren't extensible. This limitation will be addressed in an upcoming Platform Update.

## Field groups

Consider using field groups whenever possible. By using field groups, independent software vendors (ISVs) can add their fields for free when they extend a field group.

## Form controls

Moving form controls could potentially cause a break if you make the controls non-extensible by moving them.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
