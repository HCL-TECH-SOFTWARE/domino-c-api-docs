




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




 


**Function : ID Table**



**IDDeleteAll** **- Deletes
all IDs from an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDDeleteAll(**  

      DHANDLE  hTable**);**



**Description :**



This
function takes a handle to an ID Table and deletes all the IDs in it.


 


**Parameters :**



Input :  

hTable  -  A handle to the ID Table.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - If deletion and memory release of the IDs was successful.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


  

                if (IDEntries(deltable\_handle))  

   

               {   /\* Using NULL in 3rd arg avoids ERR\_REMOTE\_UNID \*/  

  

                    if (error\_status = NSFDbDeleteNotes (  

                                            db\_handle\_src,  

                                            deltable\_handle,  

                                            NULL))  

                        goto Exit;  

  

                    /\* adjust del\_count exit of while(IDScan) \*/  

  

                    printf("\n%s: %lu Notes in %s\n",  

                           (del\_count <= del\_max)? "Deleting"  

                                                 : "Deleted",  

                           (del\_count <= del\_max)? 50  

                                                 : del\_count-1,  

                           src\_name);  

                    if (error\_status = IDDeleteAll(deltable\_handle))  

                        goto Exit;  

                }  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDDelete](IDDelete.md)**


**[IDEntries](IDEntries.md)**


**[IDEnumerate](IDEnumerate.md)**


**[IDInsert](IDInsert.md)**


**[IDIsPresent](IDIsPresent.md)**


**[IDScan](IDScan.md)**


**[IDTableCopy](IDTableCopy.md)**


**[IDTableSize](IDTableSize.md)**



----------------------------------------------------------------------------------------------------------


 





