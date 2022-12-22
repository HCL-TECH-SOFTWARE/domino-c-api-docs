




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




**Initial Release 5.0.7**



**Data Type : MIME**



**MIMEPARTTYPE** **-** MIME\_PART -
cPartType


**----------------------------------------------------------------------------------------------------------**



**#include
<mimeods.h>**



**Definition :**



typedef enum
tagMIMEPartType {  

    MIME\_PART\_PROLOG              = 1,  

    MIME\_PART\_BODY         = 2,  

    MIME\_PART\_EPILOG              = 3,  

    MIME\_PART\_RETRIEVE\_INFO       = 4,  

    MIME\_PART\_MESSAGE             = 5  

} MIMEPARTTYPE;


 


**Description :**



The mime
part type cPartType within the MIME\_PART structure.


 


MIME\_PART\_PROLOG                  -
Mime part type is a prolog.  

MIME\_PART\_BODY                       - Mime part type is a body.  

MIME\_PART\_EPILOG                    - Mime part type is a epilog.  

MIME\_PART\_RETRIEVE\_INFO      - Mime part type is retrieve information.  

MIME\_PART\_MESSAGE                - Mime part type is a message.


 **See Also :**


**[MIME\_PART](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0356D2E5E7B906B185256A2500412C55)**



----------------------------------------------------------------------------------------------------------


 





