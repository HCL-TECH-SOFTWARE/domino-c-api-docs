##### Function : Search
##### NSFSearchStart - 
---
```
#include <nsfsearc.h>
STATUS far PASCAL NSFSearchStart(

	DBHANDLE  hDB,
	FORMULAHANDLE  hFormula,
	UNID far *ViewUNID,
	char far *ViewTitle,
	QUEUEHANDLE  hQueue,
	DWORD  SearchFlags,
	WORD  NoteClassMask,
	WORD  SpareUsedToBeAuxClass,
	WORD  Granularity,
	TIMEDATE  Since,
	TIMEDATE far *retUntil,
	SEARCHHANDLE far *rethSearch);
```
**Description :**



**Parameters :**
Input :
hDB  -  

hFormula  -  

ViewUNID  -  

ViewTitle  -  

hQueue  -  

SearchFlags  -  

NoteClassMask  -  

SpareUsedToBeAuxClass  -  

Granularity  -  

Since  -  

retUntil  -  

rethSearch  -  



**See Also :**
---
