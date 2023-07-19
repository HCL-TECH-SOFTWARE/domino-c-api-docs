##### Symbolic Value : Constants
##### HTML_EVENT_CLIENT_xxx - Specfic HTML client events.
---
```
#include <editods.h>
```

**Symbolic Values :**

	HTML_EVENT_CLIENT_FORM_QUERYOPEN	  -  Before the form is opened

	HTML_EVENT_CLIENT_FORM_QUERYMODE	  -  Before the form is changed to Read or Edit mode

	HTML_EVENT_CLIENT_FORM_POSTMODE	  -  After the form is changed to Read or Edit mode

	HTML_EVENT_CLIENT_FORM_POSTRECALC	  -  After the form is refreshed (and values are recalculated)

	HTML_EVENT_CLIENT_FORM_POSTSAVE	  -  After the form is saved

	HTML_EVENT_CLIENT_FORM_POSTSEND	  -  After the form is sent

	HTML_EVENT_CLIENT_FORM_QUERYRECALC		  -  Before the form is refreshed

	HTML_EVENT_CLIENT_FORM_QUERYSEND	  -  Before the form is sent

	HTML_EVENT_CLIENT_VIEW_QUERYOPEN	  -  Before the view is opened

	HTML_EVENT_CLIENT_VIEW_POSTOPEN	  -  After the view is opened

	HTML_EVENT_CLIENT_VIEW_REGIONDBLCLK	  -  Region in a calendar view or folder is double-clicked

	HTML_EVENT_CLIENT_VIEW_QUERYOPENDOC	  -  Before a document is loaded

	HTML_EVENT_CLIENT_VIEW_QUERYRECALC	  -  Before the view is refreshed

	HTML_EVENT_CLIENT_VIEW_QUERYADDTOFOLDER	  -  Before the document is added to a folder

	HTML_EVENT_CLIENT_VIEW_QUERYPASTE	  -  Before a paste operation

	HTML_EVENT_CLIENT_VIEW_POSTPASTE	  -  After a paste operation

	HTML_EVENT_CLIENT_VIEW_QUERYDRAGDROP	  -  Before a drag and drop operation

	HTML_EVENT_CLIENT_VIEW_POSTDRAGDROP	  -  After a drag and drop operation

	HTML_EVENT_CLIENT_VIEW_QUERYCLOSE	  -  The view is being closed

	HTML_EVENT_CLIENT_ONOBJECTEXECUTE	  -  Object is activated by an OLE2 server that is FX/NotesFlow enabled

	HTML_EVENT_CLIENT_DB_QUERYOPEN	  -  Before the database is opened

	HTML_EVENT_CLIENT_DB_POSTOPEN	  -  After the database is opened

	HTML_EVENT_CLIENT_DB_DOCDELETE	  -  After a document is deleted (the document is still available)

	HTML_EVENT_CLIENT_DB_QUERYCLOSE	  -  The database is being closed

	HTML_EVENT_CLIENT_DB_QUERYDELETE	  -  Before a document is marked for deletion

	HTML_EVENT_CLIENT_DB_QUERYUNDELETE	  -  Before a document is unmarked for deletion

	HTML_EVENT_CLIENT_DB_QUERYDRAGDROP	  -  Before a drag and drop operation

	HTML_EVENT_CLIENT_DB_POSTDRAGDROP	  -  After a drag and drop operation

	HTML_EVENT_CLIENT_VIEW_QUERYENTRYRESIZE	  -  Before a drag operation in a calendar folder or view

	HTML_EVENT_CLIENT_VIEW_POSTENTRYRESIZE	  -  After a drag operation in a calendar folder or view

	HTML_EVENT_CLIENT_VIEW_INVIEWEDIT	  -  Relates to in view editing

	HTML_EVENT_CLIENT_SCHED_INTERVALCHANGE	  -  Relates to a scheduled interval change event

	HTML_EVENT_CLIENT_DB_QUERYARCHIVEDRAGDROP	  -  Before an archive drag and drop operation

	HTML_EVENT_CLIENT_DB_POSTARCHIVEDRAGDROP	  -  After an archive drag and drop operation


**Description :**




**See Also :**
[CDEVENT](/domino-c-api-docs/reference/Data/CDEVENT)
---
