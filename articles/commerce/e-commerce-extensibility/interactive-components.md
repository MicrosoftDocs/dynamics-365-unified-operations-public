---
# required metadata

title: Interactive components
description: The site builder tool allows a page or fragment author to edit fields (Text, RichText, Link, Image and Video) directly on the preview canvas in a WYSIWYG manner using interactive components.
author: samjarawan
manager: annbe
ms.date: 06/29/2020
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

The site builder tool allows a page or fragment author to edit fields (Text, RichText, Link, Image and Video) directly on the preview canvas in a WYSIWYG manner using **interactive components**.  **Interactive components** ship with the e-Commerce online SDK and include **Msdyn365.Text** for text fields, **Msdyn365.RichTextComponent** for rich text, **Msdyn365.Links** for links, the **Msdyn365.Image** for images and **Msdyn365.Video** for videos. The site builder tool will allow inline editing for text, bring up a link picker for links and image/video pickers for images and videos.

For the best authoring experience, modules developers should use interactive components when rendering configuration fields to allow inline editing. Any custom implementations of these components can still be made interactive by wrapping the component in the EditableField higher order component (HOC).  Follow the guidelines below to support interactive components inside of your modules html.


## How interactive components work
An interactive component hooks an event handler to the component which will do the work of setting the specific configuration field required.

The below example shows how a text configuration field leverages an interactive component to allow inline editing of the text.

A **productTitle** config value is specified in the module definition file config section as shown below:
```json
...
    "config": {
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title"
        },
...
```

To support an interactive canvas experience, the module uses the **Msdyn365.Text** interactive component which specified an event handler "handleTextChange" which will set the config value once set.

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

### Text Component

```typescript
<Msdyn365.Text />
```

#### Example

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

| prop      | description                                          | type           |
| --------- | ---------------------------------------------------- | -------------- |
| text      | text to be displayed                                 | String         |
| tag       | html tag (div, h2, etc) to render the text           | String         |
| className | css class name                                       | String         |
| editProps | required props to enable interaction in site builder | ITextEditProps |

#### ITextEditProps

| prop           | description                                  | type            |
| -------------- | -------------------------------------------- | --------------- |
| onEdit         | function handler to handle text change event | Function        |
| requestContext | request context object                       | IRequestContext |

### RichText Component

```typescript
<Msdyn365.RichTextComponent />
```

#### Example

```typescript
 <Msdyn365.RichTextComponent
    text={`<p className='d-none d-lg-block'>${paragraph}</p>`}
    editProps={{ onEdit: this.handleParagraphChange, requestContext: this.props.context.request }}
  />
```

#### Available props

| prop      | description                                          | type           |
| --------- | ---------------------------------------------------- | -------------- |
| text      | html text to be displayed                            | String         |
| editProps | required props to enable interaction in site builder | ITextEditProps |

#### ITextEditProps

| prop           | description                                  | type            |
| -------------- | -------------------------------------------- | --------------- |
| onEdit         | function handler to handle text change event | Function        |
| requestContext | request context object                       | IRequestContext |


### Links Component

```typescript
<Msdyn365.Links />
```

#### Example
```typescript
  <Msdyn365.Links
    links={config.links}
    editProps={{ onTextChange: this.handleLinkTextChange, requestContext: this.props.context.request }}
  />
```

#### Available props

| prop      | description                                          | type            |
| --------- | ---------------------------------------------------- | --------------- |
| link      | array of link data to be rendered                    | ILinksData[]    |
| editProps | required props to enable interaction in site builder | ITLinkEditProps |

#### ILinkEditProps

| prop           | description                                       | type            |
| -------------- | ------------------------------------------------- | --------------- |
| onTextChange   | function handler to handle link text change event | Function        |
| requestContext | request context object                            | IRequestContext |

#### ILinksData

| prop                 | description                                                 | type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| linkText             | text to be shown as link                                    | String              |
| linkUrl              | url to navigate to                                          | String              |
| openInNewTab         | flag to indicate if the link should open in new tab         | boolean             |
| ariaLabel            | aria label for accessibility                                | String              |
| className            | css class name                                              | String              |
| key                  | react key                                                   | String              |
| role                 | role of the anchor tag(button, etc)                         | String              |
| additionalProperties | additional properties dictionary to be added to the element | [x: string]: string |
| linkTag              | html tag to render the link                                 | String              |
| innerClassName       | css class name for inner component in the anchor tag        | String              |
| onClick              | click handler to handle link click event                    | Function            |

