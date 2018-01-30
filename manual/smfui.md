---
layout: default
title: SMF User Interface
---
<div id="smfui1"></div>
## SMF User Interface
<ol>
<li><b>Overview</b></li>
<br>The SMF user interface is a hierarchical menu system whereby the majority of administrative operations are managed by building executable sets that can be run individually or in batches on command, or via a scheduler.
<br>
<br>
<p align="center">
<img style="float: center;" src="/manual/images/main_ui.jpg">
<br>
<br>
<div id="smfui2"></div>
<li> <b>System Settings</b></li>
<br>
<br><b>Menu Item 10 (System Setup): </b>
<br>
<p align="center">
<img style="float: center;" src="/manual/images/systemsetup_menu.jpg">
<br>
<br>
<ul>
<li> Enable silent/verbose mode - toggle this setting to reduce the number of messages displayed on the screen during operations.</li>
<li>Enable/disable dop broken views - toggle this setting for use when creating backup sets. If enabled, views will be dropped and their code saved if errors are encountered. If disabled, the backup will stop on encountering errors </li>
<li>Change admin tasks probe interval - this sets the number of seconds between checking that there are admin tasks to run </li>
<li>Change admin tasks probe timeout - this setting sets the number of retries (every second) before timing out </li>
<li>Change max DR masters run - global setting to assist with load balancing and avoiding excessive CPU usage.</li>
<li>Change max DR jobs per master Run - global setting to assist with load balancing and avoiding excessive CPU usage.</li>
<li>Set backups by DB ID or by name - toggle switch </li>
<li>Enable/disable view checking on DR. </li>
<li>Enable/Disable stats collection for backup. </li>
<li>Change metadata extraction frequency. </li>
<li>Change number of metadata extraction attempts. </li>
<li>Enable/disable temporary metadata deletion. </li>
<li>Change UI monitoring refresh interval - this sets the number of seconds between screen refresh, which would otherwise be every second and can be distracting if there are no changes to report </li>
</ul>
<br>



