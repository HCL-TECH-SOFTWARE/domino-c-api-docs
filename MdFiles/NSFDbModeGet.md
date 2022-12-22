




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




 


**Function : Database**



**NSFDbModeGet** **- Check if
DBHANDLE refers to database or a directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbModeGet(**  

      DBHANDLE  hDB,  

      USHORT far \*retMode**);**



**Description :**



This
function takes a DBHANDLE as input and returns a pointer to a USHORT that
specifies whether the handle is associated with a database or with a
directory.  It returns DB\_LOADED in the specified USHORT if the DBHANDLE is a
handle to a database or DB\_DIRECTORY if the DBHANDLE is a handle to a directory.  

  

Use this function to find out whether the DBHANDLE returned by NSFDbOpen() is a
handle to a database or a handle to a directory.


 


**Parameters :**



Input :  

hDB  -  The handle to the database or directory.  

  




Output :  

(routine)  -  Return status from this call.  A successful call returns NOERROR.  

  

  

retMode  -  The address of a USHORT that receives the database mode, DB\_LOADED
or DB\_DIRECTORY, as defined by DB\_xxx (NSFDbModeGet).  

  




 **Sample Usage :**


if (Error = NSFDbModeGet
(hDB, &usMode))  

{  

    fprintf (stderr, "Error: unable to get database mode.\n");  

    return (ERR(Error));  

}  

if (usMode & DB\_LOADED) /\* hDB refers to a normal database file \*/  

{  

    ;                   /\* this is what we expect: no output needed \*/  

}  

else if (usMode & DB\_DIRECTORY) /\* hDB refers to a directory  \*/  

{  

    fprintf (stderr, "Error: '%s' is a directory, not a file.\n",  

                                szFilename);  

    return (ERR(Error));  

}


 **See Also :**


**[NSFDbOpen](NSFDbOpen.md)**



----------------------------------------------------------------------------------------------------------


 





