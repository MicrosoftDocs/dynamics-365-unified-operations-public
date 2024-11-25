---
title: Interactive components overview
description: This article covers interactive components that let site authors edit fields for text, rich text, links, images, and videos directly on the WYSIWYG preview canvas in Microsoft Dynamics 365 Commerce site builder.
author: samjarawan
ms.date: 07/26/2024
ms.topic: overview
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Interactive components overview

[!include [banner](../includes/banner.md)]

This article covers interactive components that let site authors edit fields for text, rich text, links, images, and videos directly in visual page builder, the what-you-see-is-what-you-get (WYSIWYG) preview canvas in Microsoft Dynamics 365 Commerce site builder.

In Commerce site builder, page or fragment authors can use interactive components to edit fields for text, rich text, links, images, and videos directly in visual page builder. Interactive components are released with the Commerce online software development kit (SDK) and include **Msdyn365.Text** for text, **Msdyn365.RichTextComponent** for rich text, **Msdyn365.Links** for links, **Msdyn365.Image** for images, and **Msdyn365.Video** for videos. After the interactive components are implemented, site builder will allow for inline editing of text, and it will open a picker window for links, images, and videos.

For the best authoring experience, module developers should use interactive components when they render configuration fields, to allow for inline editing. Any custom implementations of these components can be made interactive by wrapping the component in the **EditableField** higher-order component (HOC). Follow the guidelines in this article to support interactive components inside a custom module.

## How interactive components work

An interactive component hooks an event handler to the component that will do the work of setting the specific configuration field that is required.

The following example shows how a text configuration field uses an interactive component to allow for inline editing of the text. A **productTitle** configuration value is specified in the **config** section of the module definition file.

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

To support an interactive canvas experience, the module uses the **Msdyn365.Text** interactive component. This interactive component specifies a **handleTextChange** event handler that will set the configuration value.

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

After it's implemented, the text component lets site authors edit text inline, directly in visual page builder.

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

#### Available properties

| Property  | Description                                                              | Type           |
|-----------|--------------------------------------------------------------------------|----------------|
| text      | The text to show.                                                        | String         |
| tag       | The HTML tag (for example, **DIV** or **H2**) to use to render the text. | String         |
| className | The Cascading Style Sheets (CSS) class name.                             | String         |
| editProps | Properties that are required to enable interaction in site builder.      | ITextEditProps |

#### ITextEditProps properties

| Property       | Description                                              | Type            |
|----------------|----------------------------------------------------------|-----------------|
| onEdit         | The function handler that handles the text change event. | Function        |
| requestContext | The Request context object.                              | IRequestContext |

### Rich text component

After it's implemented, the rich text component lets site authors edit rich text inline, directly in visual page builder.

#### Rich text component syntax

```typescript
<Msdyn365.RichTextComponent />
```

#### Rich text component example

```typescript
<Msdyn365.RichTextComponent
    text={`<p className='d-none d-lg-block'>${paragraph}</p>`}
    editProps={{ onEdit: this.handleParagraphChange, requestContext: this.props.context.request }}
/>
```

#### Available properties

| Property  | Description                                                             | Type           |
|-----------|-------------------------------------------------------------------------|----------------|
| text      | The HTML text to show.                                                  | String         |
| editProps | The properties that are required to enable interaction in site builder. | ITextEditProps |

#### ITextEditProps properties

| Property       | Description                                              | Type            |
|----------------|----------------------------------------------------------|-----------------|
| onEdit         | The function handler that handles the text change event. | Function        |
| requestContext | The Request context object.                              | IRequestContext |


### Links component

After it's implemented, the links component lets site authors edit an array of links in visual page builder.

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

#### Available properties

| Property  | Description                                                             | Type            |
|-----------|-------------------------------------------------------------------------|-----------------|
| link      | The array of link data to render.                                       | ILinksData\[\]  |
| editProps | The properties that are required to enable interaction in site builder. | ITLinkEditProps |

#### ILinksData properties

| Property             | Description                                                               | Type                  |
|----------------------|---------------------------------------------------------------------------|-----------------------|
| linkText             | The text to show as a link.                                               | String                |
| linkUrl              | The URL to open.                                                          | String                |
| openInNewTab         | A flag that indicates whether the link should be opened on a new tab.     | Boolean               |
| ariaLabel            | The Accessible Rich Internet Applications (ARIA) label for accessibility. | String                |
| className            | The CSS class name.                                                       | String                |
| key                  | The React key.                                                            | String                |
| role                 | The role of the anchor tag (for example, **button**).                     | String                |
| additionalProperties | A dictionary of additional properties to add to the element.              | \[x: string\]: string |
| linkTag              | The HTML tag to use to render the link.                                   | String                |
| innerClassName       | The CSS class name for the inner component in the anchor tag.             | String                |
| onClick              | The click handler that handles the link click event.                      | Function              |

