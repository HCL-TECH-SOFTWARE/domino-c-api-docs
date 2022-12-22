




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




**Initial Release 5.0.1**



**Data Type : Composite Data; Rich
Text**



**CDFRAME** **-** Used to
specify an HTML FRAME element


**----------------------------------------------------------------------------------------------------------**



**#include
<fsods.h>**



**Definition :**



typedef struct{


    WSIG Header;


    DWORD Flags;   /\* fFRxxx unused bits must be
set to 0 \*/


 


/\* In 6 this word is
used to signify variable data follows the frame \*/


/\* the data is in the
order of the bits, i.e. 0x8000 is the first chunk of   


   data\*/


/\* the first word of
each set of data is the size then the data\*/


    WORD  DataFlags;                                     


    BYTE  BorderEnable;           /\*
Specifies the FRAMEBORDER attribute for 


                                   
this Frame element \*/


    BYTE  NoResize;                       /\*
Specifies the NORESIZE attribute for this 


                                   
Frame element \*/


        WORD 
ScrollBarStyle;         /\* Specifies the SCROLLING attribute for this


                                      
\* frame element.  Must be ALWAYS\_ScrollStyle,


                                              \*
NEVER\_ScrollStyle or AUTO\_ScrollStyle \*/


    WORD  MarginWidth;            /\*
Specifies the MARGINWIDTH attribute for 


                                    this
frame element \*/


    WORD  MarginHeight;           /\*
Specifies the MARGINHEIGHT attribute for 


                                   
this frame element \*/


    DWORD dwReserved;                     /\*
Reserved for future use, must be 0 \*/


    WORD 
FrameNameLength;        /\* Length of FrameName string that follows. 


                                  
\* Set to 0 if not specified. \*/


    WORD Reserved1;


    WORD 
FrameTargetLength;      /\* Length of default target frame name. 


                                           
Set to 0 if not specified \*/


    COLOR\_VALUE
FrameBorderColor; /\* Specifies the BORDERCOLOR attribute 


                                           
for this frame element \*/


    WORD wReserved;                       /\*
Reserved for future use, must be 0 \*/


    /\* Variable length
data follows (strings not null terminated)


     \*  - Frame Name
string (Specifies the NAME attribute for this frame element \*/


    /\*  - Frame Target
string \*/


 


    /\*This is where the
data assoiciated with the Dataflags word above begins\*/


 


} CDFRAME;


 


**Description :**



Header


Flags                                  see
fFRxxx


DataFlags                           see
fFRNotesxxx


BorderEnable                      Frame
Border Attribute specified.


NoResize                            Specifies
the NoReSize attribute to this Frame.


ScrollBarStyle                     see
xxx\_ScrollStyle


MarginWidth                       Margin
Width of this Frame in pixels.


MarginHeight                      Margin
Height of this Frame in pixels.


dwReserved                       Reserved,
must be 0.


FrameNameLength             Length
of the frame name string.


Reserved1                          Reserved,
must be 0.


FrameTargetLength            Length
of the default target frame name.


FrameBorderColor              Specifies
the Border Color.


wReserved                         Reserved,
must be 0.


 


Frame Name
String and Target Name string follow the fixed portion of this CD Record.  The
strings are not null terminated.


 


 


 


 **See Also :**


**[CDFRAMESETHEADER](CDFRAMESETHEADER.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[fFRNotesxxx](fFRNotesxxx.md)**


**[fFRxxx](fFRxxx.md)**


**[xxx\_ScrollStyle](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6AB25F5A633E0D95852567AD005D747D)**



----------------------------------------------------------------------------------------------------------


 





