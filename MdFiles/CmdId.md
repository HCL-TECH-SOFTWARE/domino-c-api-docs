




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : HTML**



**CmdId** **-** Domino
Command Ids


**----------------------------------------------------------------------------------------------------------**



**#include
<urltypes.h>**



**Description :**



This enumerates the
commands supported in Domino urls


 


typedef
enum \_CmdId             


{


   
kUnknownCmdId               = 0,


   
kOpenServerCmdId            = 1,


   
kOpenDatabaseCmdId          = 2,


   
kOpenViewCmdId              = 3,


   
kOpenDocumentCmdId          = 4,


   
kOpenElementCmdId           = 5,


   
kOpenFormCmdId              = 6,


   
kOpenAgentCmdId             = 7,


   
kOpenNavigatorCmdId         = 8,


   
kOpenIconCmdId              = 9,


   
kOpenAboutCmdId             = 10,


   
kOpenHelpCmdId              = 11,


   
kCreateDocumentCmdId        = 12,


   
kSaveDocumentCmdId          = 13,


   
kEditDocumentCmdId          = 14,


   
kDeleteDocumentCmdId        = 15,


   
kSearchViewCmdId            = 16,


   
kSearchSiteCmdId            = 17,


   
kNavigateCmdId              = 18,


   
kReadFormCmdId              = 19,


   
kRequestCertCmdId           = 20,


   
kReadDesignCmdId            = 21,


   
kReadViewEntriesCmdId       = 22,


   
kReadEntriesCmdId           = 23,


   
kOpenPageCmdId              = 24,


   
kOpenFrameSetCmdId          = 25,


   
kOpenFieldCmdId             = 26,   /\* OpenField command for Java applet(s)
& HAPI \*/


   
kSearchDomainCmdId          = 27,


   
kDeleteDocumentsCmdId       = 28,


   
kLoginUserCmdId             = 29,


   
kLogoutUserCmdId            = 30,


   
kOpenImageResourceCmdId     = 31,


   
kOpenImageCmdId             = 32,


   
kCopyToFolderCmdId          = 33,


   
kMoveToFolderCmdId          = 34,


   
kRemoveFromFolderCmdId      = 35,


   
kUndeleteDocumentsCmdId     = 36,


   
kRedirectCmdId              = 37,


   
kGetOrbCookieCmdId          = 38,


   
kOpenCssResourceCmdId       = 39,


   
kOpenFileResourceCmdId      = 40,


   
kOpenJavascriptLibCmdId     = 41,


   
kUnImplemented\_01           = 42,


   
kChangePasswordCmdId        = 43,


   
kOpenPreferencesCmdId       = 44,


   
kOpenWebServiceCmdId        = 45,


   
kWsdlCmdId                  = 46,


/\* SDK END
\*/


    //hu


   
kGetImageCmdId              = 47,


                       
/\* <= add new types above here 


                                do
not reuse numbers, do not rely on "kNumberOfCmds"


                               
being the same on each side of the API \*/


 


/\* SDK
BEGIN \*/


   
kNumberOfCmds           /\* This must remain last \*/


} CmdId;


 


 




----------------------------------------------------------------------------------------------------------


 





