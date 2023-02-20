##### Function : AddIn
##### OSPreemptOccasionally - Cause a server add-in task to give up control.
---
```
#include <osmisc.h>
void LNPUBLIC OSPreemptOccasionally(
void);
```
**Description :**

This function causes a server add-in task to give up control, so that other 
tasks on the machine can run.  It is intended to be used within compute-bound 
loops in a server add-in task.

This function only has an effect on operating systems, such as Windows, that do 
not preempt compute-bound tasks.  Under preemptive operating systems, this 
function does nothing.

Under operating systems that need it, OSPreemptOccasionally is included within 
the AddInIdle call.  Therefore, standard add-in task loops (that are not 
compute bound) do not require OSPreemptOccasionally.  OSPreemptOccasionally is 
quite fast however, so there is little penalty for including it in your 
program.

**Parameters :**

Output :
(routine)  -  None



**See Also :**
[AddInIdle](/reference/Func/AddInIdle)
---
