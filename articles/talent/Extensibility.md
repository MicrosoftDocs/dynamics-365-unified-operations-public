Extensibility 
==============

Built atop the Common Data Service (CDS) for Apps platform, Dynamics 365 for
Talent can be extended in a variety of ways using the Power Platform and the
capabilities offered by CDS for Apps. This enables you to configure and
personalize the system using PowerApps and Power Flow, as well as get additional
people analytics using Power BI. The hiring process is more adaptable than ever
with the addition of custom activities such as PowerApps and Web content
(iframe). You can tailor the hiring process to suit your business needs and
processes with these new types of activities and ensure that both the hiring
team and candidates have a seamless, customized experience.

Leveraging the Power Platform 
------------------------------

Since all the data from Attract resides in CDS for Apps, you can now use tools
from the Power Platform to incorporate your unique business needs into Attract.

### PowerApps

You can use PowerApps to build and run apps that easily connect to your Attract
data, use Excel-like expressions to add logic, and run on the web, iOS, and
Android devices. You can build a lightweight app to make university career fairs
easier for recruiters – allow them to scan resumes and feed candidates to a
position within Attract or build an app to meet your organization’s compliance
needs. Learn more about PowerApps and how to build them here:
<https://docs.microsoft.com/en-us/powerapps>

### Microsoft Flow 

Using Flows you can create automated workflows that run on top of Attract data.
You can connect to hundreds of popular apps and services easily and do so
without writing code. Would you like to send a notification to an onboarding
team when a candidate accepts an offer, or announce the news on Twitter? You can
automate such actions by building Flows that interact with the Attract’s Job,
Candidate and Application entities in CDS for Apps. You can learn more about
Flows here: <https://docs.microsoft.com/en-us/flow/>

### Power BI

Power BI allows you to build and view custom reports and dashboards that provide
you a deeper insight into your Attract data. Learn more about Power BI and how
to build interactive reports and dashboards here:
<https://docs.microsoft.com/en-us/power-bi/>

Custom Activities 
------------------

You can add custom activities such as PowerApps and Web content (iframe) both at
a job process template level and while creating a new job. Such activities allow
you to customize the hiring process and bring any business logic unique to your
organization into Attract.

### PowerApp activity 

This type of activity allows the creator of a job or job process template to
embed a PowerApp into the hiring flow. Once you create a PowerApp and publish
it, you can simply enter the PowerApp’s App ID in the activity configurations.
Using a PowerApp, you will be able to read/write data into CDS for Apps and you
may also tie the PowerApp with a Flow if desired. For instance, you may want to
have a PowerApp that recruiters use to fill in a form while perform a phone
screen which will evaluate whether an applicant can be advanced further. This
type of activity can only be viewed by members of the hiring team. To learn more
about how to configure this activity please refer to the Activities in Attract
topic.

Note: The PowerApps activity is only available with the Comprehensive Hiring
Add-On.

### Web content (iframe)

The web content (iframe) activity allows you to embed a custom web solution that
you may have built to meet your business and hiring needs, right in the hiring
process or in the candidate portal. Once again, you have the ability to
read/write data directly from CDS for Apps and can tailor such a solution to
trigger Flows or leverage Azure functions. To learn more about how to configure
this activity please refer to the Activities in Attract topic.

Note: The Web content activity is only available with the Comprehensive Hiring
Add-On.


