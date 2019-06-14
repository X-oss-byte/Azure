# Using Hybrid Connections for Apps with Stateful File Content (like WordPress)
Hybrid Connections provides a way to connect to on-premises resources like databases from Azure. When you migrate a site using hybrid connections, the database state stays in sync between the local and the migrated Azure version of a site, but the file content can become divergent. Care should be taken when using applications that store state or content in their file content, as this can create problems especially if actively running both the local and Azure version of the site at the same time. 
 
For example, WordPress stores media content, such as images, in the file content of the application, and blog definitions in the database. If you migrated your WordPress site to Azure and then continue to use the local site such as to add a new post with an image, the Azure site will fail to load the image for that post because it is missing from the Azure side file content. Similarly if you add a new post with media from the Azure site, then the local site will not be able to load the media. Because of this file-system content dependency in WordPress, we strongly suggest that Hybrid Connections are used very carefully for testing until ready to switch fully to the Azure site.