### Link Component

```typescript
<Msdyn365.Link />
```

#### Example

```typescript
  <Msdyn365.Link
    link={config.links[1]}
    editProps={{ onTextChange: this.handleLinkTextChange(1), requestContext: this.props.context.request }}
  />
```

#### Available props

| prop      | description                                          | type               |
| --------- | ---------------------------------------------------- | ------------------ |
| links     | link data to be rendered                             | ILinksData         |
| editProps | required props to enable interaction in site builder | ILinkItemEditProps |

#### ILinkItemEditProps

| prop           | description                                       | type            |
| -------------- | ------------------------------------------------- | --------------- |
| onTextChange   | function handler to handle link text change event | Function        |
| requestContext | request context object                            | IRequestContext |

#### ILinksData

| prop                 | description                                                 | type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| linkText             | text to be shown as link                                    | String              |
| linkUrl              | url to navigate to                                          | String              |
| openInNewTab         | flag to indicate if the link should open in new tab         | boolean             |
| ariaLabel            | aria label for accessibility                                | String              |
| className            | css class name                                              | String              |
| key                  | react key                                                   | String              |
| role                 | role of the anchor tag(button, etc)                         | String              |
| additionalProperties | additional properties dictionary to be added to the element | [x: string]: string |
| linkTag              | html tag to render the link                                 | String              |
| innerClassName       | css class name for inner component in the anchor tag        | String              |
| onClick              | click handler to handle link click event                    | Function            |

### Image Component

```typescript
<Msdyn365.Image />
```

#### Example
```typescript
  <Msdyn365.Image
    editProps={{ key: this.props.config.image || {}, requestContext: this.props.context.request }}
    {...config.image}
    {...imageProps}
  />
```

#### Available props

| prop                 | description                                                 | type                |
| -------------------- | ----------------------------------------------------------- | ------------------- |
| src                  | image source url                                            | String              |
| fallBackSrc          | fall back url if the image fails to load                    | String              |
| altText              | alt text fo the image                                       | String              |
| caption              | image caption string                                        | String              |
| title                | title for the image                                         | String              |
| width                | width of the image                                          | number              |
| height               | height of the image                                         | number              |
| imageSettings        | settings for the image                                      | ImageSettings       |
| additionalProperties | additional properties dictionary to be added to the element | [x: string]: string |
| editProps            | required props to enable interaction in site builder        | IEditProps          |

#### IEditProps

| prop           | description                          | type            |
| -------------- | ------------------------------------ | --------------- |
| key            | path to the image property in config | Object          |
| requestContext | request context object               | IRequestContext |

### Video Component

```typescript
<MsDyn365.Video>
  <Player playerData={videoPlayerData} />
</MsDyn365.Video>
```

#### Available props

| prop      | description                                          | type       |
| --------- | ---------------------------------------------------- | ---------- |
| className | css classname                                        | String     |
| editProps | required props to enable interaction in site builder | IEditProps |

#### IEditProps

| prop           | description                    | type            |
| -------------- | ------------------------------ | --------------- |
| key            | path to the property in config | Object          |
| requestContext | request context object         | IRequestContext |


## Generic Editable Component HOC
Generic editable field component to wrap any custom components and enable interaction in the context of the site builder.

```typescript
<EditableField />
```

### Example

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

| prop           | description                                                | type                    |
| -------------- | ---------------------------------------------------------- | ----------------------- |
| fieldProps     | field properties                                           | [x: string]: string     |
| type           | type of the field (text/image/video/link)                  | FieldType               |
| requestContext | request context object                                     | IRequestContext         |
| onChange       | event handler for onchange event                           | Function                |
| onMouseOver    | event handler for onmouseover event                        | Function                |
| onMouseOut     | event handler for onmouseout event                         | Function                |
| onFocus        | event handler for onfocus event                            | Function                |
| onBlur         | event handler for onblur event                             | Function                |
| placeHolderText| text to show when text is cleared in the field             | String                  |
| disabled       | flag to enable/disable editing of the file in site builder | String                  |
