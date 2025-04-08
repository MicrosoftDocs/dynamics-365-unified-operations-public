---
title: Set up NF-e federal parameters (Brazil)
description: This article describes how to set up Nota Fiscal eletrônica (NF-e) web services, rejection codes, and schemas to generate an NF-e in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Set up NF-e federal parameters (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up Nota Fiscal eletrônica (NF-e) web services, rejection codes, and schemas to generate an NF-e in Brazil with Microsoft Dynamics 365 Finance.

You can set up NF-e web services, rejection codes, and schemas to generate an NF-e. After you generate an NF-e, XML messages are generated and submitted to the Secretaria da Fazenda (SEFAZ). 

The following procedure uses the BRMF demo company.

To set up NF-e web services, rejection codes, and schemas to generate an NF-e, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Electronic fiscal documents \> NF-e federal parameters**.
1. Select **New**. One tax authority must be created per state.  
1. In the **Authority** field, enter a value.
1. In the **Name** field, enter a value.
1. Select the **Ignore accents** checkbox.
1. Select the **Cancel as Event** checkbox. This option complies with the cancellation of NF-e through events instead of a specific XML cancellation file.  
1. Select **Save**.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e authorization.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e discard.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e inquiries.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e authorization returns.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e events.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **New**.
1. In the **Environment** field, select an option.
1. Select the web service for NF-e service status inquiries.
1. In the **Version** field, enter a value.
1. In the **Internet address** field, enter a value.
1. Select **Save**.
1. Select the **Rejection codes** tab.
1. Select **New**. 
1. In the NF-e rejection code field, enter the rejection code from the official NF-e guide.
1. In the **Description** field, enter a value.
1. In the list, mark the selected row.
1. In the **Message type** field, select an option.
1. In the **Fiscal document status** field, enter the fiscal document status that must be set when the rejection code is entered.  
1. Select **Save**.
1. Select the **Schemas** tab.
1. Select **New**. When applicable, enter the path of the XSD file that is used to validate the NF-e XML.  
1. In the **The version of the NF-e feature** field, select an option.
1. In the **Schema** field, enter a value.
1. Select **New**.
1. In the **Schema type** field, select an option.
1. In the **The version of the NF-e feature** field, select an option.
1. In the **Schema** field, enter a value.
1. Select **New**.
1. In the **Schema type** field, select an option.
1. In the **The version of the NF-e feature** field, select an option.
1. In the **Schema** field, enter a value.
1. Select **New**.
1. In the **Schema type** field, select an option.
1. In the **The version of the NF-e feature** field, select an option.
1. In the **Schema** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
