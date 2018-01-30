---
layout: default
title: Scheduler
---
<div id="scheduler1"></div>
## Scheduler

<ol>
<li><b>Overview</b></li>
<br>The SMF scheduler provides you with total flexibility in scheduling the full range of SMF tasks via the UI. The scheduler creates a script on demand to run the task, storing it in the SMF database, and this script is executed by the Cron process.  Any time interval can be selected, and the scheduler can be paused at any time to allow for load balancing or system maintenance.
<br>
<br>
<div id="scheduler2"></div>
<li> <b>Scheduling tasks</b></li>
<br> 
<br>
The process of scheduling a task involves creating a job by assigning the task to an existing run cycle. In this context, a task may be:
<ul>
	<li> A set ID in the case of DR & backup</li>
	<li> An administrative, monitoring or GRA task, or</li>
	<li> A procedure in the case of LDAP sync & secure views</li>
</ul>	 
<br> 
<p align="center">
<img style="float: center;" src="/manual/images/scheduletask.jpg">
</p>
<br>
<br>
On selecting "Schedule tasks" you are taken to the run cycle menu:
<br>
<p align="center">
<img style="float: center;" src="/manual/images/runcycles.jpg">
</p>
<br>
If the run cycle required does not already exist, first create the new run cycle and once created select the run cycle. Run cycles can be set for any time interval from minute to year, start any day and end any day, so you have total flexibility. To remove unwanted run cycles, select menu option 3 => Delete run cycle. You will not be permitted to delete a run cycle that has tasks associated with it.
<br>
<br>
<div id="scheduler3"></div>
<li> <b>De-scheduling tasks</b></li>
<br> 
<p align="center">
<img style="float: center;" src="/manual/images/deschedule.jpg">
</p>
Tasks can be removed individually from the run cycle.
<br>
<br>
<div id="scheduler4"></div>
<li> <b>Stopping & restarting Scheduler</b></li>
<br>
SMF allows you to stop and restart the scheduler at any time to allow for maintenance, load balancing, etc. On restarting the scheduler the queue will restart and continue processing the backlog.
<br> 
<p align="center">
<img style="float: center;" src="/manual/images/stopscheduler.jpg">
</p>
<br>
To stop the scheduler with immediate effect, select today´s date when prompted and an hour that is earlier than the current hour.
<br>
To restart the scheduler with immediate effect, cancel the scheduler stop.
<br>
Scheduler stops can be planned in advance by selecting a future date & time to stop and restart the scheduler.

</ol>
