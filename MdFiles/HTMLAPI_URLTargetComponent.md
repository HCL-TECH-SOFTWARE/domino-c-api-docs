




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



**HTMLAPI\_URLTargetComponent** **-** Structure
used to hold URL target component.


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef
struct


{


            UAT     AddressableType;
        /\* the kind of note object the component refers to \*/


            URT     ReferenceType; /\*
the value type of the component -- determines


                                                              
the branch of the following union to use \*/


            union


            {


                        char                 \*name;             /\*
text name of an object \*/


                        UNID                unid;                 /\*
unique note id \*/


                        NOTEID                       nid;                   /\*
note id \*/


                        USV                 special; /\*
a special value \*/


                        DBID                dbid;                 /\*
database id \*/


            }
Value;


}
HTMLAPI\_URLTargetComponent;


 


 


**Description :**



The
HTMLAPI\_URLTargetComponent is a part of HTMLAPIReference, please see below
picture. When get the HTMLAPIReference from a translated HTML text, you can
make analysis by judging the type of this HTMLAPI\_URLTargetComponent, and then
take your actions according to difference type. 


 


![](HTMLAPI_URLTargetComponent_files/image001.png)


 **Sample Usage :**


see samples
html/convattach, html/convsection


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_URLComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0ECD84DE44EACDEC482571960042001D)**



----------------------------------------------------------------------------------------------------------


 





