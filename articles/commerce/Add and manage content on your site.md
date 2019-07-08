---
# required metadata

title: 
description: This topic describes...
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

# Page Editing

## Select Content to Edit

Selecting content to edit within your page can be done in two places within the page editor:

### Select Content in the Canvas

> The most visual method for selecting something to edit is to simply click on it in the canvas preview. This will highlight the editable item with a blue border and bring up the item’s editable controls to the right in the Property Panel. Empty or unconfigured items are shown as selectable grey boxes in the Canvas.
### Select Content in the Outline View

> For more precise control over selection, or to find items that may not be easily discovered within the canvas (example: fifth Hero module within a Carousel container), the Outline View provides a better option to find and select items. Navigate through your page using the expand and collapse arrows in the Outline View. Select an item to edit by clicking on it.
Content selection between the Canvas, Outline View, and Property Panel are always linked, meaning whatever is selected in the Canvas or Outline will also be selected in the other two views.

## Add a Module

To add a module to your page:

1)  First select a container or slot that allows a child module to be added to it. \[Controlling which modules are allowed for a container or slot is defined by the page’s template and module definitions, which is covered elsewhere\].

2)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the container or slot’s name to show the action dropdown menu.

3)  Select the “Add Module” option from the dropdown \[Note: As mentioned above, if the container or slot does not allow new child modules, the “Add Module” option will be disabled\].

4)  After selecting “Add Module” option, the Module Picker modal window will launch. The Module Picker modal is automatically filtered to show only allowable modules for the chosen container/slot (as determined by the page’s template or the container module definition).

5)  From the module options, search for and select one to add to your page (‘Feature’ or ‘Hero’ modules are good ‘*Hello World’* options if trying out for the first time). Click “OK”, and the new module will be added to your page within the originally selected container/slot.

## Configure a Content Module

To configure a content module that is in your page:

1)  Select a content module on your page (examples: Feature, Hero, Banner, etc.).

2)  Notice that the selected module’s settings and content controls are displayed in the Property Panel on the right. Expand some of the nested controls in the property panel by clicking on the headers. Set any required control values, which are indicated by “\*” and validation warnings.

3)  If there is a “Data Configuration” section in the Property Panel, click to expand it.

4)  If there is a “Add Data Source” dropdown button, click it and select any content items you want to add \[For ‘Feature’ or ‘Hero’ modules, add ‘Heading’ and ‘Image’ to begin with\].

5)  Enter settings for any required or desired module controls.

6)  In the Action Button bar above the canvas click the ‘Save’ button. This will refresh the canvas with your new module settings.

## Configure a Container Module

To configure a container module that is in your page:

1)  Select a container module within your page (examples: Carousel, Fluid Container).

2)  Notice that the selected module’s settings and content controls are displayed in the Property Panel on the right. Expand some of the nested controls in the property panel by clicking on the headers. Set any required control values, which are indicated by “\*” or by validation warnings.

3)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the container’s name or next to any slots within the container. The action menu will display and you can follow the same steps enumerated in the “Add a Module” section above to populate your selected container with child modules.

## Remove a Module

To remove a module from a slot or container within your page:

1)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the name of the module you wish to remove.

2)  In the actions dropdown menu select “Delete”. This will launch a confirmation dialog asking is you are sure you want to remove the module.

3)  Assuming you wish to remove it, click “OK” and the canvas will refresh without the deleted module.

## Save as Fragment

To convert a module into a reusable fragment:

1)  Follow the previous instructions to configure your module.

2)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the name of the module you wish to convert into a fragment.

3)  In the dropdown action menu, select “Save as Fragment”. This will launch a new fragment modal window.

4)  Enter a name/metadata for your fragment.

5)  Click “OK”. This will save your module configuration as a fragment that can be added to other pages.

## Add a Fragment

To add a fragment to your page:

1)  First select a container or slot that allows children to be added to it. \[Controlling what is allowed for a container or slot is defined by the page’s template and module definitions, which is covered elsewhere\].

2)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the container or slot’s name to show the action dropdown menu.

3)  Select the “Add Fragment” option from the dropdown \[Note: As mentioned above, if the container or slot does not allow new child modules, the “Add Fragment” option will be disabled\].

4)  After selecting “Add Fragment” option, the Fragment Picker modal window will launch. The Fragment Picker modal is automatically filtered to show allowable fragments for the chosen container/slot (as determined by the page’s template or the container module definition).

5)  From the fragment options, search for and select one to add (If there are no options, you may first need to create a fragment from a supported module type for your container/slot).

6)  Click “OK”, and the new fragment will be added to your page within the originally selected container/slot.

## Remove a Fragment

To remove a fragment from a slot or container within your page:

1)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to the name of the fragment you wish to remove.

2)  In the actions dropdown menu select “Delete”. This will launch a confirmation dialog asking is you are sure you want to remove the fragment.

3)  Assuming you wish to remove it, click “OK” and the canvas will refresh without the fragment \[Note: this will *not* delete the fragment from your site, and will only remove the reference to it from within the current page\].

## Order Modules and Fragments

To reorder a module or fragment within its parent container/slot:

1)  In either the Outline View or the Canvas, click the ellipse button (“…”) next to a module that has multiple siblings within the same container/slot.

2)  Select either the “Move Up” or “Move Down” option from the displayed actions menu. This will move the selected module up or down one position relative to other modules within the same container/slot.
