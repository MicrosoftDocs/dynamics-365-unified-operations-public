# SEO considerations

This article describes at high-level the SEO lifecycle of your site from development to production and your page from creation to published.

### Site
For site **under development**, you should have no-index, no-follow metatags in place for pages so that search engines do not index them and store development versions of your site in their cache. To do this you need to have Default Metatags module on the template which will enable the default metatags properties under SEO properties section in the page editor. Metatags can be managed under SEO properties section.

**Soft launch**
When you are performing soft launch for your website, you should consider having no-index tags still in place to make sure that your soft launch is limited to the audience you intend to participate.

**Production**
For site in production you want to make sure you have all your pages properly tagged. Dynamics 365 e-Commerce feature renders all the SEO information on the page using the information entered for a page. Modules that provide this functionality are Category Page Summary, List Page Summary and Product Page Summary. Rendering framework uses information from SEO properties section as well as module specific information to optimize search engine indexing. For site in production you want to make sure that your robots.txt allows indexing your entire site and contains link to your published sitemap document. Sitemap generation should be enabled from **Site Settings** -> **Site maps enabled**.

### Pages
Because Dynamics 365 e-Commerce feature supports WYSIWYG- and authenticated preview, authors can prepare their page content without having to worry about information becoming visible to the C2 rendered site. Should there be a need to publish a page, but limit its exposure, page metatags should include the no-index tag to avoid being indexed to search engines. When the page is ready for all audiences, all of the basic SEO metadata should be present for a page to maximize search engine indexing efficiency and no-limit should be removed.

