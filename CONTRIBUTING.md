# Contributing to this documentation
Welcome! Thank you for your interest in contributing to Microsoft Dynamics 365 documentation. 

In this topic you'll find the basic process for adding or updating content for:
- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Commerce
- Dynamics 365 Talent

This documentation is published [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/index).

## Table of contents 

* [Code of conduct](#code-of-conduct)
* [Markdown, Git, and GitHub](#markdown-git-and-github)
* [Ways to contribute](#ways-to-contribute)
* [Contributing to samples](#contributing-to-samples)
* [Contributor License Agreement](#contributor-license-agreement)
* [Do's and don'ts](#dos-and-donts)

## Code of conduct
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any questions or comments.

## Markdown, Git, and GitHub
All of the topics in this repository use GitHub-flavored Markdown. Here's a list of resources to help you use Markdown:

* [Markdown basics](https://help.github.com/articles/markdown-basics/)
* [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

If you're unfamiliar with Git, you might want to review some Git terminology in the [GitHub glossary](https://help.github.com/articles/github-glossary).

The GitHub UI supports the creation of new files and dragging and dropping images. However, when you work in the UI, managing branches can be confusing so we recommend that you install the tools and learn the commands for creating and managing topics. 

* [Creating files on Github](https://github.com/blog/1327-creating-files-on-github)
* [Upload files to your repositories](https://github.com/blog/2105-upload-files-to-your-repositories)

## Ways to contribute
In this topic you'll find the basic process for adding or updating content for:
- Finance 
- Supply Chain Management
- Commerce
- Talent

You can submit minor changes or larger submissions as follows:

* **Minor changes** - You can easily contribute minor updates by selecting the **Edit** button in the topic that you want to modify.

* **Larger submissions** - If you're making substantial changes to an existing topic, adding or changing images, or contributing a new topic, you need to fork the **MicrosoftDocs/Dynamics-365-Operations** repository, use GitHub or install your favorite Markdown editor, and learn some Git commands.

### Minor changes
If you only need to make textual updates to an existing topic, you can use GitHub's web-based Markdown editor to submit your changes. 

1. Select **Edit** in the topic that you want to modify. The GitHub version of the topic will open.

2. Select the edit (pencil) icon. 

3. Edit the topic, as needed using Markdown.

4. Select the **Propose file change** button.

5. Click the **Create pull request** button to submit your changes.
 
Minor corrections or clarifications that you submit are covered by the [docs.microsoft.com Terms of Use](https://docs.microsoft.com/legal/termsofuse).

### Larger submissions
For the following sorts of work, we strongly recommend that you install and learn to use Git and GitHub tools:

* Making major changes to an existing topic.
* Creating and publishing a new topic.
* Adding new images or updating images.
* Updating a topic over a period of days without publishing changes each of those days.
* Creating content for a release that must go out on a certain day at a certain time.

If you're making substantial changes to an existing topic, adding or changing images, or contributing a new topic, follow these steps. 

1. Fork the **MicrosoftDocs/Dynamics-365-Unified-Operations** repository.

2. Create a branch for your topic.

3. Write a new topic or update an existing topic.

   - If it's a new topic, you can use this [template](./template.md) file as your starting point. It contains some writing guidelines and explains the metadata required for each topic, such as author information. We suggest that you copy this template to a new file, fill out the metadata as specified in the Metadata section, specify the title of the topic (indicated by the `#` symbol), and delete the content in the template as you add your own content.

   - For images and other static media resources, add them to the subfolder called **media**. If you are creating a new folder for content, add a media folder to the new folder.

   - Be sure to follow the proper Markdown syntax. See [Markdown basics](https://help.github.com/articles/markdown-basics/) for more information.

4. Submit a pull request from your branch to **MicrosoftDocs/Dynamics-365-Operations/master**. Your pull request will be reviewed, and we'll let you know if the change looks good or if there are any other updates or changes needed in order to approve it.

5. If needed, make any necessary updates to your branch. Your pull request will be merged into the master branch after it has been reviewed and your changes are approved.

On a certain cadence, we push all commits from the master branch into the live branch, after which you'll be able to see your contribution live at https://docs.microsoft.com/en-us/dynamics365/.

## Contributing to samples
If you have sample code, include the code as inline code blocks in your topic. There are currently no sample code repositories available for public contributions.

## Contributor License Agreement
If you submit a pull request with new or significant changes to documentation, you will need to submit an online Contributor License Agreement (CLA) if you are not an employee of Microsoft. You will need complete the online form before your pull request can be accepted. You must sign the CLA before your pull request is merged. This is a one-time requirement for projects on the Dynamics 365 documentation site. You can read more about [Contributor License Agreements (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) on Wikipedia.

## Do's and don'ts
Here are some guiding rules that you should keep in mind when you're contributing to the documentation.

- **Do** use the [template](./template.md) file as the starting point of your work.
- **Do** create a separate branch on your fork before working on topics. This makes it easier to recover from problems in your branches and go back to a good, known point.
- **Do** follow the [GitHub Flow workflow](https://guides.github.com/introduction/flow/).    
- **Don't** treat the repo as a general database store. Only store markdown text and media files in the repository. Only .md files and image files are allowed. 
- **Don't** check in anything that should not be seen by other people, for example an email address, password, access token, or internal server name. Even if you delete the text from the file, it will remain in the history and can be viewed from there. 
