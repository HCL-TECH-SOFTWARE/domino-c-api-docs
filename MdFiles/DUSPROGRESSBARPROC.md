




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




**Initial Release 5.0**



**Data Type : Domino Upgrade Services**



**DUSPROGRESSBARPROC** **-** Progress Bar
callback passed to DUS with DUSStart.


**----------------------------------------------------------------------------------------------------------**



**#include
<dus.h>**



**Definition :**



typedef void
(LNCALLBACKPTR DUSPROGRESSBARPROC)(


   DWORD  Range,


   DWORD  Position,


   char \* MessageText);


 


**Description :**



In
DUSStart(), DUSPROGRESSBARPROC is declared.  This allows the ability to display
a progress bar status within a DUS application.


 **Sample Usage :**


typedef struct  

{  

    HMODULE                hDUSModule;  

    WORD                          ExtendedError;  

    WORD                          ExtendedErrorLevel;  

    DUSPROGRESSBARPROC     ProgressBarProc;  

    DUSLOGEVENTPROC               LogEventProc;  

}DUS\_CONTEXT, \*PDUS\_CONTEXT;


char
Message[MAXSPRINTF];


 


PDUS\_CONTEXT pDUSCtx;


 


pDUSCtx->ProgressBarProc
= DUSProgressBar;


OSLoadString(pDUSCtx->hDUSModule,
STR\_DUS\_GETTING\_USERS, Message, sizeof(Message));


for(i=0, index=0; i
< \*pNumUsersReturned; i++)   

{  

    pDUSCtx->ProgressBarProc((DWORD)\*pNumUsersReturned, i, Message);  

    Sleep(100);                   /\* Allow for display of Progress Bar status
\*/  

    position = 0;   

    pExternalUsers[i].ID = i + \*pNumUsersReturned;  

    while(((FileBuffer[index] != CHAR\_CR) && (FileBuffer[index] !=
CHAR\_LF)) && (index < NumberOfBytesRead))  

    {    

           /\* Parse the data from the input file \*/  

           pExternalUsers[i].Name[position] = FileBuffer[index];  

           index++;  

           position++;  

    }  

    index+=2; /\* Hop over CRLF in the input File \*/  

}  

pDUSCtx->ProgressBarProc(\*pNumUsersReturned, \*pNumUsersReturned, Message);
/\* Reset Progress Bar \*/


 **See Also :**


**[DUSStart](DUSStart.md)**



----------------------------------------------------------------------------------------------------------


 





