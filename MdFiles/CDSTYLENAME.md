




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




 


**Data Type : Composite Data; Rich
Text**



**CDSTYLENAME** **-** Stores the
style name for a PAB


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG  Header;  

   DWORD Flags;       

   WORD  PABID;     /\* ID number of the PAB being named \*/  

   char  StyleName  /\* The style name. \*/  

         [MAX\_STYLE\_NAME+1];


/\* If
STYLE\_FLAG\_FONTID, a FONTID follows this structure... \*/


/\* If
STYLE\_FLAG\_PERMANENT, the structure is followed by:       \*/


/\*         WORD    nameLen                Length
of user name    \*/


/\*         BYTE    userName
[nameLen]     User name                     \*/  

} CDSTYLENAME;


 


**Description :**



This
structure stores the style name for a Paragraph Attributes Block (PAB).  

  

        Header              Defines this composite data item as a CDSTYLENAME
item.  

        Flags                  Optional.  May be set to 0 or to one or more of
STYLE\_FLAG\_xxx values.  

        PABID                ID number of the Paragraph Attributes Block being
named  

                                     (see CDPABDEFINITION).  

        StyleName       Style name character array.


 


If the flag
STYLE\_FLAG\_FONTID is set, the record is followed by a FONTID.


 


If
the flag STYLE\_FLAG\_PERMANENT is set, the record is followed by a word
containing the length of the user name, then the user name (padded with a null
byte if the user name is an odd length).  The user name is the name of the user
who defined this named style.


 


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[STYLE\_FLAG\_xxx](STYLE_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





