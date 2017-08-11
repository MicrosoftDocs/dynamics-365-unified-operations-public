# Mobile workspace business logic events
Mobile workspace business logic events provide places for developers to specify workspace configuration to enhace capability, and implement business-scenario-specific behaviors. All mobile business logic executes in the process of the mobile app, and busines logic execution flow is controlled by the Operations mobile app framework. 

Code that exeutes in business logic can make runtime modifications to the metadata of Pages, Actions and Controls. These runtime modifications will overlayer the static metadata that is cached in the app, but the modifications do not directly change the cached static metadata, nor do they affect the static metadata that is stored on the server. These runtime modifications only persist until the app is closed. 

Code that executes in the business logic of the app can make runtime modifications to business data that is stored in the app. These modifications (when performed according to correct practices) participate in the normal data processing framework as other business data in the app. That means adhering to the offline-first capabilities and asycnrhonous save behaviors provided by the framework.

***
## Workspace initialization
The workspace initialization event is intended for performing static configuration of metadata in the workspace. The behavior of the initialization should not depend on business data. However, it may depend on user-specific or company-specific information, and other event handlers that are registered inside of the initialization may be passed business data when they are later executed.

The workspace initialization event is fired by the framework only when:

* The user navigates to the workspace's landing Page for the first time after opening the app (such as if the user closes, and then re-opens the app).
* The user performs a pull-to-refresh while they are viewing the workspace's landing page.

The code in the event executes synchronously and will completely finish execution before the user sees the landing page. 

#### arguments 

* (object) the read-only workspace metadata

#### example

`appInit: function (appMetadata) { /// initialization code here }`
***
