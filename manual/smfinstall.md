---
layout: default
title: SMF Installation
---
<div id="smfinstall1"></div>
## SMF Installation
<ol>
<li> <h3>Setting up Primary SMF node</h3></li>
<br> Requirements:
<ul>
<li>SMF Virtual Appliance (1 required per data centre)</li>
<li>2 core</li>
<li>4 GB DRAM</li>
<li>30 GB disk storage</li>
<li>1GB+ Network Interface Card</li>
<li>Uses CENTOS and PostgreSQL standard components internally</li>
<li>Internal metadata can be queried/reported against using any PostgreSQL ODBC/JDBC client</li>
<li>Uses GitHub for remote updating of SMF software versions</li>
<li>Can use either VMWare/Vsphere to host the VMs or other products like VirtualBox</li>
</ul>
<br>
<br>
NOTE: During installation of SMF appliance access to YUM (update) server is required

<div id="smfinstall2"></div>
<li> <h3>Setting up Secondary SMF node</h3></li>

<br> To be written asap
</ol>
<div id="smfinstall3"></div>
## SMF User Interface
<ol>
<li><b>Overview</b></li>
<br>The SMF user interface is a hierarchical menu system whereby the majority of administrative tasks are managed by building executable sets that can be run individually or in batches in real time, or via a scheduler.
<br>
<br>
<li> <b>Variable Settings</b></li>
<br>
<br><b>Menu Item 11 (System Setup): </b>
<br>
<p align="center">
<img style="float: center;" src="/manual/images/systemsetup_menu.jpg">
<br>
<br>
<ul>
<li> Enable Silent/Verbose Mode - Toggle this setting to reduce the number of messages displayed on the screen during the execution of processes.</li>
<li>Enable/Disable Drop Broken Views. </li>
<li>Change Probe Interval. </li>
<li>Change Probe Timeout. </li>
<li>Change Max DR masters Run. </li>
<li>Change Max DR Jobs per Master Run. </li>
<li>Set Backups by DB ID. </li>
<li>Enable/Disable View Checking on DR. </li>
<li>Enable/Disable Stats Collection for Backup. </li>
<li>Change Metadata Extraction Frequency. </li>
<li>Change Number of Metadata Extraction Attempts. </li>
<li>Enable/Disable Temporary Metadata Deletion. </li>
</ul>
<br>



