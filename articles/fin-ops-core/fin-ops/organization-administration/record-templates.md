---
title: Record templates overview
description: Learn about the concept of record templates and explains how they can be used to create records that share information.
author: pvillads
ms.author: pvillads
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/10/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 61ada2d8-84c3-44bc-b4c5-516b1aeac3d1
---

# Record templates overview

[!include [banner](../includes/banner.md)]

This article introduces the concept of record templates and explains how you can use them to create records that share information.

Record templates can help you create records more quickly. However, you can only create record templates for some record types.

For example, imagine you're entering rental information for a car rental business that's located in San Francisco. Since most of the customers are likely to be from the San Francisco area, it would be helpful if you could automatically fill in the values for the **State**, **Country**, and **City** fields on the rental form.

> [!NOTE]
> You can apply templates only in areas that you have access to. However, you can see all template titles when you create a new record. Other users can also see all template titles if you create templates that are available to all users. Be sure to consider this visibility when naming templates. For example, avoid using names that include words such as "commission" if it's confidential that some employees in the company have commission-based salaries.

When one or more templates that you have access to exist for a specific form and you attempt to create a new record in the form, the **Select a template for** page is displayed. When you select a template from the list, the new record is created and contains default information based on the template that you selected. If you don't want to use templates when you create new records, select the **Do not ask again** check box in the **Select a template for** page. To display the template selection dialog box again, right-click any record, select **Record info**, and then select **Show template selection**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
