Chapter 10: SEO, Search Engine Visibility and Ongoing Maintenance

← Back to Main README

10.1 Introduction

After deploying Laurelite Importation Hub, I also worked on improving the website’s search engine visibility.

Having a live website is important, but I wanted to make sure search engines could discover and understand the website’s public pages.

This chapter documents the SEO improvements, metadata configuration, sitemap, robots file, Google Search Console setup and ongoing maintenance considerations.

10.2 Search Engine Optimisation

Search Engine Optimisation (SEO) involves improving a website’s structure and content so that search engines can understand and potentially display its pages in search results.

For Laurelite Importation Hub, I focused on the technical SEO configuration of the production website.

The improvements included:

* Branded page titles.
* Meta descriptions.
* Robots directives.
* Googlebot directives.
* Canonical URL configuration.
* Open Graph metadata.
* XML sitemap.
* Robots.txt configuration.
* Google Search Console verification.

10.3 Website Metadata Configuration

I updated the website’s HTML metadata to give search engines and social platforms more meaningful information about the application.

Page Title

The configured website title is:

<title>Laurelite Importation Hub | Quality Products Online</title>

This provides a branded title instead of the default development title.

Meta Description

I added a meta description to communicate the purpose of the website to search engines.

Robots Metadata

Robots directives were configured to guide search engine crawlers on how public pages should be handled.

Googlebot Metadata

Googlebot-specific metadata was also included as part of the SEO configuration.

Canonical URL

Canonical metadata was added to identify the preferred URL for the homepage.

Open Graph Metadata

Open Graph metadata was included to improve how website information is presented when shared on supported social platforms.

10.4 Robots.txt Configuration

I created a robots.txt file to provide crawler instructions and identify the website sitemap.

The configured content is:

User-agent: *
Allow: /
Sitemap: https://lovedigitals.online/sitemap.xml

The file is available at:

https://lovedigitals.online/robots.txt

This configuration allows crawlers to access the website’s public pages and provides the sitemap location.

10.5 XML Sitemap Configuration

I created an XML sitemap to identify important public pages on the website.

The sitemap is available at:

https://lovedigitals.online/sitemap.xml

The submitted sitemap includes these six public URLs:

1. Homepage.
2. Product listing page.
3. Love Digitals information page.
4. Contact page.
5. Privacy policy.
6. Copyright policy.

The sitemap helps search engines discover the public URLs included in it.

Submitting a sitemap does not guarantee that every URL will be indexed, but it provides search engines with a structured list of pages to discover.

10.6 Google Search Console Integration

I configured Google Search Console to monitor the website’s search visibility.

Domain Verification

The website was verified as a domain property using a DNS TXT record configured through Namecheap.

This established ownership of the domain within Google Search Console.

Sitemap Submission

After verification, I submitted the sitemap:

https://lovedigitals.online/sitemap.xml

The sitemap submission was successful.

URL Inspection

I also used the URL Inspection tool to test the homepage’s live URL.

The live URL test was successful, and an indexing request was accepted.

It is important to distinguish between an accepted indexing request and actual indexing. Acceptance does not guarantee that Google will index the page or display it in search results.

10.7 React and SEO Considerations

Because the frontend is built with React and Vite, I also considered how the application’s structure affects search engine discovery.

Technical SEO improvements are particularly important for a client-side rendered application.

The current configuration provides important metadata and crawler guidance.

Further improvements may include:

* More descriptive product page metadata.
* Unique titles for important pages.
* Product-specific descriptions.
* Better category page metadata.
* Structured data where appropriate.
* Continued review of search engine crawling and indexing.

10.8 Search Visibility Monitoring

Google Search Console provides information that can help monitor how the website performs in Google Search.

Areas to review include:

* Indexed pages.
* Pages excluded from indexing.
* Sitemap processing.
* Search queries.
* Impressions.
* Clicks.
* Search performance.
* Crawling and indexing issues.

Regular monitoring helps identify areas that need further SEO improvements.

10.9 Application Maintenance

Deploying a website is not the end of development.

Laurelite Importation Hub requires ongoing maintenance to keep the application reliable, secure and functional.

Important maintenance areas include:

10.9.1 Frontend Maintenance

* Reviewing frontend errors.
* Updating dependencies carefully.
* Testing responsive layouts.
* Reviewing navigation and user experience.
* Building and deploying frontend updates.

10.9.2 Backend Maintenance

* Monitoring backend processes.
* Reviewing application logs.
* Fixing API errors.
* Updating dependencies.
* Reviewing authentication and security.
* Testing important application workflows.

10.9.3 Database Maintenance

* Monitoring database connectivity.
* Reviewing database performance.
* Maintaining data integrity.
* Reviewing database access permissions.
* Maintaining appropriate backup and recovery procedures.

10.9.4 Payment and Wallet Maintenance

Financial functionality requires particular attention.

Maintenance activities should include:

* Reviewing payment verification behaviour.
* Monitoring Paystack webhook processing.
* Reviewing wallet transactions.
* Checking refund records.
* Maintaining transaction safeguards.
* Investigating failed or unexpected payment operations.

10.9.5 Cloud Infrastructure Maintenance

The AWS environment also requires ongoing attention.

Important areas include:

* EC2 instance health.
* Server resource utilisation.
* Security Group configuration.
* Nginx configuration.
* SSL certificate renewal.
* PM2 process status.
* Application logs.
* Infrastructure monitoring.

10.9.6 SEO Maintenance

SEO maintenance includes:

* Reviewing sitemap availability.
* Checking robots.txt.
* Monitoring Search Console.
* Reviewing indexing reports.
* Improving page metadata.
* Updating public website content.

10.10 Backup and Recovery Considerations

A production application needs an appropriate backup and recovery strategy.

For Laurelite Importation Hub, database backup arrangements, recovery procedures and configuration backups should remain part of ongoing operational maintenance.

The ability to recover application data and restore services is important for protecting the platform against unexpected failures.

10.11 Development and Deployment Improvements

As the platform grows, I intend to continue improving the development and deployment workflow.

Potential improvements include:

* Automated testing.
* Automated frontend and backend builds.
* GitHub Actions integration.
* Automated deployment workflows.
* More detailed monitoring and alerting.
* Improved backup automation.
* Further infrastructure security reviews.

These are areas for continued improvement and should not be interpreted as a claim that a fully automated CI/CD pipeline is already operational.

10.12 Important Note on Documentation and Source Versions

Some of the SEO improvements documented in this chapter were introduced during later production deployment work.

The original uploaded source-code ZIP represented an earlier version of the project. Its frontend/index.html still contained the default title:

<title>frontend</title>

The later live deployment improvements included the branded metadata, robots.txt, sitemap.xml and Google Search Console configuration.

This distinction is important when comparing the original source snapshot with the later production website.

10.13 Conclusion

Improving search engine visibility and maintaining the production application are ongoing responsibilities.

By configuring metadata, robots.txt, an XML sitemap and Google Search Console, I established an initial technical SEO foundation for Laurelite Importation Hub.

The project will continue to evolve through application maintenance, infrastructure improvements, security reviews and further search optimisation.

⸻

← Previous: Deployment and AWS Infrastructure | Back to Main README | Back to Table of Contents
