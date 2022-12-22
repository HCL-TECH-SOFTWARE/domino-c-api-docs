




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



**CDACTIONMODIFYFIELD** **-** Modify Field
action CD Record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG Header;  

   DWORD dwFlags;      /\* flags MODIFYFIELD\_FLAG\_xxx \*/  

    WORD wFieldNameLen; /\* Length of field name to modify \*/  

    WORD wValueLen;     /\* Length of new value \*/


           /\* Field
name follows \*/


           /\* Value
follows \*/  

} CDACTIONMODIFYFIELD;


 


**Description :**



A
CDACTIONMODIFYFIELD record is stored in fields of type TYPE\_ACTION, usually the
action field of an Agent.  When the agent containing this action is run, the
value of the specified field is modified in the notes selected by the Agent. 
The fields in this structure are:


 


Header         Defines
this composite data item as a


              
CDACTIONMODIFYFIELD item.


dwFlags        Option
flags (see MODIFYFIELD\_FLAG\_xxx)


wFieldNameLen  Length
of the field name.


wValueLen      Length
of the new value.


 


This structure
is followed by packed strings containing the field name and the new value for
the field.


 


 **See Also :**


**[MODIFYFIELD\_FLAG\_xxx](MODIFYFIELD_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





