# SAP S/4HANA and Microsoft Common Data Model integration.
This demo describes the basic integration between S/4HANA and the Microsoft Common Data Model (Model)


# From SAP S/4HANA Core Data Services (CDS) to the Common Data Model (CDM) on Azure Data Lake Gen2 
When utilizing SAP S/4HANA or SAP ECC as data-source for Data-Lake implementations, the complexity of the relational SAP data-model and corresponding SAP tables is a well-known challenge. 
For data extraction based on SAP ABAP tables, deep SAP domain expertise is required to design data-models which fullfill the requirements of AI/ML or general analytical requirements. 

Please find an example for a SAP tables without metadata description here: ![BSEG](https://www.se80.co.uk/saptables/b/bseg/bseg.htm)

Frequently in Azure Big Data analytics scenarios these SAP specific data models play in important role in the overall analytical data-model, therefore this demo provides an efficient method the convert SAP S/4HANA metadata models to CDM models. 

Like the SAP S/4HANA Core Data Services(CDS) views or SAP BW/4HANA business content, the Microsoft Common Data Model (CDM) provides semantically rich descriptions about datasets stored in the Azure Data Lake.

The Azure Data Lake Gen2(ADL Gen2) is the preferred Azure solution to design massive scalable data lake solutions that are tightly integrated into the Azure Big Data Analytics stack. (Source https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction)

One unique feature of the ADL Gen2 is the support Common Data Model(CDM) which enables consistent sharing of metadata between multiple data consumers and producers like PowerBI or Azure Databricks or Azure Data-Factory. Semantic and structural consistency of metadata, in context of Data-Lakes projects, is one of the key aspects to successfully implement new innovative use-cases.  (Source. https://docs.microsoft.com/en-us/common-data-model/data-lake).

The concept of this tutorial and prototype is to transform SAP S/4HANA specific metadata and semantics into the CDM-format. 
In practice this approach could be used for rapid prototyping using SAP S/4HANA as data-source. Productive usage beyond prototyping is not recommended. 






The conversion and data-movement will be implemented using Power BI Premium Data-Flows connected to an Azure Data Lake Gen2.
In S/4HANA analytical data models are described with CDS-view, based on SAP HANA tables, and provide option the option to export SAP-data leveraging open interfaces like OData. 
This series of blogs from Simon Kranig are an excellent introduction to CDS based data extraction
https://blogs.sap.com/2019/12/13/cds-based-data-extraction-part-i-overview/
In addition to Simons Blog I wrote a short introduction how to enable OData based extraction using CDS view.  




Currently multiple Microsoft and SAP partners build innovative analytics solution by combining SAP data with technologies like IoT or ML/AI by utilizing Azure-based cloud-analytics technologies. 
The Azure Data Lake Gen2(ADL Gen2) is the preferred solution for many partners to design massive scalable data lake solutions that are tightly integrated into the Azure Big Data Analytics stack. (Source https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction)
One unique feature of the ADL Gen2 is the Common Data Model(CDM) which enables consistent sharing of metadata between multiple data consumers and producers like PowerBI or Azure Databricks or Azure Data-Factory. Semantic and structural consistency of metadata, in context of Data-Lakes projects, is one of the key aspects to successfully implement new innovative use-cases.  (Source. https://docs.microsoft.com/en-us/common-data-model/data-lake).
Like SAP S/4HANA CDS views or SAP BW/4 business content, the Microsoft Common Data Model (CDM) provides semantically rich descriptions about datasets stored in the Azure Data Lake.
These descriptions include standard definitions of objects like customers, sales opportunities or addresses. Next to standard entities, complete industry data models are defined by the CDM.
Semantics and metadata enable data-engineers and data-scientist to consume and combine various data-sources without the necessity to be a domain or data model expert for the multiple data-sources. 
When utilizing SAP S/4HANA or SAP ECC as data-source, the complexity of the SAP data-model and corresponding SAP tables is a well-known challenge. When ETL tools connect against SAP ABAP tables, deep SAP domain expertise is required to design meaningful data-models from typical German abbreviations. Modelling the relationship between hundreds and thousands of tables makes this task even more challenging. Please find an example for a SAP tables without metadata description here. 
https://www.se80.co.uk/saptables/b/bseg/bseg.htm
In many Azure Big Data analytics scenarios these SAP specific data models play in important role in the overall analytics application, therefore tutorial provides an efficient method the convert SAP S/4HANA metadata models to CDM models. 
















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


