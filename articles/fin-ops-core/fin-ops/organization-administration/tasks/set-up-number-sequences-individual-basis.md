--- 
title: Set up number sequences on an individual basis
description: Learn about how to set up number sequences on an individual basis, including a step-by-step process for using the set up number sequences wizard.  
author: SunilGarg
ms.author: sunilg
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: NumberSequenceTableListPage, NumberSequenceDetails  
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up number sequences on an individual basis

[!include [banner](../../includes/banner.md)]

This article explains how to set up number sequences on an individual basis. Use number sequences to generate readable, unique identifiers for master data records and transaction records that need them. A master data or transaction record that needs an identifier is called a reference. Before you can create new records for a reference, you must set up a number sequence and associate it with the reference. You can set up all required number sequences at the same time by using the **Set up number sequences** wizard, or you can create or modify individual number sequences by using the **Number sequences** page.

1. Go to **Navigation pane > Modules > Organization administration > Number sequences > Number sequences**.
1. Select **Number sequence**.
1. In the **Number sequence code** field, enter a value.
1. In the **Name** field, enter a value.
1. On the **Scope parameters** FastTab, select a scope for the number sequence and select scope values from the drop-down list. The scope defines which organizations use the number sequence. In addition, number sequences that have a scope other than **Shared** can have segments that correspond to their scope. For example, a number sequence with a scope of **Legal entity** can have a legal entity segment. For more information about scopes, see [Number sequence overview](../number-sequence-overview.md).
1. Expand the **Segments** section.
    - Define the format for the number sequence by adding, removing, and rearranging segments.  
    - Number sequences of all scopes can contain *Constant segments* and *Alphanumeric segments*. Constant segments contain a set of alphanumeric characters that don't change. Use this segment type to add a hyphen or other separators between number sequence segments. Alphanumeric segments contain a combination of number signs (#) and ampersands (&). These characters represent letters and numbers that increment each time you use a number from the sequence. Use a number sign (#) to indicate incrementing numbers and an ampersand (&) to indicate incrementing letters. For example, the format `#####_2014` creates the sequence `00001_2014`, `00002_2014`, and so on. At least one alphanumeric segment must be present. Scope segments, such as company or legal entity, aren't required. However, if you don't include scope segments in the format, the system still generates numbers for the selected reference per scope.  
1. Expand the **References** section. Select the document type or record to assign this number sequence to. This step is optional for sequences that you define for special application usage patterns. In these scenarios, the system generates a new number by using the value of a number sequence code or ID, without using a reference. An example of a special application usage pattern is a voucher series that is used for specific journal names. However, don't use such patterns.  
1. Expand the **General** section. On the General FastTab, specify whether the number sequence is manual, and continuous or non-continuous. In addition, enter the lowest and highest numbers that can be used in the number sequence. Don't change a non-continuous number sequence to a continuous number sequence. The number sequence won't be truly continuous. This change might also cause duplicate key violations in the database. In addition, continuous number sequences have a larger effect on performance.
1. Select **Save**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
