




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



**Symbolic Value : Agents**



**ASSISTSEARCH\_TYPE\_xxx** **-** ODS\_ASSISTSTRUCT
- wSearchType values for agent search types.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ASSISTSEARCH\_TYPE\_NONE        -  No search type specified.  

  

      ASSISTSEARCH\_TYPE\_ALL            -  Run on all documents in database  

  

      ASSISTSEARCH\_TYPE\_NEW          -  Run on new documents added since the
last run of the Agent.  

  

      ASSISTSEARCH\_TYPE\_MODIFIED             -  Run on documents that were new
or modified since the last run of the Agent.  

  

      ASSISTSEARCH\_TYPE\_SELECTED            -  Run on selected documents.  

  

      ASSISTSEARCH\_TYPE\_VIEW         -  Run on all documents in the view.  

  

      ASSISTSEARCH\_TYPE\_UNREAD    -  Run on all unread documents.  

  

      ASSISTSEARCH\_TYPE\_PROMPT   -  Prompt the user to select the documents.  

  

      ASSISTSEARCH\_TYPE\_UI   -  Run on the document currently being viewed in
the Notes user interface.  

  

      ASSISTSEARCH\_TYPE\_COUNT      -  Total number of search types.  

  




**Description :**



The search
type specifies what documents are selected for an Agent to run against.  These
constants are used in the wSearchType field of the ODS\_ASSISTSTRUCT record for
an Agent.


 **See Also :**


**[ODS\_ASSISTSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/540A215A94BACC0385256261006222BC)**



----------------------------------------------------------------------------------------------------------


 





