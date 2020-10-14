
Data_Dictionary.xlsx is the data dictionary for the NEOCARE database.

Each *.docx file here annotates a portion of the process of setting up the NEOCARE registry. These general steps are as follows:

1. Initial raw EHR data extraction at CCF and MH.

  This is not documented anywhere in any of these files, but the queries employed and other details can be obtained from certain members of the NEOCARE team.


2. Deduplication

  This is the word we used for determining which CCF and MH data correspond to the same individual so that we could link these patients' data across the institutions. 

  **deduplication_ccf_side.docx** and **deduplication_mh_side.docx** can be taken together as explaining this multistage undertaking. They describe the actions taken on CCF's and MH's systems, respectively.


3. CCF-side data management

  **CCF_cohort_creation.docx** describes the cleaning of the raw CCF data and the subsequent creation of tables and views that contain only NEOCARE cohort data dated during 1999-2017. Since all the raw CCF data is on the Teradata database anyway, most of this is handled via SQL queries that manipulate existing tables and views.


4. MH-side data management

  Handling the MH data is more involved since it originated at MH and needed to be transferred to CCF and then uploaded to Teradata. 

  **mh_data_prep.docx** describes the preparation of MH data for transfer to CCF. All MH data were indexed by the arbitrary study_id that was assigned at the end of deduplication (see step 2 above), and all other identifiers were removed prior to transfer, except for basic demographic information that was only in the designated "demographics" files.

  **mh_death_data_prep.docx** describes the preparation of MH death data for transfer to CCF. It is specially treated since it involves a matching protocol on personal identifiers. 

  **MH_cohort_creation.docx** describes secondary manipulation of MH data taking place on the CCF servers after its transfer from MH, followed by the uploading of the data to Teradata. Like CCF_cohort_creation.docx (see step 3 above) it results in tables and views that contain only NEOCARE cohort data during 1999-2017.


5. Harmonization

  This is the word we used for combining corresponding CCF data and MH data into single tables (e.g., combining CCF's medications data and MH's medications data into a single "NEOCARE_COHORT" medications view).

  **NEOCARE_harmonization.docx** describes this process. Since all the source data are on Teradata, most of this is handled via SQL queries that manipulate existing tables and views.