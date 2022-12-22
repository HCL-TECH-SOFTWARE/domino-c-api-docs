




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



**Data Type : Character Manipulation**



**NLS\_STATUS** **-** Return code
type for National Language Services (NLS) C API functions.


**----------------------------------------------------------------------------------------------------------**



**#include
<nls.h>**



**Definition :**



typedef    WORD    NLS\_STATUS;


 


**Description :**



There are
several C API functions that return values of type NLS\_STATUS. A return value
of NLS\_SUCCESS indicates that the function completed successfully. The value of
NLS\_SUCCESS is 0.


 


Example:  

if (error = NLSFunction(...))  

     return (error);


 


The C API
defines various non-zero NLS\_STATUS values, or error codes, that are returned
by C API functions in response to various error conditions. Specific NLS\_STATUS
error codes are defined in the C API header file nls.h.


 **See Also :**


**[NLS\_find](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/50155DCE368D5A4B8525624A0060868C)**


**[NLS\_find\_substr](NLS_find_substr.md)**


**[NLS\_get](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1215FF5891D679FF852561C00079B596)**


**[NLS\_isalnum](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9B0DEB96658335578525624A0060DA94)**


**[NLS\_isalpha](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/47DB676D04D6779B8525623600583E55)**


**[NLS\_isarith](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/89BC757CE8E60F5C85256236005708AE)**


**[NLS\_iscntrl](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/732A1DC3535E76DC8525623600585FE1)**


**[NLS\_isdigit](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AC23F12FD99C7859852562360058614C)**


**[NLS\_isleadbyte](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9F81710E22AD976385256236005862AA)**


**[NLS\_islower](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D0F08625A57833F08525623600628F61)**


**[NLS\_ispunct](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5D3BA25EF320EC31852562360058658B)**


**[NLS\_isspace](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0E3C8C2005C054EE8525623600586435)**


**[NLS\_isupper](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BEEE73E750EFAD3785256236005866FB)**


**[NLS\_load\_charset](NLS_load_charset.md)**


**[NLS\_put](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85E1A3E0216850CB8525624A00613369)**


**[NLS\_put\_term](NLS_put_term.md)**


**[NLS\_string\_bytes](NLS_string_bytes.md)**


**[NLS\_string\_chars](NLS_string_chars.md)**


**[NLS\_translate](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/155C97DCEEF0C3EE8525662800461D66)**


**[NLS\_unload\_charset](NLS_unload_charset.md)**



----------------------------------------------------------------------------------------------------------


 





