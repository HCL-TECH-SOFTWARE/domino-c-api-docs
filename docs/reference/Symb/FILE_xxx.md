##### Symbolic Value : Miscellaneous
##### FILE_xxx - File Types and Search Modifiers for NSFSearch
---
```
#include <osfile.h>
```

**Symbolic Values :**

	FILE_ANY	  -  (file type value) Find all files (NSF, MDM, etc.) and all sub-directories in the searched directory.

	FILE_DBREPL	  -  (file type value) Starting in Notes Release 3, find all databases or templates that are candidates for replication in the searched directory. This flag has been replaced by FILE_DBDESIGN and is exposed for compatibility purposes for previously written programs.

	FILE_DBDESIGN	  -  (file type value) Find all databases and templates in the searched directory. If you just want to search for databases, use FILE_DBANY. If you just want to search for templates, use FILE_FTANY.

	FILE_MAILBOX	  -  (file type value) BOX - Any .BOX (mail.box, SMTP.Box...)

	FILE_DBANY	  -  (file type value) Find all .NSF, .NSG, or .NSH files in the searched directory.

	FILE_FTANY	  -  (file type value) Find all template (.NTF ) files in the searched directory.

	FILE_MDMTYPE	  -  (file type value) Find all modem script files (.MDM) in the searched directory.

	FILE_DIRSONLY	  -  (file type value) Find all directories in the searched directory.

	FILE_VPCTYPE	  -  (file type value) Find only virtual port command (.VPC) files in the searched directory.

	FILE_SCRTYPE	  -  (file type value) SCR - comm port script files.

	FILE_ANYNOTEFILE	  -  (file type value) ANY Domino database (.NS?, .NT?, .BOX)

	FILE_UNIQUETEMP	  -  (file type value) DTF - Any .DTF. Used for container and sort temp files to give them a more unique name than .TMP so we can delete *.DTF from the temp directory and hopefully not blow away other application's temp files.

	FILE_MULTICLN	  -  (file type value) CLN - Any .cln file - multi user cleanup files.

	FILE_SMARTI	  -  (file type value) Any .smi file - smarticon files.

	FILE_TYPEMASK	  -  File type mask (for FILE_xxx codes above).

	FILE_DIRS	  -  (search modifier) Find subdirectories as well as regular files.

	FILE_NOUPDIRS	  -  (search modifier) Do not find the ".." directory.

	FILE_RECURSE	  -  (search modifier) Search into subdirectories.

	FILE_LINKSONLY	  -  (search modifier) All directories, linked files & directories.


**Description :**

These flags are used with NSFSearch to control what kinds of files are found during the search.<br>
<br>
When using NSFSearch with search_flags = SEARCH_FILETYPE, you may control the search by specifying combinations of FILE_CLASS values in the item_class argument to NSFSearch.<br>
<br>
The item_class argument to NSFSearch may consists of exactly one file type plus zero or more search modifiers.<br>
<br>
The file type part of item_class may contain one and only one of the following file types:<br>
<br>
FILE_ANY
<ul><br>
FILE_DBREPL<br>
FILE_DBDESIGN<br>
FILE_MAILBOX<br>
FILE_DBANY<br>
FILE_FTANY<br>
FILE_MDMTYPE<br>
FILE_DIRSONLY<br>
FILE_VPCTYPE<br>
FILE_SRCTYPE<br>
FILE_ANYNOTEFILE<br>
FILE_UNIQUETEMP<br>
FILE_MULTICLN<br>
FILE_SMARTI<br>
<br>
Note that item_class may contain one and only one of the above file type values. You may not combine different file type values to match multiple file name extensions.<br>
<br>
The search modifier part of item_class may contain any combination of the following search modifiers:<br>
<br>
FILE_DIRS<br>
FILE_NOUPDIRS<br>
FILE_RECURSE<br>
FILE_LINKSONLY<br>
<br>
You may bitwise-OR any combination of these search modifiers together with one of the integer type codes listed previously.<br>
<br>
FILE_DIRS causes NSFSearch to call your action routine on subdirectories as well as files that match the specified file type.  Since the &quot;..&quot; directory is treated as a subdirectory, you may OR in FILE_NOUPDIRS to prevent NSFSearch from calling your action routine on the directory &quot;..&quot;. FILE_NOUPDIRS has no effect unless OR'ed with FILE_DIRS.<br>
 <br>
FILE_RECURSE causes NSFSearch to recursively search subdirectories. FILE_RECURSE causes NSFSearch to call your action routine on files that match the file type in the directory you opened and in any sub-directory below that.</ul>



**Sample Usage :**
```
/* Open the directory. */

 if (error = NSFDbOpen (full_netpath, &dir_handle))
  return (ERR(error));

/* Call NSFSearch to find files in the directory. For each file found, 
call an action routine. */

 if (error = NSFSearch (
  dir_handle,  /* directory handle */
  NULLHANDLE,  /* selection formula */
  NULL,   /* title of view in formula */
  SEARCH_FILETYPE +  /* search for files */
  SEARCH_SUMMARY,  /* return a summary buffer */
  FILE_DBANY +   /* find any .NS? file */
  FILE_DIRS +  /* find subdirectories */
  FILE_NOUPDIRS,   /* don't find the ".." dir */
  NULL,   /* starting date */
  file_action,  /* call for each file found */
  NULL,   /* argument to action routine */
  NULL))   /* returned ending date (unused) */

  {
  NSFDbClose (dir_handle);
  return (ERR(error));
  }

/* Close the directory. */

 if (error = NSFDbClose (dir_handle))
  return (ERR(error));
```

**See Also :**
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
---
