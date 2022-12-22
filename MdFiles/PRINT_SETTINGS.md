




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




 


**Data Type : Rich Text**



**PRINT\_SETTINGS** **-** Print
Settings


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


        WORD
Flags;


#ifdef
LITTLE\_ENDIAN\_ORDER


        #define
PS\_Initialized        0x0001 /\* Print settings have been initialized \*/


        #define
PS\_HeaderFooterOnFirst 0x0002 /\* Print header/footer on first page \*/


        #define
PS\_CropMarks          0x0004 /\* Print crop marks \*/


        #define
PS\_ChangeBin          0x0008 /\* Paper source should be set for 1st & Other
Pg. \*/


        #define
PS\_HeaderFooterRTL    0x0010 /\* Paper source should be set for 1st & Other
Pg. \*/


        #define
PS\_ReleaseRightMargin  0x0020 /\* Release the right margin when printing (to
print into gutter) \*/


#else


        #define
PS\_Initialized        0x8000


        #define
PS\_HeaderFooterOnFirst 0x4000


        #define
PS\_CropMarks          0x2000


        #define
PS\_ChangeBin          0x1000


        #define
PS\_HeaderFooterRTL    0x0800 /\* Paper source should be set for 1st & Other
Pg. \*/


        #define
PS\_ReleaseRightMargin  0x0400 /\* Release the right margin when printing (to
print into gutter) \*/


#endif


 


        WORD
StartingPageNum;         /\* Starting page number \*/


        WORD
TopMargin;                       /\* Height between main body & top of page
(TWIPS) \*/


        WORD
BottomMargin;            /\* Height between main body & bottom of page
(TWIPS) \*/


        WORD
ExtraLeftMargin;         /\* Extra left margin width (TWIPS) \*/


                                             /\*
(beyond whats already specified in document) \*/


        WORD
ExtraRightMargin;        /\* Extra right margin width (TWIPS) \*/


                                             /\*
(beyond whats already specified in document) \*/


        WORD
HeaderMargin;            /\* Height between header & top of page (TWIPS) \*/


        WORD
FooterMargin;            /\* Height between footer & bottom of page (TWIPS)
\*/


        WORD
PageWidth;                       /\* Page width override (TWIPS) \*/


                                             /\*
(0 = "use printer's page width") \*/


        WORD
PageHeight;                      /\* Page height override (TWIPS) \*/


                                             /\*
(0 = "use printer's page height") \*/


        WORD
BinFirstPage;


        WORD
BinOtherPage;


        WORD
PageOrientation;         /\* New in R6. 0 = undefined, 1 = Portrait, 2 =
Landscape \*/


        WORD
wSpare;                  /\* Spare word \*/


        DWORD
spare[2];                       /\* (spare dwords) \*/


        }
PRINT\_SETTINGS;


 


**Description :**



Print
settings passed to editor export procedures.  

  

Flags                                              Flags for print settings:              


      PS\_Initialized                                        Print
settings have been initialized  

      PS\_HeaderFooterOnFirst                      Header and footer are printed
on the first page  

      PS\_CropMarks                                     Crop marks will be
printed  

      PS\_ChangeBin                                     Different paper bins
will be used for the first page and all subsequent pages


      PS\_HeaderFooterRTL                           Paper
source should be set for 1st & Other Pg.


      PS\_ReleaseRightMargin                       Release
the right margin when printing (to print into gutter)  

StartingPageNum                           Page number of first page  

TopMargin                                      Height in "twips"
(1/1440 inch) between top of page and main body  

BottomMargin                                 Height in twips between bottom of
page and main body  

ExtraLeftMargin                              Additional left margin space in
twips (beyond what's already specified in the document)  

ExtraRightMargin                            Additional right margin space in
twips (beyond what's already specified in the document)  

HeaderMargin                                 Height in twips between top of
page and header  

FooterMargin                                  Height in twips between bottom of
page and footer  

PageWidth                                      If non-zero, override the
printer's page width with this dimension (in twips)  

PageHeight                                    If non-zero, override the
printer's page height with this dimension (in twips)  

BinFirstPage                                   Index of paper bin to use for
the first page  

BinOtherPage                                 Index of paper bin to use for all
other pages


PageOrientation                              New
in Notes/Domino 6.  0 = Undefined, 1 = Portrait, 2 = Landscape. See PSPO\_xxx


wSpare                                           Spare
word       


spare[2]                                          Spare
dwords


 **See Also :**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[PRINTNEW\_SETTINGS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8AE7273B8F8B59E2852560510050C99C)**


**[PSPO\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5DF38ACF8B17F66985256BB1005017DD)**


**[PS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/33C9EB0F0FA54D1A85256203007474B9)**



----------------------------------------------------------------------------------------------------------


 





