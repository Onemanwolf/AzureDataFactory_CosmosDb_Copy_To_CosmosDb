##



In the world of big data, raw, unorganized data is often stored in relational, non-relational, and other storage systems. However, on its own, raw data doesn't have the proper context or meaning to provide meaningful insights to analysts, data scientists, or business decision makers.

Big data requires service that can orchestrate and operationalize processes to refine these enormous stores of raw data into actionable business insights. Azure Data Factory is a managed cloud service that's built for these complex hybrid extract-transform-load (ETL), extract-load-transform (ELT), and data integration projects.

For example, imagine a gaming company that collects petabytes of game logs that are produced by games in the cloud. The company wants to analyze these logs to gain insights into customer preferences, demographics, and usage behavior. It also wants to identify up-sell and cross-sell opportunities, develop compelling new features, drive business growth, and provide a better experience to its customers.

To analyze these logs, the company needs to use reference data such as customer information, game information, and marketing campaign information that is in an on-premises data store. The company wants to utilize this data from the on-premises data store, combining it with additional log data that it has in a cloud data store.

To extract insights, it hopes to process the joined data by using a Spark cluster in the cloud (Azure HDInsight), and publish the transformed data into a cloud data warehouse such as Azure Synapse Analytics (formerly SQL Data Warehouse) to easily build a report on top of it. They want to automate this workflow, and monitor and manage it on a daily schedule. They also want to execute it when files land in a blob store container.

Azure Data Factory is the platform that solves such data scenarios. It is the cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale. Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores. You can build complex ETL processes that transform data visually with data flows or by using compute services such as Azure HDInsight Hadoop, Azure Databricks, and Azure SQL Database.

Additionally, you can publish your transformed data to data stores such as Azure Synapse Analytics for business intelligence (BI) applications to consume. Ultimately, through Azure Data Factory, raw data can be organized into meaningful data stores and data lakes for better business decisions.



