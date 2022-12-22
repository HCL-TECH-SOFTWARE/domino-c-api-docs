




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




 


**Symbolic Value : Rich Text**



**TPL\_FLAG\_xxx** **-** Flags
defined for the FormFlags, FormFlags2 or FormFlags3 members of the CDDOCUMENT
data structure.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      TPL\_FLAG\_REFERENCE     -  FormFlags - Use Reference Note.  

  

      TPL\_FLAG\_MAIL      -  FormFlags - Documents should be mailed when they
are saved.  

  

      TPL\_FLAG\_NOTEREF          -  FormFlags - Add note reference to
"reference note".  

  

      TPL\_FLAG\_NOTEREF\_MAIN           -  FormFlags - Add note reference to main
parent of "reference note".  

  

      TPL\_FLAG\_RECALC            -  FormFlags - When leaving a field,
recalculate its value.  

  

      TPL\_FLAG\_BOILERPLATE   -  FormFlags - Store the form used to compose the
note within the note.  

  

      TPL\_FLAG\_FGCOLOR         -  FormFlags - Use the foreground color to
paint.  

  

      TPL\_FLAG\_SPARESOK       -  FormFlags - Spare DWORDS have been zeroed.  

  

      TPL\_FLAG\_ACTIVATE\_OBJECT\_COMP      -  FormFlags - Activate OLE objects
when composing a new note.  

  

      TPL\_FLAG\_ACTIVATE\_OBJECT\_EDIT        -  FormFlags - Activate OLE objects
when editing an existing note.  

  

      TPL\_FLAG\_ACTIVATE\_OBJECT\_READ       -  FormFlags - Activate OLE objects
when reading an existing note.  

  

      TPL\_FLAG\_SHOW\_WINDOW\_COMPOSE    -  FormFlags - Show editor window if the
flag TPL\_FLAG\_ACTIVATE\_OBJECT\_COMP is set.  

  

      TPL\_FLAG\_SHOW\_WINDOW\_EDIT             -  FormFlags - Show editor window
if the flag TPL\_FLAG\_ACTIVATE\_OBJECT\_EDIT is set.  

  

      TPL\_FLAG\_SHOW\_WINDOW\_READ            -  FormFlags - Show editor window if
the flag TPL\_FLAG\_ACTIVATE\_OBJECT\_READ is set.  

  

      TPL\_FLAG\_UPDATE\_RESPONSE    -  FormFlags - V3 Updates to this note become
responses to it.  

  

      TPL\_FLAG\_UPDATE\_PARENT         -  FormFlags - V3 Updates to this note
become its parent.  

  

      TPL\_FLAG\_INCLUDEREF    -  FormFlags2 - insert copy of ref note  

  

      TPL\_FLAG\_RENDERREF     -  FormFlags2 - render ref (else it's a doclink)  

  

      TPL\_FLAG\_RENDCOLLAPSE           -  FormFlags2 - render it collapsed?  

  

      TPL\_FLAG\_EDITONOPEN   -  FormFlags2 - edit mode on open  

  

      TPL\_FLAG\_OPENCNTXT     -  FormFlags2 - open context panes  

  

      TPL\_FLAG\_CNTXTPARENT             -  FormFlags2 - context pane is parent  

  

      TPL\_FLAG\_MANVCREATE   -  FormFlags2 - manual versioning  

  

      TPL\_FLAG\_UPDATE\_SIBLING         -  FormFlags2 - updates are sibblings  

  

      TPL\_FLAG\_ANONYMOUS    -  FormFlags2 - V4 Anonymous form  

  

      TPL\_FLAG\_NAVIG\_DOCLINK\_IN\_PLACE     -  FormFlags2 - Doclink dive into
same window  

  

      TPL\_FLAG\_INTERNOTES    -  FormFlags2 - InterNotes special form  

  

      TPL\_FLAG\_DISABLE\_FX      -  FormFlags2 - Disable FX for this doc  

  

      TPL\_FLAG\_NOMENUS         -  FormFlags2 - Disable menus for this doc  

  

      TPL\_FLAG\_CHECKDISPLAY            -  FormFlags2 - Check display before
displaying background  

  

      TPL\_FLAG\_FORMISRTL      -  FormFlags2 - This is a Right to Left form.  

  

      TPL\_FLAG\_HIDEBKGRAPHIC          -  FormFlags2 - Hide Background graphic
in Design Mode.  

  

      TPL\_FLAG\_RESIZEHEADER            -  FormFlags3 - Editor resizes header
area to contents.  

  

      TPL\_FLAG\_NOINITIALFOCUS         -  FormFlags3 - No initial focus to any
object on a form or page.  

  

      TPL\_FLAG\_SIGNWHENSAVED        -  FormFlags3 - Sign this document when it
gets saved.  

  

      TPL\_FLAG\_NOFOCUSWHENF6       -  FormFlags3 - No focus when doing F6 or
tabbing.  

  

      TPL\_FLAG\_RENDERPASSTHROUGH          -  FormFlags3 - Render pass through
HTML in the client.  

  

      TPL\_FLAG\_NOADDFIELDNAMESTOINDEX             -  FormFlags3 - Don't
automatically add form fields to field index.  

  

      TPL\_FLAG\_CANAUTOSAVE            -  FormFlags3 - Autosave Documents
created using this form.  

  




**Description :**



These are
the flags that may be specified in the FormFlags, FormFlags2 or FormFlags3
members of the CDDOCUMENT data structure. They are used to define document-wide
attributes.


 **See Also :**


**[CDDOCUMENT](CDDOCUMENT.md)**



----------------------------------------------------------------------------------------------------------


 





