---
title: Use POS controls in extensions
description: This topic explains how to use POS controls in extensions.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Use POS controls in extensions

[!include [banner](../../../includes/banner.md)]

This topic explains how to use POS controls in extensions. It applies to the Retail SDK version 10.0.18 and later.

The **PosApi** library provides a consistent look and feel in the extension UI with the rest of POS by providing access to use common POS controls. These controls are available as interfaces in the **PosApi/Consume/Controls** module. Instances of these controls can be created using the **ControlFactory** provided in the extension context. The UI extension classes include views, dialogs, and custom controls.

The following code example shows how to use the **ControlFactory** to create a **DataList** control in the **onReady** function of a custom view controller.

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

More examples of how to use POS controls and the control factory can be found in the [PosSample folder](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample) of the GitHub repo.

## POS controls

The following controls are supported.

| Control | Interfaces | Description |
|---------|-----------|-------------|
| Data list | IDataList, IPaginatedDataList | The data list is a responsive list control used throughout POS to display rows of information. |
| Date picker  | IDatePicker | The date picker control used in POS. |
| Menu         | IMenu | The menu control used in POS to display contextual information. |
| Number Pad   | IAlphanumericNumPad, ICurrencyNumPad, INumericNumPad, ITransactionNumPad | Number pads are used throughout POS with various behaviors and input formatting.<ul><li>Alphanumeric numpad: Accepts alphanumeric input.</li><li>Currency numpad: Accepts monetary values.</li><li>Numeric numpad: Accepts only numeric values.</li><li>Transaction numpad: Accepts an item identifier or quantity. Typically used in a transaction scenario.</li></ul> |
| Time Picker | ITimePicker | The time picker control used in POS. |
| Toggle | IToggle | The toggle switch control used in POS. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
