--- 
# required metadata 
 
title: Set up segregation of duties
description: You can set up rules to separate tasks that must be performed by different users. 
author: maertenm
manager: AnnBe 
ms.date: 06/25/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysSecSegregationOfDutiesRule   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up segregation of duties

[!include [banner](../../includes/banner.md)]

You can set up rules to separate tasks that must be performed by different users. This concept is named segregation of duties. For example, you might not want the same person both to acknowledge the receipt of goods and to process payment to the vendor. Segregation of duties helps you reduce the risk of fraud, and it also helps you detect errors or irregularities. You can also use segregation of duties to enforce internal control policies. Complete the following procedure to create a rule. You must be a system administrator to complete the procedure. The demo data company used to create this procedure is DAT. 

1. Go to **Navigation pane > Modules > System administration > Security > Segregation of duties > Segregation of duties rules**.
2. Click **New**.
3. In the **Name** field, type a value for the rule.
4. In the **First duty** field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record. Select the first duty that is controlled by the rule.
6. In the **Second duty** field, click the drop-down button to open the lookup. 
7. In the list, find and select the desired record. Select the second duty that is controlled by the rule.
10. In the **Severity** field, select an option. Select the severity of the risk that occurs when the same user or role performs both duties.  
11. In the **Security risk** field, type a value. Enter a description of the security risk.  
12. In the **Security mitigation** field, type a value. Enter a description of the actions that you take to mitigate the security risk. For example, you can mitigate the risk by conducting more detailed reviews of the process, by conducting a monthly managerial review, or by sharing resources with other departments.     
13. Click **Save**.

