




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



**Function : MIME**



**MIMEStreamGetLine** **- Get a
line from a MIME stream.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



int
LNPUBLIC **MIMEStreamGetLine(**  

      char \*pszLine,  

      unsigned int  uiMaxLineSize,  

      MIMEHANDLE  hMIMEStream**);**



**Description :**



This function,
MIMEStreamGetLine, returns an ASCIIZ line from the input MIME stream.  You must
specify as input a pointer to an output line buffer, the maximum size of the
buffer (including space for the terminating NULL character), and the handle to
the MIME stream.


 


On entry
MIMEStreamGetLine writes a NUL byte to the first byte pointed to by 'pszLine'. 
It returns MIME\_STREAM\_SUCCESS if the line is read and returned with no errors,
MIME\_STREAM\_EOS if all data has been returned from the MIME stream, and
MIME\_STREAM\_IO if there are any errors when it attempts to read the MIME
stream.


 


 


**Parameters :**



Input :  

  

uiMaxLineSize  -  The maximum size of the output buffer in bytes, including
room for the NULL terminator  

  

hMIMEStream  -  A MIME stream handle  

  




Output :  

(routine)  -  Returns MIME\_STREAM\_SUCCESS, MIME\_STREAM\_EOS, or MIME\_STREAM\_IO  

  

  

  

pszLine  -  A pointer to an output line buffer.  

  




 **Sample Usage :**


#define MAX\_LINE\_SIZE     80


 


int iReturn;


char
aszLine[MAX\_LINE\_SIZE];


 


if ((iReturn =
MIMEStreamGetLine(aszLine, MAX\_LINE\_SIZE, hMIMEStream)) == MIME\_STREAM\_IO) {


        goto exit;


}


 


 **See Also :**


**[MIMEHANDLE](MIMEHANDLE.md)**


**[MIMEStreamPutLine](MIMEStreamPutLine.md)**



----------------------------------------------------------------------------------------------------------


 





