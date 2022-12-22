




<!--
 /\* Font Definitions \*/
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



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDEDITCTL** **-** Specifies an
embedded edit control.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      WSIG               Header; /\* Signature and length of this record. \*/  

      DWORD           Flags;  

      WORD             NameLength;


            WORD
                        SpareWORD[5];  

            DWORD           SpareDWORD[11];


            }
CDEMBEDDEDEDITCTL;


 


**Description :**



This CD
record defines an embedded element of type 'editor'. It is preceded by a
CDHOTSPOTBEGIN and a CDPLACEHOLDER. The CD record, CDPLACEHOLDER, further
defines the CDEMBEDDEDEDITCTL. The fields in this record are:


 


      Header
- Signature and Length of this CD record.


      Flags
- Embedded edit control flags, see EMBEDDEDEDITCTL\_FLAG\_xxx.


      NameLength
- Length of the optional embedded editor name. 


      SpareWord
- Reserved for future use.


      SpareDWord
-  Reserved for future use.


 


These fields
are followed by the optional embedded editor name. If you plan to use it, you
will need to declare the variable and assign a value to its length.


 


 **See Also :**


**[EMBEDDEDEDITCTL\_FLAG\_xxx](EMBEDDEDEDITCTL_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





