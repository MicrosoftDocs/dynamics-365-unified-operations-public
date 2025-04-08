---
title: View party data
description: Learn about how to view party data by using the Party page, including a list of how to add the Party page to your app.
author: RamaKrishnamoorthy 
ms.author: ramasri
ms.topic: article
ms.date: 11/23/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-11-16
---

# View party data

[!include [banner](../../includes/banner.md)]



Like account and contact data, party data can be accessed through a user interface (UI). The dual-write party and global address book solution version 3.3.0.5 provides a **Party** page where you can view, create, and manage party records together with all their associated customers, vendors, and contacts, and their postal and electronic addresses.

On the **Party** page, you can create a new party of the **Person** or **Organization** type.

The following illustration shows a party of the **Organization** type on the **General** tab.

![Example of a party of the Organization type.](media/ViewParty_Image1.PNG)

After a party is created, you can use the tabs on the **Party** page to manage it.

## Customers and Vendors tabs

The **Customers** tab lets you create and manage one or more customers from the party for different companies. If the party type is **Person**, you can create and manage customers of the **Person** type. These customers are known as *contacts*. If the party type is **Organization**, you can create and manage customers of the **Organization** type. These customers are known as *accounts*. 

![Creating a customer for a party in the Quick Create: Account dialog box.](media/ViewParty_Image2.PNG)

The **Vendors** tab resembles the **Customers** tab, but it's used to create vendors of the **Person** or **Organization** type.

## Postal Addresses and Electronic Addresses tabs

The **Postal Addresses** tab lets you create and manage one or more postal addresses for the party. You can create as many postal addresses as the party requires. These addresses appear on the quotation and sales order pages.

![Example of a party's postal addresses.](media/ViewParty_Image3.PNG)

The **Electronic Addresses** tab lets you create and manage one or more electronic addresses for the party. You can create as many electronic addresses as the party requires.

![Creating an electronic address for a party in the Quick Create: Party Electronic Address dialog box.](media/ViewParty_Image4.PNG)

## Associated Contacts tab

The **Associated Contacts** tab lets you create contact persons (**Contact for party** records) and associate them with the party.

![Creating an associated contact for a party in the Quick Create: Contact for Customer or Vendor dialog box.](media/ViewParty_Image5.PNG)

## Add the Party page to your app

You can add the **Party** page to your app by using site maps.

1. In your custom solution, under the **Components** node, find and select the **Model-driven Apps** node. Then select **Add Existing**.
2. In the **Select Solution Components** dialog box, find and select the app that should include the Party entity or other entities that have been created as part of dual-write solutions. In this example, you're updating the Sales Team Member app so that it includes the Party entity.

    ![Sales Team Member app selected in the Select Solution Components dialog box.](media/ViewParty_Image6.png)

3. Open the app.
4. In App Designer, on the **Components** tab on the right, under **Artifacts**, select **Entities**.

    ![Entities button on the Components tab in App Designer.](media/ViewParty_Image7.png)

5. Find and select the **Party** (**msdyn_party**) entity.

    ![Party (msdyn_party) entity selected on the Components tab in App Designer.](media/ViewParty_Image8.png)

6. Select **Save**.
7. Find and select the **msdyn_partyelectronicaddress**, **msdyn_vendor**, **msdyn_postaladdress**, and **msdyn_contactforparty** entities, so that the **Quick Create** dialog boxes for those tables are available on the parties page.

    ![Selecting additional entities on the Components tab in App Designer.](media/ViewParty_Image13.PNG)

8. Select **Save**.
9. In the main part of the page, in the **Site Map** section, select the **Edit** button (pencil symbol) on the **Site Map** tile.

    ![Edit button on the Site Map tile in App Designer.](media/ViewParty_Image9.png)

10. In Sitemap Designer, drag **Subarea** from the **Components** tab on the right to the section that you have to customize on the left. In this example, you're adding the new subarea to the **Customers** section.

    ![New Subarea component added to the Customer section in Sitemap Designer.](media/ViewParty_Image10.png)

11. Select the **Edit** button (pencil symbol) next to the new subarea. Then, on the **Properties** tab on the right, set the **Type** field to **Entity** and the **Entity** field to **Party**.

    ![Type and Entity fields set on the Properties tab in Sitemap Designer.](media/ViewParty_Image11.png)

12. Select **Save** and then **Publish** to make the **Party** entity available in the app.

    ![Party entity available in the Sales Team Member app.](media/ViewParty_Image12.png)
