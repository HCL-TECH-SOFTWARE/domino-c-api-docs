##### Data Type : Note Open/Note Update Hook Drivers
##### DBHOOKVEC - Hook Driver Vector
---
##### #include <nsfdb.h>
**Description :**
This data structure provides a way for API programs to hook into the NSF 
subsystem so that the API program gains control each time the NSF subsystem 
opens, updates or categorizes notes.

Use hook drivers to log access to a database, grant or refuse access requests, 
or modify the contents of notes when they are updated.

A hook driver consists of an executable program library installed in the Domino 
or Notes program directory and identified in the notes.ini file. This library 
must export an initialization function and, optionally, a note open function, a 
note update function, a note categorize function, and a termination function. 

When Domino or Notes initializes, it calls the hook driver's initialization 
function, passing, as input, a pointer to a DBHOOKVEC data structure. The hook 
driver's initialization function sets the members of this structure to point to 
the other functions provided by the hook driver. Subsequently, Domino or Notes 
calls the specified functions each time a note is opened, updated, or 
categorized. When Domino or Notes terminates, it calls the specified hook 
driver termination function.

Implement a hook driver by writing an executable program library that exports 
an initialization function, a termination function, and functions to be called 
when a note is opened, updated, or categorized, as needed. This initialization 
function must accept, as input, a pointer to a structure of type DBHOOKVEC. 
When called, it must set the <Term>, <NoteOpen>, <NoteUpdate>, and 
<DbStampNotes> members of the DBHOOKVEC as necessary. It must set unused 
members to NULL.

Under Unix, the initialization function must be named "MainEntryPoint".  Under 
Windows, the initialization function may have any name but must be the first 
(ordinal) entry point exported by the DLL (entry point @1).

Domino or Notes sets the <hModule> member of the DBHOOKVEC before it calls the 
initialization function. This allows the initialization function under Windows 
to load resources.

Under Windows, name the executable program library with a file name less than 7 
characters long and it may be prefixed with the letter ('n') for 32-bit 
Windows.  Under Unix, the executable program library must be named according to 
the convention for shared library files in that environment.  Under Solaris, 
specifically, the name of the executable program library must have the filename 
extension ".so".

Install the hook driver by copying the library into the Domino or Notes program 
directory. Edit the notes.ini file and add driver name to the variable 
NSF_HOOKS.  Separate the names of multiple drivers with a comma separator. For 
example:

NSF_HOOKS=drivera,driverb,driverc

Do not specify the prefix character or the suffix .DLL in the notes.ini file.

The hook driver Dynamic Link Library is loaded once per process. Export, in 
your DEF file, all of the driver functions that Domino or Notes will call.

All code executed by all entry points to the hook driver must be 100% reentrant 
by both multiple threads within a single process and multiple processes. 

Domino or Notes calls the function specified in the <NoteOpen> member just 
after the note is opened by the NSF subsystem but before control is returned to 
the caller or the user interface. It is called for both local and remote 
databases.  The UserName parameter is the name of the user doing the open. 
GroupList may be NULL, but when it's not it contains a list of the groups that 
the user is in.  hDB and NoteID can be used to identify the database and note. 
OpenFlags are the flags originally passed into NSFNoteOpen.  If the 
OPEN_CANONICAL flag is set in this parameter, all items in the note will be 
returned in canonical format, including the datatype WORD.  In this case, you 
must use ODSReadMemory to convert the canonical data to host data.  hNote is 
the handle to the note that is about to be returned to the caller.  Modify the 
contents of the note using the note handle.  To deny access to the note, return 
any standard Lotus C API for Domino and Notes error code.

Domino or Notes calls the function specified in the <NoteUpdate> member just 
before a note is updated by the NSF subsystem.  It is called for both local and 
remote databases.  UserName, GroupList, hDB and NoteID have the same meanings 
as in <NoteOpen>.  The pointer pUpdateFlags specifies a word containing the 
flags originally passed into NSFNoteUpdate.  hNote is the handle to the note 
that is about to be updated.  Your hook driver may modify the contents of the 
note, or may return any standard Lotus C API for Domino and Notes error code to 
cause the update to fail. Your hook driver may also modify the update flags, 
for example, to force a particular flag such as UPDATE_NOREVISION to be set.  
If the note has been opened with the OPEN_CANONICAL flag set, the application 
must perform all data type word and data value conversions;  Domino and Notes 
do not perform these conversions automatically when this option is set.  A hook 
driver may be called for databases that were opened by Domino or Notes with 
this flag set.  A hook driver can check the current state for a note by calling 
NSFNoteGetInfo() with the header member _NOTE_FLAGS, and testing for the 
presence of the flag NOTE_FLAG_CANONICAL.

Use the following algorithm in your note update hook driver to determine what 
operation is being performed:

	if (NoteID == NOTEID_ADD
   || NoteID == NOTEID_ADD_OR_REPLACE
   || NoteID == NOTEID_ADD_UNID)
  {
  if (*pUpdateFlags & UPDATE_DELETED)
   ; // Adding a new "deleted note stub" to a database
  else
   ; // Adding a new document to a database
  }
 else
	 {
  if (*pUpdateFlags & UPDATE_DELETED)
   ; // Deleting an existing document from the database.
     // Note that in this case, the contents of the hNote
     // may be nil and should be disregarded; because of
			  // this, there's no way to tell the class of a note
     // being deleted at this point
  else
   ; // Updating an existing document in the database
  }

Domino or Notes calls the function specified in the <DbStampNotes>  member just 
before a set of notes are stamped with one item value by the NSF subsystem. It 
is called for both local and remote databases.  UserName, GroupList, and hDB 
have the same meaning as above. hTable is an ID table containing the note IDs 
of all the notes being categorized. ItemName and Data indicate the data being 
used in the categorization.  Return any standard Lotus C API for Domino and 
Notes error code to fail the Stamp call.

Handles that are returned from C API functions are thread specific and should 
not be used in a different thread.  For example, if the database hook driver's 
initialization function opens a remote database, the returned file handle will 
not necessarily remain valid when one of the other exported functions in the 
hook driver is called.  You may want to open the remote database in the hook 
driver's initialization function as a means of caching the database to keep it 
in memory, but do not use the handle in other hook driver exported functions.  
Instead, open and close the desired database within each exported function that 
uses the database handle.
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
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[NSFNoteUpdate](D:/md_files/NSFNoteUpdate.md)
[NSFDbStampNotes](D:/md_files/NSFDbStampNotes.md)
---
