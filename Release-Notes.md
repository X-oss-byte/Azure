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
