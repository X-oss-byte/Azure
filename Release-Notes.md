### 1.0.0 (PS Scripts Preview) 
* SHA256 for AppServiceMigrationScripts.zip: 53E419F0C177B19130402264365FE1CC195FC9D9E5E39FB97CE67F2FBB21EA8B
* Preview of PowerShell script option for bulk assessment and migration of sites on an IIS server
* Allows override to migrate sites with identified issues
* Enables "offline" server scenario for assessing and packaging sites on a server that has limited outbound connectivity and then doing migration step from separate machine

### 1.0.9 (Preview) 

* Linux Preview which fixes issue with content publish step of Java migrations
* SHA256 for azure-appService-migrationAssistant.tar.gz: e77286168a04dc0f75e3532fc0fe77ded6ca4a2fcebad4567c122bd305e033d7, see [Install on Linux](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Linux-Notes#install-on-linux)

### 1.0.8 (Preview) 

* Preview of Java application migration for Tomcat running on Windows and Linux servers
* SHA256 for azure-appService-migrationAssistant.tar.gz: d30564a4b446de70c154c0600d9d2f39cb6560bd35c1b22262bffa35c2f544bb, see [Install on Linux](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Linux-Notes#install-on-linux)
* Updated information sent to Azure migration hub projects
* Fix for missing Azure migration projects in dropdown
* Fix for blank screen during content publishing step for large application content

### 1.0.6 

* Fix for specific operation status polling during template deployment
* Fix for resource group creation for USGov cloud target

### 1.0.5 (Preview)

* Linux Preview for migrating on-premises Docker containers using Docker Hub or Azure Container Registry
* SHA256 for azure-appService-migrationAssistant.tar.gz: ad536f70bf6fc4f5051e941f4315acea5eb1bdea5e96e4e26cbc7ee4c3ab8b9d, see [Install on Linux](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Linux-Notes#install-on-linux)
* Sync assessment data with Azure Migrate Hub for migrations with blockers

### 1.0.4

* Enable Azure Migrate Project options when targeting US Government cloud

### 1.0.2

* Improved handling of a configuration error case

### 1.0.1

* Added ability to target US Government Cloud
* Rebuilt to be independent of installed .NET Framework versions
* Automatically refresh tokens when on Login page in the same session
* Separate pre-migration validation to occur before showing migration progress, block on site name validation
* Fix for migration 404 error case when creating a new ASP
* Improved error messages when outbound connections are blocked 

### 1.0.0
* Integration with Azure Migrate Hub
* Added support for migrating to an existing App Service Plan
* Improved error handling, including better .NET Framework 4.7.2 required message

### 0.1.2 (Preview)
* Fixes for blocked assessments related to using certain properties in IIS7.5 configuration or using unsupported protocols
* Unblocking sites with connection strings issues
* Improved PHP version detection and unblocking migrations for sites with unknown or mixed PHP minor versions

### 0.1.1 (Preview)
* Add banner when newer Preview version is available
* Error logging improvements

### 0.1.0 (Preview)
* Added support for virtual directory migrations
* Added support for setting up Hybrid Connections on an alternate server
* Conversion to more comprehensive configuration assessment model

### 0.0.7
* Show a banner when a Preview version is available

### 0.0.6
* Added support for PHP applications using PHP version 5 or 7
* Specific notifications and handling for WordPress applications including database connection discovery and post-migration domain fixup assistance
* Warning for discovering only "localhost" server database connection string
* Logging uses ApplicationInsights, some additional logging

### 0.0.5
* Name change to Azure App Service Migration Assistant (from Azure App Service Migration Tool). 
* Install with already installed earlier version results in SxS rather than upgrade.
* Default to use Hybrid Connections only if non-localhost web.config connection string is discovered
* No longer uploading migration assessment report to site during migration (publish content steps reduced from 5 to 3)
 
### 0.0.4
* Single device code login
* Improved migration errors and retry behavior
* Handling for accounts with no subscriptions or disabled subscriptions
* “Preview” artifacts removed from naming
 
### 0.0.3 
* Enabled migration to an existing App Service Environment (ASEv2)
* Better error behavior when IIS is not installed
* Bug fixing around assessment report loading
* Disabled app launch during install
 
### 0.0.2
* Fixed bug with logging in – now requires logging in twice
 
### 0.0.1
* Initial release
