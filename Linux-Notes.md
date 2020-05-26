### Install on Linux
1. Download the azure-appService-migrationAssistant.tar.gz file to the machine
2. Confirm the file SHA matches the release notes SHA using command like: 
`sha256sum azure-appService-migrationAssistant.tar.gz`
3. Create (or pick) a directory where you want to place the tool, such as: `mkdir DirectoryName`
4. Unzip the file into that directory: `tar -xzf azure-appService-migrationAssistant.tar.gz -C DirectoryName`
5. Cd into the folder where you unzipped the tar.gz and launch the Migration Assistant using a command like: 
`sudo azure-appService-migrationAssistant-1.0.5/azure-appservice-migrationassistant --no-sandbox`