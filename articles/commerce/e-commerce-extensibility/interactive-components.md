---
# required metadata

title: Interactive components overview
description: This topic covers interactive components that allow site authors to edit text, Rich Text, link, image, and video fields directly on the Commerce site builder WYSIWYG preview canvas.
author: samjarawan
manager: annbe
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Interactive components overview

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic covers interactive components that allow site authors to edit text, Rich Text, link, image, and video fields directly on the Commerce site builder WYSIWYG preview canvas.

## Overview

Dynamics 365 Commerce site builder allows a page or fragment author to edit fields for text, rich text, link, image, and video directly on the WYSIWYG preview canvas using interactive components. Interactive components ship with the Commerce online software development kit (SDK) and include **Msdyn365.Text** for text, **Msdyn365.RichTextComponent** for Rich Text, **Msdyn365.Links** for links, the **Msdyn365.Image** for images, and **Msdyn365.Video** for videos. Once implemented, Commerce site builder will then allow inline editing for text and bring up picker windows for links, images, and videos.

For the best authoring experience, modules developers should use interactive components when rendering configuration fields to allow inline editing. Any custom implementations of these components can be made interactive by wrapping the component in the **EditableField** higher-order component (HOC). Follow the guidelines below to support interactive components inside a custom module.

## How interactive components work

An interactive component hooks an event handler to the component that will do the work of setting the specific configuration field required.

The following example shows how a text configuration field uses an interactive component to allow inline editing of the text. A **productTitle** configuration value is specified in the module definition file configuration section:
```json
...
    "config": {
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title"
        },
     }
...
```

To support an interactive canvas experience, the module uses the **Msdyn365.Text** interactive component which specifies an event handler "handleTextChange" that will set the configuration value.

```typescript
  public handleTextChange = (event: Msdyn365.ContentEditableEvent) => this.props.config.productTitle!.text = event.target.value;

  <Msdyn365.Text
    className={'product-title'}
    tag={'h2'}
    text={this.props.config.productTitle}
    editProps={{ onEdit: this.handleTextChange, requestContext: this.props.context.request }}
  />
```

## Interactive component reference

### Text component

Once implemented, the text component allows site authors to edit text directly inline on the site builder preview canvas.

#### Text component syntax

```typescript
<Msdyn365.Text />
```

#### Text component example

```typescript
 <Msdyn365.Text
    text={heading.text || ''}
    tag={'h2'}
    className={'display-4'}
    editProps={{ onEdit: this.handleTextChange, requestContext: this.props.context.request }}
  />

public handleTextChange = (event: Msdyn365.ContentEditableEvent) => this.props.config.heading!.text = event.target.value;
```

#### Available props

| Prop      | Description                                          | Type           |
| --------- | ---------------------------------------------------- | -------------- |
| text      | Text to be displayed                                 | String         |
| tag       | HTML tag (DIV, H2, etc.) to render the text           | String         |
| className | CSS class name                                       | String         |
| editProps | Required props to enable interaction in site builder | ITextEditProps |

#### ITextEditProps

| Prop           | description                                  | Type            |
| -------------- | -------------------------------------------- | --------------- |
| onEdit         | Function handler to handle text change event | Function        |
| requestContext | Request context object                       | IRequestContext |

### Rich Text component

Once implemented, the Rich Text component allows site authors to edit Rich Text directly inline on the site builder preview canvas.

#### Rich Text component syntax

```typescript
<Msdyn365.RichTextComponent />
```

#### Rich Text component example 

```typescript
 <Msdyn365.RichTextComponent
    text={`<p className='d-none d-lg-block'>${paragraph}</p>`}
    editProps={{ onEdit: this.handleParagraphChange, requestContext: this.props.context.request }}
  />
```

#### Available props

| Prop      | Description                                          | Type           |
| --------- | ---------------------------------------------------- | -------------- |
| text      | HTML text to be displayed                            | String         |
| editProps | Required props to enable interaction in site builder | ITextEditProps |

#### ITextEditProps

| Prop           | Description                                  | Type            |
| -------------- | -------------------------------------------- | --------------- |
| onEdit         | Function handler to handle text change event | Function        |
| requestContext | Request context object                       | IRequestContext |


### Links component

Once implemented, the links component allows site authors to edit an array of links on the site builder preview canvas.

#### Links component syntax

```typescript
<Msdyn365.Links />
```

#### Links component example

```typescript
  <Msdyn365.Links
    links={config.links}
    editProps={{ onTextChange: this.handleLinkTextChange, requestContext: this.props.context.request }}
  />
```

#### Available props

| Prop      | Description                                          | Type            |
| --------- | ---------------------------------------------------- | --------------- |
| link      | Array of link data to be rendered                    | ILinksData[]    |
| editProps | Required props to enable interaction in site builder | ITLinkEditProps |

#### ILinkEditProps

| Prop           | Description                                       | Type            |
| -------------- | ------------------------------------------------- | --------------- |
| onTextChange   | Function handler to handle link text change event | Function        |
| requestContext | Request context object                            | IRequestContext |

#### ILinksData

