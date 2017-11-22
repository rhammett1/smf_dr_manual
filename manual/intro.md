---
layout: default
---
**Smart Management Framework (SMF)** has been specifically designed to automate processes that improve the performance, availability, recoverability, and security of one or more of IBM®’s Pure Data™ for Analytics (aka Netezza) appliances.
It does this by providing parameterised and dynamically maintained metadata driven templates for the rapid implementation of best practise functionality in the following areas:
* Database backup and replication management
* LDAP/Active Directory user authentication and permission synchronisation
* Query and workload management optimisation
* Row secure tables and column secure views
* Housekeeping/system maintenance
* Change management and version control
* Configurable scheduling and auditable logging of all the above activities

## Backup/Replication Features
* Works with any kind of storage media (including NFS, Spectrum Scale, SAN/NAS, etc.)
* Bi-directional, multi-master in nature (from anywhere to anywhere, including multiple targets replicated from the same backup source, or the restoration target being on the same physical appliance as the backup source itself)
* Backup/restore increments can be as frequent as you like (from minutes to days). Multiple different concurrent
* backup sets supported per appliance Can backup/restore subsets of tables within a database (and even subsets of rows within a table)
* Ideal for Disaster Recovery, as well as Development/Test database population using sampled referentially intact subsets of production data

## LDAP Synchronisation Features 
* Dynamic creation/dropping of database users and groups based on synchronised LDAP master data
* Automatic addition/removal of users to/from groups, as well as granting/revoking of permissions to/from groups

## Performance Tuning Features 
* Automatically and regularly identifies relatively poorly performing query workloads based on configurable settings
such as query frequency, queue time, latency, and throughput
* Extracts and parses execution plans of problem queries to  identify underlying causes of poor performance
* Provides recommendations on how to resolve performance issues
* Dynamically generates code to implement accepted recommendations
* Monitors and quantifies the cumulative benefit of implemented recommendations

## Advanced Security Features
* Provides a column-level access control security model for both users and groups
* Dynamically creates views that automatically either reveal or obscure secure column values when queried, depending on the user performing the query, the permission groups they belong to, and the contents of the column-level access control security model
* Automatically rebuilds or drops views when the underlying base table’s schema changes or is dropped
* Automatically re-synchronises column-level user/group permissions with LDAP master
* Assists with the management and application of security levels, categories, and cohort security labels
* Dynamically builds row secure tables, and applies security labels to their contents, based on parameter settings and
configurable matching rules

## Housekeeping Features
* Dynamically generates, schedules, executes, and logs a variety of system management tasks essential for consistently optimal query performance
* GROOMS versions of altered tables, as well as changed/deleted rows in the most performant way. Automatically detects when RECORDS ALL is needed e.g. as a result of a changed ORGANIZE ON setting
* Generates statistics for only the tables whose contents have changed since the last time it was run
* Disconnects idle sessions outside of permitted hours of service and performs online vacuums against the system catalog host database. Can optionally schedule a service window for periodic ‘manual’ vacuums also.
