---
# required metadata

title: Workflow subsystem updates in finance and operations
description: This article reviews the workflow system in finance and operations.
author: ChrisGarty
ms.date: 06/20/2017
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
ms.assetid: 0e3aa2cd-2327-45ba-bf38-0ef543fa8f67
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Workflow subsystem updates in finance and operations

[!include [banner](../includes/banner.md)]

This article reviews the workflow system in finance and operations. It describes the changes that have been implemented since Microsoft Dynamics AX 2012 and also includes links to more information about the workflow system. 

The workflow system in finance and operations will be familiar to you if you've used Dynamics AX 2012. For more information about the workflow subsystem in Dynamics AX 2012, see the following topics.

| To learn about this subject | See this article                                             |
|-----------------------------|------------------------------------------------------------|
| The workflow system         | <https://technet.microsoft.com/library/dd309672.aspx> |
| Workflow types by module    | <https://technet.microsoft.com/library/dd362043.aspx> |
| Workflow elements           | <https://technet.microsoft.com/library/dd309626.aspx> |
| Workflow actions            | <https://technet.microsoft.com/library/dd362144.aspx> |
| Workflow participants       | <https://technet.microsoft.com/library/dd309598.aspx> |
| Workflow examples           | <https://technet.microsoft.com/library/dd309636.aspx> |
| Developing a workflow       | <https://msdn.microsoft.com/library/cc967389.aspx>    |
| Implementing a workflow     | <https://msdn.microsoft.com/library/cc585061.aspx>    |

## Primary changes to the workflow system
Here are the primary changes that have been implemented in finance and operations:

-   Integration with the new Application State Machine feature enables workflow events to be bound to state transitions on the underlying entity's state machine. This binding enables business logic to be centralized within the state machine and also enables the workflow system to be a declarative consumer of that state machine. The workflow metadata can reference a state transition that is performed when a specific workflow event occurs. Therefore, you can do state transitions within a workflow without writing any additional code.
-   The workflow editor is now a program that you click one time to download. The editor communicates with finance and operations by using services, which means that you can carry forward the rich, graphical workflow design experience from Dynamics AX 2012.
-   Workflow development wizards have been ported into Microsoft Visual Studio.


## Additional resources

[Technical Concepts Guide for Developers](../dev-tools/developer-home-page.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
