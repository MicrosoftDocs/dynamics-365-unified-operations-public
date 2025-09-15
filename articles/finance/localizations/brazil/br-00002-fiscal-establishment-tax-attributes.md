---
title: Fiscal establishment tax attributes (Brazil)
description: This article describes how to create one or more fiscal establishments for a legal entity in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---

# Fiscal establishment tax attributes (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create one or more fiscal establishments for a legal entity in Brazil with Microsoft Dynamics 365 Finance.

The following procedure walks through how to create one or more fiscal establishments for a legal entity. A fiscal establishment requires a Cadastro Nacional da Pessoa Jurídica (CNPJ) or Inscrição Estadual (IE) tax registration number. You can group fiscal establishments and set up tax groups for each fiscal establishment group in the Taxes matrix page. The procedure uses the BRMF demo company.

To create one or more fiscal establishments for a legal entity, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. In the **Name** field, select the link.
1. Expand the **Addresses** section.
1. Select **Add**.
1. In the **Name or description** field, enter a value.
1. In the **Purpose** field, enter or select a value.
1. In the **Country/region** field, enter a value.
1. Select **Yes**.
1. In the **ZIP/postal code** field, enter a value.
1. In the **Street number** field, enter a value.
1. Select **OK**.
1. Close the page.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishment groups**.
1. Create a new fiscal establishment group.
1. In the **Fiscal establishment group** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Create a new fiscal establishment.
1. In the **Fiscal establishment ID** field, enter a value.
1. In the **Fiscal establishment group** field, enter or select a value.
1. In the **CNPJ** field, enter the CNPJ of the new fiscal establishment.
1. Expand the **Address** section.
1. In the **Name** field, enter or select a value.
1. In the **IE** field, enter the IE of the fiscal establishment based on the state in the address.
1. Select **Save**.
1. Close the page.
1. Go to **Inventory management \> Setup \> Inventory breakdown \> Sites**.
1. Select **New**.
1. In the **Site** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Fiscal establishment ID** field, enter or select a value.
1. Expand the **Financial dimensions** section.
1. In the **Filial** field, select the link.
1. Select **New**.
1. In the **Dimension value** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Add** to open the dialog.
1. Select **Add**.
1. Select **Save**.
1. Close the page.
1. In the **Filial** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Open the **Advanced row selection** dialog.
1. In the **Fiscal establishment ID** field, enter a filter value of "NovaFilial" using the "is exactly" filter operator.
1. Select **Fiscal document types**.
1. Select **New**.
1. In the **Fiscal document type** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Series** field, enter a value.
1. In the **Fiscal document number sequence** field, enter or select a value.
1. In the **Document model** field, enter or select a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
