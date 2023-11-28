

## Unstructured Data

Can be 
- Video
- Audio
- Doucuments


Supports
- Access through URL in cloud storage
- Share file access URLs


Image Stage URLs
- Scoped URL (24 hour scoped)
    - encoded snowflake hosted URL with temp access to the file 
    - Expires when persisted query result period ends(24 hours)
    - `BUILD_SCOPED_URL(@stage_azure, 'Logo.png')`
- File URL (Dropbox file URL)
    - Prolonged like a dropbox file no expiration
    - `BUILD_STAGE_FILE_URL(@stage_azure, 'Logo.png')`
- Pre-signed URL
    - HTTPS:// URL accessed from browser
    - I think it's like download
    - Configurable access time
    - `GET_PRESIGNED_URL(@stage_azure, 'Logo.png', 60)`
    
## Directory Tables

Storing metadata of our staged files
- Layered on a stage
- Set properties (priviliges) on the stage to query from this table
- Retrieve file URLs to access files
- Need to refresh metadata
    - `alter stage stage_azure refresh`
    - or with event notifications


`CREATE STAGE stage_azure url = <'url'>`
`ALTER stage_azure set directory = (ENABLE = TRUE)`


why tf is this backwords?
`select * from directory(@stage_name)`

## Data Sampling

- Row / Bernoulli (Percent) Andre Ropercent
    - Each row is 10% (accurate sample, small table)
    - `SELECT * FROM TABLE SAMPLE ROW 10 Seed(15) --means ten percent` 
- Block / System
    - Block of 10% (fast sample, large table)
    - `SELECT * FROM TABLE SAMPLE SYSTEM 10 Seed(15) --means ten percent` 



## Tasks

- Basically a cron job
    - Schema level object
    - cloned with database
- ` CREATE TASK my_task warehouse = my_wh schedule = '15 minute' as
     INSERT INTO my_table(time_col) values(CURRENT_TIMESTAMP)`
- Run using privileges of task owner
- Execute managed task account
- Create task schema
- Usage on schema and database
    - will use snowflake managed compute unless we specify the warehouse property


Starting a task
- `Alter task my_task resume;`
- `Alter task my_task suspend`

- Directed Acylic Graph
    - Limit: 1000 tasks in total
    - LImit: One single task is limited to 100 child tasks

## Stream
- Record data manipulation, langauge changes
- Streames record inserts, updates, and deletes
- Schema level object


`Create stream my_stream on table my_table`

`select * from my_stream`

Stream types
- Standard (insert, update, delete)
- Append-Only (Insert, better performance)
    - Not for external tables
    - For standard tables, directory tables, views and secure view
- Insert only stream
    - Only for external tables

Staleness
- Stream is stale when offset is outside data retention period of sourrce table
    - unconsumed change records won't be accessible

Delta load, track additional changes

Metadata
- Action
- ISUpdate
- Row Id

- Stale_After

Stream extends retntion to 14 days default (all snowflake editions, even standard)
    - 90 days with entteriprise using max_data_extension_time_in_days

`SYSTEM$STREAM_HAS_DATA('MY_STREAM)`


hmmmmm.....
Query from the stream to insert the values that are recorded