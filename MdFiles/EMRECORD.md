




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



**Data Type : Extension Manager**



**EMRECORD** **-** Data
structure passed to EMHANDLER callback functions.


**----------------------------------------------------------------------------------------------------------**



**#include
<extmgr.h>**



**Definition :**



typedef struct {  

   EID        EId;              /\* identifier \*/  

   WORD       NotificationType; /\* EM\_BEFORE or EM\_AFTER \*/  

   STATUS     Status;           /\* core error code \*/  

   VARARG\_PTR Ap;               /\* ptr to args \*/  

} EMRECORD;


 


**Description :**



This
structure contains context information provided by the extension manager
facility.  Information in the structure identifies the operation being
performed and provides access to the arguments of the Domino or Notes core
function.


 


The fields
in this structure are:


 


EId -
Extension manager ID code for the core function call;  see EM\_xxx for a list of
function codes.


 


NotificationType
- This field will be set to EM\_BEFORE if the callback function is being called
before the operation is attempted, or EM\_AFTER if the callback function is
being called after the operation is completed.


 


Status - If
the NotificationType is EM\_AFTER, this field contains the status value from the
core operation.


 


Ap - Pointer
to the argument list provided to the core function.  The format of the argument
list depends on the actual function.  These parameters may be accessed using
the variable argument macros;  see VARARG\_PTR for more information.


 **See Also :**


**[EID](EID.md)**


**[EMHANDLER](EMHANDLER.md)**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[VARARG\_PTR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8B0E9C0C9F111F58525624200614B5E)**



----------------------------------------------------------------------------------------------------------


 





