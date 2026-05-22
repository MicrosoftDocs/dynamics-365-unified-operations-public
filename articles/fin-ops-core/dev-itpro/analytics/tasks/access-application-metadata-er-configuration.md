---
title: Access application metadata by using ER configuration
description: The article describes how a Regulatory configuration service user can design a new Electronic reporting model mapping by using the metadata.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---

# Access application metadata by using ER configuration

[!include [banner](../../includes/banner.md)]

The following steps explain how a Regulatory configuration service (RCS) user in the System Administrator or Electronic Reporting Developer role can design a new Electronic reporting (ER) model mapping by using the application metadata. You access application metadata by using an ER metadata configuration that contains a sample set of metadata to access foreign trade transactions. To complete these steps, in RCS you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md) procedure. Then complete the steps in the article, [Prepare application metadata to be used in RCS](prepare-application-metadata-rcs.md).

## Prerequisites

1. Go to **All workspaces** > **Electronic reporting**.
1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

## Import metadata configuration

1. Select **Metadata configurations**.
1. Import the ER metadata configuration that contains metadata that is configured to generate electronic documents for foreign trade business. This ER metadata configuration is exported as XML file while the steps in the [Prepare application metadata to be used in RCS](prepare-application-metadata-rcs.md) procedure are completed.
1. Select **Exchange**.
1. Select **Load from XML file**.
1. Select **Browse** and select the **Foreign trade metadata.xml** file.
1. Select **OK**.
1. Close the page.

## Create data model configuration

1. Select **Reporting configurations**.
1. Select **Create configuration** to open the form.
1. In the **Name** field, enter *Foreign trade model*.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Root*.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Transaction*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Commodity code*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Invoiced amount*.
1. In the **Item type** field, select **Real**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Date*.
1. In the **Item type** field, select **Date**.
1. Select **Add**.
1. Select **Root reference**.
1. Select **OK**.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

## Create model mapping configuration

1. Select **Create configuration** to open the form.
1. In **New**, enter *Model Mapping based on data model Foreign trade model*.
1. In **Name**, type *Foreign trade mapping*.
1. Select **Create configuration**.
1. Expand the **Prerequisites** section.
1. Select **Edit**.
1. Select **New**.
1. In the list, select the row.
1. In **Prerequisite component type**, select **Configuration**.
1. Select **Foreign trade metadata** configuration.
1. Select **Save**.
1. You add the reference to version 1 of the **Foreign trade metadata** configuration. Application metadata from this configuration is offered while you design this model mapping.
1. Close the page.
1. Select **Designer**.
1. Select **Designer**.
1. In the tree, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
1. In **Name**, type *Intrastat*.
1. Select **Intrastat** table records.
1. Select **OK**.

> [!NOTE]
> You see only two tables because you added only two tables into the set of metadata that you're currently using.

1. Select **Bind**.
1. In the tree, expand **Intrastat**.
1. In the tree, select **Intrastat\AmountMST**.
1. In the tree, expand **Transaction = Intrastat**.
1. In the tree, select **Transaction = Intrastat\Invoiced amount**.
1. Select **Bind**.
1. In the tree, select **Intrastat\TransDate**.
1. In the tree, select **Transaction = Intrastat\Date**.
1. Select **Bind**.
1. In the tree, expand **Intrastat\>Relations**.
1. In the tree, expand **Intrastat\>Relations\IntrastatCommodity**.
1. In the tree, select **Intrastat\>Relations\IntrastatCommodity\Code**.
1. In the tree, select **Transaction = Intrastat\Commodity code**.
1. Select **Bind**.
1. Select **Validate**.

> [!NOTE]
> You successfully bind elements of data model with items of data sources that are described by using details of application metadata from the referred ER metadata configuration.

1. Select **Save**.
1. Close the page.
1. Close the page.
1. When needed, you can extend the existing set of metadata and then export the new completed version of ER metadata configuration. You can then import it to RCS, and update the prerequisites of the configured model mapping configuration referring to a new version of imported metadata configuration.

> [!NOTE]
> This way of getting information about application metadata is the only one available for locally deployed applications (when local business data (LBD), or on-premises, deployment model is used).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
