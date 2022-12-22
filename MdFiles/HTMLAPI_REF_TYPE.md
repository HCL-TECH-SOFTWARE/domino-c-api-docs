




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



**HTMLAPI\_REF\_TYPE** **-** Reference
Types within a generated HTML URL


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef enum


{


            HTMLAPI\_REF\_UNKNOWN
= 0                                    /\* unknown purpose \*/


            ,HTMLAPI\_REF\_HREF
= 1                                /\* A tag HREF= value \*/


            ,HTMLAPI\_REF\_IMG
= 2                                              /\* IMG tag SRC= value \*/


            ,HTMLAPI\_REF\_FRAME
= 3                             /\* (I)FRAME tag SRC= value \*/


            ,HTMLAPI\_REF\_APPLET
= 4                            /\* Java applet reference \*/


            ,HTMLAPI\_REF\_EMBED
= 5                             /\* plugin SRC= reference \*/


            ,HTMLAPI\_REF\_OBJECT
= 6                            /\* active object DATA= referendce \*/


            ,HTMLAPI\_REF\_BASE
= 7                                /\* BASE tag value \*/


            ,HTMLAPI\_REF\_BACKGROUND
= 8                             /\* BODY BACKGROUND \*/


            ,HTMLAPI\_REF\_CID
= 9                                               /\* IMG SRC= value from MIME
message \*/


 


}
HTMLAPI\_REF\_TYPE;


 


**Description :**



Indicate the
purpose / use of the rerference. For detailed HTML reference type and its
usage, please turn to the HTML specification.


 


 **Sample Usage :**


           for ( t = 0;
t < nTargets; t++) 


               {       


                       //check
if the refer type is 2 : that is image, then use HTMLSetrRferenceText to 


                       //change
the text,


                       tgt
= pRef->pTargets[t].Target;


                       


                       switch(pRef->RefType)
{


                       case
HTMLAPI\_REF\_OBJECT:


                        //
do object processing


                              break;


                       case
HTMLAPI\_REF\_IMG:


                        //
do  image processing


                              break;


                       }


               }


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_URLComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0ECD84DE44EACDEC482571960042001D)**



----------------------------------------------------------------------------------------------------------


 





