## Copy Activity

1. First we must create a new container to copy in CosmosDb with the correct Partition Key

2. Next We need top Create a Azure Data Factory in Azure.

3. Goto the Azure Dashboard and select Create a resource.

![text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DashboardHome.png?raw=true 'Request Pipeline')

4. Type Data Factory in the Search.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SearchDataFactory.png?raw=true 'Request Pipeline')

5. You will land on a the Data Factory Create page click Create.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DataFactoryCreatePage.png?raw=true 'Request Pipeline')

6. Create Data Factory Page File out resource group: create new:CVSHealthDFRSG, Region: East US, Name: CVSHealthDataFactoryV2,Version 2.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CreateDataFactorySettings.png?raw=true 'Request Pipeline')

7. Click Next Git configuration.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CreateDataFactorySettingsGitConfiguraton.png?raw=true 'Request Pipeline')

8. Click Configure Git Later.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CreateDataFactorySettingsConfigureGitlater.png?raw=true 'Request Pipeline')

9. Click Create and Review Once Validation is successful ClickCreate Once the Data Factory is Deployed Click Go to Resource

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DeploymentComplete.png?raw=true 'Request Pipeline')

10. Click on Author & Monitor

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DataFactoryDashClickOnAuthor_Monitor.png?raw=true 'Request Pipeline')

11. Click on the Copy data in the Let's get started area

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/AzureDataFactoryGetStartedPage.png?raw=true 'Request Pipeline')

12. Add a Task name CVSCopyCosmosDBToCosmosDb

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CreateLinkPage.png?raw=true 'Request Pipeline')

13. Click Create new connection

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SourceDataConnection.png?raw=true 'Request Pipeline')

14. Search for Azure Cosmos DB or if visible Select Azure CosmosDB (SQL API)

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SelectedConnectorSearch.png?raw=true 'Request Pipeline')

15. Once select the Continue button will become active click

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SelectConnectorCosmosContinue.png?raw=true 'Request Pipeline')

16. New linked Service and add Name: CosmosDbLink, Description:Link to Source (add your database name here) Database. ClickTest Connection and then click Create

17. Leave default Connection via intergration AutoResolveIntegrationRuntime, Select the subscription, select the Azure Database Account name from drop down,
    Database name: select the source database from drop down.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/NewLinkedServicesConnectionSettings.png?raw=true 'Request Pipeline')

18. Click on the Link we just created and then click next.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CosmosDBLinkSorce.png?raw=true 'Request Pipeline')

19. Select the source Container you wish to copy from you can see a preview of the data ,

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SourceTableSelectionandPreview.png?raw=true 'Request Pipeline')

20. Select Page size the default is 1 we will go with that andselect preferred regions now click next.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DataSetFilterPageSize.png?raw=true 'Request Pipeline')

21. Destination data store, in this window select theCosmosDbLink we created we will configure the destination now

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CosmosDBLinkDestination.png?raw=true 'Request Pipeline')

22. Select the Container you created to move the data to in this case it is the FamilyContainerPk

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/SelectDestionationContainer.png?raw=true 'Request Pipeline')

23. Settings We leave this blank for now but lets explore the options just to see what is available.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DestinationSettings.png?raw=true 'Request Pipeline')

24. Summary: You are running pipeline to copy data from AzureCosmos DB (SQL API) to Azure Cosmos DB (SQL API).

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/CopyPipelineSummary.png?raw=true 'Request Pipeline')

25. After clicking Next.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/DeploymentCompletAzureCosmosDBCopyPipeline.png?raw=true 'Request Pipeline')

26. Click finish this will take you back to the home page. NowClick on the Monitor button on the left hand side navigation bar.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/MonitorButton.png?raw=true 'Request Pipeline')

27. In this window you can observer Pipelines success or failure.

![alt text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/MonitorDashPipelineRuns.png?raw=true 'Request Pipeline')

> Note: If there are duplicate recorders in the destination Container the pipeline Copy Task will fail.

Error if Document already exists in Target

