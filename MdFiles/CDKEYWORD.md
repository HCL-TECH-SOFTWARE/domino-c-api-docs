




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



**CDKEYWORD** **-** Keyword
values for a field


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG   Header;    /\* Tag and length \*/  

   FONTID FontID;    /\* Font ID \*/  

   WORD   Keywords;  /\* number of keywords \*/  

   WORD   Flags;     /\* see CDKEYWORD\_xxx \*/  

/\* char   OnOff[];      array indicating state \*/  

/\* char   TextValues[]; packed buffer of keyword text \*/  

} CDKEYWORD;


 


**Description :**



This
structure is the header of a record containing the predefined keywords allowed
for a field (defined by a CDFIELD record).  

  

        Header       Defines this composite data item as a CDKEYWORD item.  

        FontID                    Defines the font to be used in this field. 
See FONTID.  

        Keywords   Number of keyword values  

        Flags                      If CDKEYWORD\_RADIO, only one keyword value
may be selected;  otherwise, any number  

                                     of values may be selected.  

  

This record structure is followed by an array of bytes, one byte per keyword,
indicating whether or not the corresponding keyword is enabled, '1' for On or
'0' for Off.  Following this array is a Text\_List containing the text of the
allowable keywords.


 **See Also :**


**[CDFIELD](CDFIELD.md)**


**[TYPE\_xxx [TEXT\_LIST]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA0CCEF9D263BFBB8525622E0063A01A)**


**[CDKEYWORD\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2C29EE3B03036CDD8525627B007D301E)**



----------------------------------------------------------------------------------------------------------


 





