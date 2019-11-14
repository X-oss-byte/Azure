## Overview of how the Assistant works

The Azure App Service Migration Assistant is made up of 2 main parts: an Electron application UI and a helper iisConfigAssistant.exe that is used to read the site configuration information. The Migration Assistant does not make any changes to site content and does not change the local IIS configuration. The only changes made to the local server when using the tool are that it creates some temporary files (such as a mapping file to de-anonymize assessment results and a .zip of the site content during migration).

When the app is started, it calls the helper .exe to get the list of sites on the machine. 

Once a site is selected, the helper .exe is called to create an anonymized representation of the site configuration. This anonymized configuration is sent to the assessment API to check for unsupported configuration patterns and a report of those results is returned. There are also some assessment checks that are done locally. 

If a site does not have any migration blockers, the next step is logging in to an Azure account. This is done by requesting a device code which is shown to the user. The user may then complete the login on any device while the app polls for the token. 

Once the login is complete, the application queries ARM APIs to get option information such as available subscriptions, resource groups, app service plans, etc. When a deployment is started, the app creates an ARM template based on the selected options and starts a deployment to Azure, which it polls until complete. At this time the app queries for the created site publishing information, uses the helper .exe to create a .zip of the site content, and publishes the site content .zip to the Azure site. If Hybrid Connection was selected there is then another page explaining how to complete the in-network setup step. 

At this point the application Azure resources have been created, content has been published, and the site is ready to manage and test out in Azure.


# Outbound connections
**Outbound connections made by the Azure App Service Migration Assistant include:**
* appmigration.microsoft.com (Optional)
  * checks if newer versions of the Assistant are available
* dc.services.visualstudio.com (Optional)
  * Azure App Insights logging if enabled - see https://github.com/Microsoft/ApplicationInsights-Home/blob/master/EndpointSpecs/ENDPOINT-PROTOCOL.md for more details
* readinessapi.trafficmanager.net 
  * online assessment endpoint that evaluates anonymized configuration information for supported or unsupported patterns
* login.microsoftonline.com
* graph.microsoft.com (Optional)
  * for displaying friendly tenant names if changing tenants
* management.azure.com
  * for listing and creating Azure resources
* Your target site scm endpoint - format of: [CreatedAzureSiteName].scm.[azurewebsites.net|ASE dnsSuffix] 
  * for publishing site content
* Azure Migration endpoints if updating Azure Migrate Project status (Optional)
* items like: static2.sharepointonline.com, spoprod-a.akamaihd.net/files/fabric/assets/icons/[...] (Optional)
  * Office UI Fabric element items, like icons

