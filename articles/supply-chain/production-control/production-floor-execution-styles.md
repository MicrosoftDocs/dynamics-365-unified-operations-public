---
# required metadata

title: User interface control styles for production floor execution
description: This topic contains the requirements through which the different form controls can automatically pick up the default Production Floor Execution styles.
author: TBD
manager: tfehr
ms.date: 02/22/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

audience: Developer
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: inkharki
ms.search.validFrom: 2021-02-22
ms.dyn365.ops.version: Release 10.0.15
---

# User interface control styles for production floor execution

[!include [banner](../includes/banner.md)]

[!include [preview banner](../includes/preview-banner.md)]

This topic contains the requirements through which the different form controls can automatically pick up the default Production Floor Execution styles.

## Grid

Styles are applied automatically.

## Card view

Requirements for card views:

+ Each card view should be nested inside a form group.
+ The group name should start with **CardGroup**, for example, **CardGroupJobsView**.

An example the card view without elements inside:

![Card without elements](media/pfe-styles-empty-card.png)

An example the card view with elements inside:

![Card with elements](media/pfe-styles-elements.png)

## Business card

Requirements for business cards:

+ Each business card should be nested inside a form group.
+ The group name should start with **BusinessCardGroup**, for example, **BusinessCardGroupJobsList**.
+ The grid should have the following setup:

    - **Style**: **list**
    - **Extended style**: **cardList**
    - **Multi Select**: **No**
    - **Show Col Labels**: **No**

## Radio button

Implementing a radio button has the following requirements.

+ Command Buttons should be added with the following setup:

    - **Toggle button**: **Check**
    - **Toggle value**: **On** if radio button should be selected; otherwise, **Off**.
    - Each command button should be nested inside a form group.
    - The group name should start with **RadioTextBelow** or **RadioTextRight** depending on where you want the text to appear.

### Radio text below

![Radio buttons with text below](media/pfe-styles-radio-text-below.png)

### Radio text right

![Radio buttons with text right](media/pfe-styles-radio-text-right.png)

### Internet Explorer

Radio buttons aren't supported in Internet Explorer. In Internet Explorer, the radio buttons look like:

![Radio buttons in Internet Explorer](media/pfe-styles-browser.png)

## Buttons

All buttons, to be styled similarly to the default Production Floor Execution buttons are required to:

+ Button should have these properties:

    - **Button Display**: **TextWithImageLeft**.
    - **Normal Image** shouldn't be empty. For example, **CoffeeScript**
    - **Text** shouldn't be empty. For example, **Start Break**
    - **Width**: Auto
    - **Height**: Auto

Each group of buttons should be nested inside a form group. All buttons within each group will have the same styles.

### Primary button

To highlight a button, it should be located inside a group that has **DefaultButtonGroup** or  **PrimaryButtonGroup**"  in its name, for example, **DefaultButtonGroup10**.

![Primary button appearance](media/pfe-styles-first.png)

### Secondary button

Secondary buttons should be located inside a group. There are two options for naming the group:

+ **Right panel**
+ Starting with **SecondaryButtonGroup**

![Secondary button appearance](media/pfe-styles-second.png)

### Third-group button

Third-group buttons should be located inside a group. There are two options for naming the group:

+ **Left panel**
+ Starting with **ThirdButtonGroup**

![Third-group button appearance](media/pfe-styles-third.png)

### Fourth-group button

Fourth-group buttons should be located inside a group that has a name starting with **FourthButtonGroup**.

Property setup:

- **Button Display**: **TextOnly**
- **Normal Image** should be empty.
- **Text** shouldn't be empty. For example, it could be **View** or **Edit**.
- **Width**: Auto
- **Height**: Auto

![Fourth-group button appearance](media/pfe-styles-fourth.png)

### FlatButtonGroup

FlatButtonGroup should be located inside a group that has a name starting with **FlatButtonGroup**.

Property setup:

+ **Button Display**: **ImageOnly**
+ **Normal Image** shouldn't be empty. For example, **CoffeeScript**
+ **Text** should be empty.
+ **Width**: Auto
+ **Height**: Auto

![Flat button appearance](media/pfe-styles-flat-button.png)

## Combo box

A combo box is a combination of three controls, an input control, a button to clear the input control, and a button for search. Requirements for combo boxes:

+ Each combo box should be nested inside a form group.
+ The group name should start with **Combobox**.
+ Inside the group, the first control should be an **AxFormStringControl** control. This control will be used as the display of the current value, and it will be where the user enters the required value.
+ The second control should be a **CommonButton** control. The name should start with **ClearButton**. The element must contain code using the **enable** property to show or hide the button. For example, to show or hide the **Clear** button when the user is typing information into the input field, the following code should be used:

    ```xpp
    public void textChange()
    {
        super();
        ClearButtonSerial.enabled(this.text()? true : false);
    }
    ```

    We recommend that you have one method where the data is set into the input box, and add enabling **Clear** button there. For example:

    ```xpp
    public void setSerialId(str _serialId)
    {
        JmgTmpJobBundleProdFeedback.InventSerial = _serialId;
        ClearButtonSerial.enabled(_serialId? true : false);

        if (_serialId)
        {
            this.addSerialNumber();
        }
    }
    ```

    Then you can use the following code for the **clicked** method of the **Clear** button:

    ```xpp
    public void clicked()
    {
        element.setSerialId('');
        InventSerialId.setFocus(); // set focus back to the input box
    }
    ```

    Set the value into the input control (**AxFormStringControl**) for the combo box when the form is initialized (**init** method). If value is set (not empty), then the **Clear** button should be enabled. Otherwise, the **Clear** button should be disabled.

+ The third control should be a **CommonButton** control. The name should start with **SearchButton**. The following image shows two combo box controls. The left combo box has an empty text box and no clear button. The right combo box has text in the text box and a clear button (**X**).

    ![Combo box appearance](media/pfe-styles-combo.png)

## Dialogs

The styles for all these controls keep the same rules when they're included in a dialog form, if the name of the dialog form starts with **JmgProductionFloorExecutionDialog**. To apply the correct style for the **Ok** and **Cancel** buttons:

+ **Ok** button. It should be located in a group with the name **OkButtonGroup**.
+ **Cancel** button. It should be located in a group with name **CancelButtonGroup**.