```console

Operation on target Copy_jfy failed: ErrorCode=UserErrorDocumentDBWriteError,'Type=Microsoft.DataTransfer.Common.Shared.HybridDeliveryException,Message=Documents failed to import. Error message:Message: {"Errors":["Encountered exception while executing function. Exception = Error: {\"Errors\":[\"Resource with specified id or name already exists.\"]}\r\nStack trace: Error: {\"Errors\":[\"Resource with specified id or name already exists.\"]}\n at createCallback (script.js:6223:26)\n at Anonymous function (script.js:686:29)"]} ActivityId: 6c8d404b-2138-4b38-a74a-1c63b0173c1a, Request URI: /apps/9d722ed0-abe2-4bf1-a7dc-1ea945eb0588/services/e5ae84cc-1d1b-4f14-b2b4-a8b2520b2b08/partitions/77306050-e8a5-4419-b69b-08b6cc0ed8ee/replicas/132452205015901146p/, RequestStats: RequestStartTime: 2020-09-22T15:29:42.3617807Z, RequestEndTime: 2020-09-22T15:29:42.3617807Z, Number of regions attempted:1 ResponseTime: 2020-09-22T15:29:42.3617807Z, StoreResult: StorePhysicalAddress: rntbd://cdb-ms-prod-eastus1-fd51.documents.azure.com:14310/apps/9d722ed0-abe2-4bf1-a7dc-1ea945eb0588/services/e5ae84cc-1d1b-4f14-b2b4-a8b2520b2b08/partitions/77306050-e8a5-4419-b69b-08b6cc0ed8ee/replicas/132452205015901146p/, LSN: 6, GlobalCommittedLsn: 6, PartitionKeyRangeId: 0, IsValid: True, StatusCode: 400, SubStatusCode: 409, RequestCharge: 3.16, ItemLSN: -1, SessionToken: -1#6, UsingLocalLSN: False, TransportException: null, ResourceType: StoredProcedure, OperationType: ExecuteJavaScript , SDK: Microsoft.Azure.Documents.Common/2.11.0, documentdb-dotnet-sdk/2.5.1 Host/64-bit MicrosoftWindowsNT/6.2.9200.0.,Source=Microsoft.DataTransfer.DocumentDbManagement,''Type=Microsoft.Azure.Documents.DocumentClientException,Message=Message: {"Errors":["Encountered exception while executing function. Exception = Error: {\"Errors\":[\"Resource with specified id or name already exists.\"]}\r\nStack trace: Error: {\"Errors\":[\"Resource with specified id or name already exists.\"]}\n at createCallback (script.js:6223:26)\n at Anonymous function (script.js:686:29)"]} ActivityId: 6c8d404b-2138-4b38-a74a-1c63b0173c1a, Request URI: /apps/9d722ed0-abe2-4bf1-a7dc-1ea945eb0588/services/e5ae84cc-1d1b-4f14-b2b4-a8b2520b2b08/partitions/77306050-e8a5-4419-b69b-08b6cc0ed8ee/replicas/132452205015901146p/, RequestStats: RequestStartTime: 2020-09-22T15:29:42.3617807Z, RequestEndTime: 2020-09-22T15:29:42.3617807Z, Number of regions attempted:1 ResponseTime: 2020-09-22T15:29:42.3617807Z, StoreResult: StorePhysicalAddress: rntbd://cdb-ms-prod-eastus1-fd51.documents.azure.com:14310/apps/9d722ed0-abe2-4bf1-a7dc-1ea945eb0588/services/e5ae84cc-1d1b-4f14-b2b4-a8b2520b2b08/partitions/77306050-e8a5-4419-b69b-08b6cc0ed8ee/replicas/132452205015901146p/, LSN: 6, GlobalCommittedLsn: 6, PartitionKeyRangeId: 0, IsValid: True, StatusCode: 400, SubStatusCode: 409, RequestCharge: 3.16, ItemLSN: -1, SessionToken: -1#6, UsingLocalLSN: False, TransportException: null, ResourceType: StoredProcedure, OperationType: ExecuteJavaScript , SDK: Microsoft.Azure.Documents.Common/2.11.0, documentdb-dotnet-sdk/2.5.1 Host/64-bit MicrosoftWindowsNT/6.2.9200.0,Source=Microsoft.Azure.Documents.Client,'
```
