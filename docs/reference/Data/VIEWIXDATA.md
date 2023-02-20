##### Data Type : Views
##### VIEWIXDATA - Data structure passed from Notes to view import/export module
---
```
#include <ixview.h>
```
**Description :**

Notes passes this data structure to a view-level import or export module. It 
contains the information the view import/export module needs to import document 
into the view or export data from the view.

Notes passes a pointer to a data structure of this type as the IXContext input 
parameter to a view level import/export module. A view level import/export 
module consists of an executable program library that Notes can load and call 
when necessary. This library must provide an entry point that Notes can call. 
The syntax of this entry point must conform to the IXENTRYPROC definition in 
ixview.h.

**Sample Usage :**
```
VIEWIXDATA *ViewData,
char    *szStaticText,
char    *szItemName1,
char    *szItemName2)
STATUS   error = NOERROR;
HANDLE   hSelectedList; /* handle to ID table of Selected notes */
DBHANDLE DbHandle;
DWORD    notes_scanned;  /* used in procedure IDScan() */
NOTEID   note_id;        /* gets NOTEIDs stored in ID table */
    
        
hSelectedList = ViewData->hSelectedList;
if (hSelectedList == NULLHANDLE)
    return (NOERROR);

DbHandle = ViewData->hNoteFile;
if (DbHandle == NULLHANDLE)
    return (NOERROR);

while(IDScan(hSelectedList, (FLAG)(notes_scanned++==0L), &note_id))
{
    if (error = ReadNote(DbHandle, note_id,
                            szStaticText,
                            szItemName1,
                            szItemName2))
    {
        return(error);
    }
}
```
**See Also :**
[IXENTRYPROC](/reference/Data/IXENTRYPROC)
[EDITEXPORTDATA](/reference/Data/EDITEXPORTDATA)
[EDITIMPORTDATA](/reference/Data/EDITIMPORTDATA)
---
