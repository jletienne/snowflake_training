## Time Travel

--59.

Good job!
Snowflake has implemented BEFORE | AT extensions to SQL that allows to query historic data based on
TIMESTAMP, OFFSET (time difference), STATEMENT (query id).

Time Travel allos to restore dropped tables, schemas, and databases

Account level min
MIN_DATA_RETENTION_TIME_IN_DAYS

Time Travel Default is one Day
- Standard - 1 Day
- Enterprise - 90 Days
- Business Critical - 90 Days
- Virtual Private - 90 Days


Fail Safe 7
- Days
- Non-Configurable
- Restoration only by Snowflake


Snowflake.account_usage.storage_usage
Snowflake.account_usage.table_storage_metrics






permanent tables
- time travel 0-90 days
- Non configurable 7-day Fail Safe

transient tables
- time travel 0-1 days
- no fail safe
- kept until droped

Cant save transient tables

Temporary Tables
- time travel 0-1 days
- no fail safe
- available until session end


If database is transient, all objects are transient


Table types are immutable




























;
