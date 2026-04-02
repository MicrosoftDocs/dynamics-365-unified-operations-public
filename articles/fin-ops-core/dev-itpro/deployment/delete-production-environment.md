---
title: Delete a production finance and operations apps environment
description: Learn about the process of deleting a production finance and operation apps environment by using a self-service experience.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-12-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.1
---

# Delete a production finance and operations apps environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains how to delete a production [self-service environment](infrastructure-stack.md). You rarely need to delete a production self-service environment after a customer goes live with the software. However, you might need to delete the environment several times as part of the preparation for the final deployment. In many cases, customers go through the motions of deploying the production environment, applying code, bringing in data, and capturing how long each step of the process takes. If you want to delete and repeat the steps, this article helps you accomplish that task.

> [!IMPORTANT]
> Deleting a production environment that you use for your business can have severe consequences. To help safeguard against mistakes, only project owners in the Microsoft Dynamics Lifecycle Services project who are also from the same Microsoft Entra tenant that owns the project can perform this process.

## Delete a production environment

You can delete an environment that's in the **deployed** state directly through the environment details page. To delete an environment, go to the environment details page, and select the **Delete** button on the action bar. A confirmation dialog box prompts you to enter the name of the environment that you want to delete.

:::image type="content" source="media/deleteprodenvironment_1.png" alt-text="Screenshot of the prompt to enter the environment name to delete the environment.":::

After you enter the environment name and select **Yes**, you're prompted to confirm that you want to delete the production environment. In the **Step 2 of 2 - Delete environment** dialog box, you're prompted to enter your name to confirm and capture your intent to delete the environment.

:::image type="content" source="media/deleteprodenvironment_2-dk.png" alt-text="Screenshot of the prompt to enter your first and last names to delete the production environment.":::

After the final confirmation, the deletion operation starts. When it finishes, if you want to redeploy the production environment, the **Configure** button for the environment is available on the project dashboard.

> [!IMPORTANT]
> Solely for enterprises with an address or VAT registration in Denmark:  Microsoft retains accounting materials (that is, all documents that comprise bookkeeping, including recorded transactions and receipts) for legal entities in Denmark in a Microsoft-managed storage for five years from the end of the financial year the materials concern as required by Danish law. For more information, see [Compliance with requirements for digital standard bookkeeping systems in Denmark](https://go.microsoft.com/fwlink/?linkid=2258103). 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

