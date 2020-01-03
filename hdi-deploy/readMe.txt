***Consider this as v4 of the DB POC***

This app has created the HDI Container with 3 table (DnB.DUNS_TABLE, DnB.SIC_TABLE, DnB.SIC_DESC), 1 view (SICView) and has records inserted via a csv file:

HANA Service instance: 	data_cloud_hdi_shared_v4 (hdi-shared plan)

HDI Container App: 	data_cloud_hdi_container_v4



DB Artifacts:
-----------------------------------------------------------------------------------------------------

- Namespace: 		com.sap.datacloud.view
- View: 		SICView

	Columns:	ID_NUMBER	String(9)
			SIC1		String(8)
			DESC1		String(50)
			SIC2		String(8)
			DESC2		String(50)
			SIC3		String(8)
			DESC3		String(50)	 
			SIC4		String(8)
			DESC4		String(50)	 
			SIC5		String(8)
			DESC5		String(50)	 
			SIC6		String(8)
			DESC6		String(50)

-----------------------------------------------------------------------------------------------------

- Namespace: 		com.sap.datacloud.data
- Table: 		DnB.DUNS_TABLE


	Columns:	ID_TYPE 	String(5)
			ID_NUMBER	String(9)   //Key
			BUSINESS_NAME	String(120) //Fuzzy index on
			CEO		String(30)
			STREET_ADR_1	String(64)
			STREET_ADR_2	String(64)
			CITY		String(50)
			STATE		String(50)
			POSTAL_CODE	String(16)
			COUNTRY_NAME	String(50)
			COUNTRY_CODE	String(3) ------------------------------------------------------------------------------------------------------

- Namespace: 		com.sap.datacloud.data
- Table: 		DnB.SIC_TABLE


	Columns:	ID_NUMBER	String(9)   //Key  //Association to DnB.DUNS_TABLE.ID_NUMBER
			SIC1		String(8)	   //Association to DnB.SIC_DESC.SIC
			SIC2		String(8)          //Association to DnB.SIC_DESC.SIC
			SIC3		String(8)	   //Association to DnB.SIC_DESC.SIC
			SIC4		String(8)	   //Association to DnB.SIC_DESC.SIC
			SIC5		String(8)	   //Association to DnB.SIC_DESC.SIC
			SIC6		String(8)	   //Association to DnB.SIC_DESC.SIC
------------------------------------------------------------------------------------------------------

- Namespace: 		com.sap.datacloud.data
- Table: 		DnB.SIC_DESC


	Columns:	SIC		String(8)   //Key
			SIC_DESC	String(50)

