---
# required metadata

title: Delete a production finance and operations apps environment
description: This article explains how to delete a production environment by using a self-service experience.
author: laneswenka
ms.date: 04/19/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Delete a production finance and operations apps environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains the process of deleting a production [self-service environment](infrastructure-stack.md). Deletion of a production self-service environments is rarely done after a customer goes live with the software. However, it might be done several times as part of the preparation for the final deployment. In many cases, customers will go through the motions of deploying the production environment, applying code, bringing in data, and capturing how long each step of the process takes. If you want to delete and repeat the steps, this article will help you accomplish that task.

> [!IMPORTANT]
> Deletion of a production environment that's used for your business can have severe consequences. To help safeguard against mistakes, this process is available only to project owners in the Microsoft Dynamics Lifecycle Services project who are also from the same Azure Active Directory (Azure AD) tenant that owns the project.

## Delete a production environment

You can delete an environment that's in the deployed state directly through the environment details page. To delete an environment, go to the environment details page, and select the **Delete** button on the action bar. A confirmation dialog box prompts you to enter the name of the environment that you want to delete.

:::image type="content" source="media/deleteprodenvironment_1.png" alt-text="Screenshot of the prompt to enter the environment name to delete the environment.":::

After you enter the environment name and select **Yes**, you're prompted to confirm that you want to delete the production environment. In the **Step 2 of 2 - Delete environment** dialog box, you're prompted to enter your name to confirm and capture your intent to delete the environment.

:::image type="content" source="media/deleteprodenvironment_2.png" alt-text="Screenshot of the prompt to enter your first and last names to delete the production environment.":::

After the final confirmation, the deletion operation starts. After it's completed, if you want to redeploy the production environment, the **Configure** button for the environment is available on the project dashboard.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
