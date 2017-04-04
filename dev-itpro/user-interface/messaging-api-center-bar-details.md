---
# required metadata

title: Message center, message bar, and message details API
description: This topic describes the messaging system.
author: sericks007
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 64153
ms.assetid: b69ec992-9bde-469e-99bb-773feb9489ff
ms.search.region: Global
# ms.search.industry: 
ms.author: aorth
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Message center, message bar, and message details API

This topic describes the messaging system.

Message API
-----------

Microsoft Dynamics AX 2012 has an all-purpose, "one size fits all" window that displays a list of the most calls to **info()**, **warning()**, and **error()**. This window was appropriately and generically named the "Information Log," or “Infolog” for short. Although the Infolog was a useful tool in some cases, its “one size fits all” approach was deemed ineffective for differentiating severity and determining whether the user should be interrupted. Microsoft Dynamics 365 for Operations has implemented a new messaging system to improve the experience. This richer, more powerful messaging system that includes the following features:

-   Improved association of a message with its context (form versus global).
-   Improved level of interruption (none, subtle, and interrupting).
-   Improved clarity between types of messages and their use.
-   The control that is used to display messages is deterministic and based on form context.

## Legacy API support: info(), warning()/checkfailed(), and error()
The legacy **info()**, **warning()**, and **error()** application programming interfaces (APIs) are still supported. However, they now sit upon the framework's new messaging system, and their destination is deterministic. In other words, it uses the context of the call to determine the best way to present the message to the user. In general, if the use of the API originated from a form, the message appears in a message bar on that same form. (A drop dialog and a slider dialog are both considered forms.) **Note:** There are a few exceptions to this rule. If the message API was called from a slider dialog, and that dialog was closed, the message appears on the slider's parent form. Alternatively, if that slider was closed, and it was hosted by a workspace, the message is routed to the Message center. The message API never "eats" a message. If an appropriate host form isn't found, the message is sent to the Message center. The following screen shot shows the info, warning/checkfailed, and error bars. [![1\_API](./media/1_api.jpg)](./media/1_api.jpg)

## Message API and batch or asynchronous operations
If **info()**, **warning()**/**checkfailed()**, or **error()** is called from an asynchronous process (for example, a batch), there is no form context to consider, and the messages are sent to the Message center. (To open the Message center, click the flag icon on the navigation bar.) [![2\_API](./media/2_api.png)](./media/2_api.png)

## Legacy API support: SetPrefix()
This version also supports the **SetPrefix()** API. This too remains backward-compatible. However, in Dynamics 365 for Operations, the results of **SetPrefix()** don't actively interrupt the user. Instead, the results are collected and stored (as in previous versions), and a message bar or Message center notification is presented to the user. This notification indicates that the related task has been completed, and that it might have messages that the user should review. The "Notification of results" message actually uses the task's first call to **SetPrefix()** to frame the message. This behavior is similar to the behavior in previous versions, where the first call was the "title" of the results. In this example, "Posting Results" comes from the application's first call to **SetPrefix()**.[![3\_API](./media/3_api.png)](./media/3_api.png) The user can then click **Message Details** to open the new **Message details** pane. [![4\_API](./media/4_api.png)](./media/4_api.png)

| Message type | Description                                                                                                                                                                                                                                                                                                                                  |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Info         | A *notification* informs a user about events that are unrelated to the current user activity. The notification can be caused by a user action or significant system event, or it can offer potentially useful information from the product. You notify the user by using the **info()** API.                                                 |
| Warning      | A *warning* alerts the user about a condition that might cause a problem in the future. Data that is in an incorrect state isn’t an error. However, an attempt to use that data might cause an error, and therefore invalid data triggers a warning. You express data validation issues by using the **warning()** or **checkfailed()** API. |
| Error        | An *error* alerts a user about a problem that has already occurred. A user action that has failed triggers an error. You express a passive error (non-interrupting) by using the **error()** API. You express an interrupting error to the user by using the **box::** API.                                                                  |

The messaging system is deterministic. Results are displayed in either a message bar or the Message center, depending where the message is called from in the code:

-   For messages that are the result of synchronous form actions (actions where the user must wait for the result), the results are displayed in a message bar on the current form. The exceptions are messages for a slider dialog that was closed just after the action was started. Those messages appear on the parent form.
-   For asynchronous (disconnected) actions, where the user can continue to do other tasks while the action is being processed, the results are displayed in the Message center.

If a synchronous or other form action or evaluation produces an error, there can be two types of errors:

-   An interrupting error, where a direct action can't be completed and must be corrected immediately. This type of error is shown in a dialog.
-   A non-interrupting error, which is often the result of a task/batch operation failure. This type of error is shown in a message bar.


See also
--------

[User interface development home page](user-interface-development-home-page.md)

