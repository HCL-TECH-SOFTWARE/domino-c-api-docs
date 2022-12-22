




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




**Initial Release 4.6**



**Data Type : Agents; Composite Data**



**CDACTIONJAVAAGENT** **-** Java agent
action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   WORD  wClassNameLen;  /\* Agent name length \*/  

   WORD  wCodePathLen;  

   WORD  wFileListBytes;  

   WORD  wLibraryListBytes;  

   WORD  wSpare[1];  

   DWORD dwSpare[1];  

/\* Strings follow \*/  

} CDACTIONJAVAAGENT;


 


**Description :**



A
CDACTIONJAVAAGENT record is stored in fields of type TYPE\_ACTION, usually the
action field of an Agent.  This record identifies the Java class files that
will be executed when the agent is run.  The fields in this structure are:


 


Header                               Defines
this composite data item as a CDACTIONJAVAAGENT item.


wClassNameLen                 Length
of the Java class name (the class to be invoked).


wCodePathLen                    Length
of the Java code pathname.


wFileListBytes                    Length
of the Java class file list.


wLibraryListBytes               Length
of the shared Java Library list.


 


This
structure is followed by the three strings, stored asLMBCS strings with no NULL
delimiter.  The Java class files are stored as $FILE items in the document; 
the Java class file name is the file name of the $FILE item.


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





