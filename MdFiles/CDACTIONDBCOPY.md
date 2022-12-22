




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.0**



**Data Type : Agents; Composite Data**



**CDACTIONDBCOPY** **-** Database
Copy action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;      /\* flags \*/  

   WORD  wServerLen;   /\* length of server name \*/  

   WORD  wDatabaseLen; /\* length of database filespec \*/


           /\* server
name follows \*/  

           /\* database filespec follows \*/  

} CDACTIONDBCOPY;


 


**Description :**



A
CDACTIONDBCOPY record is stored in fields of type TYPE\_ACTION, usually the
action field of an Agent.  When the agent containing this action is run, a copy
of the data selected by the agent is placed in the named database.  The fields
in this structure are:


 


Header             Defines
this composite data item as a CDACTIONDBCOPY item.


dwFlags           Option
flags (see ACTIONDBCOPY\_FLAG\_xxx)


wServerLen      Length
of the server name


wDatabaseLen  Length
of the database name


 


This
structure is followed by packed strings containing the server name and database
name.


 **See Also :**


**[ACTIONDBCOPY\_FLAG\_xxx](ACTIONDBCOPY_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





