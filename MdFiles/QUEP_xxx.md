




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




 


**Symbolic Value :** 



**QUEP\_xxx** **-** Some of the
query setting flags.


**----------------------------------------------------------------------------------------------------------**



**#include <dbmisc.h>**


 **Symbolic Values :**      QUEP\_NO\_EXEC     -  Explain only mode, only plan and return
the explain output.  

  

      QUEP\_DEBUG         -  Produce debugging output (notes.ini setting is
independent of this).  

  

      QUEP\_VIEWREFRESH        -  Refresh all views when they are opened(default
is NO\_UPDATE).  

  

      QUEP\_PARSEONLY             -  To check for syntax only - stops short of
planning.  

  

      QUEP\_EXPLAIN       -  Governs producing Explain output.  

  

      QUEP\_DSGNCATREFRESH             -  Before running the query,
build/refresh the design catalog, will have no effect if you have less than
Designer privileges on the database.  

  

      QUEP\_DSGNCATREBUILD   -  Before running the query, rebuild the design catalog,
will have no effect if you have less than Designer privileges on the database.  

  




 **See Also :**




----------------------------------------------------------------------------------------------------------


 





