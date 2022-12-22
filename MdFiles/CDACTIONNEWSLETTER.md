




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



**CDACTIONNEWSLETTER** **-** Generate
Newsletter action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;      /\* flags \*/  

   DWORD dwGather;     /\* gather at least n documents \*/  

   WORD  wViewNameLen; /\* View to use to display data \*/  

   WORD  wSpare;  

   WORD  wFieldLen[ACTIONSENDMAIL\_FIELDCOUNT];


           /\* View name
follows \*/  

           /\* To field follows \*/  

           /\* cc field follows \*/  

           /\* bcc field follows \*/  

           /\* Subject field follows \*/


           /\* Body
field follows \*/  

} CDACTIONNEWSLETTER;


 


**Description :**



A
CDACTIONNEWSLETTER record is stored in fields of type TYPE\_ACTION, usually the
action field of an Agent.  When the agent containing this action is run, a
"newsletter" is generated.  A newsletter consists of a doclink to
each note identified by the query segment of this Agent.  The fields in this
structure are:


 


Header             Defines
this composite data item as a CDACTIONNEWSLETTER item.


dwFlags           Option
flags (see ACTIONNEWSLETTER\_FLAG\_xxx).


dwGather          Minimum
number of documents to gather.


wViewNameLen 
Length, in bytes, of the name of the view used to display the data


wSpare             Reserved; 
must be 0.


wFieldLen         Array
of lengths for the send mail fields


 


This record
is followed by the string values for the view name and the send mail fields, in
packed format (no NULL terminators).  The strings contain:


 


ViewName        Name
of view used to display the data


To                    Recipient
list


cc                    Courtesy
copy recipient list


bcc                   "Blind"
courtesy copy recipient list


Subject             Message
subject


Body                Message
body


 


**Note:**  Newsletter
formula flags are the same as sendmail flags, so do not use the
ACTIONSENDMAIL\_FLAG\_xxx flag values for newsletter flags.


 **See Also :**


**[ACTIONNEWSLETTER\_FLAG\_xxx](ACTIONNEWSLETTER_FLAG_xxx.md)**


**[ACTIONSENDMAIL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DD2064848CFADF3285256261004FD244)**



----------------------------------------------------------------------------------------------------------


 





