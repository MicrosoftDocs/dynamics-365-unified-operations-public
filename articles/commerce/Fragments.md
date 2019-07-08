---
# required metadata

title: Fragments
description: This topic describes why, when, and how to use fragments within the e-commerce authoring toolset.
author: Nick Holman
manager: Brendan Sullivan
ms.date: 07/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: phinneyridge
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Fragments overview
---
Fragments enable a centralized authoring experience for re-usable module configurations needed throughout your site. For example: headers, footers, and banners are often configured as fragments because they are shared across many pages. A great way to think of fragments is that they act like mini webpages that can be inserted into other pages within your site. Fragments have their own lifecycle, which means they are created, referenced, updated, and deleted as independent entities within the authoring tools. Once fragments are configured, they are available to use everywhere that a module can be used within your site structure. Fragments can be referenced within pages, templates, master templates, and even within other fragments (note: fragments can nest up to 7 levels deep).

As an example, let’s imagine a seasonal event that we want to promote across many pages within our site. We could use a fragment to do this. Our new fragment will begin by choosing a module type to start from. For this example, we could choose for our fragment to be built from a Hero module.
  > [!NOTE]
  > Fragments can be built from any module type. 
  
We can then configure this Hero fragment with our specific promotional content, and localize it if necessary. This new stand-alone Hero fragment is now consumable as a pre-configured module throughout our site. We can easily add it to templates, specific pages, or even within other fragments that can contain Hero modules. All the places where the fragment is added are references to the central Hero fragment that we created. If we decide to publish changes to our fragment, these will immediately be reflected everywhere the fragment is referenced across our site. Fragments are a powerful and efficient way to re-use and centrally manage module configurations within a site, and effective use can add up to significant agility and cost savings when managing site content.

![Common Concepts - Fragments Diagram 1](../commerce/media/fragment-figure1.png)
# Create a fragment

## Save as Fragment

To convert a module into a reusable fragment:

1)  Select an already configured module within your page.

2)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the name of the module you wish to convert into a fragment.

3)  In the dropdown action menu, select “Save as Fragment”. This will launch a new fragment modal window.

4)  Enter a name/metadata for your fragment.

5)  Click “OK”. This will save your module configuration as a fragment that can be added to other pages.


# Add or remove fragments within a page
## Add a fragment
To add a fragment to your page:

1)  First select a container or slot that allows children to be added to it. \[Controlling what is allowed for a container or slot is defined by the page’s template and module definitions, which is covered elsewhere\].

2)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the container or slot’s name to show the action dropdown menu.

3)  Select the “Add Fragment” option from the dropdown \[Note: As mentioned above, if the container or slot does not allow new child modules, the “Add Fragment” option will be disabled\].

4)  After selecting “Add Fragment” option, the Fragment Picker modal window will launch. The Fragment Picker modal is automatically filtered to show allowable fragments for the chosen container/slot (as determined by the page’s template or the container module definition).

5)  From the fragment options, search for and select one to add (If there are no options, you may first need to create a fragment from a supported module type for your container/slot).

6)  Click “OK”, and the new fragment will be added to your page within the originally selected container/slot.

## Remove a fragment
To remove a fragment from a slot or container within your page:

1)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the name of the fragment you wish to remove.

2)  In the actions dropdown menu select “Delete”. This will launch a confirmation dialog asking is you are sure you want to remove the fragment.

3)  Assuming you wish to remove it, click “OK” and the canvas will refresh without the fragment.
  > [!NOTE]
  > Removing a fragment from a page will *not* delete the fragment from your site, and will only remove the reference to it from within the current page.  Deleting a fragment from your site must be done from the fragment inspector UI, and can only be performed if no pages, templates, or other fragments reference it.
# Edit a fragment
Todo

