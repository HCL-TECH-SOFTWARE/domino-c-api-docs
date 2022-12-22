




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



**NAME\_LOOKUP\_xxx** **-** Flags to
control NAMELookup function


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**


 **Symbolic Values :**      NAME\_LOOKUP\_ALL           -  Return all entries in the view  

  

      NAME\_LOOKUP\_NOSEARCHING    -  Only look in first Address book containing
desired view for specified names  

  

      NAME\_LOOKUP\_EXHAUSTIVE        -  Search ALL Address books, not just the
first Address book that contains a match.  

  

      NAME\_LOOKUP\_UPDATE   -  Force the namespaces (views) to be made current.  

  




**Description :**



**Note:**Address books refer to both the Notes Client Address books, and
Domino Directories (the Domino Server Address books).


 


       These
flags modify the behavior of the NAMELookup() function. Specify any combination
of these flags bitwise OR-ed together in the Flags parameter to NAMELookup().  

  

When Flags is zero, NAMELookup() searches for each specified name in each
specified view across all the  Address books in use. It returns information
about all the matching names in all the specified views in the first Address
book containing a match.  

  

If the NAME\_LOOKUP\_ALL bit is set in Flags, NAMELookup() returns information
about all the names in each specified view rather than just the specified
names. Use this flag to obtain, for example, a list of all the full names of
all person records in the $Users view of the first Address book.  

  

If the NAME\_LOOKUP\_NOSEARCHING bit is set in Flags, NAMELookup only searches
the first Address book containing each desired view. If it does not find a name
in the specified view in the first database containing that view, it skips to
the next name rather than proceeding to search the next  Address book. Note
that this flag does not stop NAMELookup from searching past the first Address
book in the list - just the first one containing the desired view.


  

If the NAME\_LOOKUP\_EXHAUSTIVE bit is set in Flags, NAMELookup() returns
information about all the matching names in all the specified views in ALL
Address books containing a match.


 


        If
the NAME\_LOOKUP\_UPDATE bit is set in Flags, NAMELookup() forces updated views.


 **See Also :**


**[NAMELookup](NAMELookup.md)**



----------------------------------------------------------------------------------------------------------


 





