




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



**CDACTIONSENDMAIL** **-** Send Mail
action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags; /\*      flags \*/


   WORD 
wFieldLen[ACTIONSENDMAIL\_FIELDCOUNT]; /\* Lengths for each of


                                                 
the fields \*/


           /\* To field
follows \*/  

           /\* cc field follows \*/  

           /\* bcc field follows \*/  

           /\* Subject field follows \*/


           /\* Body
field follows \*/  

} CDACTIONSENDMAIL;


 


**Description :**



The Send
Mail action is stored in a CDACTIONSENDMAIL record in fields of type
TYPE\_ACTION, usually the action field of an Agent.  The fields in this
structure are:


 


Header    
SIG\_ACTION\_SENDMAIL and total record length


dwFlags   
ACTIONSENDMAIL\_FLAG\_xxx flags


wFieldLen  Array of
lengths for the send mail fields


 


This record
is followed by the string values for the send mail fields.  These strings are **not**
in packed format;  each string has a NUL terminator, and may contain a padding
byte if necessary to make the length an even number of bytes.  The strings
contain:


 


To                    Recipient
list


Cc                    Courtesy
copy recipient list


Bcc                  "Blind"
courtesy copy recipient list


Subject             Message
subject


Body                Message
body


 


 **See Also :**


**[ACTIONSENDMAIL\_FLAG\_xxx](ACTIONSENDMAIL_FLAG_xxx.md)**


**[ACTIONSENDMAIL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DD2064848CFADF3285256261004FD244)**



----------------------------------------------------------------------------------------------------------


 





