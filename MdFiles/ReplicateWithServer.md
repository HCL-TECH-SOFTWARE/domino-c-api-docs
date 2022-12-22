




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




 


**Function : Replication**



**ReplicateWithServer** **- Replicate
with a server from a local system.**


**----------------------------------------------------------------------------------------------------------**



**#include <repl.h>**



STATUS
LNPUBLIC **ReplicateWithServer(**  

      char far \*PortName,  

      char far \*ServerName,  

      WORD  Options,  

      WORD  NumFiles,  

      const char far \*FileList,  

      REPLSERVSTATS far \*retStats**);**



**Description :**



This routine
replicates Domino database files on the local system with a specified server. 
Either all common files can be replicated or a specified list of files can be
replicated.  The number of file names is specified in the parameter NumFiles. 
The file names must be concatenated into a single list, with each name
terminated by a NUL ('\0') character.  

  

Replication can be performed in either direction or both directions (push,
pull, or both).  

  

Note:  

    The REPLSERVSTATS data structure must be initialized to zeros to get the
correct results; see example below.


 


**Parameters :**



Input :  

PortName  -   Name of the port on which to access the server.  Specify NULL to
allow Domino or Notes to use the "most available" port to the given
server.  

  

ServerName  -  Name of server to replicate with.    A hierarchical server name
needs to be specified in the abbreviated hierarchical name format (such as
ServerC/Operations/Acme).  

  

Options  -  Replication options.  These options are defined in REPL\_OPTION\_xxx
and may be bitwise or'ed together for combined functionality.  If the option
REPL\_OPTION\_ALL\_DBS is specified, all local Domino database files are added to
the list of names (if used).  If the option REPL\_OPTION\_ALL\_NTFS is specified,
all local Domino template files are added to the list of names.  If the option
REPL\_OPTION\_ALL\_FILES is specified, both database and template files are
added.  The priority flags, REPL\_OPTION\_PRI\_LOW, REPL\_OPTION\_PRI\_MED, and REPL\_OPTION\_PRI\_HI,
are only meaningful if one of the flags REPL\_OPTION\_ALL\_DBS,
REPL\_OPTION\_ALL\_NTFS, or REPL\_OPTION\_ALL\_FILES is specified.  

  

NumFiles  -  Number of files in the file list.  If no file names are specified,
this parameter should be set to 0.  

  

FileList  -  (Optional)  A pointer to the concatenated null-terminated database
filenames to replicate;  may be NULL.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Data replication succeeded.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error status as a string that you may display/log for the user.  

  

  

retStats  -   Pointer to the returned replication statistics structure.  

  




 **Sample Usage :**


memset( &retStats,
'\0', sizeof(REPLSERVSTATS) );  

error = ReplicateWithServer(


   PORTNAME,


   ServerName,   

   REPL\_OPTION\_RCV\_NOTES | REPL\_OPTION\_SEND\_NOTES,  /\* pull, push \*/  

   1,  

   DBName,  

   &retStats))


 **See Also :**


**[ReplicateWithServerExt](ReplicateWithServerExt.md)**


**[REPLSERVSTATS](REPLSERVSTATS.md)**


**[REPL\_OPTION\_xxx](REPL_OPTION_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





