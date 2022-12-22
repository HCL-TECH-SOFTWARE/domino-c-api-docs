




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



**CDACTIONRUNAGENT** **-** Run agent
action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;       /\* flags \*/  

   WORD  wAgentNameLen; /\* Agent name length \*/  

   WORD  wSpare;


/\* agent name follows
\*/  

} CDACTIONRUNAGENT;


 


**Description :**



The action
to run another Agent is stored in a CDACTIONRUNAGENT record in fields of type
TYPE\_ACTION, usually the action field of an Agent.  This record consists of
this data structure, followed by the name of the agent.  The fields in this
structure are:


 


Header                         Defines
this composite data item as a CDACTIONRUNAGENT item.


dwFlags                       Reserved; 
must be 0.


wAgentNameLen           Length
of the agent name (in bytes).


wSpare             Reserved; 
must be 0.


 


This
structure is followed by a packed string containing the agent name.


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





