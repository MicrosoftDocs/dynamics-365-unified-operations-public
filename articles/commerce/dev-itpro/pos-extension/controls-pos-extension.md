---
title: Use POS controls in extensions
description: This topic explains how to use Point of Sale (POS) controls in extensions.
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

# Use POS controls in extensions

[!include [banner](../../../includes/banner.md)]

This topic explains how to use Point of Sale (POS) controls in extensions. It applies to version 10.0.18 and later of the Retail software development kit (SDK).

The **PosApi** library provides a consistent look and feel between the extension user interface (UI) and the rest of POS by giving access to common POS controls. These controls are available as interfaces in the **PosApi/Consume/Controls** module. Instances of these controls can be created by using the control factory that is provided in the extension context. The UI extension classes include views, dialog boxes, and custom controls.

The following example shows how to use the control factory to create a **DataList** control in the **onReady** function of a custom view controller.

```Javascript
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
        this.state.commandBar.commands.forEach(
            command => command.canExecute = (
                ["Create", "PingTest"].some(name => name == command.name) ||
                this.viewModel.isItemSelected()
            )
        );
    });

    this.state.isProcessing = true;
    this.viewModel.load().then((): void => {
        // Initialize the data list with what the view model loaded
        this.dataList.data = this.viewModel.loadedData;
        this.state.isProcessing = false;
    });
}
```

For more examples that show how to use POS controls and the control factory, see the [PosSample folder](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample) in the GitHub repository (repo).

## POS controls

The following POS controls are supported.

| Control | Interfaces | Description |
|---------|------------|-------------|
| Data list | IDataList, IPaginatedDataList | A responsive list control that is used throughout POS to show rows of information. |
| Date picker  | IDatePicker | The date picker control that is used in POS. |
| Menu | IMenu | The menu control that is used in POS to show contextual information. |
| Number Pad | IAlphanumericNumPad, ICurrencyNumPad, INumericNumPad, ITransactionNumPad | <p>Number pads that are used throughout POS. Different types of number pads have different behaviors and input formatting:</p><ul><li>**Alphanumeric numpad** – This type of number pad accepts alphanumeric input.</li><li>**Currency numpad** – This type of number pad accepts monetary values.</li><li>**Numeric numpad** – This type of number pad accepts only numeric values.</li><li>**Transaction numpad** – This type of number pad accepts item identifiers or quantities. It's typically used in transaction scenarios.</li></ul> |
| Time Picker | ITimePicker | The time picker control that is used in POS. |
| Toggle | IToggle | The toggle switch control that is used in POS. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
