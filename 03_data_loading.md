
## Stages

stages in snowflake are locations used to store data.


we can load data from a stage
we can put data in a stage


internal tages are managed by snowflake

external stages are s3 buckets and azure containers


Connect to SQL loads GZIP 128 or 256 bit compressed file

`put copy into my_table`

Grab Data from internal stage

`COPY INTO GET`


Internal Stage Types 
- User Stage
    - Tied to one user and only accessed by user
    - No access 
    - To avoid storage costs delete after loading
    - Referred to with `'@~'`
    - Every user has defualt stage, can't be altered or dropped

- Table
    - automatically created with a table
    - Only accessed by one table
    - Can't be altered or dropped
    - Load to one table
    - Used with `'@%Table_Name'`

- Internal Names Staged
    - `Create stage`
    - Snowflake database object
    - Everyone with privileges can access
    - Most flexible
    - Referred with `'@STAGE_NAME'`
    - If you have csv files on your local machine


## External Stage

- External Stage
    - Create Stage
    - Snowflake database object
    - Referred with `'@STAGE_NAME'`
    - REferences S3 Bucket


`Create stage my_stage 
    url = s3://bucket/path/`


`create stage url = 'azure://accountblob.core.windows.net/container/path'`    

COPY INTO STAGE
COPY FROM STAGE

SELECT * FROM @STAGE_NAME

`SELECT $1, $2, $3 from STAGE_NAME$`
 

Can store credentials in a strage integration object


## Copy Into Bulk Loading


COPY INTO TABLE_NAME  FROM @STAGE_NAME for bulk loading

Files must be in internal or external stage
    Warehouses are needed
    Data transfer costs may apply

CSV (Default), JSON, AVRO, ORC, PARQUET, XML


Can add files param   `FILES = file_name1,`  
Or even Pattern param `PATTERN = *.sales.*`


`Desc STAGE my_db.my_schema.my_aws_stage` 


Bulk data loading manual

Snowpipe is a superglue pipeline for stages/blob storage. Serverless feature managed by snowflake
    Can set auto ingest to true

event noti: noti interation
Containers queue storage serverless laod


Cost is per second. Loads within 1 minute
File size 100-250mb

Load history retained for 14 days

No duplicate data is loaded within the retention period


## Copy Options 

Skip by Number or by Percentage. bort statement
on  error = continue


snowpipe dfaults to skip value

- On error: specifies error
- size limit: n bytest
- purge: after loading
- return_failed_only: only failed files
- match_column_by_name: for semi-structured data
- enforce length: truncate text strings (default true)
- truncatecolumns: truncate text strings
- force: load files if loaded before
- load_uncertain_files: even if status unknown


## Validation mode

Validate data instead of loading

return_<n>_rows -> return_5_rows