| Prop                 | Description                                                 | type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| linkText             | Text to be shown as link                                    | String              |
| linkUrl              | URL to navigate to                                          | String              |
| openInNewTab         | Flag to indicate if the link should open in new tab         | boolean             |
| ariaLabel            | Aria label for accessibility                                | String              |
| className            | CSS class name                                              | String              |
| key                  | React key                                                   | String              |
| role                 | Role of the anchor tag (button, etc.)                         | String              |
| additionalProperties | Additional properties dictionary to be added to the element | [x: string]: string |
| linkTag              | HTML tag to render the link                                 | String              |
| innerClassName       | CS class name for inner component in the anchor tag        | String              |
| onClick              | Click handler to handle link click event                    | Function            |

### Link component

Once implemented, the link component allows site authors to edit single links on the site builder preview canvas.

#### Link component syntax

```typescript
<Msdyn365.Link />
```

#### Link component example

```typescript
  <Msdyn365.Link
    link={config.links[1]}
    editProps={{ onTextChange: this.handleLinkTextChange(1), requestContext: this.props.context.request }}
  />
```

#### Available props

| Prop      | Description                                          | Type               |
| --------- | ---------------------------------------------------- | ------------------ |
| links     | Link data to be rendered                             | ILinksData         |
| editProps | Required props to enable interaction in site builder | ILinkItemEditProps |

#### ILinkItemEditProps

| Prop           | Description                                       | Type            |
| -------------- | ------------------------------------------------- | --------------- |
| onTextChange   | Function handler to handle link text change event | Function        |
| requestContext | Request context object                            | IRequestContext |

#### ILinksData

| Prop                 | Description                                                 | Type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| linkText             | Text to be shown as link                                    | String              |
| linkUrl              | URL to navigate to                                          | String              |
| openInNewTab         | Flag to indicate if the link should open in new tab         | boolean             |
| ariaLabel            | Aria label for accessibility                                | String              |
| className            | CSS class name                                              | String              |
| key                  | React key                                                   | String              |
| role                 | Role of the anchor tag (button, etc.)                         | String              |
| additionalProperties | Additional properties dictionary to be added to the element | [x: string]: string |
| linkTag              | HTML tag to render the link                                 | String              |
| innerClassName       | CSS class name for inner component in the anchor tag        | String              |
| onClick              | Click handler to handle link click event                    | Function            |

### Image component

Once implemented, the image component allows site authors to edit images directly on the site builder preview canvas.

#### Image component syntax

```typescript
<Msdyn365.Image />
```

#### Image component example

```typescript
  <Msdyn365.Image
    editProps={{ key: this.props.config.image || {}, requestContext: this.props.context.request }}
    {...config.image}
    {...imageProps}
  />
```

#### Available props

| Prop                 | Description                                                 | Type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| src                  | Image source URL                                            | String              |
| fallBackSrc          | Fall back URL if the image fails to load                    | String              |
| altText              | Alt text for the image                                       | String              |
| caption              | Image caption string                                        | String              |
| title                | Title for the image                                         | String              |
| width                | Width of the image                                          | number              |
| height               | Height of the image                                         | number              |
| imageSettings        | Settings for the image                                      | ImageSettings       |
| additionalProperties | Additional properties dictionary to be added to the element | [x: string]: string |
| editProps            | Required props to enable interaction in site builder        | IEditProps          |

#### IEditProps

| Prop           | Description                          | Type            |
| -------------- | ------------------------------------ | --------------- |
| key            | Path to the image property in config | Object          |
| requestContext | Request context object               | IRequestContext |

### Video component

Once implemented, the video component allows site authors to edit videos directly on the site builder preview canvas.

#### Video component syntax

```typescript
<MsDyn365.Video></MsDyn365.Video>
```
#### Video component example

```typescript
<MsDyn365.Video>
  <Player playerData={videoPlayerData} />
</MsDyn365.Video>
```

#### Available props

| Prop      | Description                                          | Type       |
| --------- | ---------------------------------------------------- | ---------- |
| className | CSS classname                                        | String     |
| editProps | Required props to enable interaction in site builder | IEditProps |

#### IEditProps

| Prop           | Description                    | Type            |
| -------------- | ------------------------------ | --------------- |
| key            | Path to the property in config | Object          |
| requestContext | Request context object         | IRequestContext |

## Generic editable higher-order component (HOC)

Generic editable field components wrap any custom components and enable interactions in the context of site builder.

#### Generic editable higher-order component syntax

```typescript
<EditableField />
```

### Generic editable higher-order component example

```typescript
  <EditableField
    onChange={this.props.editProps ? this.props.editProps.onEdit : this.onEdit} // handle innerHTML change
    requestContext={this.props.editProps?.requestContext}
    fieldProps={{
        text: this.props.text,
        tag: this.props.tag,
        className: this.props.className
    }}
    type={FieldType.Text}
  />
```

### Available props

| Prop           | Description                                                | Type                    |
| -------------- | ---------------------------------------------------------- | ----------------------- |
| fieldProps     | Field properties                                           | [x: string]: string     |
| type           | Type of the field (text/image/video/link)                  | FieldType               |
| requestContext | Request context object                                     | IRequestContext         |
| onChange       | Event handler for onChange event                           | Function                |
| onMouseOver    | Event handler for onMouseover event                        | Function                |
| onMouseOut     | Event handler for onMouseout event                         | Function                |
| onFocus        | Event handler for onFocus event                            | Function                |
| onBlur         | Event handler for onBlur event                             | Function                |
| placeHolderText| Text to show when text is cleared in the field             | String                  |
| disabled       | Flag to enable or disable editing of the file in site builder | String                  |

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Work with modules](work-with-modules.md)
 
[Work with fragments](work-with-fragments.md)
