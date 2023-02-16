---
# required metadata

title: Create pages for on behalf of functionality in site builder
description: This article describes how to create pages in for on behalf of functionality in Microsoft Dynamics 365 Commerce site builder.
author:  mariash529
ms.date: 03/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-27
ms.dyn365.ops.version: 10.0.33
---

# Create pages for on behalf of functionality in site builder

[!include[banner](../includes/banner.md)]

This article describes how to create pages in for on behalf of functionality in Microsoft Dynamics 365 Commerce site builder. These pages allow account managers to sign in to a business-to-business (B2B) e-commerce website and perform operations on behalf of B2B buyers.

To enable on behalf of functionality in site builder, follow these steps. 

1. Create a new page for selecting a business partner organization.
1. Create a new page for selecting a business partner.
1. Modify B2B sign-in page to include a button for the account manager sign-in. 
1. Optional: Modify word "For" for the header. 

Refer to the steps below for more details about each step. In addition, for the newly created sites, T-1 staging environment will contain the sample pages. 

## Step 1: Create a business partner organization selection page

To create a business partner organization selection page, follow these steps. 

1. Follow the [instructions](add-new-page.md) to create a new page in site builder.
1. Edit the page:
    1. In the main slot, add a container.
    1. Add a **business partner** module to the container.
    1. Edit the property of the container. For example, set the heading to be "Select a Business Partner Organization".
    1. When done editing, save and publish the page.
 1. Configure a route for the page:
     1. Go to **Site settings \> Extensions \> Routes**.
     1. Set “Business partner selection” to be the page you created.
     1. Click “Save and Publish” button.

:::image type="content" source="./media/obo-site-builder-page.png" alt-text="Add a business partner module when creating a new page for business partner organization Selection":::

## Step 2: Create a business partner selection page

To create a business partner selection page, follow the same steps as for the business partner organization page using the same Business partner module. For the property of the container, specify a different heading (for example, "Select a Business Partner").

## Step 3: Modify B2B sign-in page to include "Employee sign-in" button

To modify a B2B sign-in page to include an employee sign-in button, follow these steps. 

 1. Edit the **B2B sign-in page**. 
 2. Check **Render B2B Account Sign-in button** in the **Sign in 1** container in the main slot.
 3. Optional: Change the button label text from **Employee sign-in** as needed. 
 4. Click **Save** and publish the page.

:::image type="content" source="media/obo-sign-in-experience.png" alt-text="include a Render B2B Account Sign-in button":::

## Step 4: (Optional) Modify word “For” in the header. 

For the on behalf of scenario, a header should contain the names of the account manager and the buyer that is being represented. By default, the word "For" is used, for example, "Alexander For Cameron Hartnett". This word can be modifiedm or removed in the header.definition.json file. For more information, see [Change module library static strings](e-commerce-extensibility/change-module-library-strings.md).


