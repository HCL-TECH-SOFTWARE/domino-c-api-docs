




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




 


**Function : Views**



**NIFFindDesignNoteByName** **- \*
OBSOLETE \* Calls NIFFindDesignNote with the Class argument set to
NOTE\_CLASS\_ALL.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindDesignNoteByName(**  

      DBHANDLE  hFile,  

      char \*Name,  

      NOTEID \*retNoteID**);**



**Description :**



This is a
macro that calls NIFFindDesignNote with the Class argument set to
NOTE\_CLASS\_ALL.  If there are more than one form, view, helpindex, macro,
field, or replication formula note with the given name, only the first one
found is returned.  

  

This function provides compatibility for applications prior to version 3.0 of
the API.  Otherwise, this function is obsolete.  Use NIFFindDesignNote or
NIFFindView instead.


 


**Parameters :**



Input :  

hFile  -  Handle to the database.  

  

Name  -  A pointer to a null-terminated character string, that holds the name
of the form, view, helpindex, macro, field, or replication formula note, you
want to find.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_NOT\_FOUND  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retNoteID  -  Pointer to the returned NOTEID.  

  




 **Sample Usage :**


/\* This code fragment
shows how to get a collection of  

the notes in a view, given the view's name. \*/  

  

          if (error = NIFFindDesignNoteByName(  

                   hDB,   

                   szViewName,   

                   &ViewID))  

           return(error);  

  

           if (error = NIFOpenCollection(  

                                   hDB,     

                                   hDB,       

                                  ViewID,   

                                   0,                 

                                  NULLHANDLE,        

                          &hCollection,    

                                  NULL,               

                                  NULL,            

                                   NULL,            

                                  NULL))    

                    return(error);  

  

  




 **See Also :**


**[NIFFindDesignNote](NIFFindDesignNote.md)**


**[NIFFindView](NIFFindView.md)**



----------------------------------------------------------------------------------------------------------


 





