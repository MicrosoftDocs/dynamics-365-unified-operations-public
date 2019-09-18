# Add a logo
This topic describes how to add a logo to your Dynamics 365 for Commerce website.

Probably one of the first things you'll do when building your site is to add your company or brand's logo to the header of the site. The Starter Kit for Dynamics 365 Commerce provides a module that makes this task easy. 

It is possible to add a logo directly into a template, layout or page so that you can change the logo that appears on certain pages or groups of pages. However, this article will cover the most common scenario where you add your logo to a reusable header fragment that can be reused across all the pages of your site. 

## Prerequisites

Before you can add a logo to all the pages of your site, you must

- Upload your logo to the digital asset manager, which is accessed through the Assets tab. See the [[topic name]](foo.md) topic instructions on how to upload images. 
- Create a header fragment. See the [topic name] topic for more information on creating and using fragments
- Include the header fragment in the template that the pages of your site use for their layout and module options. See the [topic name] topic for an overview of templates. 


## Adding a logo to your site's header fragment

To add a logo to the Header fragment for your site, follow these steps:

1. Open your site's Header fragment by clicking on **Fragments** in the left nav and clicking on the fragment
2. Click **Check out** to make the fragment writeable 
3. Expand the **Header slot** and the **Logo slot**
4. Click the ellipsis to the right of the Logo slot and select **Add module**
5. Select the Logo module
6. Configure the Logo module to display your logo. For an explanation of the properties in the Logo module, see the [Logo module](http://) help topic.
7. Save, check in and publish your Header fragment

After you publish your Header fragment, all pages whose template includes the header fragment you updated in the steps above will display your logo. 

 

 

