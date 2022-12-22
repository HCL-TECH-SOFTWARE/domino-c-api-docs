




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



**CDDECSFIELD** **-** Pertains to
data connection resource information in a field or form.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct {  

      WSIG   Header;  

      WORD Flags;  

      WORD ExternalNameLength;  

      WORD MetadataNameLength;  

      WORD DCRNameLength;  

      WORD Spare[8];  

} CDDECSFIELD;


 


 


**Description :**



This CD
Record gives information pertaining to data connection resource information in
a field or form. The fields in this structure are:  

  




Header -
Defines this composite data item as a CDDECSFIELD item.


  

Flags - see FDECS\_xxx 


 


ExternalNameLength
- Length of external field name when external data source is used 


  

MetadataNameLength - Metadata object name length   

  




DCRNameLength
- Data Connection Resource name length   

  




Spare[8] -
Reserved for future use


 


These fields
may be followed by optional items. If you plan to use them, you will need to
declare the variables and assign values to their lengths.


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical conversion
on CD record structures such as this when accessing rich text item data in a
note. 


 **See Also :**


**[FDECS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7EAFC57D96A5604C8525697D00670E90)**



----------------------------------------------------------------------------------------------------------


 





