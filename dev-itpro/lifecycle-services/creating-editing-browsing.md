---

title: Create, edit, and browse BPM libraries
description: This topic provides information about how to create or edit a BPM library and how to browse an existing library..
author: kfend
manager: AnnBe
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service:  dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 13301
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ntecklu
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---
# Create, edit, and browse BPM libraries

[!include[banner](../includes/banner.md)]

This topic provides information about how to create or edit a BPM library.

## Create a new BPM library

1. On the **Business Process Libraries** page, select **New library**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost04-300x172.png "image")

2. Enter a library name, and then click **Create**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost05-300x188.png "image")

3. The new library is now available to users in the current project.
4. Select the library to open it in BPM. Use BPM to build, edit, and browse your library.

## Add a new process

1. Select an existing process in your library.
2. On the toolbar, click **Add process**. Here you can add a process as a child or sibling of the selected process node. This allows you to create a semantic hierarchy of business processes.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost06.png "image")

## Edit the properties of a business process

1. In the BPM library, select the process node that you want to edit.
2. In the **Overview** pane, click **Edit mode**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost07.png "image")

3. Enter a name and a description for the process node.
4. Select the industries and countries/regions that this process applies to. Here you can also add keywords and links. Keywords can be used to define categories, work streams, or other metadata. Links (URLs) allow you to reference external sites or documentation.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost08-194x300.png "image")

5. When you are finished editing, click **Save**.

## Move a process node

You can move or assign a business process node to another parent node in the BPM hierarchy.

1. Select the process node that you want to move, and then on the toolbar, select **Move process**. You can move up, down, or select **Move** for more options.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost09.png "image")

2. If you select **Move** , you can browse the hierarchy, select a destination node to move to, and then select **Move as child** or **Move as sibling**. 
3. Click **Cancel** to cancel the move operation.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost10.png "image")

## Delete a process

To delete a business process, select the process that you want to delete, and then on the toolbar, select **Delete**.

## Copy a Global or Corporate library to your project

You can browse a BPM library that is a Global or Corporate library. However, to edit and work with a BPM library, it must be part of your LCS project. Libraries distributed by Microsoft appear under **Global libraries**, while libraries that are published by your organization appear under **Corporate libraries**.

Use this guide to copy a global or corporate library to your project

1. In your LCS project, open the **Business process libraries** page.
2. On the tile of the library that you want to copy, click the ellipsis (…), and then select **Copy**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost11.png "image")

3. Enter a library name, and then click **Create**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost12.png "image")

## Browse a BPM library
1. On the **Business process libraries** page, double-click the tile of the library that you would like to browse.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/1.PNG "image1")

2. In the BPM library, select a process to view it's substeps.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/2.PNG "image2")

3. Use the toolbar to add, delete, or import processes as a child or sibling. You can also select **Collapse all** to view only parent processes. 

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/3.PNG "image3")

## Search a BPM library

You can search for words or phrases in your BPM library. The search functionality searches through business process names and descriptions.

- To search for a _word_, enter the word in the search bar and press **Enter**.
- To search for a _phrase_, use double quotes around the search phrase. For example, enter _technology_ (word) or _&quot;information technology&quot;_ (phrase) in the search bar.
- You can also search for AOT elements that are part of the Dynamics 365 for Operations Task recordings in your library. These are typically form names or menu items names. When you search for an AOT element, prefix it with the $ sign. For example, _$CustTable_.

![image 10](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/searching.png "image10")
