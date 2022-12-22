




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




**Initial Release 5.0.3**



**Data Type : DSAPI**



**FilterInitData** **-** DSAPI Filter
initialization entry point prototype.


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef struct {


   unsigned int  
serverFilterVersion;


   unsigned int  
appFilterVersion;


   unsigned int   eventFlags;


   unsigned int  
initFlags;


   char          
filterDesc[kMaxFilterDesc+1];


} FilterInitData;


 


**Description :**




The
FilterInitData structure is referenced in the FilterInit entry point
prototype.  The FilterInit entry point defines the filter initialization. 
Filter initialization is called when the HTTP task loads the filter, which
occurs as part of the HTTP task startup..  It is also called when the HTTP task
is restarted with the domino server command "tell http restart".  The
filter initialization proto type would be defined as follows:


 


      typedef
unsigned int FilterInit( FilterInitData\* initData );


 


FilterInitData
Structure:


serverFilterVersion  -
Input parameter:         The server's version of the filter software.


appFilterVersion      -
Output parameter:       The filter's version of the filter software.  Set this
to kInterfaceVersion.


eventFlags             -
Output parameter:       Indicates for which event the filter wants to be
called, see EventFlags.


initFlags                 -
not used


filterDesc                -
Output parameter:       a short description of the filter.


 


 **See Also :**


**[EventFlags](EventFlags.md)**



----------------------------------------------------------------------------------------------------------


 





