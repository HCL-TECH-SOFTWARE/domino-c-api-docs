##### Data Type : Signal Handler
##### OSSIGPROGRESSPROC - Function pointer template for progress bar signal handler.
---
```
#include <ossignal.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR OSSIGPROGRESSPROC)(
   WORD Option,
   void * Data1,
   void * Data2);
```

**Description :**

Definition of a pointer to a function that will handle the progress bar signal.  The progress signal handler displays a progress bar.  The progress position will generally start at 0 and end at Range.  The current progress supplied is either absolute (SETPOS) or a delta from the previous progress state (DELTAPOS).  As the operation which is supplying progress information is peformed, the range may change.  If it does, an additional SETRANGE will be signaled.<br>
<br>
This signal handler requires three parameters:<br>
<br>
    Option - Values are defined in PROGRESS_SIGNAL_xxx.<br>
<br>
    Data1 - DWORD.  See the following table for detail.<br>
                          <br>
    Data2 - DWORD.  See the following table for detail.<br>

<table width="100%" border="1">
<tr valign="top"><td width="33%">Option</td><td width="33%">Data1</td><td width="33%">Data2</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_BEGIN</b></td><td width="33%">NULL</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_END</b></td><td width="33%">NULL</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_SETRANGE</b></td><td width="33%">Range</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_SETTEXT</b></td><td width="33%">pointer to the text (pText1)</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_SETPOS</b></td><td width="33%">New progress bar position</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_DELTAPOS</b></td><td width="33%">Delta of the progress bar position</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_SETBYTERANGE</b></td><td width="33%">Total bytes</td><td width="33%">NULL</td></tr>

<tr valign="top"><td width="33%"><b>PROGRESS_SIGNAL_SETBYTEPOS</b></td><td width="33%">Bytes done</td><td width="33%">NULL</td></tr>
</table>



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
