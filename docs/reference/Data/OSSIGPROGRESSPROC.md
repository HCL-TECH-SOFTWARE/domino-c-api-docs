##### Data Type : Signal Handler
##### OSSIGPROGRESSPROC - Function pointer template for progress bar signal handler.
---
```
#include <ossignal.h>
```
**Description :**

Definition of a pointer to a function that will handle the progress bar 
signal.  The progress signal handler displays a progress bar.  The progress 
position will generally start at 0 and end at Range.  The current progress 
supplied is either absolute (SETPOS) or a delta from the previous progress 
state (DELTAPOS).  As the operation which is supplying progress information is 
peformed, the range may change.  If it does, an additional SETRANGE will be 
signaled.

This signal handler requires three parameters:

    Option - Values are defined in PROGRESS_SIGNAL_xxx.

    Data1 - DWORD.  See the following table for detail.
                          
    Data2 - DWORD.  See the following table for detail.

Option	Data1	Data2
PROGRESS_SIGNAL_BEGIN	NULL	NULL
PROGRESS_SIGNAL_END	NULL	NULL
PROGRESS_SIGNAL_SETRANGE	Range	NULL
PROGRESS_SIGNAL_SETTEXT	pointer to the text (pText1)	NULL
PROGRESS_SIGNAL_SETPOS	New progress bar position	NULL
PROGRESS_SIGNAL_DELTAPOS	Delta of the progress bar position	NULL
PROGRESS_SIGNAL_SETBYTERANGE	Total bytes	NULL
PROGRESS_SIGNAL_SETBYTEPOS	Bytes done	NULL


**Sample Usage :**
```
OSSIGPROGRESSPROC ProgressProc;
char STARTTEXT[100]="Look at the progress";
int  i;
   .
   .
   .

/* Get the Progress signal handler function pointer. */
ProgressProc = (OSSIGPROGRESSPROC) OSGetSignalHandler(OS_SIGNAL_PROGRESS);

/* Start the Progress signal. */
(*ProgressProc)(PROGRESS_SIGNAL_BEGIN,NULL,NULL);

/* Set the header of the Progress bar. */
(*ProgressProc)(PROGRESS_SIGNAL_SETTEXT,(DWORD)STARTTEXT,NULL);

/* Set the starting position. */
(*ProgressProc)(PROGRESS_SIGNAL_SETPOS, 0,NULL);

/* Set the range. */
(*ProgressProc)(PROGRESS_SIGNAL_SETRANGE,1000,NULL);


/* Let's see the Progress. */
for (i=2;i<1000;i++)
{
  (*ProgressProc)(PROGRESS_SIGNAL_SETPOS, i,NULL);
}

/* It's done. */
(*ProgressProc)(PROGRESS_SIGNAL_END,NULL,NULL);

```
**See Also :**
[OSSIGPROC](/domino-c-api-docs/reference/Data/OSSIGPROC)
[PROGRESS_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/PROGRESS_SIGNAL_xxx)
---
