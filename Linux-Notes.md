### Install on Linux
1. Download the azure-appService-migrationAssistant.tar.gz file to the machine
2. Confirm the file SHA matches the release notes SHA using command like: 
`sha256sum azure-appService-migrationAssistant.tar.gz`
3. Create (or pick) a directory where you want to place the tool, such as: `mkdir DirectoryName`
4. Unzip the file into that directory: `tar -xzf azure-appService-migrationAssistant.tar.gz -C DirectoryName`
5. Cd into the folder where you unzipped the tar.gz and launch the Migration Assistant using a command like: 
`sudo azure-appService-migrationAssistant-1.0.5/azure-appservice-migrationassistant --no-sandbox`

### Shell Options
If you don't have a UI on your Linux machine or simply prefer to use shell only, you can do most of the things the application can do for docker container migrations with Azure CLI instead. Please check out this example of one way you might use Azure CLI to move a container from your Linux machine to App Service: https://github.com/Azure/App-Service-Migration-Assistant/wiki/Using-Azure-CLI