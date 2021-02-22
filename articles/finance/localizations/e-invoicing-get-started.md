---
# required metadata

title: Get started with the Electronic invoicing add-on
description: This topic provides information that will help you get started with the Electronic invoicing add-on in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 02/03/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the Electronic invoicing add-on

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with the Electronic invoicing add-on.

The following table lists the Electronic invoicing features and the business documents that they can be applied to.

| Feature name                         | Business document |
|--------------------------------------|-------------------|
| Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> |
| Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> |
| Brazilian NF-e (BR)                  | <p>Fiscal document model 55</p><p>Correction letter</p> |
| Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document |
| Brazilian NFS-e São Paulo (BR)       | Service Fiscal document |
| Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> |
| Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> |
| Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> |
| Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> |
| French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> |
| German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> |
| FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice</p> |
| Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> |
| Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> |
| Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> |
| Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> |
| PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> |

## Prerequisites

Before you complete the procedures in this topic, the following prerequisites must be in place:

- Configure your Regulatory Configuration Service (RCS) and your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment so that you can submit to the Electronic invoicing add-on.
- Create a service environment, and publish it to the Electronic invoicing add-on. For more information, see [Get started with the Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md).
- Create a connected application. For more information, see [Get started with the Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md).
- Create a configuration provider for your organization. For more information, see [Create configuration provider and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

## Import an Electronic invoicing feature from the Microsoft configuration provider 

1. Sign in to your Regulatory Configuration Service (RCS) account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing add-on** tile.
3. Select **Import**, and then select **Synchronize**.
4. Filter the **Configuration provider** column by the term **Microsoft**.
5. Select the name of an Electronic invoicing feature from the table at the beginning of this topic, and then select **Import**.

## Create an Electronic invoicing feature under your organization provider

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-on** tile.
2. Select **Add** > **Based on existing feature**, and in the **Name** field, enter the name of the Electronic invoicing feature.
3. In the **Description** field, enter a description of the feature.
4. In the **Base feature field**, select the imported Electronic invoicing feature from the Microsoft configuration provider.
5. Select **Create feature**.

## Configure the Electronic invoicing feature

Depending on the country or region, the Electronic invoicing feature might require additional configuration. 

For the specific steps, see the "Get started" documentation that is available for your country or region.

## Configure the application setup

1. Select the Electronic invoicing feature that you created.
2. On the **Version** tab, verify that the **Draft** version is selected.
3. On the **Setups** tab, select **Application setup**.

    > [!NOTE]
    > Verify that your organization is set as the **Active** configuration provider. For more information, see [Create configuration provider and mark them as active.](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

4. Select **Feature setup**, and then select **Connected application**.
5. In the **Electronic document types** section, select **Add**.
6. For each business document that the feature supports, select and enter a **Table name** value according to the following table.

    | Feature name                         | Business document | Table name |
    |--------------------------------------|-------------------|------------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | Fiscal document |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document | Fiscal document |
    | Brazilian NFS-e São Paulo (BR)       | Service Fiscal document | Fiscal document |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Customer invoice journal |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |

7. For each business document that the feature supports, select and enter a **Context** value according to the following table.

    | Feature name                         | Business document | Context |
    |--------------------------------------|-------------------|---------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | <p>Customer invoice context model – Fiscal document context</p><p>Customer invoice context model – FD correction letter context</p> |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document| Customer invoice context model – Fiscal document context |
    | Brazilian NFS-e São Paulo (BR)       | Service Fiscal document| Customer invoice context model – Fiscal document context |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Customer invoice context model – Customer invoice context |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |

8. For each business document that the feature supports, select and enter a **Business document mapping** value according to the following table.

    | Feature name                         | Business document | Business document mapping |
    |--------------------------------------|-------------------|---------------------------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | <p>Fiscal document mapping – Fiscal document mapping</p><p>Fiscal document mapping – correction letter mapping</p> |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document | Fiscal document mapping – Fiscal document mapping |
    | Brazilian NFS-e São Paulo (BR)       | Service Fiscal document | Fiscal document mapping – Fiscal document mapping |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Invoice model mapping – Customer invoice |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |

Depending on the country or region, the Electronic invoicing feature might require additional configuration.

For specific steps, see the "Get started" documentation that is available for your country or region.

## Deploy the Electronic invoicing feature

1. On the **Versions** tab, select the version of the Electronic invoicing feature that you want to deploy.
2. Select **Change status** \> **Complete**.
3. Select **Change status** \> **Publish**.
4. Select **Deploy**.
5. Set the **Deploy to connected application** option to **Yes**.
6. On the **Connect application** page, select the connection that is associated with your instance of Finance or Supply Chain Management.
7. Set the **Deploy to service environment** option to **Yes**.
8. In the **Service environment** field, select the Electronic invoicing add-on service environment where you want to deploy the Electronic invoicing feature.
9. In the **From date** field, select the date when the Electronic invoicing feature must become effective in the Electronic invoicing add-on.
10. Select **OK**.

## Turn on the Electronic invoicing feature in Finance or Supply Chain Management

1. Sign in to Finance or Supply Chain Management, and verify that you're in the correct legal entity.
2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. On the **Features** tab, select the feature reference or references that are listed in the following table to turn on the Electronic invoicing feature for Finance or Supply Chain Management.

    | Feature name                         | Country/region  | Feature reference |
    |--------------------------------------|-----------------|-------------------|
    | Austrian electronic invoices (AT)    | Austria         | EUR-00023 |
    | Belgian electronic invoice (BE)      | Belgium         | EUR-00023 |
    | Brazilian NF-e (BR)                  | Brazil          | BR-00053 |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Brazil          | BR-00095 |
    | Brazilian NFS-e São Paulo (BR)       | Brazil          | BR-00095 |
    | Danish electronic invoice (DK)       | Denmark         | <p>EUR-00023</p><p>DK-00001</p> |
    | Dutch electronic invoice (NL)        | The Netherlands | EUR-00023 |
    | Egyptian electronic invoice (EG)     | Egypt           | EG-00008 |
    | Estonian electronic invoice (EE)     | Estonia         | EUR-00023 |
    | Finnish electronic invoice (FI)      | Finland         | EUR-00023 |
     French electronic invoice (FR)       | France           | EUR-00023 |
    | German electronic invoice (DE)       | Germany         | EUR-00023 |
    | Mexican CFDI Interfactura (MX)       | Mexico          | <p>MX-00010</p><p>MX-00016</p> |
    | Norwegian electronic invoice (NO)    | Norway          | <p>EUR-00023</p><p>NO-00010</p> |
    | Spanish electronic invoice (ES)      | Spain           | <p>EUR-00023</p><p>ES-00025</p> |
    | Italian electronic invoice (IT)      | Italy           | <p>EUR-00023</p><p>IT-00036</p> |
    | PEPPOL electronic invoice            | Europe          | EUR-00023 |

4. Select **Save**.

## Issue electronic invoices

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**.
2. On the **Record to include** FastTab, select **Filter**.
3. Select **Add** to add a table name to the query filter.
4. Select the table that contains the invoices.

    > [!NOTE]
    > The table name must be listed in the table in the [Configure the application setup](#configure-the-application-setup) section earlier in this topic.

5. Select the field name from the table that you want to query.
6. Enter the table name and field name for the criteria to query on.
7. Repeat steps 5 and 6 to add more fields and criteria to the query, and then select **OK**.
8. Select **OK**.

## View submission logs

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**.
2. In the **Document type** field, select the table that contains the invoices.

    > [!NOTE]
    > The table name must be listed in the table in the [Configure the application setup](#configure-the-application-setup) section earlier in this topic.

3. Select an invoice in the grid, and then select **Inquire** \> **Submission details**.


## Related topics

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on for Brazil](e-invoicing-bra-get-started.md)
- [Get started with the Electronic invoicing add-on for Mexico](e-invoicing-mex-get-started.md)
- [Get started with the Electronic invoicing add-on for Italy](e-invoicing-ita-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]