




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




**Initial Release 7.0.2**



**Data Type : HTML**



**HTMLAPI\_URLArg** **-** Structure
used to hold a URL argument value.


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef
struct


{


            CmdArgID                                Id;                    /\*
CmdArgID identifier \*/


            CmdArgValueType                    Type;               /\*
type of target or arg value (e.g., CAVT\_String, CAVT\_Int, etc.) \*/


            union


            {


                        int                    n;                                 /\*
When Type == CAVT\_Int,                  value as int \*/


                        NOTEID                       nid;                               /\*
When Type == CAVT\_NoteId, value as NOTEID \*/


                        UNID                unid;                             /\*
When Type == CAVT\_UNID,              value as UNID \*/


                        char                 \*s;                                /\*
When Type == CAVT\_String, value as nul-terminated string \*/


                        struct                                                   /\*
When Type == CAVT\_StringList,value is list of NULL terminated strings. \*/


                        {


                                    DWORD
count; /\* number of strings in the list - 0 indicates empty list ('first' is
undefined) \*/


                                    char
\*first;        /\* pointer to first string in list - undefined if count==0 \*/


                        }
slist;


            }
Value;


 


}
HTMLAPI\_URLArg;


 


**Description :**




The HTMLAPI\_URLArg is a part
of HTMLAPIReference, please see below picture. When get the HTMLAPIReference
from a translated HTML text, you can make analysis by judging the type of this
HTMLAPI\_URLArg, and then take your actions according to difference type. 


 


![](HTMLAPI_URLArg_files/image001.png)


 


 **Sample Usage :**


see sample
html/convattach


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_URLComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0ECD84DE44EACDEC482571960042001D)**



----------------------------------------------------------------------------------------------------------


 





