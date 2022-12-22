




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




**Initial Release 5.0**



**Symbolic Value : Constants; Rich
Text**



**CDRESOURCE\_FLAGS\_xxx** **-** Flags
defined in a CDRESOURCE.


**----------------------------------------------------------------------------------------------------------**



**#include <rsrcods.h>**


 **Symbolic Values :**      CDRESOURCE\_FLAGS\_FORMULA              -  The type's data is
a formula valid for CDRESOURCE\_TYPE\_URL and CDRESOURCE\_TYPE\_NAMEDELEMENT.  

  

      CDRESOURCE\_FLAGS\_NOTELINKINLINE   -  The notelink variable length data
contains the notelink itself - not an index into a $Links items.  

  

      CDRESOURCE\_FLAGS\_ABSOLUTE            -  If specified, the link is to an
absolute database or thing. Used to make a hard link to a specific DB.  

  

      CDRESOURCE\_FLAGS\_USEHINTFIRST     -  If specified, the server and file
hint are filled in and should be attempted before trying other copies.  

  

      CDRESOURCE\_FLAGS\_CANNEDIMAGE     -  The type's data is a canned image
file (data/domino/icons/[\*].gif) valid for CDRESOURCE\_TYPE\_URL &&
CDRESOURCE\_CLASS\_IMAGE only.  

  

      CDRESOURCE\_FLAGS\_PRIVATE\_DATABASE        -  The object is private in its
database.  

NOTE: CDRESOURCE\_FLAGS\_PRIVATE\_DATABASE and CDRESOURCE\_FLAGS\_PRIVATE\_DESKTOP
are mutually exclusive.  

  

      CDRESOURCE\_FLAGS\_PRIVATE\_DESKTOP          -  The object is private in the
desktop database.  

NOTE: CDRESOURCE\_FLAGS\_PRIVATE\_DATABASE and CDRESOURCE\_FLAGS\_PRIVATE\_DESKTOP
are mutually exclusive.  

  

      CDRESOURCE\_FLAGS\_REPLICA\_WILDCARD        -  The replica in the CD
resource  

  

      CDRESOURCE\_FLAGS\_SIMPLE      -  Used with class view and folder to mean
"Simple View"  

  

      CDRESOURCE\_FLAGS\_DESIGN\_MODE     -  Open this up in design mode.  

  

      CDRESOURCE\_FLAGS\_RESERVED1          -  Reserved meaning for each resource
link class.  

  

      CDRESOURCE\_FLAGS\_RESERVED2          -  Reserved meaning for each resource
link class.  

  

      CDRESOURCE\_FLAGS\_RESERVED3          -  Reserved meaning for each resource
link class.  

  

      CDRESOURCE\_FLAGS\_RESERVED4          -  Reserved meaning for each resource
link class.  

  




 **See Also :**


**[CDRESOURCE](CDRESOURCE.md)**



----------------------------------------------------------------------------------------------------------


 





