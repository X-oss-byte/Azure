### Migrate a container on Linux 
Azure CLI ([documentation](https://docs.microsoft.com/en-us/cli/azure/?view=azure-cli-latest)) provides a way to automate many Azure operations. For example, if you'd like to use a shell to migrate an existing Docker container on Linux to a new App Service site (by way of a new Azure Container Registry), then you could run a script like this one: 
[https://github.com/Azure/App-Service-Migration-Assistant/blob/master/MigrationDocs/ContainerToAppServiceWithAzureCLISample.sh](https://github.com/Azure/App-Service-Migration-Assistant/blob/master/MigrationDocs/ContainerToAppServiceWithAzureCLISample.sh). 

Just follow the 3 prerequisite steps noted at the top of the script (installing AzureCLI, logging in to Azure, and selecting your target subscription), and change the parameter values to names you'd like to use and an id for a container on your server. This script is meant to be used just as an example of how to use some of the commands - it won't prevent you from errors from things like picking site names that are already in use. 


