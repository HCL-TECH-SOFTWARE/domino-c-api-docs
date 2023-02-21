##### Symbolic Value : Agents
##### ASSISTTRIGGER_TYPE_xxx - ODS_ASSISTSTRUCT - wTriggerType values for agent trigger types.
---
```
#include <queryods.h>
```
**Description :**

These constants are used in the wTriggerType field of the ODS_ASSISTSTRUCT 
record to determine the schedule for the agent.  Note that because there are 
different types of schedules, the meaning of the fields in the structure is 
sometimes ambiguous. Use the following rules:

When wTriggerType == ASSISTTRIGGER_TYPE_SCHEDULED:
 This trigger type means that the agent should run based on a timed schedule.

	wSearchType: Any of the following are valid: ASSISTSEARCH_TYPE_ALL, 
TYPE_NEW, and
	 TYPE_MODIFIED.

	wIntervalType: This is the type of interval: minutes, days, etc.
  Any of the following are valid: ASSISTINTERVAL_TYPE_MINUTES, TYPE_DAYS, 
TYPE_WEEK,
	 TYPE_MONTH.

	wInterval: This is the interval with which the agent will run.
  This number is expressed in units of iIntervalType. For example, if 
iIntervalType == TYPE_DAYS,
	 and iInterval is 2, then the assistant will execute once every two 
days.

	dwTime1 and dwTime2: These variables depend on iIntervalType:
  Note: Time of day units are TICKS since midnight GMT
	 (i.e., 2AM would be 2 * 60 * TICKS_PER_MINUTE)

	 ASSISTINTERVAL_TYPE_MINUTES: dwTime1 and dwTime2 represent the 
starting and
	 ending times of the days during which the agent will run. For example, 
if iInterval is 30, dwTime1
	 is 2PM and dwTime2 is 11PM, then the agent will run every 30 minutes 
starting at 2PM until
	 11PM. If the fNoWeekends flag is set, then the agent will not run on 
weekends. If dwTime1 is 0
	 and dwTime2 is TICKS_IN_DAY, then it means that the agent should run 
all day.

	 ASSISTINTERVAL_TYPE_DAYS: dwTime1 represents the time of the day at 
which the
	 agent will run. If the fNoWeekends flag is set, then the agent will 
not run on weekends.

	 ASSISTINTERVAL_TYPE_WEEK: dwTime1 represents the time of the day at 
which the
	 agent will run; dwTime2 represents the day of the week (1-7) on which 
it will run. For example, if
  dwTime1 is 10pm and dwTime2 is 4, then the agent will run once a week on 
Wednesday at
	 10pm. The fNoWeekends flags is ignored.

	 ASSISTINTERVAL_TYPE_MONTH: dwTime1 represents the time of the day on 
which the
	 agent will run; dwTime2 is the day of the month (1-31). For example, 
if dwTime1 is 5pm and
	 dwTime2 is 27, then the agent will run once per month on the 27th at 
5PM. The fNoWeekends
	 flags is ignored.

wTriggerType == ASSISTTRIGGER_TYPE_NEWMAIL:
 This tigger type means that the agent should run whenever new mail is 
delivered, there are no time
	constraints.

	iSearchType: This parameter is ignored since we always operate on new 
documents.

wTriggerType == ASSISTTRIGGER_TYPE_DOCUPDATE:
 This tigger type means that the agent should run whenever a data class 
document is updated (via
	NSFNoteUpdate) in the indicated database, there are no time constraints.

	wSearchType: This value is ignored since we always operate on new 
documents.

wTriggerType == ASSISTTRIGGER_TYPE_PASTED:
 This trigger type means that the agent should run when documents are pasted 
(through the UI) into the
	database.

	wSearchType: This value is ignored since we always operate on new 
documents.

wTriggerType == ASSISTTRIGGER_TYPE_MANUAL:
 This trigger type may only be run through the UI.

	wSearchType: The following are valid: ASSISTSEARCH_TYPE_SELECTED, 
TYPE_VIEW, TYPE_ALL,
	 TYPE_UNREAD, TYPE_PROMPT, TYPE_UI.

**See Also :**
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
