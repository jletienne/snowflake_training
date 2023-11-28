
Query Profile


Graphical representation we can use to get additional execution details


Locations
    Query History in our Activity (Snowsite)
    Query history table function in information schema
        how much data spilling has occurred
        number of bytes scanned
    Query History View Account Usage Schema


### Caching

Result Cache
    In service layer (no compute resources)
    only if data has not changed
    no UDFs, external functions, or context functions
    24 hours (reset up to 30 days if warrehouse is up)

Data Cache
    Local SSD stoarage that is directly connected

Remote Disk (not a cache)

Metadata cache 
    which just contains some statisticts for tables, columns and micro partitions.


Virtual Private Edition, has metadata store that is not share with any other customers


Query result reuse


ALTER SESSSION SET USE_CACHED_RESULT = FALSE


Micro Partition
    50-500MB compressed

Compressed at the micro partition levle

Standard feature can't be disabled

Micro partisions are impmutable


## Clustering


SYSTEM$CLUSTERING_INFORMATION

SYSTEM$CLUSTERING_DEPTH

## Search Optimization
- Starts in standard

## Search Optimization in Business Critical Mode


Search Optimzation is best for selective point