---
# required metadata

title: Metadata and markdown template
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author:  
ms.date: 02/17/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: 
ms.custom: <remove if blank>
ms.search.region: Global
ms.author: 
ms.search.validFrom: 
ms.search.form:
ms.dyn365.ops.version:
---

# Metadata and Markdown template

[!include[banner](../includes/banner.md)]

This template contains examples of Markdown syntax, as well as guidance on setting the metadata. To get the most of it, you must view both the [raw Markdown](https://raw.githubusercontent.com/MicrosoftDocs/Dynamics-365-Operations/main/template.md?token=AUBjQ-wxx8wHU3pnuQiYvPdvbodbxP2uks5Ypg9_wA%3D%3D) and the [rendered view](https://github.com/MicrosoftDocs/Dynamics-365-Operations/edit/main/template.md) (for instance, the raw Markdown shows the metadata block, while the rendered view does not).

When creating a Markdown file, you should copy this template to a new file, fill out the metadata as specified below, set the H1 heading above to the title of the article, and delete the content. 

## Metadata 

A full markdown block is shown at the top of this file. The metadata is divided into required fields and optional fields. **DO NOT** use a colon (:) in any of the metadata elements. 

Here are some key things to note about metadata.

- **title** - The title will appear in search engine results. 
    - The title doesn't need be identical to the title in your H1 heading, though we prefer that the TOC entry, the title, and the H1 heading all match. 
    - The title should contain 65 or fewer characters.
- **description** - This is the full description that appears in the search results. It should contain 160 or fewer characters.
- **author** - This is your GitHub alias, which is required for ownership and sorting in GitHub.
- **ms.date** - This should be the first proposed publication date, in the mm/dd/yy format.
- **ms.topic** - Enter "article" or if the topic contains overview material, enter "overview" instead.
- **audience** - Use these values: Application User, Developer, or IT Pro. If you use more than one value, separate them with a comma.
- **ms.reviewer** - This is the Microsoft alias of your Content Strategist.  
- **ms.custom** - Add "NotInToc" if the topic is not in the table of contents. Enter "intro-internal" if the topic contains getting started material. If you use more than one value, separate them with a comma.
- **ms.search.region** - Use "global" or enter a country-region value.
- **ms.author** - Use your Microsoft alias.  
- **ms.search.industry** - Leave it out, rather than leaving it blank.
- **ms.search.validFrom** - Month/year of release that feature was introduced in, in format yyyy-mm-dd.
- **ms.search.form** - The form ID. This value is used to lookup relevant topics from the Help Pane for specific forms.
- **ms.dyn365.ops.version** - Name of release that feature was introduced in, see list here: [Help system and Versions metadata for docs topics](https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29])

### Don't use these metadata

