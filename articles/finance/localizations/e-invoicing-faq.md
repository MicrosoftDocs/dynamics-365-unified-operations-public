# Electronic invoicing add-on – Frequent Asked Questions

## 

## Question 1: What is so important about electronic invoicing? Why should it matter to me?

Operational complexity and risk continue to intensify as organizations
grow globally and expand their footprints across regions. Maintaining
compliance and adapting to frequently changing regulations is a growing
challenge and is of particular importance when it comes to invoicing.
Invoicing has traditionally been expensive and prone to errors as
companies rely on paper documents and manually intensive processes.  

Organizations have begun to move away from paper invoices to reduce
costs and speed up the end-to-end process. Moreover, governments are
increasingly turning to electronic invoicing as a key component of tax
digitalization. By requiring organizations to digitally submit real-time
tax information to tax authorities, governments can minimize tax evasion
and manipulation, and reduce fraud. 

The world is shifting to paperless document processing and without
implementing electronic invoicing customers' risk compliance issues,
unnecessary costs and lagging behind competitors. 

## Question 2: Doesn't Dynamics 365 Finance, Supply Chain Management and Project Operations already including electronic invoicing functionality? What value does the Electronic Invoicing add-on bring to me as a customer? 

The Electronic invoicing add-on extends the electronic invoicing
capabilities existing in Dynamics 365 Finance, Supply Chain Management
and Project Operations, simplifies adherence to newest electronic
invoicing standards and provides coherent experiences for different
geographies in electronic invoice processing and exchange. Electronic
Invoicing's capabilities unlock an array of benefits including: 

-   Faster and easier adoption to country / region specific requirements
    > (Brazilian and Mexican electronic invoicing is now made fully
    > configurable) 

<!-- -->

-   Standardization of e-Invoicing solution implementations  

-   Enhanced e-invoice processing traceability  

-   Easier maintenance to comply with changing legal requirements and
    > local business practices 

-   Simplified solution packaging

-   Scaling capabilities in case of big volume of submitted documents
    > that results in faster turnaround

-   Possibility to share your solutions with other companies.

## Question 3: Does the Electronic invoicing add-on support the on-premises installations of Dynamics 365 Finance, Supply Chain Management and Project Operations? Are there any plans to release the add-on for on-premises scenarios?

The current Microservices platform does not allow to use hyper-scalable
for on-premises version. It's not on the roadmap as of now.

## Question 4: Does the Electronic invoicing add-on interface with the vendor import automation feature?

No, it does not. We plan to interface, but there are not dates defined.
When planned, the dates will be announced through release plans.

## Question 5: How does the Electronic invoicing add-on handle file attachments into the electronic invoice? Is a SharePoint server needed when embedding PDF-files into the XML file?

The attached files into the electronic invoice are handled as embedded
binary data in an XML element. A SharePoint server is not needed for
embedding PDF-files, but the attachment must be stored in the Dynamics
365 Finance, Supply Chain Management and Project Operations document
management system.

## Question 6: Is the Electronic invoicing add-on available according to the regulations of my country?

The Electronic invoicing add-on is a microservice platform which will be
globally available.

Microsoft plans to publish the electronic invoice formats and
integrations for the countries that are functionally localized by
Microsoft, as of now, listed in [Availability of electronic invoicing
features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs#availability-of-electronic-invoicing-features).

If the electronic invoicing format for your country is not listed here,
the platform aims to support this scenario too, you can still benefit
from the configuration capabilities the Electronic invoicing add-on has,
and configure the electronic invoicing format by yourself, or you can
hire a partner/ISV to configure those for your organization.

## Question 7: Is the Dynamics 365 for Regulatory Services a new module such as HR or Project Operations that is linked to Dynamics 365 Finance or Supply Chain Management? Are there extra costs for that?

The Dynamics 365 for Regulatory Services, aka Regulatory Configuration
Services (RCS) is a cloud service for configuration of Globalization
resources. It is free of charge for all Dynamics 365 Finance, Supply
Chain Management and Project Operations license holders.

For sign-up in RCS, go to
<https://marketing.configure.global.dynamics.com/>

For more information, see [Regulatory Configuration Services (RCS) -
Globalization features - Finance | Dynamics 365 | Microsoft
Docs](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-globalization-feature)

## Question 8: Is the Electronic invoicing add-on available to all regions? Do I need to sign up somewhere, or just turn it on in Feature Management?

The Electronic invoicing add-on as a microservice platform will be
globally available (also see Question \#6).

If you are Dynamics 365 Finance, Supply Chain Management and Project Operations license holder, for sign-up in Electronic invoicing add-on, see [Get started with
Electronic invoicing add-on service administration - Finance | Dynamics
365 | Microsoft
Docs](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started-service-administration).

## Question 9: Does the Electronic invoicing add-on work with Tier 1 virtual machines? What is the minimal environment does it require to work?

The integration with Electronic invoicing add-on requires at least a
Tier 2 virtual machines for hosting Dynamics 365 Finance or Supply Chain
Management. For more information about environment planning, see
[Environment planning - Finance & Operations | Dynamics 365 | Microsoft
Docs](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning)

## Question 10: Does the Electronic invoicing add-on have a "test" mode for testing of submission of invoices?

This can be achieved by configuration. For testing the submission of
invoices, you can connect a Dynamics 365 Finance or Supply Chain
Management from an UAT (User Acceptance Test) environment, from where
you can submit the test invoices. Furthermore, the Electronic invoicing
add-on supports the configuration of test digital certificates, as well
the setup of URL from test web services, published by the tax
authorities, in the cases where the e-invoice requires digital approval.

## Question 11: Is there any documentation about the out-of-box country-specific Electronic invoicing add-on features, such as supported formats, supported providers, etc?

The availability of the Electronic invoicing add-on features as well the
formats they support are listed in the following article: [Availability
of electronic invoicing
features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs#availability-of-electronic-invoicing-features).

> [!NOTE] If you did not find the answer you was looking for, please feel free to
> e-mail your question to the Product Development Team, through <D365EInvoicePreview@microsoft.com> and we can either
> contact you or improve the coverage of this FAQ.
