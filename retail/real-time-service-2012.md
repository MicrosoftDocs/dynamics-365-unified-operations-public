---
# required metadata

title: Install the Retail Real-time service for Dynamics AX 2012 R3 for use with Dynamics 365 for Operations
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: jashanno
manager: AnnBe
ms.date: 05/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: margoc
# ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: [used by loc]
ms.assetid: 34cd95f8-bda1-4a7c-a365-aa9921574bc0
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.dyn365.intro: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Install the Retail Real-time service for Dynamics AX 2012 R3 for use with Dynamics 365 for Operations




This Dynamics 365 for Operations template contains examples of Markdown syntax, as well as guidance on setting the metadata. To get the most of it, you must view both the [raw Markdown](https://raw.githubusercontent.com/MicrosoftDocs/Dynamics-365-Operations/master/template.md?token=AUBjQ-wxx8wHU3pnuQiYvPdvbodbxP2uks5Ypg9_wA%3D%3D) and the [rendered view](https://github.com/MicrosoftDocs/Dynamics-365-Operations/edit/master/template.md) (for instance, the raw Markdown shows the metadata block, while the rendered view does not).

When creating a Markdown file, you should copy this template to a new file, fill out the metadata as specified below, set the H1 heading above to the title of the article, and delete the content. 


## Metadata 

The full metadata block is above (in the [raw Markdown](https://raw.githubusercontent.com/MicrosoftDocs/Dynamics-365-Operations/master/template.md?token=AUBjQ-wxx8wHU3pnuQiYvPdvbodbxP2uks5Ypg9_wA%3D%3D)), divided into required fields and optional fields. **DO NOT** use a colon (:) in any of the metadata elements. 

Here are some key things to note about metadata.

- **Required metadata**
    - **title** - The title will appear in search engine results. You can also add a pipe (|) followed by the product name (for example, `title: Action search | Microsoft Docs`). The title doesn't need be identical to the title in your H1 heading and it should contain 65 characters or less (including | PRODUCT NAME).
    - **description** - This is the full description that appears in the search results. Usually this is the first paragraph of your topic.
    - **author** - This is your GitHub alias, which is required for ownership and sorting in GitHub.
    - **manager** - Use "annbe" in this field.
    - **ms.date** - This should be the first proposed publication date.
    - **ms.topic** - Enter "article" here.
    - **ms.prod** 
    - **ms.service** - Always use "Dynamics365Operations".
    - **ms.technology** 

- **Optional metadata**
    - **audience** - Use of these values: Application User, Developer, or IT Pro.
    - **ms.reviewer** - This is the Microsoft alias of your Content Strategist.  
    - **ms.custom** 
    - **ms.assetid** - This is the GUID of the article that is used for internal tracking purposes. When creating a new Markdown file, get a GUID from [https://www.guidgenerator.com](https://www.guidgenerator.com).
    - **ms.search.region** - Use "global" or enter a country-region value.
    - **ms.author** - Use your Microsoft alias.  

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

You can use a [Markdown table generator tool](http://www.tablesgenerator.com/markdown_tables) to help creating them more easily. 

## Code

Use three backticks (&#96;&#96;&#96;) to begin and end a code example block . You an also indent a line to have it rendered as a code example.

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

Use backticks (&#96;) for `inline code`. Use inline code for command-line commands, database table and column names, and language keywords.

## Blockquotes

> The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended. Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight. In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.