![text](https://github.com/Onemanwolf/AzureDataFactory_CosmosDb_Copy_To_CosmosDb/blob/master/How_Session/Images/overview.png?raw=true  'Request Pipeline'  )

# How does it work?
Data Factory contains a series of interconnected systems that provide a complete end-to-end platform for data engineers.

## Connect and collect
Enterprises have data of various types that are located in disparate sources on-premises, in the cloud, structured, unstructured, and semi-structured, all arriving at different intervals and speeds.

The first step in building an information production system is to connect to all the required sources of data and processing, such as software-as-a-service (SaaS) services, databases, file shares, and FTP web services. The next step is to move the data as needed to a centralized location for subsequent processing.

Without Data Factory, enterprises must build custom data movement components or write custom services to integrate these data sources and processing. It's expensive and hard to integrate and maintain such systems. In addition, they often lack the enterprise-grade monitoring, alerting, and the controls that a fully managed service can offer.

With Data Factory, you can use the Copy Activity in a data pipeline to move data from both on-premises and cloud source data stores to a centralization data store in the cloud for further analysis. For example, you can collect data in Azure Data Lake Storage and transform the data later by using an Azure Data Lake Analytics compute service. You can also collect data in Azure Blob storage and transform it later by using an Azure HDInsight Hadoop cluster.

## Transform and enrich
After data is present in a centralized data store in the cloud, process or transform the collected data by using ADF mapping data flows. Data flows enable data engineers to build and maintain data transformation graphs that execute on Spark without needing to understand Spark clusters or Spark programming.

If you prefer to code transformations by hand, ADF supports external activities for executing your transformations on compute services such as HDInsight Hadoop, Spark, Data Lake Analytics, and Machine Learning.

## CI/CD and publish
Data Factory offers full support for CI/CD of your data pipelines using Azure DevOps and GitHub. This allows you to incrementally develop and deliver your ETL processes before publishing the finished product. After the raw data has been refined into a business-ready consumable form, load the data into Azure Data Warehouse, Azure SQL Database, Azure CosmosDB, or whichever analytics engine your business users can point to from their business intelligence tools.

# Monitor
After you have successfully built and deployed your data integration pipeline, providing business value from refined data, monitor the scheduled activities and pipelines for success and failure rates. Azure Data Factory has built-in support for pipeline monitoring via Azure Monitor, API, PowerShell, Azure Monitor logs, and health panels on the Azure portal.

## Top-level concepts
An Azure subscription might have one or more Azure Data Factory instances (or data factories). Azure Data Factory is composed of below key components.

- Pipelines
- Activities
- Datasets
- Linked services
- Data Flows
- Integration Runtimes

These components work together to provide the platform on which you can compose data-driven workflows with steps to move and transform data.

## Pipeline
A data factory might have one or more pipelines. A pipeline is a logical grouping of activities that performs a unit of work. Together, the activities in a pipeline perform a task. For example, a pipeline can contain a group of activities that ingests data from an Azure blob, and then runs a Hive query on an HDInsight cluster to partition the data.

The benefit of this is that the pipeline allows you to manage the activities as a set instead of managing each one individually. The activities in a pipeline can be chained together to operate sequentially, or they can operate independently in parallel.

## Mapping data flows
Create and manage graphs of data transformation logic that you can use to transform any-sized data. You can build-up a reusable library of data transformation routines and execute those processes in a scaled-out manner from your ADF pipelines. Data Factory will execute your logic on a Spark cluster that spins-up and spins-down when you need it. You won't ever have to manage or maintain clusters.

## Activity
Activities represent a processing step in a pipeline. For example, you might use a copy activity to copy data from one data store to another data store. Similarly, you might use a Hive activity, which runs a Hive query on an Azure HDInsight cluster, to transform or analyze your data. Data Factory supports three types of activities: data movement activities, data transformation activities, and control activities.

## Datasets
Datasets represent data structures within the data stores, which simply point to or reference the data you want to use in your activities as inputs or outputs.

## Linked services

Linked services are much like connection strings, which define the connection information that's needed for Data Factory to connect to external resources. Think of it this way: a linked service defines the connection to the data source, and a dataset represents the structure of the data. For example, an Azure Storage-linked service specifies a connection string to connect to the Azure Storage account. Additionally, an Azure blob dataset specifies the blob container and the folder that contains the data.

Linked services are used for two purposes in Data Factory:

- To represent a data store that includes, but isn't limited to, a SQL Server database, Oracle database, file share, or Azure blob storage account. For a list of supported data stores, see the copy activity article.

- To represent a compute resource that can host the execution of an activity. For example, the HDInsightHive activity runs on an HDInsight Hadoop cluster. For a list of transformation activities and supported compute environments, see the transform data article.

## Triggers
Triggers represent the unit of processing that determines when a pipeline execution needs to be kicked off. There are different types of triggers for different types of events.

## Pipeline runs
A pipeline run is an instance of the pipeline execution. Pipeline runs are typically instantiated by passing the arguments to the parameters that are defined in pipelines. The arguments can be passed manually or within the trigger definition.

## Parameters
Parameters are key-value pairs of read-only configuration.  Parameters are defined in the pipeline. The arguments for the defined parameters are passed during execution from the run context that was created by a trigger or a pipeline that was executed manually. Activities within the pipeline consume the parameter values.

A dataset is a strongly typed parameter and a reusable/referenceable entity. An activity can reference datasets and can consume the properties that are defined in the dataset definition.

A linked service is also a strongly typed parameter that contains the connection information to either a data store or a compute environment. It is also a reusable/referenceable entity.

## Control flow
Control flow is an orchestration of pipeline activities that includes chaining activities in a sequence, branching, defining parameters at the pipeline level, and passing arguments while invoking the pipeline on-demand or from a trigger. It also includes custom-state passing and looping containers, that is, For-each iterators.

## Variables
Variables can be used inside of pipelines to store temporary values and can also be used in conjunction with parameters to enable passing values between pipelines, data flows, and other activities

# Getting Started Cosmos DB Copy Activity


# Copy Activity

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