#### ILinkEditProps properties

| Property       | Description                                                   | Type            |
|----------------|---------------------------------------------------------------|-----------------|
| onTextChange   | The function handler that handles the link text change event. | Function        |
| requestContext | The Request context object.                                   | IRequestContext |


### Link component

After it's implemented, the link component lets site authors edit single links in visual page builder.

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

#### Available properties

| Property  | Description                                                         | Type               |
|-----------|---------------------------------------------------------------------|--------------------|
| links     | The link data to render.                                            | ILinksData         |
| editProps | Properties that are required to enable interaction in site builder. | ILinkItemEditProps |

#### ILinksData properties

| Property             | Description                                                           | Type                  |
|----------------------|-----------------------------------------------------------------------|-----------------------|
| linkText             | The text to show as a link.                                           | String                |
| linkUrl              | The URL to open.                                                      | String                |
| openInNewTab         | A flag that indicates whether the link should be opened on a new tab. | Boolean               |
| ariaLabel            | The ARIA label for accessibility.                                     | String                |
| className            | The CSS class name.                                                   | String                |
| key                  | The React key.                                                        | String                |
| role                 | The role of the anchor tag (for example, **button**).                 | String                |
| additionalProperties | A dictionary of additional properties to add to the element.          | \[x: string\]: string |
| linkTag              | The HTML tag to use to render the link.                               | String                |
| innerClassName       | The CSS class name for the inner component in the anchor tag.         | String                |
| onClick              | The click handler that handles the link click event.                  | Function              |

#### ILinkItemEditProps properties

| Property       | Description                                                   | Type            |
|----------------|---------------------------------------------------------------|-----------------|
| onTextChange   | The function handler that handles the link text change event. | Function        |
| requestContext | The Request context object.                                   | IRequestContext |

### Image component

After it's implemented, the image component lets site authors edit images directly in visual page builder.

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

#### Available properties

| Property             | Description                                                         | Type                  |
|----------------------|---------------------------------------------------------------------|-----------------------|
| src                  | The URL of the image source.                                        | String                |
| fallBackSrc          | The fallback URL if the image can't be loaded.                      | String                |
| altText              | The alt text for the image.                                         | String                |
| caption              | The caption string for the image.                                   | String                |
| title                | The title for the image.                                            | String                |
| width                | The width of the image.                                             | number                |
| height               | The height of the image.                                            | number                |
| imageSettings        | Settings for the image.                                             | ImageSettings         |
| additionalProperties | A dictionary of additional properties to add to the element.        | \[x: string\]: string |
| editProps            | Properties that are required to enable interaction in site builder. | IEditProps            |

#### IEditProps properties

| Property       | Description                               | Type            |
|----------------|-------------------------------------------|-----------------|
| key            | The path of the image property in the **config** section of the module definition file. | Object          |
| requestContext | The Request context object.               | IRequestContext |

### Video component

After it's implemented, the video component lets site authors edit videos directly in visual page builder.

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

#### Available properties

| Property  | Description                                                         | Type       |
|-----------|---------------------------------------------------------------------|------------|
| className | The CSS class name.                                                 | String     |
| editProps | Properties that are required to enable interaction in site builder. | IEditProps |

#### IEditProps properties

| Property       | Description                         | Type            |
|----------------|-------------------------------------|-----------------|
| key            | The path of the property in the **config** section of the module definition file. | Object          |
| requestContext | The Request context object.         | IRequestContext |

## Generic editable HOC

Generic editable field components wrap any custom components and enable interactions in the context of site builder.

### Generic editable HOC syntax

```typescript
<EditableField />
```

### Generic editable HOC example

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

### Available properties

| Property       | Description                                                          | Type                  |
|----------------|----------------------------------------------------------------------|-----------------------|
| fieldProps     | Field properties.                                                    | \[x: string\]: string |
| type           | The type of the field (**text**, **image**, **video**, or **link**). | FieldType             |
| requestContext | The Request context object.                                          | IRequestContext       |
| onChange       | The event handler for the **onChange** event.                        | Function              |
| onMouseOver    | The event handler for the **onMouseover** event.                     | Function              |
| onMouseOut     | The event handler for the **onMouseout** event.                      | Function              |
| onFocus        | The event handler for the **onFocus** event.                         | Function              |
| onBlur         | The event handler for the **onBlur** event.                          | Function              |
| placeHolderText| The text to show when text is cleared from the field.                | String                |
| disabled       | A flag that enables or disables editing of the file in site builder. | String                |

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Platform settings file](platform-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Configure module properties to be shown based on context](configure-properties-context.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)

[Work with modules](../work-with-modules.md)

[Work with fragments](../work-with-fragments.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
