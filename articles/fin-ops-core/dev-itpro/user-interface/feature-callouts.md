---
title: Feature callouts
description: Learn about feature callouts and the APIs that are used to construct them, with overviews on resetting feature callouts and disabling feature callouts.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/16/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-05-31
ms.dyn365.ops.version: Platform update 26
---

# Feature callouts

[!include [banner](../includes/banner.md)]


## Introduction
While documentation is helpful for explaining new features, it’s also important to raise awareness of these new capabilities as users encounter the feature while using the product. As a result, feature callouts are available in Platform update 26. You can use feature callouts to point out a new capability to a user and optionally provide a hyperlink for the user to learn more about the feature. 

In this article, the APIs that are used to construct feature callouts are discussed in detail.   

![Feature callout for Navigation Pane changes.](./media/cli_featureCallout_noLink.png "Feature callout for Navigation Pane changes released in Platform update 22")
  
## The "Got it" button
When a feature callout is triggered, the user can simply click the **Got it** button to dismiss the popup. This saves the state of this feature callout in the personalization subsystem, which prevents that specific feature callout from being triggered again. 

## Resetting feature callouts
Even though the feature callout state is stored in personalization, clearing personalizations will not delete the state of all previously dismissed feature callouts. Instead, separate actions have been added to reset all feature callouts so that they fire again. These actions are located on the **Personalization** tab on the **Usage data** page as well as on the **Manage per user** tab on the **Personalization** page.   

## Disabling feature callouts 
If needed, administrators can turn off feature callouts for an environment using the **Feature callouts enabled** option on the **Client performance options** page. 
  
## Implementation details
The SystemNotificationsWhatsNewManager class contains two variant APIs for triggering a feature callout. 

### AddWhatsNewWithActionLink() 
Add a feature callout to a control with a "Learn more" link that is configured to open the documentation associated with the new product capability.  

#### Parameters

| Parameter     | Description                                                               |
|---------------|---------------------------------------------------------------------------|
| ruleID        | Generate a unique GUID.                                                    | 
| title         | Provide a (localized) title.                                               | 
| bodyText      | Provide a (localized) description.                                         | 
| targetControl | Provide the name of the control you want to attach the feature callout to. | 
| urlLink       | Provide the URL to open in a new tab when the "Learn more" link is clicked. If a URL is not specified, then a "Learn more" link will not be displayed. |


### AddWhatsNew() 
Add a feature callout to a control without a "Learn more" link. 

#### Parameters

| Parameter     | Description                                                               |
|---------------|---------------------------------------------------------------------------|
| ruleID        | Generate a unique GUID.                                                    | 
| title         | Provide a (localized) title.                                               | 
| bodyText      | Provide a (localized) description.                                         | 
| targetControl | Provide the name of the control you want to attach the feature callout to. | 

### Example
The following code snippet will trigger a feature callout attached to the control named *TestStringControl*.  

```xpp
public void init() 
{
     super(); 
     
     SystemNotificationsWhatsNewManager::AddWhatsNewWithActionLink(
          MyTestKey, 
          "My title" , 
          "My description", 
          TestStringControl.name(), 
          "https://www.microsoft.com"
     );
}
```

## Notes
-  Multiple feature callouts can be shown on a page at one time.
-  Only one feature callout is allowed per control. If multiple callouts exist, the last one to get triggered will be displayed.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
