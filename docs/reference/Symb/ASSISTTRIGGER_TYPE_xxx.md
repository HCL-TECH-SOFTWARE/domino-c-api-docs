##### Symbolic Value : Agents
##### ASSISTTRIGGER_TYPE_xxx - ODS_ASSISTSTRUCT - wTriggerType values for agent trigger types.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ASSISTTRIGGER_TYPE_NONE	  -  No trigger type; the agent is unavailable.

	ASSISTTRIGGER_TYPE_SCHEDULED	  -  Launch according to time schedule.

	ASSISTTRIGGER_TYPE_NEWMAIL	  -  Launch when new mail delivered.

	ASSISTTRIGGER_TYPE_PASTED	  -  Launch when documents pasted into database.

	ASSISTTRIGGER_TYPE_MANUAL	  -  Launch when requested by user (manually executed).

	ASSISTTRIGGER_TYPE_DOCUPDATE	  -  Launch when document is updated.

	ASSISTTRIGGER_TYPE_SYNCHNEWMAIL	  -  Synchronous new mail agent executed by router.

	ASSISTTRIGGER_TYPE_EVENT	  -  When an server event executes.


**Description :**

These constants are used in the wTriggerType field of the ODS_ASSISTSTRUCT record to determine the schedule for the agent.  Note that because there are different types of schedules, the meaning of the fields in the structure is sometimes ambiguous. Use the following rules:
<ul><br>
<br>
<font size="2">When wTriggerType == ASSISTTRIGGER_TYPE_SCHEDULED:<br>
	This trigger type means that the agent should run based on a timed schedule.</font><br>
<br>
<font size="2">	wSearchType: Any of the following are valid: ASSISTSEARCH_TYPE_ALL, TYPE_NEW, and</font><br>
<font size="2">		TYPE_MODIFIED.</font><br>
<br>
<font size="2">	wIntervalType: This is the type of interval: minutes, days, etc.<br>
		Any of the following are valid: ASSISTINTERVAL_TYPE_MINUTES, TYPE_DAYS, TYPE_WEEK,</font><br>
<font size="2">		TYPE_MONTH.</font><br>
<br>
<font size="2">	wInterval: This is the interval with which the agent will run.<br>
		This number is expressed in units of iIntervalType. For example, if iIntervalType == TYPE_DAYS,</font><br>
<font size="2">		and iInterval is 2, then the assistant will execute once every two days.</font><br>
<br>
<font size="2">	dwTime1 and dwTime2: These variables depend on iIntervalType:<br>
		Note: Time of day units are TICKS since midnight GMT</font><br>
<font size="2">		(i.e., 2AM would be 2 * 60 * TICKS_PER_MINUTE)</font><br>
<br>
<font size="2">		ASSISTINTERVAL_TYPE_MINUTES: dwTime1 and dwTime2 represent the starting and</font><br>
<font size="2">		ending times of the days during which the agent will run. For example, if iInterval is 30, dwTime1</font><br>
<font size="2">		is 2PM and dwTime2 is 11PM, then the agent will run every 30 minutes starting at 2PM until</font><br>
<font size="2">		11PM. If the fNoWeekends flag is set, then the agent will not run on weekends. If dwTime1 is 0</font><br>
<font size="2">		and dwTime2 is TICKS_IN_DAY, then it means that the agent should run all day.</font><br>
<br>
<font size="2">		ASSISTINTERVAL_TYPE_DAYS: dwTime1 represents the time of the day at which the</font><br>
<font size="2">		agent will run. If the fNoWeekends flag is set, then the agent will not run on weekends.</font><br>
<br>
<font size="2">		ASSISTINTERVAL_TYPE_WEEK: dwTime1 represents the time of the day at which the</font><br>
<font size="2">		agent will run; dwTime2 represents the day of the week (1-7) on which it will run. For example, if<br>
		dwTime1 is 10pm and dwTime2 is 4, then the </font><font size="2">agent will run once a week on Wednesday at</font><br>
<font size="2">		10pm. The fNoWeekends flags is ignored.</font><br>
<br>
<font size="2">		ASSISTINTERVAL_TYPE_MONTH: dwTime1 represents the time of the day on which the</font><br>
<font size="2">		</font><font size="2">agent will run; dwTime2 is the day of the month (1-31). For example, if dwTime1 is 5pm and</font><br>
<font size="2">		dwTime2 is 27, then the </font><font size="2">agent will run once per month on the 27th at 5PM. The fNoWeekends</font><br>
<font size="2">		flags is ignored.</font><br>
<br>
<font size="2">wTriggerType == ASSISTTRIGGER_TYPE_NEWMAIL:<br>
	This tigger type means that the agent should run whenever new mail is delivered, there are no time</font><br>
<font size="2">	constraints.</font><br>
<br>
<font size="2">	iSearchType: This parameter is ignored since we always operate on new documents.</font><br>
<br>
<font size="2">wTriggerType == ASSISTTRIGGER_TYPE_DOCUPDATE:<br>
	This tigger type means that the agent should run whenever a data class document is updated (via</font><br>
<font size="2">	NSFNoteUpdate) in the indicated database, there are no time constraints.</font><br>
<br>
<font size="2">	wSearchType: This value is ignored since we always operate on new documents.</font><br>
<br>
<font size="2">wTriggerType == ASSISTTRIGGER_TYPE_PASTED:<br>
	This trigger type means that the agent should run when documents are pasted (through the UI) into the</font><br>
<font size="2">	database.</font><br>
<br>
<font size="2">	wSearchType: This value is ignored since we always operate on new documents.</font><br>
<br>
<font size="2">wTriggerType == ASSISTTRIGGER_TYPE_MANUAL:<br>
	This trigger type may only be run through the UI.</font><br>
<br>
<font size="2">	wSearchType: The following are valid: ASSISTSEARCH_TYPE_SELECTED, TYPE_VIEW, TYPE_ALL,</font><br>
<font size="2">		TYPE_UNREAD, TYPE_PROMPT, TYPE_UI.</font></ul>



**See Also :**
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
