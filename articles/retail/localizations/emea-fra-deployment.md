---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic is a deployment guide for the Retail localization for France.
author: AlexChern0v
manager: ezubov
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: v-alexec
ms.search.scope: Retail
ms.search.validFrom: 2018-3-15
ms.dyn365.ops.version: 7.3.2
---
# Deployment guidelines for cash registers for France

[!include[banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 for Retail localization for France. The localization consists of several extensions of Retail components. For example, the extensions let you print custom fields on receipts, register additional audit events and sales and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the Retail localization for France, see [Cash registers for France](./emea-fra-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.
