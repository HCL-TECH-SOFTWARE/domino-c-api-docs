




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



**Function : MIME**



**MIMEItemNameToHeaderName** **- Map a
Notes item name name to an Internet header, optionally providing additional
information about the item.** 


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEItemNameToHeaderName(**  

      WORD  wMessageType,  

      char \*pszItemName,  

      char \*retszHeaderName,  

      WORD  wHeaderNameSize,  

      WORD \*retwHeaderType**);**



**Description :**



This
function accepts a Notes item name input and returns the corresponding header
name, along with optional additional information.


 


You must
specify as input the message type (default: MIME\_HEADER\_MAP\_EMAIL), a pointer
to the ASCIIZ item name (e.g., "SendTo"), a pointer to an output
buffer for the ASCIIZ header name, the size of the output header name buffer
(including the terminating '\0' character), and an optional pointer to the
output header type.


 


Upon entry
MIMEItemNameToHeaderName sets the return header type to
MIME\_HEADER\_FORMAT\_TEXT.


 


If
MIMEItemNameToHeaderName finds an header name for the input item name, it
returns the header name in the output item name buffer and the header type the
output header type.


 


If
MIMEItemNameToHeaderName cannot find a header name for the input item name, it
sets the output header name to "X-Notes-Item".


 


 


**Parameters :**



Input :  

wMessageType  -  Type of RFC822 Message  

  

pszItemName  -  Notes Item Name to Convert  

  

wHeaderNameSize  -  Size of RFC822 Header Name Buffer  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the note.  

     ERR\_MISC\_RETURN\_TRUNC - Error returned if the output header name was
truncated.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retszHeaderName  -  Return RFC822 Header Name Buffer.  

  

retwHeaderType  -  Optional Return the Type of Header.  

  




 **Sample Usage :**


#define
MAX\_HEADER\_NAME\_LEN 32


 


char
aszHeaderName[MAX\_HEADER\_NAME\_LEN];


WORD wHeaderType;


STATUS error;


 


if (error =
MIMEItemNameToHeaderName(


                       MIME\_HEADER\_MAP\_EMAIL,    
// Type of Message


                       "SendTo",                  
// Item Name


                       aszHeaderName,             
// Return Header Name Buffer


                       MAX\_HEADER\_NAME\_LEN,       
// Size of Header Name Buffer (including '\0' terminator)


                       &wHeaderType
)) {           // Optional Return the Type of Header: MIME\_HEADER\_FORMAT\_XXXX


        goto exit;


}


 


 **See Also :**


**[MIMEHeaderNameToItemName](MIMEHeaderNameToItemName.md)**


**[MIME\_HEADER\_FORMAT\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/3E0A3164C4A8A7CE48257192001E43FF)**


**[MIME\_HEADER\_MAP\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/8A14513AFE614B2248257192001E11B8)**



----------------------------------------------------------------------------------------------------------


 





