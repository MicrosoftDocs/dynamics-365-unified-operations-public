---
title: Create a custom view in POS
description: This topic explains how to create a custom view in Point of Sale (POS).
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Create a custom view in POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to create a custom view in Point of Sale (POS). It applies to version 10.0.18 and later of the Retail software development kit (SDK).

Custom views in POS are a great way to add new functionality to POS. This approach works best in scenarios where you want to support more scenarios in POS. If you want to extend existing POS workflows, a custom dialog box is a better approach.

All new views in POS are extended from the **CustomViewControllerBase** class in the **PosApi/Create/Views** module, and they must implement the following abstract methods:

+ **onReady** – The POS framework calls the view's **onReady** method when the page has been added to the Document Object Model (DOM). This method is responsible for rendering the view inside the HTML element that is provided.
+ **dispose** – The POS framework calls the view's **dispose** method when the view is removed from the DOM and the POS navigation history. This method should release any resources that the view created.

In addition to the preceding required abstract methods, a custom view controller can implement the following page lifecycle methods:

+ **onShown** – This method is called every time that the view is shown.
+ **onHidden** – This method is called every time that the view is hidden.

## Configuring the custom view controller

The **CustomViewControllerBase** class accepts an optional configuration object that enables extension views to control common view functionality, such as the title of the page and the app bar. The page title that is specified in the configuration object is shown on the POS header when the view is visible.

The values that are specified in the **ICustomViewControllerConfiguration** object are transferred to the **state** field in the **CustomViewControllerBase** class. Some of the values can be updated throughout the view's lifecycle.

The following example shows the configuration of the custom view controller. You can download the example from the [ExampleView.ts file](https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.28/src/PosSample/Pos.Extension/Views/ExampleView.ts) in the GitHub repository (repo).

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

## Using the app bar

The **config** object contains a **commandBar** configuration that is used to add commands to the POS app bar when the custom view is visible. The **commandBar** configuration contains a collection of command definitions that are shown when the view is visible. These command definitions are shown in order: the first command is farthest to the right on the page.

Each command definition must implement the **ICommandDefinition** interface that is exported from the **PosApi/Create/Views** module. Here is a list of the properties and methods for the command definition.

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

| Property | Description |
|---|---|
| execute | This field runs when the command is invoked. |
| icon | This field defines the icon that is used for the command. |
| name | This field defines the command's name. This name must be unique in the view where it's used. |
| label | This field defines the label that is used for the command on the app bar. This label should be localized. |
| canExecute | This field specifies whether the command should be enabled when it's first created. |
| isVisible | This field specifies whether the command should be visible when it's first created. |

## Changing a command's visibility, and enabling and disabling commands

After the commands are created in the constructor, their **isProcessing** and **canExecute** fields can be updated in the view. These updates control whether the commands are enabled and visible in the user interface (UI).

The following example shows how to use the data list's **SelectionChanged** event to enable the **Edit** and **Delete** commands.

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
