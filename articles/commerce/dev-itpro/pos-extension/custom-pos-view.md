---
# required metadata

title: Create a Custom View in POS
description: This topic walkthrough how to create custom View in POS.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# Create a Custom View in POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to create custom View in POS, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

Creating a custom view in POS is a great way to add new functionality to POS. Creating a new view is best in scenarios where you want to support additional scenarios in POS whereas a custom dialog is better suited to extend existing POS workflows.

All new views in POS should extend from the CustomViewControllerBase class in the “PosApi/Create/Views” module, and should implement the following abstract methods.

**onReady:** The POS framework will call the view’s onReady method will be called when the page has been added to the DOM. This method is responsible for rendering the view inside of the provided HTML element.

**dispose:** The POS framework will call the view’s dispose method when the view is removed from the DOM and the POS navigation history. This method should release any resources created by the view.

In addition to the required methods above a custom view controller can also implement the page life cycle methods below.

**onShown:** This method will be called every time when the view is displayed.
**onHidden:** This method will be called every time when the view is hidden.

### Configuring the custom view controller

The CustomViewControllerBase class accepts an optional configuration object that enables extension views to control common view functionality like the title of the page and the AppBar. The page title specified in the config object will be displayed on the POS Header when the view is visible.
The values specified in the ICustomViewControllerConfiguration object will be transferred to the state field in the CustomViewControllerBase class, and some of them can be updated throughout the views lifecycle.
An example of configuring the custom view controller can be found in our sample here and in the snippet below.

```TypeScript
export default class ExampleView extends Views.CustomViewControllerBase {
    constructor(context: Views.ICustomViewControllerContext) {
        let config: Views.ICustomViewControllerConfiguration = {
            title: context.resources.getString("string_0001"),
            commandBar: {
                commands: [
                    {
                        name: "Create",
                        label: context.resources.getString("string_2001"),
                        icon: Views.Icons.Add,
                        isVisible: true,
                        canExecute: true,
                        execute: (args: Views.CustomViewControllerExecuteCommandArgs): void => {
                            this.createExampleEntity().then((entityCreated) => {
                                if (entityCreated) {
                                    // Re-load the list, since the underlying data was amended
                                    this.dataList.data = this.viewModel.loadedData;
                                }
                            });
                        }
                    },
                    {
                        name: "Edit",
                        label: context.resources.getString("string_2002"),
                        icon: Views.Icons.Edit,
                        isVisible: true,
                        canExecute: false,
                        execute: (args: Views.CustomViewControllerExecuteCommandArgs): void => {
                            this.state.isProcessing = true;
                            this.editExampleEntity().then((editsMade) => {
                                if (editsMade) {
                                    // Re-load the list since the underlying data changed
                                    this.dataList.data = this.viewModel.loadedData;
                                }
                                this.state.isProcessing = false;
                            });
                        }
                    },
                    {
                        name: "Delete",
                        label: context.resources.getString("string_1006"),
                        icon: Views.Icons.Delete,
                        isVisible: true,
                        canExecute: false,
                        execute: (args: Views.CustomViewControllerExecuteCommandArgs): void => {
                            this.state.isProcessing = true;
                            this.deleteExampleEntity().then(() => {
                                // Re-load the list, since the data has changed
                                this.dataList.data = this.viewModel.loadedData;
                                this.state.isProcessing = false;
                            });
                        }
                    },
                    {
                        name: "PingTest",
                        label: context.resources.getString("string_3001"),
                        icon: Views.Icons.LightningBolt,
                        isVisible: true,
                        canExecute: true,
                        execute: (args: Views.CustomViewControllerExecuteCommandArgs): void => {
                            this.state.isProcessing = true;
                            setTimeout(() => {
                                this.state.isProcessing = false;
                            }, 100);
                        }
                    }
                ]
            }
        };
        super(context, config);
    }
}
```
### Using the AppBar

The config object contains a commandBar which is used to add commands the POS AppBar when the custom view is visible. The command bar configuration contains a collection of command definitions to be displayed when the view is visible. These command definitions will be displayed in order with the first command being the furthest right on the page.

Each command definition must implement the ICommandDefinition interface which is exported from the “PosApi/Create/Views” module. Below is a list of the fields and methods on the command definition.

```TypeScript
export interface ICommandDefinition extends Commerce.Extensibility.ICommandDefinition {
    readonly execute: (args: CustomViewControllerExecuteCommandArgs) => void;
    readonly icon: Commerce.Framework.UI.IconName;
    readonly name: string;
    readonly label: string;
    readonly canExecute: boolean;
    readonly isVisible: boolean;
}
```
**execute:** This method will be executed when the command is invoked.

**icon:** This field defines the icon to be used for the command.

**name:** This field defines the command’s name which should be unique within the view where it is used.

**label:** This value will be used as the label on the AppBar for the command and should be localized.

**canExecute:** The value indicating if the command should be enabled when it is first created.

**isVisible:** The value indicating if the command should be visible when it is first created.

### Changing A Command’s Visibility and Enabling/Disabling commands

Once the commands are created in the constructor the isProcessing and canExecute fields on the commands can be updated within the view and the changes will control the enabled and visibility status of the commands on the UI.
The snippet below shows how to use the DataList’s “SelectionChanged” event to enable the “Edit” and “Delete” commands.

```TypeScript
public onReady(element: HTMLElement): void {
        // DataList
        let dataListOptions: IDataListOptions<Entities.ExampleEntity> = {
            interactionMode: DataListInteractionMode.SingleSelect,
            data: this.viewModel.loadedData,
            columns: [
                {
                    title: this.context.resources.getString("string_1001"), // Int data
                    ratio: 40, collapseOrder: 1, minWidth: 100,
                    computeValue: (data: Entities.ExampleEntity): string => data.IntData.toString()
                },
                {
                    title: this.context.resources.getString("string_1002"), // String data
                    ratio: 60, collapseOrder: 2, minWidth: 100,
                    computeValue: (data: Entities.ExampleEntity): string => data.StringData
                }
            ]
        };

        let dataListRootElem: HTMLDivElement = element.querySelector("#exampleListView") as HTMLDivElement;
        this.dataList = this.context.controlFactory.create(this.context.logger.getNewCorrelationId(), "DataList", dataListOptions, dataListRootElem);

        this.dataList.addEventListener("SelectionChanged", (eventData: { items: Entities.ExampleEntity[] }) => {
            this.viewModel.seletionChanged(eventData.items);

            // Update the command states to reflect the current selection state.
            this.state.commandBar.commands.forEach((command) => {
               if (command.name === "Edit" || command.name === "Delete") {
                  command.canExecute = eventData.items.length;
               }
            });
        });
    }
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
