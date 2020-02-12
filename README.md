# Conversion of SAP S/4HANA Core Data Services to the Microsoft Common Data Model.
This demo describes the basic integration between S/4HANA semantics and the Microsoft Common Data Model (CDM)


## From SAP S/4HANA Core Data Services (CDS) to the Common Data Model (CDM) on Azure Data Lake Gen2 (ADL Gen2) 
When utilizing SAP S/4HANA or SAP ECC as data-source for Data-Lake implementations, the complexity of the relational SAP data-model and corresponding SAP tables is a well-known challenge. 
For data extraction based on SAP ABAP tables, deep SAP domain expertise is required to design specfic data-models which fullfill the requirements of AI/ML or genral analytical scenarios. 

Please find an example for a SAP tables without metadata description here: [BSEG](https://www.se80.co.uk/saptables/b/bseg/bseg.htm)

Frequently in Azure Big Data analytics scenarios these SAP specific data models and semantics play in important role in the overall analytical data-model, therefore this demo provides an efficient method the convert SAP S/4HANA semantics to CDM models. 

ADL Gen2 supports the Common Data Model(CDM) which enables consistent sharing of metadata between multiple data consumers and producers like PowerBI or Azure Databricks or Azure Data-Factory. Semantic and structural consistency of metadata, in context of Data-Lakes projects, is one of the key aspects to successfully implement new innovative use-cases. [Source](https://docs.microsoft.com/en-us/common-data-model/data-lake)

Like the SAP S/4HANA Core Data Services(CDS) views or SAP BW/4HANA business content, the Microsoft Common Data Model (CDM) provides semantically rich descriptions about datasets stored in the Azure Data Lake.

## Introduction demo scenario and architecture 

The concept of this tutorial and prototype is to transform SAP S/4HANA specific metadata and semantics into the CDM-format including the data export.  
In practice this approach could be used for rapid prototyping using SAP S/4HANA as data-source. Productive usage beyond prototyping is currently not yet recommended. 

The conversion and data-movement will be implemented using Power BI Premium Dataflows connected to an Azure Data Lake Gen2.
In S/4HANA analytical data models are described with CDS-view, based on SAP HANA tables, and provide option the option to export SAP-data leveraging open interfaces like OData. 

![Architecture](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/SCENARIO_ARCHITECTURE.png)

This series of blogs from Simon Kranig are an excellent introduction to CDS based data extraction: [Link](https://blogs.sap.com/2019/12/13/cds-based-data-extraction-part-i-overview/)

In addition to Simons Blog there is an introduction how to enable OData based extraction using CDS view:
[Link](https://github.com/ROBROICH/SAP_ODP_ODATA_CLIENT)

In this scenario the S/4HANA CDS view for extracting the cash flow was selected. This CDS view joins multiple tables or CDS-view to provide the S4/HANA cash-flow for data extraction:
![Cash-Flow](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/CDS_VIEW_CASHFLOW.png)



## Prerequisites 
To implement this prototype, the following prerequisites must be implemented:
*An ABAP based CDS view must be exposed as ODP OData service
  *	The prerequisite for exposing CDS views as ODP is the CDS-tag data-extraction = true. 
   ![ExtractionTrue](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/CDS_EXTRACTION_TRUE.png)
  
 * The only required modification is to expose the CDS-view as OData service. Further details how this can be achieved and a description how to implement the CDC / delta-logic can be found here: [Link](https://github.com/ROBROICH/SAP_ODP_ODATA_CLIENT)

*	The PBI On-Premise Gateway was used to connect the OData service with the PBI Dataflow. The installation guide can be found here:[Link](https://docs.microsoft.com/en-us/power-bi/service-gateway-onprem)




## Connecting the PBI dataflow to S/4HANA
In this  example a S/4HANA system running on Azure was used to implement the prototype.
To establish the connectivity between the S/4HANA system and the PBI dataflow the installation of the on prem data gateway is required. 

After the successful installation of the data gateway, following steps are required to consume the OData service usinh PBI DataFlow:

#### 1. Create a new PBI DataFlow 

Introduction for creating PBI Dataflows: [Link](https://docs.microsoft.com/en-us/power-bi/service-dataflows-create-use)

![PBIDATAFLOW](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_CREATE_DATA_FLOW.png)

#### 2. Select "Define new entities"

![PBISCREATENEWENTITY](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_CREATE_DATA_NEW_ENTITY.png)

#### 3. Select OData as data source 

![PBISCREATENEWENTITY](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_SELECT_ODATA.png)

#### 4. Enter the URL of the S/4 ODP-OData service and select the On-Premise data gateway

![PBIMAINTAINODATA](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_MAINTAIN_ODATA.png)

#### 5. Select the full load URL

![PBIODATAPREVIEWSERVIVCE](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_ODATA_PREVIEWS_SERVICE.png)

#### 6. If required, apply transformations in PBI Power Query


#### 7. Select the full load URL

![PBIODATAPREVIEWSERVIVCE](https://github.com/ROBROICH/SAP_AND_COMMON_DATA_MODEL_DEMO/blob/master/PBI_ODATA_PREVIEWS_SERVICE.png)























