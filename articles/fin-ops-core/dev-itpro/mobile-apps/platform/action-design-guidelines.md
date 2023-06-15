---
title: Action design guidelines
description: This article provides action design guidelines for mobile apps.
author: jasongre
ms.date: 05/24/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
ms.collection: get-started
---

# Action design guidelines

[!include [banner](../../includes/banner.md)]
[!include [mobile app deprecated](../../includes/mobile-app-deprecation-banner.md)]

Actions let users create, update, or delete data, and also run business processes on that data (such as *submit*, *confirm*, and *post*). A user who completes an action first supplies the data for the action (if the action accepts data input). When the user has finished supplying the data, the action is put into a queue of similar actions (which are sometimes referred to as *data sync operations*). If the device is connected/online, the queue is processed immediately. Otherwise, it's processed the next time that the device is connected. The queue is processed asynchronously and doesn’t require the user’s attention unless there is an error during data synchronization. Errors of this type can occur because of server-side data validation. Actions are powered by a server-side mechanism that resembles Task recordings. This mechanism extracts the user’s input from the action and then automatically runs the business process steps on the server by using the input values that the user supplied. The mechanism automatically opens forms, clicks buttons on the forms, and enters the user's input into controls on the forms. This process of playing back the action against the forms on the server occurs asynchronously, against “headless” forms. The mobile app informs the user when the process is completed, and shows the user any info, warning, or error messages that the forms logged. When you design an action, it’s important that you first consider what entity the action is related to. In the current framework, an action must operate on only one entity. An action should not update multiple entities at the same time. For example, an action to create a new sales order should create only the header for the order. It should not also try to create lines, because the lines are separate entities. When you decide to design the action, consider the following questions to determine how to proceed.

### How do I design an action that enables an entity to be created?

1.  Identify or create a list view page for the entity.
2.  Make sure that the form that is used for the list view page includes a **New** button that can be used to add new records to the list.
3.  Use the designer to create a new action for the page. While you're designing the action, be careful not to perform any unnecessary actions. Enter data only in those fields that should be available to the user, and click only those buttons that are required (for example the **New** button and the **Save** button).

### How do I design an action that enables an entity to be edited?

1.  Identify or create a details view page for the entity.
2.  Make sure that the form that is used for the details view page includes an **Edit** button that can be used to edit the visible record.
3.  Make sure that the form that is used for the details view page lets users open a specific record by applying filters in the filter pane.
4.  Use the designer to create a new action for the page. While you're designing the action, be careful not to perform any unnecessary actions. Enter data only in those fields that should be available to the user, and click only those buttons that are required (for example, the **Edit** button and the **Save** button).

### How do I design an action that enables an entity to be deleted?

1.  Identify or create a details view page for the entity.
2.  Make sure that the form that is used for the details view page includes a **Delete** button that can be used to delete the visible record.
3.  Make sure that the form that is used for the details view page lets users open a specific record by applying filters in the filter pane.
4.  Use the designer to create a new action for the page, and just click **Delete** as a part of the process of designing the action.

### How do I design an action that enables a business action to be performed on an entity?

1.  Identify or create a details view page for the entity.
2.  Make sure that the form that is used for the details view page includes a **Delete** button that can be used to delete the visible record.
3.  Make sure that the form that is used for the details view page lets users open a specific record by applying filters in the filter pane.
4.  Use the designer to create a new action for the page, and just perform the steps that are required in the business action. You don't necessarily have to enter data in fields as part of the action. For an action such as *submit*, you just have to click the **Submit** button (and acknowledge any confirmations that appear).

### How do I design an action that enables a field value to be set via a rich lookup?

Lookups for fields in the mobile app don't have a correlation to the advanced lookup behaviors in the cloud version of the app. Regardless of whether you have a custom lookup in the cloud vesion of the app or an automatic lookup that uses a simple query, the mobile app doesn't run existing lookup code when it must determine which UI to show the user. (Remember that the user might be offline while using the app, and server-side code isn’t run until the action is synchronized.) However, lookup/control overrides such as *modified* are run when the value is set by the mobile back end as it synchronizes the data from the action. When the mobile app detects that a field on an action was selected from a lookup field on a form, it shows a device-native combo box/list picker control, and populates the items by directly querying the backing table of that lookup field. The items in the list show the user data from the TitleField for records in that table. Follow these steps to add the rich lookup experience to your action. This lookup experience includes a full-page multi-column lookup selector that has offline search.

1.  Identify or create a list view page for the entity behind the lookup. You can reuse existing list view pages that you've already created.
2.  After you've finished designing the action, select the field to add rich lookup functionality to, and then click **Properties**.
3.  In the **Control properties** dialog box, select the list view page that you identified or created in step 1, and set the other related properties. 

![Setting the control properties.](media/lookupdesigner.png)

4.  Save and publish your changes to the action.

If you don't see the property for the existing list view page or can't access the **Control properties** dialog box when you're designing your action, you might be using an older build of the app. In this case, you can still add rich lookup functionality by using a business logic file.

```xpp
function main(metadataService, dataService, cacheService, $q) { 
    return { 
        appInit: function (appMetadata) { 
            metadataService.configureLookup(
                // specify the name of the Action to add the lookup to
                'Add-Reservation',                      
                // specify the name of the Action’s field to add the lookup to
                'FMRental_Customer',                    
                { 
                    // specify the name of the Page for the Entity for the lookup
                        lookupPage: 'All-Customers',          
                    // specify the Page’s field which contains the value to set on the lookup
                // this value should be the same value you can type into the field on the Form
                        valueField: 'FMCustomer_RecId',        
                        // specify the Page’s field which contains the value to display to the user
                        // this value is only used for display. The value field is passed to the Form
                        displayField: 'FMCustomer_FullName',  
                        // set this to true to enable the rich lookup
                        showLookupPage: true                  
                }
            );
        }, 
    }; 
}
```

### How do I prevent an action from appearing in the list of actions for a page?

To prevent an action from appearing in the list of actions for any page, call the following code from the **appInit()** section of your business logic. In this code, **action-name** is the name of your action (as specified in the **Action name** field in the designer).

```xpp
function main(metadataService, dataService, cacheService, $q) { 
    return { 
        appInit: function (appMetadata) { 
            metadataService.configureAction('action-name', { visible: false });
        }, 
    }; 
}
```

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
