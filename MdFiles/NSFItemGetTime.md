




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




 


**Function : Item (Field)**



**NSFItemGetTime** **- Get the
value of TYPE\_TIME Item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFItemGetTime(**  

      NOTEHANDLE  note\_handle,  

      const char far \*td\_item\_name,  

      TIMEDATE far \*td\_item\_value**);**



**Description :**



This
function takes a handle to an open note and the name for the Item whose value
you wish to get.  It returns the Item in the TIMEDATE variable identified by
the pointer you provide.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

td\_item\_name  -  A pointer to a null-terminated item name.  

  




Output :  

(routine)  -  TRUE - If Item was present and successfully retrieved.  FALSE  -
if Item was not present.  

  

  

td\_item\_value  -  The address of a TIMEDATE structure in which the Domino
binary time/date retrieved from name Item in the open note is returned.  

  




 **Sample Usage :**


  

   /\* Print the TIMEDATE ITEM \*/  

  

   if (NSFItemGetTime(note1\_handle, TIME\_ITEM, &original\_td))  

   {  

       /\* Spec Time/Date string format for convert function        \*/  

       td\_format.Date = TDFMT\_FULL;   /\* show year, month, and day \*/  

       td\_format.Time = TTFMT\_FULL;   /\* show hour, minute, and sec\*/  

       td\_format.Zone = TZFMT\_ALWAYS; /\* TZ- show on at all times  \*/  

  

       td\_format.Structure = TSFMT\_DATETIME; /\* req'd. Overall Time\*/  

                                             /\* /Date structure    \*/  

       timedate\_str = &text\_buf2[0];  

       if (error\_status = ConvertTIMEDATEToText(&intl\_format,  

                                      &td\_format,  

                                      &original\_td, timedate\_str,  

                                      MAXALPHATIMEDATE, &text\_len))  

           goto Exit;  

       timedate\_str[text\_len] = '\0'; /\* provide NULL terminator \*/  

       printf("%s: %s\n", TIME\_ITEM, timedate\_str);  

   }  

  




 **See Also :**


**[NSFItemSetTime](NSFItemSetTime.md)**


**[NSFItemTimeCompare](NSFItemTimeCompare.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





