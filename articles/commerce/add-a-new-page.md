# Add a new page
This topic describes how to add a new page to your e-Commerce website.

After you have finished with your templates and fragments, next step is to start creating pages that utilize them.

First, you need to open the authoring tool and navigate to the site you would like to add the new page on. Make sure that "Pages" is selected from the action ribbon, no pages are selected and then proceed to activate the "New page"-button.

You will be presented with a new page dialog where you are asked which template you would like to use for the new page.  You are also required to enter the name for the new page and you can optionally enter the URL for the page.

### Template
You can choose to use either Layout or Template for your new page. For more information on Layouts, please see (link here) and for Templates, please see (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/niholman-Templates-and-layouts/articles/commerce/Templates-and-layouts.md#create-a-new-template).

### Page Name
Page Name is unique to your page. You should give your page a descriptive name so that you are able to find it easily in the future and so that other people know what the page is used for. Choose the page name carefully, it cannot be changed later.

### URL
You have the option of entering URL for your new page. If you choose to enter the URL at the time of new page creation, new URL is created and your new page is assigned to that URL. You can change the URL at later time before publishing the page. For more information about URLs, please see (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/pull/5732/files#diff-52d02a4ac5f62ea90af3f36617ffa0ce).

When you have entered all the required information and press "OK", the page is created and page editor opens to your new page with it checked out to you. The "Page Outline"-view reflects the structure of the template you selected for your new page. You may continue modifying your page or create another one.

Note: Dynamics 365 e-Commerce feature decouples URLs and content. Page can be created without associating it with an URL and vice versa. This allows switching the content for an URL with zero downtime and allows easy management of redirections.

For more information on page editing, please see the following articles
- (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/pull/5781/files#diff-c38debc450971f13ad973303bba03074)
