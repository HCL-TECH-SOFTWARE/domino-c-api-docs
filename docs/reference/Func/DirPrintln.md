##### Function : Dir
##### DirPrintln - A DIRPRINTLN_PROC that writes a line(s) to the Notes/Domino console via xprintf(). 
---
```
#include <dirprint.h>
void LNCALLBACK DirPrintln(

	void *printctx,
	const char *line);
```
**Description :**

A DIRPRINTLN_PROC that writes a line(s) to the Notes/Domino console via 
xprintf(). 

**Parameters :**
Input :
printctx  -  Not used 

line  -  Line(s) to print. Multiple lines have '\n' separators. (does not include '\n' terminator) 



**See Also :**
---
