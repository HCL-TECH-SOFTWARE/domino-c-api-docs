




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




 


**Symbolic Value : OLE**



**OLEREC\_FLAG\_xxx** **-** OLE object
definition flags.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      OLEREC\_FLAG\_OBJECT     -  The data is an OLE embedded
object.  

  

      OLEREC\_FLAG\_LINK           -  The data is an OLE link.  

  

      OLEREC\_FLAG\_AUTOLINK             -  If this is a link, it is an Automatic
(hot) link.  

  

      OLEREC\_FLAG\_MANUALLINK         -  If this is a link, it is a Manual
(warm) link.  

  

      OLEREC\_FLAG\_NEWOBJECT         -  This is a new object that was just
inserted into the note.  

  

      OLEREC\_FLAG\_PASTED     -  This is a new object that was just pasted into
the note.  

  

      OLEREC\_FLAG\_SAVEOBJECTWHENCHANGED     -  This object came from a form and
should be saved every time it changes in the server.  

  

      OELREC\_FLAG\_NOVISUALIZE        -  This object was inherited from a form,
or object incapable of rendering itself, so don't visualize it.  

  




**Description :**



These flags
are used to define the type of OLE object a note contains.  These flags are
used by the Flags member of the CDOLEBEGIN data structure.


 **See Also :**


**[CDOLEBEGIN](CDOLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





