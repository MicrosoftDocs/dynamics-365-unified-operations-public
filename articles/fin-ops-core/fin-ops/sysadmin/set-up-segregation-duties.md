--- 
title: Set up segregation of duties
description: Learn about how you can set up rules to separate tasks that must be performed by different users, including a step-by-step process. 
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/21/2025
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysSecSegregationOfDutiesRule
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up segregation of duties

[!include [banner](../../../finance/includes/banner.md)]

You can set up rules to separate tasks that different users must perform. This concept is named segregation of duties. For example, you might not want the same person to acknowledge the receipt of goods and to process payment to the vendor. Segregation of duties helps you reduce the risk of fraud, and it also helps you detect errors or irregularities. You can also use segregation of duties to enforce internal control policies. Complete the following procedure to create a rule. You must be a system administrator to complete the procedure.

1. Go to **System administration** > **Security** > **Segregation of duties** > **Segregation of duties rules**.
1. Select **New**.
1. In the **Name** field, enter a value for the rule.
1. In the **First duty** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. Select the first duty that the rule controls.
1. In the **Second duty** field, select the drop-down button to open the lookup. 
1. In the list, find and select the desired record. Select the second duty that the rule controls.
1. In the **Severity** field, select an option. Select the severity of the risk that occurs when the same user or role performs both duties.  
1. In the **Security risk** field, enter a value. Enter a description of the security risk.  
1. In the **Security mitigation** field, enter a value. Enter a description of the actions that you take to mitigate the security risk. For example, you can mitigate the risk by conducting more detailed reviews of the process, by conducting a monthly managerial review, or by sharing resources with other departments.     
1. Select **Save**.

> [!IMPORTANT]
> Compliance with the rules for segregation of duties isn't verified when you create a rule. You can create a rule that creates a conflict for existing roles. Existing user role assignments can also conflict with the new rule. You must validate compliance after you create or modify a rule. For more information, see [Identify and resolve conflicts in segregation of duties](identify-resolve-conflicts-segregation-duties.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]