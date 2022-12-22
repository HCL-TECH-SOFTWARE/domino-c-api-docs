




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



**Symbolic Value : Rich Text**



**ACTIVEOBJECT\_FLAG\_xxx** **-** Flag
settings for ACTIVEOBJECT.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      ACTIVEOBJECT\_FLAG\_MAYSCRIPT           -  Active object is an
applet that accesses JavaScript.  

  

      ACTIVEOBJECT\_FLAG\_CORBA\_APPLET    -  Active object is a Java applet that
uses CORBA.  

  

      ACTIVEOBJECT\_FLAG\_CORBA\_SSL          -  This is a CORBA applet that uses
SSL.  

  

      ACTIVEOBJECT\_FLAG\_MAIL\_PLUGIN        -  This object comes from a mime
mail message.  

  

      ACTIVEOBJECT\_FLAG\_NOCORBADOWNLOAD      -  Don't automatically download
the jar stuff for applets.  

  

      ACTIVEOBJECT\_FLAG\_DIGESTAPPLETFILES        -  Reserved part of
ACTIVEOBJECT struct contains applet files digested for signature verification.  

  




**Description :**



Flag
settings for the Flags member within an ACTIVEOBJECT record.


 **See Also :**


**[ACTIVEOBJECT](ACTIVEOBJECT.md)**



----------------------------------------------------------------------------------------------------------


 





