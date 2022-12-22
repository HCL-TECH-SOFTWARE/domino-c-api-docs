




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



**Data Type : HTML**



**CAI** **-** Domino
Command Argument Ids


**----------------------------------------------------------------------------------------------------------**



**#include
<urltypes.h>**



**Definition :**



typedef enum


{


   
CAI\_Start                   = 0,


   
CAI\_StartKey                = 1,


   
CAI\_Count                   = 2,


   
CAI\_Expand                  = 3,


   
CAI\_FullyExpand             = 4,


   
CAI\_ExpandView              = 5,


   
CAI\_Collapse                = 6,


   
CAI\_CollapseView            = 7,


   
CAI\_3PaneUI                 = 8,


   
CAI\_TargetFrame             = 9,


   
CAI\_FieldElemType           = 10,


   
CAI\_FieldElemFormat         = 11,


   
CAI\_SearchQuery             = 12,


   
CAI\_OldSearchQuery          = 13,


   
CAI\_SearchMax               = 14,


   
CAI\_SearchWV                = 15,


   
CAI\_SearchOrder             = 16,


   
CAI\_SearchThesarus          = 17,


   
CAI\_ResortAscending         = 18,


   
CAI\_ResortDescending        = 19,


   
CAI\_ParentUNID              = 20,


   
CAI\_Click                   = 21,


   
CAI\_UserName                = 22,


   
CAI\_Password                = 23,


   
CAI\_To                      = 24,


   
CAI\_ISMAPx                  = 25,


   
CAI\_ISMAPy                  = 26,


   
CAI\_Grid                    = 27,


   
CAI\_Date                    = 28,


   
CAI\_TemplateType            = 29,


   
CAI\_TargetUNID              = 30,


   
CAI\_ExpandSection           = 31,


   
CAI\_Login                   = 32,


   
CAI\_PickupCert              = 33,


   
CAI\_PickupCACert            = 34,


   
CAI\_SubmitCert              = 35,


   
CAI\_ServerRequest           = 36,


   
CAI\_ServerPickup            = 37,


   
CAI\_PickupID                = 38,


   
CAI\_TranslateForm           = 39,


   
CAI\_SpecialAction           = 40,


   
CAI\_AllowGetMethod          = 41,


   
CAI\_Seq                     = 42,


   
CAI\_BaseTarget              = 43,


   
CAI\_ExpandOutline           = 44,


   
CAI\_StartOutline            = 45,


   
CAI\_Days                    = 46,


    CAI\_TableTab               
= 47,


   
CAI\_MIME                    = 48,


   
CAI\_RestrictToCategory      = 49,


   
CAI\_Highlight               = 50,


   
CAI\_Frame                   = 51,


   
CAI\_FrameSrc                = 52,


   
CAI\_Navigate                = 53,


   
CAI\_SkipNavigate            = 54,


   
CAI\_SkipCount               = 55,


   
CAI\_EndView                 = 56,


   
CAI\_TableRow                = 57,


   
CAI\_RedirectTo              = 58,


   
CAI\_SessionId               = 59,


   
CAI\_SourceFolder            = 60,


   
CAI\_SearchFuzzy             = 61,


   
CAI\_HardDelete              = 62,


   
CAI\_SimpleView              = 63,


   
CAI\_SearchEntry             = 64,


   
CAI\_Name                    = 65,


   
CAI\_Id                      = 66,


   
CAI\_RootAlias               = 67,


   
CAI\_Scope                   = 68,


   
CAI\_DblClkTarget            = 69,


   
CAI\_Charset                 = 70,


   
CAI\_EmptyTrash              = 71,


   
CAI\_EndKey                  = 72,


    CAI\_PreFormat              
= 73,


   
CAI\_ImgIndex                = 74,


   
CAI\_AutoFramed              = 75,


   
CAI\_OutputFormat            = 76,


   
CAI\_InheritParent           = 77,


   
CAI\_Folder                  = 78,


   
CAI\_Form                    = 79,


   
CAI\_PresetFields            = 80,


   
CAI\_StartAtLastPage         = 81,


   
CAI\_PasswordNew             = 82,


   
CAI\_PasswordConfirm         = 83,


   
CAI\_Option                  = 84,


   
CAI\_j\_username              = 85,


   
CAI\_j\_password              = 86,


   
CAI\_PreferenceType          = 87,


   
CAI\_EmbedFlags              = 88,


   
CAI\_UploadFile              = 89,


   
CAI\_UntilKey                = 90,


   
CAI\_KeyType                 = 91,


   
CAI\_ui                      = 92,


   
CAI\_ACF                     = 93,


   
CAI\_TZType                  = 94,


   
CAI\_OpenSoftDeleted         = 95,


   
CAI\_EmbeddedEditor          = 96,


   
CAI\_StartUnid               = 97,


   
CAI\_SearchQueryType         = 98,


    CAI\_SearchDate             
= 99,


   
CAI\_SearchDateType          = 100,


   
CAI\_SearchAuthor            = 101,


   
CAI\_StartIndex              = 102,


   
CAI\_GetTotalEntries         = 103,


   
CAI\_UseStartKeyOnly         = 104,


   
CAI\_FileName                = 105,


   
CAI\_PosPrev                 = 106,


   
CAI\_GetRangeEntries         = 107,


   
CAI\_NavigateReverse         = 108,


   
CAI\_Last


}
CmdArgID;


 


 


**Description :**



This enumerates the
command arguments supported in Domino urls.  (e.g., &Start=...,
&Count=...).


/\*


\*   CAI =
Command Argument ID


\*/


 


 




----------------------------------------------------------------------------------------------------------


 





