




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Address Book;
Domino Directory**



**NAME\_xxx** **-** Options for
function NAMEGetAddressBooks().


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**


 **Symbolic Values :**      NAME\_GET\_AB\_TITLES      -  Add the title of the database to
each entry in the buffer returned by NAMEGetAddressBooks.  

  

      NAME\_DEFAULT\_TITLES    -  If NAME\_GET\_AB\_TITLES is specified then return
the database path in place of the title for any database that has no title.
NAME\_DEFAULT\_TITLES has no effect if NAME\_GET\_AB\_TITLES is not also specified.  

  

      NAME\_GET\_AB\_FIRSTONLY           -  Return only the first Address book in
use locally or Domino Directory on a server.  

  

      NAME\_GET\_MAB\_ONLY      -  Return only the name of the Directory
Assistance Database.  

  

      NAME\_GET\_ED\_ONLY        -  Get server based Enterprise Directory name
only.  

  

      NAME\_INCLUDE\_ED            -  Include server based Enterprise Directory
as the last Domino Directory.  

  

      NAME\_GET\_ALL\_EDS         -  Get All enterprise Directories.  

  

      NAME\_ADMIN\_ONLY           -  Include only NAB's that this server is the
administration server of.  

  

      NAME\_INCLUDE\_CONFIGNAB        -  Include Configuration (userless) NAB's.  

  

      NAME\_CONFIG\_ONLY         -  Include First AB that has configuration
information.  

  




**Description :**



These flags
modify the behavior of function NAMEGetAddressBooks(). The wOptions parameter
to NAMEGetAddressBooks may be zero or any combination of these flags bitwise 
OR'd together.  

  

If none of these flags are set in the wOptions parameter to
NAMEGetAddresssBooks, then the buffer returned contains a list of Address Book
database file paths.


 **See Also :**


**[NAMEGetAddressBooks](NAMEGetAddressBooks.md)**


**[OSPathNetParse](OSPathNetParse.md)**



----------------------------------------------------------------------------------------------------------


 





