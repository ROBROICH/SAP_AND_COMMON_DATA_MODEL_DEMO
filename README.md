# SAP S/4HANA and Microsoft Common Data Model integration.
This demo describes the basic integration between S/4HANA and the Microsoft Common Data Model (CDM)


## From SAP S/4HANA Core Data Services (CDS) to the Common Data Model (CDM) on Azure Data Lake Gen2 
When utilizing SAP S/4HANA or SAP ECC as data-source for Data-Lake implementations, the complexity of the relational SAP data-model and corresponding SAP tables is a well-known challenge. 
For data extraction based on SAP ABAP tables, deep SAP domain expertise is required to design specfic data-models which fullfill the requirements of AI/ML or genral analytical scenarios. 

Please find an example for a SAP tables without metadata description here: [BSEG](https://www.se80.co.uk/saptables/b/bseg/bseg.htm)

Frequently in Azure Big Data analytics scenarios these SAP specific data models play in important role in the overall analytical data-model, therefore this demo provides an efficient method the convert SAP S/4HANA metadata models to CDM models. 

ADL Gen2 supports the Common Data Model(CDM) which enables consistent sharing of metadata between multiple data consumers and producers like PowerBI or Azure Databricks or Azure Data-Factory. Semantic and structural consistency of metadata, in context of Data-Lakes projects, is one of the key aspects to successfully implement new innovative use-cases. [Source](https://docs.microsoft.com/en-us/common-data-model/data-lake)

Like the SAP S/4HANA Core Data Services(CDS) views or SAP BW/4HANA business content, the Microsoft Common Data Model (CDM) provides semantically rich descriptions about datasets stored in the Azure Data Lake.

## Introduction demo scenario and architecture 

The concept of this tutorial and prototype is to transform SAP S/4HANA specific metadata and semantics into the CDM-format including the data export.  
In practice this approach could be used for rapid prototyping using SAP S/4HANA as data-source. Productive usage beyond prototyping is currently not recommended. 

The conversion and data-movement will be implemented using Power BI Premium Data-Flows connected to an Azure Data Lake Gen2.
In S/4HANA analytical data models are described with CDS-view, based on SAP HANA tables, and provide option the option to export SAP-data leveraging open interfaces like OData. 

This series of blogs from Simon Kranig are an excellent introduction to CDS based data extraction: [Link](https://blogs.sap.com/2019/12/13/cds-based-data-extraction-part-i-overview/)

In addition to Simons Blog I wrote a short introduction how to enable OData based extraction using CDS view:
[Link](https://github.com/ROBROICH/SAP_ODP_ODATA_CLIENT)

In this scenairo the S/4HANA CDS view for extracting the cash flow was selected. This CDS view joins multiple tables to provide the cash-flow for data extraction:
![Cash-Flow](/blob/master/CDS_VIEW_CASHFLOW.png)






















This demo is a basic extension of an existing Azure IoT tutorial to demonstrate SAP connectivity leveraging a public SAP Gateway demo system. 

The intention is to have a repeatable and public SAP and Azure IoT demo based on:

* Azure Raspberry emulator

* Azure IoT Hub and Logic App

* Public SAP demo system 

![Demo high level overview](https://github.com/ROBROICH/REPO1/blob/master/images/DEMO_ARCHITECTURE.jpg)

# Demo scenario and basic story line 

* Imagine the Raspberry Emulator as IoT device used in shipping of heat-sensitive vaccines

* If the temperature is measured above 30°, the vaccine is damaged and must be replaced  

* To replace the vaccine, a sales order is automatically created in SAP ECC in case the measured temperature is above 30° 

* For excel users the current sales order SAP ECC will be displayed in Excel 

# Demo implementation

The following steps are required to implement the demo:

* Raspberry PI emulator
* Notifications with Azure Logic Apps
* Get access to public SAP system
* Adjust Logic-App
* Show sales order in Excel or Power BI

![Demo flow](https://github.com/ROBROICH/REPO1/blob/master/images/DEMO_FLOW.jpg)


