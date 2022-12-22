




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




**Initial Release 6**



**Data Type : DSAPI**



**FilterAuthorize** **-** DSAPI
FilterAuthorize structure


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef struct
\_FilterAuthorize{


        const
char             \*pURL;         /\* Input. The input URL \*/


        char                   \*pBuffer;      /\*
Input. The resulting mapping is contained 


                                                     in
the supplied buffer \*/


        unsigned
int   bufferSize;            /\* Size of the buffer supplied \*/


        unsigned
int   mapType;               /\* Mapping type. \*/


        unsigned
int   isAuthorized;          /\* Result of operation, 1 if successful, 0
otherwise. \*/


}  FilterAuthorize;


 


**Description :**



The
FilterAuthorize structure is used in the kFilterAuthorized event.  It's
described below:


 


pURL                      -
(Input)  The http request URL.


 


pBuffer                   -
(Input)  This buffer contains the path to the target resource.


 


bufferSize               -
(Input)  The total size in bytes of the supplied buffer.


 


mapType                -
(Input)  Set to one of the following:


kURLMapUnknown       -
Unknown mapping type.


kURLMapPass              -
File system mapping rule


kURLMapExec              -
CGI mapping rule


kURLMapRedirect         -
Redirect mapping rule


kURLMapService          -
(Obsolete). Not used anymore in Notes/Domino 6.


kURLMapDomino          -
Domino mapping rule 


 


isAuthorized            -
(Output)  Set to 1 if the user is granted access to the resource, 0 otherwise.


 **See Also :**


**[EventFlags](EventFlags.md)**



----------------------------------------------------------------------------------------------------------


 





