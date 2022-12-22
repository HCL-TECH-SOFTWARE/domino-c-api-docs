




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : HTML**



**HTMLSetHTMLOptions** **- Set HTML
Options**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLSetHTMLOptions(**  

      HTMLHANDLE  hHTML,  

      const char \*optionList[]**);**



**Description :**



1) In one
notes document, you may have animation table and other style tables, besides,
you may have sections, to specify the HTML Convertting options, you can
determine the convertting behaviors and the convertting results of the HTML
APIS. For example, you have have a below table in your notes document.




|  |  |
| --- | --- |
| Cell
 1 | Cell
 2 |
| cell
 3 | cell
 4 |


 


If
you don't specify the Option RowAtATimeTableAlt as 1, the html code you get
will only show one table row for you.However, if you specify the option
RowAtATimeTableAlt as 1, you will get the two table rows both appear.


 


2)
You also have chance to do similar thing in the API HTMLSetDefaultArgs, some
arguments you set will also affect the convertting behaviors of the HTML
converter and the convertting result.


 


 


**Parameters :**



Input :  

hHTML  -  The handle of HTML converter  

  

optionList[]  -  The argument "optionList" is a NULL pointer
terminated array of pointers to NULL terminated strings.  

 \* (argv structure).  

 \* Each entry represents a name=value pair, with "name" the name of
an HTMLOption.  

 \* The options override options with the same name that were specified in the
notes.ini  

 \* or on the form (using the $$HTMLOptions field).  

 \*  

 \* Current Set of HTMLOptions:  

 \*    ForceSectionExpand - 1 = expand all sections in the generated html  

 \*    ForceOutlineExpand - 1 = expand all outlines in the generated html  

 \*    RowAtATimeTableAlt - 1 = alternate representation for row-at-a time
tables  

 \*                             that shows all of the rows and the tab label.  

 \*/  

  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  




 **Sample Usage :**


const char\*
HTMLOption[4] = {"ForceSectionExpand=1",


                               "RowAtATimeTableAlt=1",



                              "ForceOutlineExpand=1",
NULL};


  if(nstat
= HTMLSetHTMLOptions(cvtr, HTMLOption))


     
PrintAPIError(nstat);


 **See Also :**


**[HTMLGetProperty](HTMLGetProperty.md)**


**[HTMLHANDLE](HTMLHANDLE.md)**


**[HTMLSetProperty](HTMLSetProperty.md)**



----------------------------------------------------------------------------------------------------------


 





