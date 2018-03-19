---
layout: default
title: NPS Setup/Management
---
<div id="npssetup1"></div>
## NPS Setup/Management

<ol> 
  <li><h3>Adding NPS</h3></li> 
<b>Overview</b>
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
<b>Main Menu Item 6 (NPS setup) -> Menu Item 3 (Add NPS)</b>
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
<br><b>Main Menu Item 6 (NPS Setup) -> Menu Item 2 (Edit NPS) </b>
<br>
<br>Then select NPS from List. The following menu provides 16 operations for the NPS you have selected:
<br>
<br>
<p align="center">
<img style="float: center;" src="/manual/images/edit_nps_menu.jpg">
</p>
<br>NOTE: Columns metadata reload differs from all other functions on this menu. To extract column information the metadata is pulled directly from the IBM Netezza database, so running menu option 16 (Reload All Data) excludes reloading of columns metadata.
<br>
<div id="npssetup3"></div>
  <li><h3>Reloading Storage After SMF Restart</h3></li> 
The SMF appliance provides DR (disaster-recovery / replication)  software components without any need to assign storage dedicated to SMF . The Customer can use any storage type which is currently supported and connected to IBM Netezza (NFS, SAN, GPFS) as a backup device,  and SMF can use it as replication source. 
<br>  
<br>To keep data in sync, increase replication stability and decrease storage utilisation SMF creates its own storage layout and mounts it accordingly to sync data. To  save infrastructure resources storage is not verified automatically (this can be adjusted). 
<br>
<br>In case of any reboot, after restarting SMF, to safely resume DR operations the following menu option needs to be invoked:
<br>
<br><b>Main Menu Item 6 (NPS Setup) -> Menu Item 4 (Reload DR storage)</b>
<br>
<br>
<div id="npssetup4"></div>
  <li><h3>Clearing Temporary Data</h3></li>
SMF uses  temporary space to analyse IBM Netezza Appliance objects. In the event that an operation is interrupted temporary data may not be cleared and this would block metadata reload operations. This can be safely cleared if no other operation is running at the time.
<br>
<br><b>Main Menu: Item: 6 (NPS Setup) -> Menu Item 4 (Clear Temp Space)</b>
<br>
<br>CAUTION: Running the “Clear Temp Space” operation when another operation is running may lead to corrupted metadata.
<br>
<br>
</ol>

