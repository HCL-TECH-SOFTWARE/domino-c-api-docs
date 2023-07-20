##### Data Type : Note Open/Note Update Hook Drivers
##### DBHOOKVEC - Hook Driver Vector
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct dbhookvec {

   HMODULE hModule; /* Module handle of the hook library */

   /* Initialization function. Called for each process that does a
      NotesInit. Must be ordinal #1 in hook driver DLL. */

   STATUS (LNCALLBACKPTR Init)(
              struct dbhookvec far *vec);

   /* Termination function. Called once for each process that did an
      Init call, just prior to the process's exiting. */

   STATUS (LNCALLBACKPTR Term)(
              struct dbhookvec far *vec);

   /* Note open hook.  This routine is called just AFTER a note is
      opened by the NSF subsystem. */

   STATUS (LNCALLBACKPTR NoteOpen)(
              struct dbhookvec far *vec,
              char far *UserName,
              LIST far *GroupList,
              DBHANDLE hDB,
              NOTEID NoteID,
              NOTEHANDLE hNote,
              WORD OpenFlags);

   /* Note add/update hook, also handles deletion. Called before a
      note is updated. */

   STATUS (LNCALLBACKPTR NoteUpdate)(
              struct dbhookvec far *vec,
              char far *UserName,
              LIST far *GroupList,
              DBHANDLE hDB,
              NOTEID NoteID,
              NOTEHANDLE hNote,
              WORD far *UpdateFlags);

   /* Note stamp (Categorization) hook.  Called just BEFORE a set of
      notes is Categorized by the NSF subsystem. */

   STATUS (LNCALLBACKPTR DbStampNotes)(
              struct dbhookvec far *vec,
              char far *UserName,
              LIST far *GroupList,
              DBHANDLE hDB,
              HANDLE hIDTable,
              char far *ItemName,
              WORD ItemNameLength,
              void far *Data,
              WORD Length);

   /* Flags used by Domino or Notes to describe the hook driver -- RESERVED */

   DWORD Flags;

} DBHOOKVEC;
```

**Description :**

This data structure provides a way for API programs to hook into the NSF subsystem so that the API program gains control each time the NSF subsystem opens, updates or categorizes notes.<br>
<br>
Use hook drivers to log access to a database, grant or refuse access requests, or modify the contents of notes when they are updated.<br>
<br>
A hook driver consists of an executable program library installed in the Domino or Notes program directory and identified in the notes.ini file. This library must export an initialization function and, optionally, a note open function, a note update function, a note categorize function, and a termination function. <br>
<br>
When Domino or Notes initializes, it calls the hook driver's initialization function, passing, as input, a pointer to a DBHOOKVEC data structure. The hook driver's initialization function sets the members of this structure to point to the other functions provided by the hook driver. Subsequently, Domino or Notes calls the specified functions each time a note is opened, updated, or categorized. When Domino or Notes terminates, it calls the specified hook driver termination function.<br>
<br>
Implement a hook driver by writing an executable program library that exports an initialization function, a termination function, and functions to be called when a note is opened, updated, or categorized, as needed. This initialization function must accept, as input, a pointer to a structure of type DBHOOKVEC. When called, it must set the &lt;Term&gt;, &lt;NoteOpen&gt;, &lt;NoteUpdate&gt;, and &lt;DbStampNotes&gt; members of the DBHOOKVEC as necessary. It must set unused members to NULL.<br>
<br>
Under Unix, the initialization function must be named &quot;MainEntryPoint&quot;.  Under Windows, the initialization function may have any name but must be the first (ordinal) entry point exported by the DLL (entry point @1).<br>
<br>
Domino or Notes sets the &lt;hModule&gt; member of the DBHOOKVEC before it calls the initialization function. This allows the initialization function under Windows to load resources.<br>
<br>
Under Windows, name the executable program library with a file name less than 7 characters long and it may be prefixed with the letter ('n') for 32-bit Windows.  Under Unix, the executable program library must be named according to the convention for shared library files in that environment.  Under Solaris, specifically, the name of the executable program library must have the filename extension &quot;.so&quot;.<br>
<br>
Install the hook driver by copying the library into the Domino or Notes program directory. Edit the notes.ini file and add driver name to the variable NSF_HOOKS.  Separate the names of multiple drivers with a comma separator. For example:<br>
<br>
NSF_HOOKS=drivera,driverb,driverc<br>
<br>
Do not specify the prefix character or the suffix .DLL in the notes.ini file.<br>
<br>
The hook driver Dynamic Link Library is loaded once per process. Export, in your DEF file, all of the driver functions that Domino or Notes will call.<br>
<br>
All code executed by all entry points to the hook driver must be 100% reentrant by both multiple threads within a single process and multiple processes. <br>
<br>
Domino or Notes calls the function specified in the &lt;NoteOpen&gt; member just after the note is opened by the NSF subsystem but before control is returned to the caller or the user interface. It is called for both local and remote databases.  The UserName parameter is the name of the user doing the open. GroupList may be NULL, but when it's not it contains a list of the groups that the user is in.  hDB and NoteID can be used to identify the database and note. OpenFlags are the flags originally passed into NSFNoteOpen.  If the OPEN_CANONICAL flag is set in this parameter, all items in the note will be returned in canonical format, including the datatype WORD.  In this case, you must use ODSReadMemory to convert the canonical data to host data.  hNote is the handle to the note that is about to be returned to the caller.  Modify the contents of the note using the note handle.  To deny access to the note, return any standard Lotus C API for Domino and Notes error code.<br>
<br>
Domino or Notes calls the function specified in the &lt;NoteUpdate&gt; member just before a note is updated by the NSF subsystem.  It is called for both local and remote databases.  UserName, GroupList, hDB and NoteID have the same meanings as in &lt;NoteOpen&gt;.  The pointer pUpdateFlags specifies a word containing the flags originally passed into NSFNoteUpdate.  hNote is the handle to the note that is about to be updated.  Your hook driver may modify the contents of the note, or may return any standard Lotus C API for Domino and Notes error code to cause the update to fail. Your hook driver may also modify the update flags, for example, to force a particular flag such as UPDATE_NOREVISION to be set.  If the note has been opened with the OPEN_CANONICAL flag set, the application must perform all data type word and data value conversions;  Domino and Notes do not perform these conversions automatically when this option is set.  A hook driver may be called for databases that were opened by Domino or Notes with this flag set.  A hook driver can check the current state for a note by calling NSFNoteGetInfo() with the header member _NOTE_FLAGS, and testing for the presence of the flag NOTE_FLAG_CANONICAL.<br>
<br>
Use the following algorithm in your note update hook driver to determine what operation is being performed:<br>
<br>
<tt><font size="2">	if (NoteID == NOTEID_ADD<br>
			|| NoteID == NOTEID_ADD_OR_REPLACE<br>
			|| NoteID == NOTEID_ADD_UNID)<br>
		{<br>
		if (*pUpdateFlags &amp; UPDATE_DELETED)<br>
			; // Adding a new &quot;deleted note stub&quot; to a database<br>
		else<br>
			; // Adding a new document to a database<br>
		}<br>
	else<br>
		{<br>
		if (*pUpdateFlags &amp; UPDATE_DELETED)<br>
			; // Deleting an existing document from the database.<br>
			 &nbsp;// Note that in this case, the contents of the hNote<br>
			 &nbsp;// may be nil and should be disregarded; because of<br>
</font></tt><tt><font size="2">	</font></tt><tt><font size="2">	</font></tt><tt><font size="2">	 &nbsp;</font></tt><tt><font size="2">// this, there's no way to tell the class of a note<br>
			 &nbsp;// being deleted at this point<br>
		else<br>
			; // Updating an existing document in the database<br>
		}<br>
</font></tt><br>
Domino or Notes calls the function specified in the &lt;DbStampNotes&gt;  member just before a set of notes are stamped with one item value by the NSF subsystem. It is called for both local and remote databases.  UserName, GroupList, and hDB have the same meaning as above. hTable is an ID table containing the note IDs of all the notes being categorized. ItemName and Data indicate the data being used in the categorization.  Return any standard Lotus C API for Domino and Notes error code to fail the Stamp call.
<ul><br>
<br>
Handles that are returned from C API functions are thread specific and should not be used in a different thread.  For example, if the database hook driver's initialization function opens a remote database, the returned file handle will not necessarily remain valid when one of the other exported functions in the hook driver is called.  You may want to open the remote database in the hook driver's initialization function as a means of caching the database to keep it in memory, but do not use the handle in other hook driver exported functions.  Instead, open and close the desired database within each exported function that uses the database handle.</ul>



**Sample Usage :**
```
STATUS LNPUBLIC TrackerInit(DBHOOKVEC * pDBHooks)
{
    /* Initialize the DBHOOK vector.*/
    pDBHooks->Term         = TrackerTerm;
    pDBHooks->NoteOpen     = TrackerNoteOpen;
    pDBHooks->NoteUpdate   = TrackerNoteUpdate;
    pDBHooks->DbStampNotes = TrackerDbStampNotes;

    return (NOERROR);
}
```

**See Also :**
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[NSFDbStampNotes](/domino-c-api-docs/reference/Func/NSFDbStampNotes)
---
