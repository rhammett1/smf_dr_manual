---
layout: default
title: DR Management
---
<div id="drman1"></div>
## DR Management
<ol> 
 <li><h3>Overview </h3></li> 
<br>
SMF allows you to replicate any database to one or more Netezza machines. The synchronization is multi-mastered, meaning that each set can contain as many master and slave databases as desired, with no limit to the number of sets built. SMF supports omnidirectional streaming which results in complete flexibility for balancing workloads. Synchronization of databases can be set to occur continuously, or at intervals. All of these options are driven from this menu.
<br>
<br> DR Menu:
<p align="center">
<img style="float: center;" src="/manual/images/drmenu.jpg">
<br>
</p>
<div id="drman2"></div>
<li><b>DR Monitoring</b></li>
<br>
<br>
Text to be added
<br>
<br>
<div id="drman3"></div>
<li><b>Running DR Sets</b></li>
<br>
<br>
Text to be added
<br>
<br>
<div id="drman4"></div>
<li><b>Creating DR Sets</b></li>
<br>
<br>
When creating a DR Set <b>(Menu Option 4)</b>, choose one of the following 3 options:
<ul>
<li>Create Single Full DR Set – for ad-hoc use to create a Database DR Set</li>
<li>Create Multiple Full DR Sets – this option allows you to clone an existing Full DR set, or to create a new set to clone for the rest</li>
<li>Create Table DR Set – this option allows you to choose specific tables to replicate</li>
</ul>
<br>
<br>
When creating a single set, the steps are:
<ol>
<li>Selection of Netezza appliance from a list of online appliances</li>
<li>Selection of a database</li>
<li>Selection of storage mount points<sup>1</sup></li>
<li>The ratio of write:read<sup>2</sup></li>
</ol>
<br>
<br>
When creating multiple sets, items 3 & 4 are cloned
<br><br>
When creating a Table DR, additional steps are:
<ol>
<li>Specify table selection per set</li>
<li>Specify table selection per slave</li>
</ol>
<br>
<br>
<b>NOTES:</b>
<ol>
<li>SMF supports all types of local devices or storage devices natively supported by Netezza (NFS, SAN & GPFS)</li>
<li>Ratio of write:read – the default of 1 means that you will write immediately for each read sequence but in situations where you may wish to delay writing of data you may choose any number</li>
</ol>
<br>
<br>
<div id="drman5"></div>
<li><b>Editing DR Sets</b></li>
<br>
<br>
<div id="drman6"></div>
<li><b>Changing the Active Set Master</b></li>
<br>
<br>
Text to be added
<br>
<br>
<div id="drman7"></div>
<li><b>Checking DR Consistency</b></li>
<br>
<br>
Text to be added
<br>
<br>
<div id="drman8"></div>
<li><b>Changing DR Settings</b></li>
<br>
<br>
Text to be added
<br>
<br>
<div id="drman9"></div>
<li><b>Blocking & Unblocking DR Sets</b></li>
<br>
<br>
Text to be added
<br>
<br>


