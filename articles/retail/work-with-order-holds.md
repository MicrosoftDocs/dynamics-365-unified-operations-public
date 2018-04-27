---
# required metadata

title: Order holds
description: This topic describes holds on orders using Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 04/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: MCRHoldCodeTable, MCRSalesTableOrderHistory, MCRHoldCodeTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 79132
ms.assetid: 7c00dc35-73e5-400a-8587-22f37ddfc0e0
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Working with call center order holds

[!INCLUDE [banner](includes/banner.md)]

This topic describes order hold features for call center orders using Dynamics 365 for Retail.

# Configuration of call center order hold features

In order to use the call center order hold features, hold codes must be defined.  Navigate to **Sales and marketing** \> **Setup** \> **Sales orders** \> **Order hold codes** to create a set of user-defined hold codes based on your business needs.   If desired, one of the codes can be flagged as the default when creating a hold on a sales order by using the **Default for sales order** slider.  If a sales order has reserved inventory and there is a need to systematically remove those reservations if the order is placed on hold for a particular reason, set the **Remove inventory reservations** slider to **Yes** for those reason codes.

Navigate to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters** and in the **General** tab under the **Sales setup** fast tab, set the **Note type** parameter to indicate the type of note that will be captured when users enter optional notes when placing a sales order on hold.   Use the **On Hold sales order status** field to define a color that will be used to highlight sales orders that are on hold when viewing them from the **Customer service** form.  

Navigate to **Retail** \> **Channel setup** \> **Info codes** to create an optional set of hold reason codes.  These can be used as a secondary reason code to further define the main hold code if desired.  Click **New** to create a reason code set and use the **Subcodes** action to define the list of additional reasons.

Navigate to **Retail** \> **Channels** \> **Call centers** \> **All call centers** to link the optionally defined Info codes to the call center channel.  This is configured on the **General** fast tab in the **Hold code** field.

# Placing orders on hold

Orders created by a call center user in the backoffice Dynamics 365 for Retail application can be put on hold manually or systematically in certain situations.

During order entry and prior to order submission/confirmation, the user may wish to place the order on hold manually to prevent the order from being released to the warehouse for further processing.  This may be necessary if the customer placing the order is not ready to commit to the order, or perhaps critical data is missing that would be required for the order to process.   

From the order entry screen, the call center user may place an order on hold by using the **Order holds** option found in the **SALES ORDER** tab of the order entry menu.  A call center user can alternatively create an order hold by clicking the **Hold** menu option from the **Sales order summary** form which appears when the user chooses the **Complete** action on a call center sales order.   

Either method of execution will open the **Order holds** form where the user may select the **New** action to create a hold on the order.  The user should select an appropriate code in the **Hold code** field that best describes the reason for holding the order.  The user can optionally also select an additional code in the **Reason code** field that may provide a second level of description for the hold.

From the **Notes** fast tab, the user may add additional free-form notes in the **Hold Notes** textbox to give additional context or information about the hold to help others who may be reviewing or working to manage the hold order in the future.

Once the hold information is created and saved, the user may close the **Order holds** form which returns them to the sales order entry form.  If there are no further actions needed on the sales order, the user may close the sales order form.  

When an order is placed on hold, adding a payment to the order when the **Enable order completion** flag is turned on in the call center channel is optional.   A payment will still be necessary before the order hold is released, but unlike a sales order that is not held, the system will not force the user to apply a payment in order to leave the sales order entry form.

Call center users also may place a manual fraud hold on orders that are being held due to suspicious reasons.  Orders can also be put on hold systematically when they match active fraud criteria and rules.   Please see call center [fraud feature](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/set-up-fraud-alerts) documentation for more information on these types of order holds.

# Viewing and managing orders on hold

To view hold information for a single sales order:

From the **Customer service** form, you can see that an order is on hold visually based on the configuration of the **On Hold sales order status** parameter in **Accounts receivable parameters**.   The color selected in this parameter will be used to highlight the order line in customer service (note you can not see the color if the line is actively selected on the form).

Users can also view the **Detailed status** on the sales order to know if an order is on hold.  The **Detailed status** is accessible from the **All sales orders** or **Customer service** forms.  The **Do not process** flag will be enabled for held orders and the **Detailed status** field will indicate a status of **On Hold** or **Fraud Hold** depending on the scenario.

To view the details of an individual order hold, the user can open the **Order hold** screen in a detailed view from the **Customer service** form using the **Options** menu for the selected order.  A user can also access this same view from the **All sales order** form by clicking the **Order holds** menu option found under the **SALES ORDER** tab.

To view and manage all held orders:

Navigate to **Retail** \> **Customers** \> **Order holds** to view and work with all orders that have been placed on manual or systematic hold.

The **Order holds** workbench provides users with a list view of all orders on hold due to manual or fraud related hold actions.  Users can take advantage of standard filter/sort options on the form to create views which allow them to work with or manage specific hold codes that they may be responsible for reviewing.   The **Order holds** form gives users information indicating the number of days the order has been in hold to assist in prioritizing the queue.

To get additional details about the held orders, users can click the **Order hold** option from the menu. This opens a more detailed view of the orders on hold providing information about the customer, any notes that have been applied to the order, customer or hold action as well as details on the reason for systematic hold if the order was held due to a fraud rules match.

From the **Order holds** list or detailed view, users will have access to view/edit additional order related information such as payments, totals and notes.

The options found under the **HOLD CHECKOUT** tab provide an optional feature that may be useful if your company has multiple users all working the hold queue at the same time.  A user can click the **Check out** option under this menu to indicate they are working to review and investigate the order hold so that other users do not waste time also attempting to do the same work.  You can view information related to the checkout date/time and the user who has checked out the hold record from the detailed order hold view.

Once checked out, only the user that checked out the hold line can clear the checkout.  This is again to prevent other users from taking records being worked on by others.  The user can click the **Clear checkout** option to release the order back to the queue for others to work.  Please note that clearing the checkout does not release the hold.   

In certain situations (a user is out sick or has left the company) it may be necessary for a manager to re-assign a checked out record to another user.  This can be accomplished using the **Override checkout** function.

# Releasing orders on hold

From the **Order holds** form while in list or detailed view, the **CLEAR HOLD** tab on the menu contains the options for releasing the order hold.  Use the **Clear holds** option to release the order from the selected hold code.  Please note that call center orders require a payment and will fail to clear fully if a payment has not been applied.  Please ensure the **Submit when cleared** parameter has been enabled in the **Call center parameters form** on the **Holds** tab.  This will ensure a cleared hold order goes through the proper order submission logic to validate and authorize payments as needed. If payments are missing, the user will receive and error and the hold code will not be cleared. 

If the **Submit when cleared** parameter has not been set, users should select the **Clear and submit** option from the **CLEAR HOLD** menu to ensure the order goes through all of the necessary payment validations.  Failure to process the order submission when **Enable order completion** is enabled on your call center channel will result in the order being released from order hold status, but the **Do not process** flag will remain enabled causing the order to not release to the warehouse until proper payments have been applied and validated.

If the user wishes to clear the hold but also make additional changes to the order before it releases to further processing, they may choose the **Clear and modify** option.  This removes the hold code and opens up the sales order details to allow for additional order modification if desired.  This also gives the user an opportunity to apply payment and submit the sales order through payment validation logic when the **Enable order completion** flag has been set for the call center channel.

# Reporting options

Navigate to **Retail** \> **Inquiries and reports** \> **Call center reports** \> **Order holds report** to run a report on order holds by date range, hold code, or other related criteria.




