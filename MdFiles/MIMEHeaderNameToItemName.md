




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



**MIMEHeaderNameToItemName** **- Map an
Internet header name to a Notes item name, optionally providing additional
information about the item.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEHeaderNameToItemName(**  

      WORD  wMessageType,  

      char \*pszHeaderName,  

      char \*pszHeaderBody,  

      char \*retszItemName,  

      WORD  wItemNameSize,  

      WORD \*retwHeaderType,  

      WORD \*retwItemFlags,  

      WORD \*retwDataType**);**



**Description :**



This
function accepts an input header name and returns the corresponding Notes item
name, along with optional additional information such as the item flags and
data type.


 


You must
specify as input the message type (default: MIME\_HEADER\_MAP\_EMAIL), a pointer
to the ASCIIZ header name (e.g., "To"), an optional pointer to the
header "body" (i.e., everything after the header name, ':', space), a
pointer to an output buffer for the ASCIIZ item name, the size of the output
item name buffer (including the terminating '\0' character), an optional
pointer to the output header type, an optional pointer to the output item
flags, and an optional pointer to the output item data type.


 


Upon entry
MIMEHeaderNameToItemName writes a null byte, '\0', to the output item name
buffer, sets the output header type to MIME\_HEADER\_FORMAT\_TEXT, sets the output
item flags to 0, and sets the output data type to TYPE\_TEXT.


 


If the input
header name is a Content header --e.g., Content-Transfer-Encoding--
MIMEHeaderNameToItemName returns the Content header name with a '$' prefix
--e.g., $Content-Transfer-Encoding-- in the output item name buffer.  The
output header type and output item flags are returned with their initial values
as described above.


 


If
MIMEHeaderNameToItemName finds an item name for the input header name, it
returns the item name in the output item name buffer.  It also returns the
output header type, output item flags, and output data type that were found
with the output item name.


 


If
MIMEHeaderNameToItemName cannot find an item name for the input header name and
the input header name is 'X-Notes-Item', MIMEHeaderNameToItemName checks the
input header body pointer.  If the pointer is NULL, MIMEHeaderNameToItemName
returns the ERR\_MISC\_INVALID\_ARGS error; otherwise, it parses the header body
for the item name, returning it in the output item buffer.  In addition, it
parses the header body for the the output header type, output item flags, and
output data type, returning the parsed values.


 


 


**Parameters :**



Input :  

wMessageType  -  Type of message: MIME\_HEADER\_MAP\_XXXX  

  

pszHeaderName  -  Pointer to input ASCIIZ RFC822 header name  

  

pszHeaderBody  -  Optional pointer to ASCIIZ RFC822 header body (for processing
X-Notes-Item headers)  

  

wItemNameSize  -  Size of item name buffer (including '\0' terminator).  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the note.  

     ERR\_MISC\_INVALID\_ARGS - If input header name is X-Notes-Item and
'pszHeaderBody' is NULL.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

retszItemName  -  Pointer to output ASCIIZ item name buffer.  

  

retwHeaderType  -  Optional pointer to output header type:
MIME\_HEADER\_FORMAT\_XXXX  

  

retwItemFlags  -  Optional pointer to output item flags: ITEM\_XXXX  

  

retwDataType  -  Optional pointer to output data type: TYPE\_XXXX  

  




 **Sample Usage :**


#define MAX\_ITEM\_NAME\_LEN
32


 


char
aszItemName[MAX\_ITEM\_NAME\_LEN];


WORD wHeaderType;


WORD wItemFlags;


WORD wDataType;


STATUS error;


 


if (error =
MIMEHeaderNameToItemName(


                       MIME\_HEADER\_MAP\_EMAIL,    
// Type of Message


                       "To",                      
// RFC822 Header Name


                       NULL,                      
// Optional RFC822 Header Body (for processing X-Notes-Item headers)


                       aszItemName,               
// Return Item Name Buffer


                       MAX\_ITEM\_NAME\_LEN,         
// Size of Item Name Buffer (including '\0' terminator)


                       &wHeaderType,              
// Optional Return the Type of Header: MIME\_HEADER\_FORMAT\_XXXX


                       &wItemFlags,               
// Optional Return Item Flags: ITEM\_XXXX


                       &wDataType
)) {             // Optional Return Data Type: TYPE\_XXXX


        goto exit;


}


 


 **See Also :**


**[ITEM\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[MIMEItemNameToHeaderName](MIMEItemNameToHeaderName.md)**


**[MIME\_HEADER\_FORMAT\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/3E0A3164C4A8A7CE48257192001E43FF)**


**[MIME\_HEADER\_MAP\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/8A14513AFE614B2248257192001E11B8)**


**[TYPE\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





