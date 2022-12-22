




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Symbolic Value : Miscellaneous**



**FILE\_xxx** **-** File Types
and Search Modifiers for NSFSearch


**----------------------------------------------------------------------------------------------------------**



**#include <osfile.h>**


 **Symbolic Values :**      FILE\_ANY    -  (file type value) Find all files (NSF, MDM,
etc.) and all sub-directories in the searched directory.  

  

      FILE\_DBREPL          -  (file type value) Starting in Notes Release 3,
find all databases or templates that are candidates for replication in the
searched directory. This flag has been replaced by FILE\_DBDESIGN and is exposed
for compatibility purposes for previously written programs.  

  

      FILE\_DBDESIGN      -  (file type value) Find all databases and templates
in the searched directory. If you just want to search for databases, use
FILE\_DBANY. If you just want to search for templates, use FILE\_FTANY.  

  

      FILE\_MAILBOX        -  (file type value) BOX - Any .BOX (mail.box,
SMTP.Box...)  

  

      FILE\_DBANY            -  (file type value) Find all .NSF, .NSG, or .NSH
files in the searched directory.  

  

      FILE\_FTANY            -  (file type value) Find all template (.NTF )
files in the searched directory.  

  

      FILE\_MDMTYPE      -  (file type value) Find all modem script files (.MDM)
in the searched directory.  

  

      FILE\_DIRSONLY      -  (file type value) Find all directories in the
searched directory.  

  

      FILE\_VPCTYPE        -  (file type value) Find only virtual port command
(.VPC) files in the searched directory.  

  

      FILE\_SCRTYPE       -  (file type value) SCR - comm port script files.  

  

      FILE\_ANYNOTEFILE            -  (file type value) ANY Domino database
(.NS?, .NT?, .BOX)  

  

      FILE\_UNIQUETEMP             -  (file type value) DTF - Any .DTF. Used for
container and sort temp files to give them a more unique name than .TMP so we
can delete \*.DTF from the temp directory and hopefully not blow away other
application's temp files.  

  

      FILE\_MULTICLN      -  (file type value) CLN - Any .cln file - multi user cleanup
files.  

  

      FILE\_SMARTI          -  (file type value) Any .smi file - smarticon
files.  

  

      FILE\_TYPEMASK     -  File type mask (for FILE\_xxx codes above).  

  

      FILE\_DIRS   -  (search modifier) Find subdirectories as well as regular
files.  

  

      FILE\_NOUPDIRS      -  (search modifier) Do not find the ".."
directory.  

  

      FILE\_RECURSE       -  (search modifier) Search into subdirectories.  

  

      FILE\_LINKSONLY     -  (search modifier) All directories, linked files
& directories.  

  




**Description :**



These flags
are used with NSFSearch to control what kinds of files are found during the
search.  

  

When using NSFSearch with search\_flags = SEARCH\_FILETYPE, you may control the
search by specifying combinations of FILE\_CLASS values in the item\_class
argument to NSFSearch.  

  

The item\_class argument to NSFSearch may consists of exactly one file type plus
zero or more search modifiers.  

  

The file type part of item\_class may contain one and only one of the following
file types:  

  

FILE\_ANY


FILE\_DBREPL


FILE\_DBDESIGN


FILE\_MAILBOX  

FILE\_DBANY  

FILE\_FTANY  

FILE\_MDMTYPE  

FILE\_DIRSONLY  

FILE\_VPCTYPE


FILE\_SRCTYPE


FILE\_ANYNOTEFILE


FILE\_UNIQUETEMP


FILE\_MULTICLN


FILE\_SMARTI  

  

Note that item\_class may contain one and only one of the above file type
values. You may not combine different file type values to match multiple file
name extensions.  

  

The search modifier part of item\_class may contain any combination of the
following search modifiers:  

  

FILE\_DIRS  

FILE\_NOUPDIRS  

FILE\_RECURSE


FILE\_LINKSONLY  

  

You may bitwise-OR any combination of these search modifiers together with one
of the integer type codes listed previously.  

  

FILE\_DIRS causes NSFSearch to call your action routine on subdirectories as
well as files that match the specified file type.  Since the ".."
directory is treated as a subdirectory, you may OR in FILE\_NOUPDIRS to prevent
NSFSearch from calling your action routine on the directory "..".
FILE\_NOUPDIRS has no effect unless OR'ed with FILE\_DIRS.  

   

FILE\_RECURSE causes NSFSearch to recursively search subdirectories.
FILE\_RECURSE causes NSFSearch to call your action routine on files that match
the file type in the directory you opened and in any sub-directory below that.


 **Sample Usage :**


/\* Open the directory.
\*/  

  

    if (error = NSFDbOpen (full\_netpath, &dir\_handle))  

           return (ERR(error));  

  

/\* Call NSFSearch to find files in the directory. For each file found,   

call an action routine. \*/  

  

    if (error = NSFSearch (  

           dir\_handle,            /\* directory handle \*/  

           NULLHANDLE,            /\* selection formula \*/  

           NULL,                  /\* title of view in formula \*/  

           SEARCH\_FILETYPE +      /\* search for files \*/  

           SEARCH\_SUMMARY,               /\* return a summary buffer \*/  

           FILE\_DBANY +           /\* find any .NS? file \*/  

           FILE\_DIRS +            /\* find subdirectories \*/  

           FILE\_NOUPDIRS,                /\* don't find the ".." dir
\*/  

           NULL,                  /\* starting date \*/  

           file\_action,           /\* call for each file found \*/  

           NULL,                  /\* argument to action routine \*/  

           NULL))                 /\* returned ending date (unused) \*/  

  

           {  

           NSFDbClose (dir\_handle);  

           return (ERR(error));  

           }  

  

/\* Close the directory. \*/  

  

    if (error = NSFDbClose (dir\_handle))  

           return (ERR(error));


 **See Also :**


**[NSFSearch](NSFSearch.md)**



----------------------------------------------------------------------------------------------------------


 





