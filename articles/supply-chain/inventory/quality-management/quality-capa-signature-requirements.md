---
title: Electronic signature requirement for CAPA case closure
description: An electronic signature confirms the identity of a person who is about to start or approve a computing process. This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off as well as when a CAPA case is reopened.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Electronic signature requirement for CAPA case closure

[!include [banner](../../includes/banner.md)]

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one. This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off as well as when a CAPA case is reopened.

## Setting up Electronic signature requirements

Using the Organization module, you maintain the various requirements for determining which events should trigger an electronic signature. For this feature, we have added the option to indicate that a signature is required for the event "Close/Cancel CAPA case". If selected, whenever the status of a CAPA case is changed to Closed or Canceled or when a CAPA case is reopened, electronic signature is required.

| **Path: Organization administration \> Setup \> Electronic signature \> Electronic signature requirements** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| New | Allows new electronic signature requirements to be added as User defined options. Requires customizations. |  |
| Delete | Allows a User defined electronic signature to be deleted. |  |
| Properties | Used when creating User defined electronic signature options as part of the customization. |  |
| **Fields** | &nbsp; | &nbsp; |
| Name | Represents the name of the electronic signature requirement. Built in requirements are available to the user without customizations. User defined requirements need customization. | Close/Cancel CAPA case is the new Built in Requirement that has been added as part of this feature. |
| Procedure type | Two options exist for procedure type. Built in means that they are ready to be triggered as desired without customization. User defined means that they have to be built. | This feature provides a Built in requirement as all of the work to turn this requirement on has been done as part of this feature. |
| Signature required | This checkbox represents which events in the system should drive an electronic signature to complete. | If desired, Close/Cancel CAPA Case can be selected which would then drive an electronic signature when a CAPA case is closed, cancelled or reopened. |
|  |  |  |

## Triggering Electronic signature from CAPA case close or cancel

From a CAPA Case, the Change status ribbon action is the trigger point for electronic signature if the "Close/Cancel CAPA Case" is selected under the Electronic signature requirements. The following chart represents the CAPA case status changes that trigger electronic signature.

| Initial CAPA case Status | Possible Status Changes | Will Electronic Signature be triggered? |
|-------------------------------------|------------------------------------|----------------------------------------------------|
| Opened                              | In Process                         | NO                                                 |
|                                     | Canceled                           | YES                                                |
| In Process                          | Opened                             | NO                                                 |
|                                     | Canceled                           | YES                                                |
|                                     | Closed                             | YES                                                |
| Canceled                            | Opened                             | YES                                                |
|                                     | In Process                         | YES                                                |
| Closed                              | Opened                             | YES                                                |
|                                     | In Process                         | YES                                                |

Using the Inventory Management module, you can process a CAPA case to completion. Adjusting the CAPA case status is an important step in the process. Closing or canceling a CAPA Case, will trigger an electronic signature. Additionally, if a CAPA Case has already been closed or canceled and the user wants to reopen it by changing the status back to Opened or In Process, Electronic signature will also be triggered. The user may also use the new Ribbon action of "Signature review" to review existing signatures against the selected CAPA case.

| **Path: Inventory management \> Common \> CAPA management \> All/My CAPA Cases** | &nbsp; | &nbsp; |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** | &nbsp; | &nbsp; |
| Signature review | Allows the users to review all existing electronic signatures against a given CAPA case. | Using the buttons on the bottom of this form, you can see all associated electronic signature records for the selected CAPA Case. This is offering a filtered view of the Database log/Signature review. |
