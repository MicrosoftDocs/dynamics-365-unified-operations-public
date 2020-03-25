---
# required metadata

title: Switch between vendor designs
description: This topic describes how to switch vendor data integration between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 09/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-09-20

---

# Switch between vendor designs

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

## Vendor data flow 

If you choose to use the **Account** entity to store vendors of the **Organization** type and the **Contact** entity to store vendors of the **Person** type, configure the following workflows. Otherwise, this configuration isn't required.

## Use the extended vendor design for vendors of the Organization type

The **Dynamics365FinanceExtended** solution package contains the following workflow process templates. You will create a workflow for each template.

+ Create Vendors in Accounts Entity
+ Create Vendors in Vendors Entity
+ Update Vendors in Accounts Entity
+ Update Vendors in Vendors Entity

To create new workflow processes by using the workflow process templates, follow these steps.

1. Create a workflow process for the **Vendor** entity, and select the **Create Vendors in Accounts Entity** workflow process template. Then select **OK**. This workflow handles the vendor creation scenario for the **Account** entity.

    ![Create Vendors in Accounts Entity workflow process](media/create_process.png)

2. Create a workflow process for the **Vendor** entity, and select the **Update Vendors in Accounts Entity** workflow process template. Then select **OK**. This workflow handles the vendor update scenario for the **Account** entity.
3. Create a workflow process for the **Account** entity, and select the **Create Vendors in Vendors Entity** workflow process template.
4. Create a workflow process for the **Account** entity, and select the **Update Vendors in Vendors Entity** workflow process template.
5. You can configure the workflows as either real-time workflows or background workflows, depending on your requirements. To configure a workflow as a background workflow, select **Convert to a background workflow**.

    ![Convert to a background workflow button](media/background_workflow.png)

6. Activate the workflows that you created for the **Account** and **Vendor** entities to start to use the **Account** entity to store information for vendors of the **Organization** type.

## Use the extended vendor design for vendors of the Person type

The **Dynamics365FinanceExtended** solution package contains the following workflow process templates. You will create a workflow for each template.

+ Create Vendors of type Person in Vendors Entity
+ Create Vendors of type Person in Contacts Entity
+ Update Vendors of type Person in Contacts Entity
+ Update Vendors of type Person in Vendors Entity

To create new workflow processes by using the workflow process templates, follow these steps.

1. Create a workflow process for the **Vendor** entity, and select the **Create Vendors of type Person in Contacts Entity** workflow process template. Then select **OK**. This workflow handles the vendor creation scenario for the **Contact** entity.
2. Create a workflow process for the **Vendor** entity, and select the **Update Vendors of type Person in Contacts Entity** workflow process template. Then select **OK**. This workflow handles the vendor update scenario for the **Contact** entity.
3. Create a workflow process for the **Contact** entity, and select the **Create Vendors of type Person in Vendors Entity** template.
4. Create a workflow process for the **Contact** entity, and select the **Update Vendors of type Person in Vendors Entity** template.
5. You can configure the workflows as either real-time workflows or background workflows, depending on your requirements. To configure a workflow as a background workflow, select **Convert to a background workflow**.
6. Activate the workflows that you created on the **Contact** and **Vendor** entities to start to use the **Contact** entity to store information for vendors of the **Person** type.
