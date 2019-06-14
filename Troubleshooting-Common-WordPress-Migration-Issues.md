Below are some descriptions of common issues with migration WordPress sites to Azure and how to resolve them. 
 
## Redirected to local site when clicking links on migrated Azure site
Going to the root of your site works to display the homepage, but when you click on links such as for a post, you are taken to a URL with the original local site domain rather than staying on your new Azure site. Alternatively the links may be correct, but the styles and rendering of the site are not correct.
### What's happening?
Hostname is stored in the WordPress database and used to generate links that are stored as relative paths to the hostname, so if you did not migrate a custom domain to the Azure site, you will get constantly redirected to the database hostname value rather than your Azure site hostname. 
### Troubleshooting steps:
1. Follow the steps on the final Results page of the Assessment tool to edit your wp-config.php with a temporary domain override - these steps are included below in case you no longer have the Assistant open:
* Login to portal.azure.com and search for your site resource, select it
* Scroll down to Development Tools > App Service Editor and Go to the editor
* Select wp-config.php in the left-hand file menu
* Paste in the below lines to your wp-config.php file (replace YOUR_SITE_NAME with your actual site name):

`define('WP_HOME', 'https://YOUR_SITE_NAME.azurewebsites.net');`
`define('WP_SITEURL', 'https:// YOUR_SITE_NAME.azurewebsites.net');`

* Refresh your WordPress site. At this point your application should generally work – though there may still be specific hardcoded references to your old domain in post content.
2.  When you’re ready to fully switch to the Azure site, you can update the database values (“siteurl” and “home” in wp_options table) and remove the ones in your wp-config.php. You may want to check out WordPress’ documentation on changing your domain for additional fixup options as needed (in case there are any hard-coded / permalinks that would require a database search-and-replace action to correct):  https://wordpress.org/support/article/moving-wordpress/#changing-your-domain-name-and-urls 


## Unable to view media in new posts
This may be related to using Hybrid Connections and having local and migrated sites running simultaneously. [Learn more about this](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Known-Issues#using-hybrid-connections-for-apps-with-stateful-file-content-like-wordpress)
 

 
# Database connection issues
 
## Unable to establish database connection after changing “localhost” server to machine name locally
Either you are using "localhost" or you have updated wp-config.php to use machine name but that breaks the database connections. 
### What's happening?
This is typically due to the MySQL database running on the same machine as the web server and the MySQL configuration not allowing for a "remote" connection. The db user login is often created as for @'localhost'.
### Troubleshooting steps:
1. Update db user to enable remote connections. Open up the MySQL Command Line Client (or use a tool like MySQL WorkBench), and enter the MySQL server admin password to connect to your server. Then run the below lines, replacing YOUR_DB_USER_NAME with your actual db user name (DB_USER from wp-config.php)

`UPDATE mysql.user SET Host='%' WHERE Host='localhost' AND User='YOUR_DB_USER_NAME';
UPDATE mysql.db SET Host='%' WHERE Host='localhost' AND User='YOUR_DB_USER_NAME';
FLUSH PRIVILEGES;`

2. Update the wp-config.php file in wordpress site with the machine name rather than "localhost" for DB_HOST
 

## Unable to establish database connection after migration when using Hybrid Connections
The WordPress application works fine locally, but fails to establish a database connection after migration
### Troubleshooting steps:
1. Confirm that you are using a DNS server name and not "localhost" for the database server name in your wp-config.php file - search for the "DB_HOST" configuration value (like this one: "define('DB_HOST', ‘localhost’);"). If you are using "localhost" then you will need to change it to the database server name. Confirm this works for your local site first before trying it on a migrated site to isolate database configuration issues. 
2. Confirm that your Hybrid Connection is set up and connected.
* Go to your site resource on portal.azure.com
* Select the Settings > Networking view. Look for the "Hybrid connections" section and click "Configure your hybrid connection endpoints"
* In the Hybrid Connections page you should see a hybrid connection listed at the bottom with a name like YOUR_SITE_NAMERelay0-a123 (where "a123" is some random combination of letters and numbers). 
  * If you do not see this connection then Hybrid Connection setup was not done correctly during migration. Please try migrating again making sure that setting up hybrid connections is selected on the Azure Options page of the Migration Assistant, and if this still occurs then please open an issue. If you don't think you need hybrid connections because your database is internet accessible, then to go (4) 
  * If the status of the connection is "Connected" then make a note of the "ENDPOINT" value and move on to (3), if not connected, then leave this page open
* Go to the machine where you installed the Hybrid Connection manager, and open the "Hybrid Connection Manager UI" application. Look for a connection with a name matching the one you just found in the portal
  * If you do not see a connection with the matching name, then add it: go back to the Hybrid Connections page you left open in portal, select the Hybrid Connection to open a Properties menu, and copy the "GATEWAY CONNECTION STRING" to your clipboard. Then in the Hybrid Connection Manager UI click the "Enter Manually" button and paste the value in as the "Connection String" and click "Add". 
  * If the connection exists and the status is not "Connected", try restarting the Hybrid Connection Manager service. Open "Services" application and look for a service with the name "Azure Hybrid Connection Manager Service". Restart this service and check the status again
  * If the connection status is still not "Connected", check out these Hybrid Connection troubleshooting notes: https://docs.microsoft.com/en-us/azure/app-service/app-service-hybrid-connections#troubleshooting
3. Confirm that your Hybrid Connection ENDPOINT server name exactly matches the value used for "DB_HOST" in wp-config.php. Also confirm that the ENDPOINT port is correct for your MySQL server (this value is commonly the default MySQL port of 3306). 
* If you need to update your wp-config.php values, then you can do this in the browser by going to portal.azure.com and finding your site resource, scroll down to Development Tools > App Service Editor and Go to the editor, select wp-config.php in the left-hand file menu and make your changes. If the connection still does not work, make the same changes on your local site and troubleshoot there first.
* If you need to update the Hybrid Connection values then you can either follow directions on this page to add a new Hybrid Connection (https://docs.microsoft.com/en-us/azure/app-service/app-service-hybrid-connections#add-and-create-hybrid-connections-in-your-app) or use Migration Assistant to migrate the site again with different values in Azure Options and delete the original migrated site and relay.
4. Check for db configuration issues outside of Hybrid Connections
* Using the connection information in your wp-config.php file, make sure you can connect to the database from a different machine in your network.
 
