Zero-Copy Cloniong


Only external stage pipes can be cloned

Name internal stages cannot be cloned

historical records reference normal.
incremental records reference micro-partitions


databases dont inherit privileges


only child objects inherit privileges

- select: table
- owner: pipe stream task
- usage: all other

metadata is not copied

can copy time travel



Data sharing. Let customer use their own compute resources

idk use a secure view. also something something reader accounts


Best practice to share a secure view with the columns you need. then grant select


create a managed account

- show grants on order shard
- show managed acounts
- share_restrictions=False
- show shares


need to be accountadmin to see shares

consuming
`create database data_share_db from share source.orders_share`


enable source and target


1 database can be included in a share

`SYSTEM$GLOBAL_ACCOUNT_SET_PARAMETER` function to set the ENABLE_ACCOUNT_DATABASE_REPLICATION parameter to true.

Named Internal Stages and pipes that are not referencing external stages cannot be cloned.


Ownership is needed to clone a task

;
