




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




**Initial Release 6**



**Data Type : Agents**



**SCRIPTCONTEXTDESCR** **-** Structure
for passing LotusScript context information.


**----------------------------------------------------------------------------------------------------------**



**#include
<agents.h>**



**Definition :**



typedef struct {


    DWORD Length;


    char 
szNameOfContextClass[MAXIMUM\_ID\_NAME\_LENGTH + 1];


}SCRIPTCONTEXTDESCR;


 


**Description :**



This
structure is used to pass the LotusScript context information to the
AgentLSTextFormat API.  Following are the name of the context class assigned
for each LotusScript context:


 




|  |  |
| --- | --- |
| **If the LotusScript was contained in:**  | **Specify the following text as "szNameOfContextClass":** |
| Form | NOTESUIDOCUMENT |
| Page | NOTESUIDOCUMENT |
| Subform | NOTESUIDOCUMENT |
| View | NOTESUIVIEW |
| Action | BUTTON |
| Field | FIELD |
| Database
 Script | NOTESUIDATABASE |


 


 


 **Sample Usage :**


Here is the
code snippet for filling up the SCRIPTCONTEXTDESCR structure if a LotusScript
was contained in a button:


 



SCRIPTCONTEXTDESCR
\* pSCD;


           
HANDLE hData = NULLHANDLE;


 


          
error = OSMemAlloc(0,sizeof(SCRIPTCONTEXTDESCR),&hData);


          
pSCD = OSLock(SCRIPTCONTEXTDESCR,hData);


 


          
pSCD->Length = sizeof(SCRIPTCONTEXTDESCR);


          
strcpy(pSCD->szNameOfContextClass, "BUTTON" );


 


          
OSUnlock( hData);


 


          
AgentLSTextFormat( hSrc, &hDest, &hErrs, dwFlags, &hData ); 


            


 **See Also :**


**[AgentLSTextFormat](AgentLSTextFormat.md)**



----------------------------------------------------------------------------------------------------------


 





