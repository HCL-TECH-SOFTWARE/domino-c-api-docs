




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



**IDIsPresent** **- Determine
if ID is present in an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



BOOL
LNPUBLIC **IDIsPresent(**  

      DHANDLE  hTable,  

      DWORD  id**);**



**Description :**



This is a
function takes a HANDLE to an ID Table and a  DWORD containing a note ID, and
returns whether the DWORD is present in the ID Table.


 


**Parameters :**



Input :  

hTable  -  A HANDLE of the ID Table.  

  

id  -  The note ID you wish to search for in the ID Table.  

  




Output :  

(routine)  -  Returns one of the following values:  

  

TRUE - ID is present in ID Table.  

FALSE - Could not find ID in ID Table.  

  

  




 **Sample Usage :**


  

   /\* Demo using one table to cleanup another - safe way \*/  

  

           notes\_scanned = 0L;  

           while(IDScan(cpytable\_handle,  

                        (FLAG)(notes\_scanned++==0L), &note\_id))  

           {  

               if (IDIsPresent(idtable\_handle, note\_id))  

               {  

                   error\_status = IDDelete(idtable\_handle,  

                                                note\_id, &ok\_flag);  

                   if (!ok\_flag || error\_status)  

                   {  

                       printf("\nIDDelete from idtable failed.\n");  

                       goto Exit;  

                   }  

               }  

           }  

  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDInsert](IDInsert.md)**


**[IDDelete](IDDelete.md)**


**[IDDeleteAll](IDDeleteAll.md)**


**[IDEnumerate](IDEnumerate.md)**


**[IDEntries](IDEntries.md)**


**[IDScan](IDScan.md)**


**[IDTableSize](IDTableSize.md)**


**[IDTableCopy](IDTableCopy.md)**


**[IDTableSize](IDTableSize.md)**



----------------------------------------------------------------------------------------------------------


 





