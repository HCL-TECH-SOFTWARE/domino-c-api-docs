




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



**Data Type : Backup**



**NOTE\_RESTORE\_CALLBACK\_INFO** **-** Note restore
callback information structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef struct {


        WORD           InfoSize;      /\*
Size of this structure, use this to determine 


                                        
if future fields are avail \*/ 


        NOTEID         NoteId; /\*
NoteID for note being altered \*/


        NOTEHANDLE     hNote;  /\*
Handle to note being retrieved \*/


        TIMEDATE       TranTime;      /\*
Time the transaction ran for which you are being called \*/


        char
far\*      UserName;      /\* If avail, else a pointer to "" \*/


        char
far\*      PathName;      /\* Path & file name of DB \*/


}
NOTE\_RESTORE\_CALLBACK\_INFO;


 


**Description :**



Information
structure to be used with NOTERESTORECALLBACKFUNCTION.


 **See Also :**


**[NOTERESTORECALLBACKFUNCTION](NOTERESTORECALLBACKFUNCTION.md)**



----------------------------------------------------------------------------------------------------------


 





