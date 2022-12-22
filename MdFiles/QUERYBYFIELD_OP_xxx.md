




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




**Initial Release 4.0**



**Symbolic Value : Agents**



**QUERYBYFIELD\_OP\_xxx** **-** Comparison
operators for field-level query.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      QUERYBYFIELD\_OP\_GREATER      -  Select document if field is
greater than value.  

  

      QUERYBYFIELD\_OP\_LESS              -  Select document if field is less
than value.  

  

      QUERYBYFIELD\_OP\_NOTEQUAL    -  Select document if field is not equal to
value.  

  

      QUERYBYFIELD\_OP\_BETWEEN     -  Select document if field is in specified
range (between Date1 and Date2 for TYPE\_TIME, between Number1 and Number2 for
TYPE\_NUMBER).  

  

      QUERYBYFIELD\_OP\_NOTWITHIN   -  Select document if field is not in the
specified range.  

  

      QUERYBYFIELD\_OP\_EQUAL           -  Select document if field is equal to
value.  

  

      QUERYBYFIELD\_OP\_CONTAINS     -  Select document if field contains the
specified value.  

  

      QUERYBYFIELD\_OP\_DOESNOTCONTAIN   -  Select document if field does not
contain the specified value.  

  

      QUERYBYFIELD\_OP\_INTHELAST   -  Select document if the field value is
within the last n days.  

  

      QUERYBYFIELD\_OP\_INTHENEXT   -  Select document if the field value is
within the next n days.  

  

      QUERYBYFIELD\_OP\_OLDERTHAN             -  Select document if the field
value is older than n days.  

  

      QUERYBYFIELD\_OP\_DUEIN            -  Select document if the field value is
due more than n days from now.  

  




**Description :**



These
operators are specified in the wOperator field of the CDQUERYBYFIELD record. 
The operator code identifies how the value of the field in the document is to
be tested against the field value supplied in the query record.


 **See Also :**


**[CDQUERYBYFIELD](CDQUERYBYFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





