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
