NPS Setup/Management
Adding NPS
Concept
SMF is not storing root/nz passwords anywhere. Root password is being used only during setup.
SMF is creating smartadm users (shell and database) on every IBM Pure Data for Analytics appliance for which it is connected to. 
Shell user doesn’t have permissions to modify data in /nz directory. 
Shell user have mount/umount options granted. 
NOTE: This option can be manually revoked (by editing /etc/sudoers) . Please note that SMF doesn’t have option to read /etc/sudoers and as such presence of this entry is not validated and being treated as present. During backup/restore option if RO (ready-Only) mode selection will be set – scripts will show errors and warning messages will appear in system logs
Smartadm database user have all administrative privileges. 
Commands
UI 
Through UI (automatically opened when logged in as smartadm user): 7 (NPS management) -> NPS setup

Script ask for following details:
IP/FQDN – IP / FQDN of IBM PureData for Analytics Appliance 
root password for currently active host 
Machine alias – it will be displayed for future reference (can be modified afterwards)
MIGR ID confirmation – if only one SMF host is present in data center confirm by enterting ‘y’
NOTE: In case DR functionality is desired SMF provide feature to synchronize data between SMF nodes. As such – preferable option is to have one SMF per data center / shared storage group(s). 
In case SMF DR data Synchronization will be used – set up sufficient master for each NPS
SMF Shell 
Command line option is using same syntax as UI. To launch NPS setup:
/opt/SmartMF/scripts/inits/setupnps.sh

Updating NPS
Concept
SMF stores all metadata in internal database. Each object type have own – unique object type id across all available IBM PureData for Analytics appliances. Each SMF functionality reload Metadata on all affected appliances per functionality requirements. Each functionality reloads one appliance at a time for all scripts (except columns metadata reload) input attribute is internal appliance ID (further referenced as NPSID)
NOTE: Each script reloads required metadata before it’s run. Metadata reload options doesn’t need to be invoked manually.
General system information (schema support, NPS release, authentication)
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 1
SMF Shell
/opt/SmartMF/scripts/machines/update_dbo_nzrev.sh NPSID
SMF Table
machines_history
Update IP
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 2 -> enter new IP
SMF Shell
/opt/SmartMF/scripts/machines/update_IP.sh NPSID
SMF Table
machines_history

Time zone
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 3
SMF Shell
/opt/SmartMF/scripts/machines/update_tzoffset.sh NPSID
SMF Table
machines_history


Databases 
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 4
SMF Shell
/opt/SmartMF/scripts/databases/update_nps_datadabases.sh NPSID
SMF Table
databases – all databases information
active_databases – general information about active databases

Schemas
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 5
SMF Shell
/opt/SmartMF/scripts/databases/load_dbs_schemas.sh NPSID
SMF Table
dbschema

Tables
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 6
SMF Shell
/opt/SmartMF/scripts/databases/load_dbs_tables.sh NPSID
SMF Table
Dbtables

Columns
Columns metadata reload differs from all other functionalities as to extract this information metadata needs to be pulled directly from IBM PureData for analytics database. 
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 7 -> Select DB ID or type ALL/all (for all DBs rescan)
SMF Shell
/opt/SmartMF/scripts/databases/load_dbs_columns.sh DBID
SMF Table
dbcolumns – contains all information about all columns (includes all NPS specific metadata) in reloaded databases

Users
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 8

SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_users.sh NPSID
SMF Table
Users

Groups
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 9
SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_groups.sh NPSID
SMF Table
usergroups

Users/Groups allocation
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 10
SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_usersgroups.sh NPSID
SMF Table
Useringroups

All user/group/allocation informations
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 11
SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_usersgroups.sh NPSID
SMF Table
useringroups

Non-admin permissions
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 12
SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_permissions.sh NPSID
SMF Table
permission_non_admin
Admin permissions
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 13
SMF Shell
/opt/SmartMF/scripts/LDAP/load_db_permissions_admin.sh NPSID
SMF Table
permission_admin
Storage
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 14
SMF Shell
/opt/SmartMF/scripts/storage/reload_nps_storage.sh NPSID
SMF Table
storage
Update Backup host name
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 15
SMF Shell
/opt/SmartMF/scripts/machines/update_backuphostname.sh NPSID
SMF Table
machines_history

Reload all data (except columns)
UI
Main UI: 6 -> NPS UI: 2 -> Select NPSID -> Option: 16

Reload data after SMF restart
SMF appliance is providing DR (disaster-recover) / replication software components without any need to assign dedictaed storage only to SMF . Customer can use any storage type which is currently supported and connected to IBM Pure Data for Analytics (NFS, SAN, GPFS) for backup purposes – and SMF can use it as replication source. 
To keep data in sync, increase replication stability and decrease storage utilisation– SMF is creating own storage layout and mount it accordingly to sync data – to save resources on infrastructure storage is not being verified automatically (this will be adjustable). 
In case of any reboot, after restart of SMF  to safely resume DR operations – following needs to be invoked:
UI
Main UI: 6 -> NPS UI: 4
SMF Shell
/opt/SmartMF/scripts/inits/on_start_sync.sh

Clearing temporary data
SMF is using temp space to analyse IBM Pure Data for Analytics PPLIANCE objects. In case script were interrupted temporary data might not be cleared and block metadata reload operations. This can be safely cleared if no other operation is running at the time. 
NOTE: In case any operation is running – at the time and you clear up temporary space – metadata might be will be invalidated. 
UI
Main UI: 6 -> NPS UI: 5