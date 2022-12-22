




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




**Initial Release 4.5**



**Symbolic Value : OLE**



**OBJINFO\_FLAGS\_xxx** **-** OLE object
information flags


**----------------------------------------------------------------------------------------------------------**



**#include <oleods.h>**


 **Symbolic Values :**      OBJINFO\_FLAGS\_SCRIPTED          -  Object is scripted.  

  

      OBJINFO\_FLAGS\_RUNREADONLY              -  Object is run in read-only
mode.  

  

      OBJINFO\_FLAGS\_CONTROL           -  Object is a control.  

  

      OBJINFO\_FLAGS\_FITTOWINDOW   -  Object is sized to fit to window.  

  

      OBJINFO\_FLAGS\_FITBELOWFIELDS          -  Object is sized to fit below
fields.  

  

      OBJINFO\_FLAGS\_UPDATEFROMDOCUMENT        -  Object is to be updated from
document.  

  

      OBJINFO\_FLAGS\_INCLUDERICHTEXT       -  Object is to be updated from
document.  

  

      OBJINFO\_FLAGS\_ISTORAGE\_ISTREAM     -  Object is stored in
IStorage/IStream.  

  

      OBJINFO\_FLAGS\_HTMLDATA         -  Object has HTML data. In this case, the
CDOLEOBJ\_INFO structure is followed by OLEOBJHTMLDATA which is followed by a
number of OLEOBJHTMLEVENT strucutures, followed by a number of OLEHTMLPARAM
structures.  

  




**Description :**



These flags
are stored in the Flags field of the CDOLEOBJ\_INFO record.


 **See Also :**


**[CDOLEOBJ\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B21DB118D79474488525667A0076EC43)**



----------------------------------------------------------------------------------------------------------


 





