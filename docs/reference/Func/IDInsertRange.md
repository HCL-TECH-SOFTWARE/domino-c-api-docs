##### Function : ID
##### IDInsertRange - Inserts a DWORD Range of IDs into an ID table. 
---
```
#include <idtable.h>
STATUS IDInsertRange(

	DHANDLE  hTable,
	DWORD  IDFrom,IDTo,
	Boolean  AddToEnd);
```
**Description :**

This function inserts a range of IDs into a given ID table. The range is 
inclusive. Also, if "AddtoEnd" parameter is set to TRUE, it gurantees that the 
ID range does not overlap any IDs in the table and are the largest IDs in the 
table. 

**Parameters :**
Input :
hTable  -  Handle of ID table.


IDFrom,IDTo  -   Range of the IDs to insert (inclusive).


AddToEnd  -   if TRUE, caller GUARANTEES that the ID range does not overlap any IDs in the table and are the largest IDs in the table!Handle of ID table. 

Output :
(routine)  -  On invalid or NULL arguments, returns ERR_MISC_INVALID_ARGS error, on successful conversion returns NOERROR. On all other error returns NOTES Error. 



**Sample Usage :**
```
STATUS far PASCAL ParseRecords(char *buffer)
{
char tag[6];
char *ptag = tag;
char *p;
DWORD IDFrom, IDTo;
char buffercopy[400];
BOOL parsed = FALSE;
strncpy(buffercopy, buffer, sizeof(buffercopy));
p = strtok(buffer," ");

while (p != NULL)
{
//depending on what the tag is, read the rest of the line
if((strcmp(p, "BUFFER") == 0))
{
parsed = TRUE;
p = strtok(NULL, " ");
IDFrom = strtol(p, &p, 16);
p = strtok(NULL, " ");
IDTo = strtol(p, &p, 16);
IDInsertRange (hTable, IDFrom, IDTo, FALSE);
return(NOERROR);
}
else 
{
parsed = TRUE;
return(NOERROR); 
}
p = strtok(NULL, " ");
}

if(!parsed)
printf("ignoring line %s\n", buffercopy);

return(NOERROR);
}
```
**See Also :**
[CalCreateEntry](/reference/Func/CalCreateEntry)
[CalReadEntry](/reference/Func/CalReadEntry)
---
