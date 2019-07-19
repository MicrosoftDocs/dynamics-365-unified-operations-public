This topic describes the process for adding the necessary script code to your pages to support the collection of client-side telemetry. 

Web analytics are an essential tool for understanding how your customers interact with your site and helping you make decisions that optimize the experience for maximum conversion. There are many web analytics packages available to help you in this regard, including (but not limited to) Google Analytics, Clicky, Moz Analytics, KISSMetrics and others. 

Most web analytics packages require you to add client-side script within the <head> tag of the HTML on all pages of your site. Here is how you add the script code for your web analytics package to your Dynamics 365 for Commerce site. NOTE: These instructions are equally applicable for any other custom client-side functionality not offered natively by Dynamics 365 for Commerce. 

Follow these steps To add client-side script to all the pages of your site

### Create a reusable fragment to contain your script code

1. Go to the **Fragments** menu in the site authoring environment
2. Click **New page fragment**
3. Select **External Script,** name your fragment and click **OK**.
4. In the fragment hierarchy, click the **script injector** module child of the fragment you just created
5. Add your client-side script and make other configuration options in the property panel at the right. See the help topic for the [External Script module](http://) for information about configuring this module.  

### Add the fragment to your master template(s)

1. Go to the **Master templates** menu in the site authoring environment
2. Open the master template for the pages you want to add your web analytics script to
3. Expand the template hierarchy in the left pane to expose the **HTML Head** slot
4. Click on the ellipsis for the HTML Head slot and click **Add fragment**
5. Select the fragment you created for your web analytics script
6. Save the template and check it in.

### Publish your changes. 

NOTE: you will need to publish the fragment and the master template. 

You can also add scripts to individual pages by adding an External script module directly to the HTML Head slot of a page. 

For further information about adding script to master templates, see the [Add script to master templates](http://) help topic

 

 

 

 

 