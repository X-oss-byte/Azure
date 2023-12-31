Welcome to the App-Service-Migration-Assistant wiki!

## Looking for info about...

* Using Migration Assistant on Linux -> see [Linux Notes](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Linux-Notes)
* The PowerShell scripts -> check out [PowerShell Scripts](https://github.com/Azure/App-Service-Migration-Assistant/wiki/PowerShell-Scripts)
* Migrating Java applications from Apache Tomcat servers -> see [TOMCAT Java Information](https://github.com/Azure/App-Service-Migration-Assistant/wiki/TOMCAT-Java-Information)

# Getting Started
* [Introducing App Service Migration Assistant for ASP.NET applications](https://azure.microsoft.com/en-us/blog/introducing-the-app-service-migration-assistant-for-asp-net-applications/?utm_source=t.co&utm_medium=referral)
* [Migrate Your .NET Web Our New Step-By-Step Assistant - PRE10](https://www.youtube.com/watch?v=KYwPVok3-qI)
* [Start your .NET and PHP app assessments and migrations now](https://appmigration.microsoft.com)

# FAQs
1. **Does App Service Migration Assistant support apps running on Windows and Linux?**
    At this time we support .NET app migration from Windows OS to Azure App Service. Java Tomcat app migrations from Windows and Linux machines is in Preview.

2. **What are the current server requirements to use the Migration Assistant?**
    * Windows server IIS version greater than or equal to 7.5
    * Administrator access
    * Outbound connections allowed (see here for details: https://github.com/Azure/App-Service-Migration-Assistant/wiki/How-the-Assistant-Works#outbound-connections)
    * Local IIS configuration (clustered / remote IIS server configurations not supported)

3.  **What are all the readiness checks that the Azure Migration Assistant makes?**
    * [App Service Migration Assistant Readiness Checks](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks)
   
4. **What are the current list of conditions that we consider that make an application unsuitable for automatic migration?**
    Below is the list: 
    * Apps that depend on session state that would break in our environment
    * Dependence on ISAPI filters
    * Dependence on ISAPI extensions
    * Bindings that are not HTTP or HTTPS
    * Endpoints that are not 80 for HTTP, or 443 for HTTPS
    * Authentication schemes other than anonymous
    * Dependencies on applicationhost.config settings made with a location tag
    * Applications that use more than one application pool
    * Use of an application pool that uses a custom account

## Getting Help
Migration assistant tooling is provided as-is, and the way to get help or report issues is by using the [Issues](https://github.com/Azure/App-Service-Migration-Assistant/issues) page.