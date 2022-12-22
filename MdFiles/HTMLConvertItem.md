




<!--
 /\* Font Definitions \*/
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



**HTMLConvertItem** **- Convert a
specific item within a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLConvertItem(**  

      HTMLHANDLE  hHTML,  

      DBHANDLE  hDB,  

      NOTEHANDLE  hNote,  

      char \*pszItemName**);**



**Description :**




1) This
function is used to convert note item to HTML.  The results of the routine is
retained in the converter object (until the next "convert") and are
retrieved with GetText().


2) Only
items of type RichText or MIME can be converted.  If the item is of a different
type, ERR\_HTMLAPI\_NOT\_SUPPORTED is returned.


 


**Parameters :**



Input :  

hHTML  -  handle to the converter  

  

hDB  -  handle to open database  

  

hNote  -   handle to note containing item  

  

pszItemName  -  refers to an item within the note indicated by hNote.  The
first item found with name pszItemName is converted.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

  

  




 **Sample Usage :**


                                          


            rslt
= NSFNoteOpen(m\_DBHandle, NoteID, OPEN\_EXPAND, &nt\_handle);


            if(NSFItemIsPresent(nt\_handle,ItemName
,strlen(ItemName)))


            {


                        if(nstat
= HTMLCreateConverter(&cvtr))


                        {


                                    cerr
<< "Error in Creating HTMLConverter" << endl;


                                    return
FALSE;


                        }


            


                        printf("%s%s\n",
"\*\*Converting Item: ", ItemName);


            


                        nstat
= HTMLConvertItem(cvtr, m\_DBHandle, hNote, ItemName);


            


                        if
(nstat) {


                                    cprintf(%s%s\n",
"E: Error converting item ",ItemName);


                                    char
szErrorString[BuufferSize];


                                    OSLoadString(NULL,
ERR(nstat), szErrorString, BuufferSize-1);


                                    return
FALSE;


                        }                       


            }


            fprintf(flog,
"\nthe Events Item does not present!\n");


            NSFNoteClose(nt\_handle);


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLConvertElement](HTMLConvertElement.md)**


**[HTMLConvertImage](HTMLConvertImage.md)**


**[HTMLConvertItem](HTMLConvertItem.md)**


**[HTMLConvertNote](HTMLConvertNote.md)**


**[HTMLCreateConverter](HTMLCreateConverter.md)**


**[HTMLGetReference](HTMLGetReference.md)**


**[HTMLGetText](HTMLGetText.md)**


**[HTMLHANDLE](HTMLHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





