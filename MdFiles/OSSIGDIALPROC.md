




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




 


**Data Type : Signal Handler**



**OSSIGDIALPROC** **-** Function
pointer template for Dial signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include
<ossignal.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR OSSIGDIALPROC)(


   char far \* pServer,  

   char far \* pPort,


   char far \* pDialParams,


   char far \*
pRetServer,


   char far \*
pRetPort);


 


**Description :**



Definition
of a pointer to a function that will handle the Dial signal.  The default Dial
signal handler displays a dialog box allowing the user to specify options for
dialing.  The return value from this function is ERR\_NET\_CONTINUE if dialing is
to continue, an error code if an error occurs, NOERROR otherwise.  

  

An application may use OSSetSignalHandler to redefine this signal handler in
order to do some processing prior to dialing out. For example, the signal
handler may warn the user that a call is about to be made and alow the user to
continue or cancel. The user-defined handler should return ERR\_NET\_CONTINUE to
continue with the call or any other error code to cancel the call. The API
function (such as NSFDbOpen) which initiated the call will receive the signal
handler's returned error code.  

  

This signal handler requires five parameters:  

  

    pServer - Far pointer to a null-terminated string containing the name of
the server to dial.  

            May be NULL.  

  

    pPort - Far pointer to a null-terminated string containing the name of the
port to use.  

            May be NULL.  

  

    pDialParams - Reserved for future use; should be set to NULL.  

  

    pRetServer - Pointer to a buffer where the actual name of the server to be
called is to be placed.  

            May be NULL if this information is not needed.  

  

    pRetPort - Pointer to a buffer where the actual name of the port to be used
is to be placed.  

            May be NULL if this information is not needed.


 **See Also :**


**[IXPostMessage](IXPostMessage.md)**


**[OSGetSignalHandler](OSGetSignalHandler.md)**


**[OSSetSignalHandler](OSSetSignalHandler.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





