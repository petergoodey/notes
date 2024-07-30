# Azure Data Factory

## Tool for ETL/ELT (among other things)

Key components

* Pipelines
* Activities
* Datasets
* Linked Services
* Data Flows
* Integration Runtimes
* Triggers

## [Pipelines and Activities](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities?tabs=data-factory)

[Documentation](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities?tabs=data-factory)

A **pipeline** is a logical grouping of **activities**.

A Data Factory may have:

* One or more **pipelines** each consisting of a logical grouping of **activities** that perform a unit of work/task

### Activity Types

**Activities** are processing steps.

#### [Data Movement Activities](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities?tabs=data-factory#data-movement-activities)

Copying data from source to sink - see link above on what can be used as a source and as a sink under which integration runtimes.

#### [Data Transformation Activities](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities?tabs=data-factory#data-transformation-activities)

#### [Control Flow Activities](https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities?tabs=data-factory#control-flow-activities)

* Move and Transform
  * Copy Data
  * Data Flow
    * [Supported Connectors](https://learn.microsoft.com/en-us/fabric/data-factory/connector-overview#supported-data-connectors-in-dataflows)

* Datasets
  * Data structures within datastores
  * Reference the data used in activities as inputs or outputs
  * Can be Azure blob dataset - folder with data
* Linked Services
  * Defines the target data store or compute service
  * Think of like connections strings to the data source (Azure Storage Account)

### Integration Runtime

* Provides the compute environment between the activity and the linked service
* Should be in a region closest to the data store
* Security and compliance should be considered
* One can be auto-created but you might it's recommended to create your own optimized one

#### Types of Integration Runtimes

* Azure Integration Runtime
  * Managed elastically by Azure
  * Default cna be auto generated
* Self Hosted Integration Runtime
  * Can run copy activities between a cloud data store and a data store in a private network
* Azure SQL Server Integration Services (SSIS)
  * A fully managed cluster of Azure VMS or Nodes dedicated to running SSIS packages

#### Why create your ow IR:

    * Default region is unspecified
    * Specify region explicitly - e.g. for compliance
    * Better granularity over data flow runtime (memory, cores TTL etc.)
    * Cost reduction
    * You can self host anode for debugging in development

### Triggers

* Start the pipeline execution
* Can be:
  * Scheduled
  * Tumbling Window - fires periodically while retaining state
  * Storage Events

#### Data Transformation

#### Control Activities

## Walkthrough

* Create Storage Account to store incoming file
  * Subscription
  * Resource Group
  * Networking
  * Redundancy
  * Data Protections
  * Encryption
  * Forthis example we'll use Azure Blob Storage
* Within Storage Account create
  * Source - data to transform
  * Sink - transformed data
* Create Data Flow or Copy Data
  * You will need to create a Source Dataset
    * Set format as delimited text for example
    * Create new linked service as Azure Blob Storage
      * Specify Integration Runtime - can auto resolve
      * Set authentication method:
        * Set as Account Key from Azure Subscription
        * Use storage account name
        * Now you should be able to test the connection
        * Set file path in properties