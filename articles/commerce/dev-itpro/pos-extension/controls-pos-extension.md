---
# required metadata

title: Using POS Controls in Extensions
description: This topic explains how to use POS Controls in Extensions.
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

# POS Controls in Extensions

[!include [banner](../includes/banner.md)]

This topic explains how to use POS Controls in Extensions, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

The PosApi library enables extension UI to maintain a consistent look and feel with the rest of POS by providing access to use commonly used POS controls in extensions. These controls are available as interfaces in the “PosApi/Consume/Controls” module, and instances of these controls can be created using the Control Factory provided in the extension context for UI extension classes like Views, Dialogs and Custom Controls. 
The example below shows how to use the ControlFactory to create a DataList control in the onReady function of a custom view controller.

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

More examples of how to use POS controls and the control factory can be found in the [PosSamples](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample).

### POS Controls List

| Control Name | Interface Name(s)                                                        | Description                                                                                                                                        |
|--------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| Data List    | IDataList, IPaginatedDataList                                            | The data list is a responsive list control used throughout POS to display rows of information.                                                     |
| Date Picker  | IDatePicker                                                              | The date picker control used in POS.                                                                                                               |
| Menu         | IMenu                                                                    | The menu control used in POS to display contextual information.                                                                                    |
| Number Pad   | IAlphanumericNumPad, ICurrencyNumPad, INumericNumPad, ITransactionNumPad | The number pads are used throughout POS with a variety of different behaviors and input formatting.                                                                                                                                                                 <br />The alphanumeric numpad is designed to accept alphanumeric input. <br />The currency numpad is focused on scenarios where the user will be inputting monetary values.                 <br />The numeric numpad is optimized for scenarios where the user will only be entering a numeric value.                                                                             <br />The transaction numpad behavior is targeted for transaction scenarios where the user is likely to be inputting an item identifier and/or quantity.  |
| Time Picker         | ITimePicker                                 | The time picker control used in POS.                                                                                    |
| Toggle         | IToggle                                                                    | The toggle switch control used in POS.                                                                                    |