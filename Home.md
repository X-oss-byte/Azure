Welcome to the App-Service-Migration-Assistant wiki!

# Getting Started
* [Introducing App Service Migration Assistant for ASP.NET applications](https://azure.microsoft.com/en-us/blog/introducing-the-app-service-migration-assistant-for-asp-net-applications/?utm_source=t.co&utm_medium=referral)
* [Migrate Your .NET Web Our New Step-By-Step Assistant - PRE10](https://www.youtube.com/watch?v=KYwPVok3-qI)
* [Start your app assessments and migrations now](https://appmigration.microsoft.com)

# Documentation
* [App Service Migration Assistant Readiness Checks](https://appmigration.microsoft.com/readinesschecks)

# FAQs
1. **Does App Service Migration Assistant support apps running on Windows and Linux?**
    At this time we support .NET app migration from Windows OS to Azure App Service.

2. **What are the current list of conditions that we consider that make an application unsuitable for automatic migration?**
    Below is the list: 
    * IIS version less than 7.0
    * Apps with a dependency on assemblies in the GAC that we don’t offer in our configuration
    * Apps that depend on session state that would break in our environment
    * Dependence on ISAPI filters
    * Dependence on ISAPI extensions
    * Bindings that are not HTTP or HTTPS
    * Endpoints that are not 80 for HTTP, or 443 for HTTPS
    * Authentication schemes other than anonymous
    * Dependencies on applicationhost.config settings made with a location tag
    * Applications that use more than one application pool
    * Use of an application pool that uses a custom account

