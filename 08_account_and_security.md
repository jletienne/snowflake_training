



Access Control

DAC
    Each Object has an owner
    owner grants access to objects

RBAC
    Role-based access control (RBAC)
    Priviliges -> roles -> users



Securable object
    Object can be granted
    access denied unless granted

Privilege
    defined level of access

Role
    entity to which priviligess are granted
    assigned to users

User
    Identity associated with person or program

grant privilege on object to role



Org Admin - account usage

Account Admin - limited number of users
    manage all objects in accounts
    include share and reader accounts
    modify account level params
    manage resource and billing

Security Admin
    manage any object grant globally
    manager grants and users
    inherits user admin privileges
Sys Admin
    all custom roles should be assigned
    grant privileges on warehouses, databases, and other objects
    cusstom roles should be assigned to sysadmin

user Admin
    create user & create role privileges
    can manage users and roles that are owned


Public
    granted to all users
    when no access controls are needed



Priviliges
    grant privilige on object to role
    revoke privilige on object from role

Global privilieges
    Create share
    import share
    apply masking policy


Virtual warehouses privileges
    modify
    monitor
    operate
    usage
    ownership
    all

Databases
    modify
    monitor
    usage
    reference

Stages
    read
    usage
    right
    all
    ownership


Tables
    select
    insert
    updated
    trunate
    delt
    all
    ownership



SCIM Support

min 2048 bit rsa

alter user to change the key

`alter table my_table modify column my_column set masking policy my_policy`

Column Level Security
    Not in Stadard but starting in enterprise


Dynmamic Data Masking

External tokenization
    analytic value preserved
    sensitive info protekted

    tokenized pre-load and detokenized at query runtime

Row Level Security / Row access policies
    Not in standard

Schema level object

### Network policies all editions

rekeying is enabled, key rotates every year
    Enterprisee edition

All data at all time is always encrypted. at rest and in transit. this is default for all editions


256 bit encryption (AES). key rotation every 30 days. TLS 1.2 (transport level)

Tri Secret Secure for business critial

### Account Usage and Information Schema

Account Usage Schema
    In snowflake database
    Shared database default available to all accounts
    Admin can see in this schema
    Not real time 45min to 3 hours
    available only to admin
    Includes dropped objects


    Query Object Metadata
        View copy history
        view columns
    Query Historical Usage Data

Reader Account Usage
    Limited to reader accounts

Information Schema
    Available in all databses
    Between 7 days and 6 months
    Real time
    No dropped objects


### Release Process

Weekly release schedule

Seamless with no downtime
    Full Release
    Patch Release

Full release new features, enhancements, updates,

Patch release bug fixes


Behaviour changes, monthly

Enterprise has access to early access by request only

Standard has regurla access on day or way day two





;