If you think you need to use any of these, talk to your Content Strategist first. For valid values, see [Taxonomies for Docs](https://review.docs.microsoft.com/en-us/help/contribute/metadata-taxonomies?branch=main). 

- **ms.search.scope** - Set at the folder level, see [docfx.json](articles/docfx.json). We are using these values:
    + Legacy values. Don't remove these from topics. They need to stay until all customers are on the new system.
        + `Core` - Indicates that a topic should show up in the Help Pane.
        + `Operations`
        + `Retail`
    + New values.
        + `ShowInHelp` - Indicates that a topic should show up in the Help Pane.
        + `Commerce`
        + `Finance`
        + `Supply Chain`
        + `Talent`
        + `CrossApp` - This topics usually also have ShowInHelp.
        + `Developer` - These topics usually don't have ShowInHelp.

- **ms.service** - Set at the folder level. see [docfx.json](articles/docfx.json). We are using these values:
    - `dynamics-365-finance`: Finance
    - `dynamics-365-cross-app`: Cross app
    - `dynamics-365-supply-chain`: Supply Chain Management
    - `dynamics-365-commerce`: Commerce
    - `dynamics-365-talent`: Talent
    - `dynamics-365-human-resources`: Human Resources
- **manager** - The best practice is to not use **manager**.
- **ms.assetid** - We aren't using this value anymore, but it's not in conflict with any other metadata.
- **ms.prod** - This is only used for AX2012 content or for content that is on-prem only. If neither value is needed, leave it out. You can't have both **ms.prod** and **ms.service**, but if you enter **ms.prod**, you need to include **ms.service** with a blank value. 

### No blank metadata

If the metadata is blank, it's better to leave it out altogether. The exception is **ms.prod**, if you use a value for **ms.prod** you need to include **ms.service** with a blank value. 

## Basic Markdown, GFM, and special characters

All basic and GitHub Flavored Markdown (GFM) is supported. For more information, see:

- [Baseline Markdown syntax](https://daringfireball.net/projects/markdown/syntax)
- [GFM documentation](https://guides.github.com/features/mastering-markdown)

Markdown uses special characters such as \*, \`, and \# for formatting. If you wish to include one of these characters in your content, you must do one of two things:

- Put a backslash before the special character to "escape" it (for example, `\*` for a \*)
- Use the [HTML entity code](http://www.ascii.cl/htmlcodes.htm) for the character (for example, `&#42;` for a &#42;).

## File name

File names use the following rules:

* Contain only lowercase letters, numbers, and hyphens.
* No spaces or punctuation characters. Use the hyphens to separate words and numbers in the file name.
* Use action verbs that are specific, such as develop, buy, build, troubleshoot. No -ing words.
* No small words - don't include a, and, the, in, or, etc.
* Must be in Markdown and use the .md file extension.
* Keep file names short. They are part of the URL for your articles.  

## Headings

Use sentence-style capitalization. Do not overcapitalize. 

Headings should use atx-style, that is, use 1-6 hash characters (#) at the start of the line to indicate a heading, corresponding to HTML headings levels H1 through H6. Examples of first- and second-level headers are used above. 

There **must** be only one first-level heading (H1) in your topic, which will be displayed as the on-page title.

If your heading finishes with a `#` character, you need to add an extra `#` character in the end in order for the title to render correctly. For example, `# Define a data method in C# #`.     

Second-level headings will generate the on-page TOC that appears in the "In this article" section under the on-page title.

### Third-level heading
#### Fourth-level heading
##### Fifth level heading
###### Sixth-level heading
 
## Text styling

*Italics*
 Use for files, folders, paths (for long items, split onto their own line) - new terms - URLs (unless rendered as links, which is the default).

**Bold**
Use for UI elements.

## Links

### Internal links

To link to a header in the same Markdown file (also known as anchor links), you'll need to find the ID of the header that you're trying to link to. To confirm the ID, view the source of the rendered article, find the ID of the header (for example, `id="blockquote"`), and link using # + id (for example, `#blockquote`).

**Note:** You need to follow the casing of the header ID. In the following examples, the README.md file is all caps, so that's how this needs to be written in Markdown. Most IDs are lowercase. 

The ID is auto-generated based on the header text. So, for example, given a unique section named `## Step 2`, the ID would look like this `id="step-2"`.

- Example: [Chapter 1](#chapter-1)

To link to a Markdown file in the same repo, use [relative links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), including the ".md" at the end of the filename.

- Example: [Readme](README.md)

To link to a header in a Markdown file in the same repo, use relative linking + hashtag linking.

- Example: [Links](#links)

### External links

To link to an external file, use the full URL as the link.

- Example: [GitHub](http://www.github.com)

If a URL appears in a Markdown file, it will be transformed into a clickable link.

- Example: http://www.github.com

## Lists

### Ordered lists

1. This 
1. Is
1. An
1. Ordered
1. List  


#### Ordered list with an embedded list

1. Here
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. list


### Unordered Lists

- This
- is
- a
- bulleted
- list


##### Unordered list with an embedded list

- This 
- bulleted 
- list
    - Mrs. Peacock
    - Mr. Green
- contains  
- other
    1. Colonel Mustard
    1. Mrs. White
- lists


## Horizontal rule

---

## Tables

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| col 1 is default | left-aligned     |    $1 |

You can use a [Markdown table generator tool](https://www.tablesgenerator.com/markdown_tables) to help creating them more easily. 

## Code

Use three backticks (&#96;&#96;&#96;) to begin and end a code example block . You an also indent a line to have it rendered as a code example. You must add a language to the code block. Common languages in our doc set are `xpp`, `csharp`, `javascript`, `powershell`, `xml`, `json`, `dos`, and `plaintext`.

```xpp
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

Use backticks (&#96;) for `inline code`. Use inline code for command-line commands, database table and column names, and language keywords.

## Blockquotes

> The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended. Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight. In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.

## Images

### Static image or animated gif

![this is the alt text.](../images/Logo_DotNet.png)

### Image with border

Sometimes it's nice to have a border an around an image, especially if it's screenshot where background matches the docs page.

:::image type="content" source="<folderPath>" alt-text="<alt text>":::

## Videos

### YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/g2a4W6Q7aRw" frameborder="0" allowfullscreen></iframe>

## docs.microsoft extensions

docs.microsoft provides a few additional extensions to GitHub Flavored Markdown. 

### Alerts

It's important to use the following alert styles so they render with the proper style in the documentation site. However, the rendering engine on GitHub doesn't diferentiate them.     

#### Note

> [!NOTE]
> This is a NOTE

#### Warning

> [!WARNING]
> This is a WARNING

#### Tip

> [!TIP]
> This is a TIP

#### Important

> [!IMPORTANT]
> This is IMPORTANT

And they'll render like this:
![Alert styles.](../images/alerts.png)


