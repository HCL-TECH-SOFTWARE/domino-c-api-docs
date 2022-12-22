




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



**HTMLCreateConverter** **- Create
new converter object.**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLCreateConverter(**  

      HTMLHANDLE \*phHTML**);**



**Description :**



A converter object is
used to access most of the HTML API's features.


 The
handle is passed as an argument to the those API functions.


 


 


**Parameters :**




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

phHTML  -  the handle to the newly created converter.  

  




 **Sample Usage :**



    STATUS nstat =
NOERROR;


        HTMLHANDLE
cvtr = NULLHANDLE;


        if(nstat
= HTMLCreateConverter(&cvtr))


        {


               printf("%s\n",
"Error in Creating HTMLConverter");


               return
nstat;


        }


 **See Also :**


**[HTMLDestroyConverter](HTMLDestroyConverter.md)**


**[HTMLHANDLE](HTMLHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





