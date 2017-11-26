---
layout: default
title: NPS Setup/Management
---
<div id="npssetup1"></div>
## NPS Setup/Management

<ol> 
  <li><h3>Adding NPS</h3></li> 
<b>Principles</b>
  <ul>
      <li>SMF does not store root/nz passwords anywhere. Root password is used only during setup.</li>
      <li>SMF creates users (shell and database) on every IBM Pure Data for Analytics (Netezza) appliance that it is connected to. </li>
      <li>Shell users do not have permissions to modify data in /nz directory. </li>
      <li>Shell users have mount/umount options granted. </li>
     <li>Smartadm database user has all administrative privileges. </li>
</ul>
<br>
NOTE: This option can be manually revoked by editing /etc/sudoers. SMF does not have the option to read /etc/sudoers and as such    presence of this entry is not validated but is assumed present. During backup/restore option if RO (ready-Only) mode selection is set scripts will show errors and warning messages will appear in system logs.
<br>
<br>
<b>To add NPS:</b>
<br>
<br>
<b>Menu Item 7 (NPS setup) -> Menu Item 3 (Add NPS)</b>
<br>
<br>
  The script asks for following details:
  <ul>
    <li>IP/FQDN – IP / FQDN of IBM PureData for Analytics Appliance  </li>
     <li>root password for currently active host </li>
     <li>Machine alias – it will be displayed for future reference (can be modified afterwards)</li>
     MIGR ID confirmation – if only one SMF host is present in data center confirm by enterting ‘y’
 </ul> 
 <br>NOTE: In case DR functionality is desired SMF provides feature to synchronize data between SMF nodes. As such preferable option is to have one SMF per data centre / shared storage group(s). 
 <br>In case SMF DR data Synchronization will be used – set up sufficient masters for each NPS
 <div id="npssetup2"></div>
 <li><h3>Reloading NPS MetaData</h3></li>
<b>Principles</b>
  <ul>
<li>SMF stores all metadata in its internal database.</li>
  <li>Each object type has its own unique object type id across all available Netezza appliances. </li>
  <li>Each SMF function reloads its requisite metadata on the respective NPS appliance.  </li>
  <li>Each function reloads scripts one NPS at a time (except columns metadata reload). The input attribute is internal appliance ID (further referenced as NPSID)</li>
  </ul>
  <br> NOTE: Each script reloads its requisite metadata before running. Metadata reload options do not need to be invoked manually. However, in the event that it is necessary to reload metadata manually:
<br>
<br><b>Menu Item 6 (NPS Setup) -> Menu Item 2 (Reload NPS Metadata)</b>
<br>
<p align="center">
<img style="float: center;" src="/manual/images/edit_nps_menu.jpg">
</p>
<br>




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
