




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



**Function : HTML**



**HTMLConvertElement** **- Converts
a portion of a note item**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLConvertElement(**  

      HTMLHANDLE  hHTML,  

      DBHANDLE  hDB,  

      NOTEHANDLE  hNote,  

      char \*pszItemName,  

      DWORD  ItemIndex,  

      DWORD  Offset**);**



**Description :**




 1)
An element is a part of a notes rich text item.


 


 2)
If you look at the HTML generated for a rich text item that has an image
embedded in it, you may see a URL of the form:   


                        /database.nsf/*viewUNID*/*docUNID*/RText/10.A4?**OpenElement**.


   
The "RText" is the name of the item.  The "10" means that
it is the  index (represented in decimal) of  possibly several RText items (if
the item is > 64K).  The "A4" is the byte index into the CD stream
for RText pointing to the CD record that starts the image. So, it is your duty
to parse the generated HTML text and get the ItemIndex and the element offset
value which will be used as the last two parameters in this API.


 


 3)
HTMLConvertElement() is an API to the ?OpenElement URL functionality.


 


 


**Parameters :**



Input :  

hHTML  -  handle to the converter  

  

hDB  -  Handle to the database which is being converted  

  

hNote  -  handle to the note which is being converted  

  

pszItemName  -  pointer to the rich text field which is being converted  

  

ItemIndex  -   the relative item index -- if there is more than one, Item with
the same pszItemName, then this indicates which one (zero relative)  

  

Offset  -  byte offset in the Item where the element starts  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

NOERROR - action successful  

  

  




 **Sample Usage :**



rslt =
HTMLGetProperty(cvtr, HTMLAPI\_PROP\_NUMREFS, &retval);


        fprintf(m\_pLogFile,
LogInfoFormat, "<HAPI:RefList count=", retval); 


 


        for
( refi = 0 ; refi < retval; refi++ )


        {


       
rslt = HTMLGetReference(cvtr, refi, &hRef);


               if(rslt)


               {


                       PrintLogInfo("Error
in Getting Reference");


                       return
rslt;


               }


               


               rslt
= HTMLLockAndFixupReference(hRef, &pRef);


               if(rslt)


               {


                       PrintLogInfo("Error
in Lock And Fixup Reference");


                       return
rslt;


               }


               


               fprintf(m\_pLogFile,
"%s%d%s\n", "<Reference N=\"", refi,
"\"");


               fprintf(m\_pLogFile,
LogInfoFormat, "  Type:     ", pRef->RefType);


               fprintf(m\_pLogFile,
LogInfoFormat, "  CmdId:    ", pRef->CommandId);


               fprintf(m\_pLogFile,
LogInfoFormat, "  Text:     ", pRef->pRefText);


               fprintf(m\_pLogFile,
LogInfoFormat, "  NTargets: ", pRef->NumTargets);


 


        //
show the target components of one reference.


       
nTargets = pRef->NumTargets;


 


        for
(t = 0; t < nTargets; t++) 


               {


           
tgt = pRef->pTargets[t].Target;


                       fprintf(m\_pLogFile,
"%s%d%s\n", "            <Component N=\"", t,
"\"");


                       fprintf(m\_pLogFile,
LogInfoFormat, "                 AddressableType: ", 


                              GetAddressType(tgt));


                       fprintf(m\_pLogFile,
LogInfoFormat, "                 ReferenceType:   ",


                              GetReferenceType(tgt));


                       fprintf(m\_pLogFile,
"%s\n", "                        <RefValue>:");


 


           
switch( tgt.ReferenceType ) {


                       case
URT\_None: 


                              PrintLogInfo("                        -none-");


                              break;


                       case
URT\_Name:  


                              fprintf(m\_pLogFile,
"%s%s\n", "                              ", tgt.Value.name);



                              break;


                       case
URT\_Unid: 


                              PrintLogInfo("                        -uViewID-");
break;


                       case
URT\_NoteId: 


                              fprintf(m\_pLogFile,
LogInfoFormat, "                         ", (void\*)tgt.Value.nid);


                              break;


                       case
URT\_Special: 


                              fprintf(m\_pLogFile,
LogInfoFormat, "                         ", tgt.Value.special);


                              break;


                       case
URT\_RepId: 


                              PrintLogInfo("                        -repid-");


                              break;


           
}


                       PrintLogInfo("                        </RefValue>\n");


                       PrintLogInfo("         </Component>");


                       PrintSeperator();


        }


 


               PrintLogInfo("</Reference>");


               pointFound
= FALSE;


               ItemIndex
= 0;


               ElemIndex
= 0;


               postion
= 0;


               


               for
( t = 0; t < nTargets; t++) 


               {       


                       //check
if the refer type is 2 : that is image, then use HTMLSetrRferenceText to 


                       //change
the text,


                       tgt
= pRef->pTargets[t].Target;


                       


                       switch(pRef->RefType)
{


                       case
HTMLAPI\_REF\_OBJECT:


                              break;


                       case
HTMLAPI\_REF\_IMG:


                              {       


                                      if(t
== (nTargets - 2))


                                      {


                                             if(tgt.AddressableType
== UAT\_Field)


                                                     pszItemName
= tgt.Value.name;


                                      }


                                      


                                      if(t
== (nTargets - 1))


                                      {


                                             elemOffset
= tgt.Value.name;


                                             if(tgt.AddressableType
== UAT\_FieldOffset)


                                             {


                                                     /\*Get
the element number and the offset number which will be used 


                                                      
in the API HTMLConvertElement        \*/


                                                     


                                                     for(pos
= 0; pos < strlen(elemOffset); pos++)


                                                     {


                                                            if(\*(elemOffset+pos)
== '.')


                                                            {


                                                                    pointFound
= TRUE;


                                                                    postion
= pos;


                                                                    continue;


                                                            }


                                                            if(!pointFound)


                                                             {


                                                                    ElemNumber[pos]
= elemOffset[pos];


                                                                    continue;


                                                            }


                                                            


                                                            OffsetNumber[pos
- postion -1] = elemOffset[pos];


                                                     }


                                                     


                                                     ItemIndex
= atoi(ElemNumber);


                                                     length
= strlen(OffsetNumber)-1;


                                                     for(aa
= length; aa >=0; aa--)


                                                     {       


                                                            ElemIndex
+= (int)pow(16, length-aa) \* convert(OffsetNumber[aa]);


                                                     }


        


                                                     if(rslt
= HTMLCreateConverter(&hHTML))


                                                     {


                                                            PrintLogInfo("Converter
creation fail");


                                                     //      PrintAPIError(rslt);


                                                            return
rslt;


                                                     }


                              


                                                     rslt
= HTMLConvertElement(hHTML, m\_DBHandle, m\_NoteHandle, pszItemName, 


                                                             (DWORD)ItemIndex,(DWORD)ElemIndex);


                                                     if(rslt)


                                                     {


                                                            PrintLogInfo("Error:
Convert Element fail");


                                                             HTMLDestroyConverter(hHTML);


                                                            return
rslt;


                                                     }


                                                     rslt
= HTMLGetProperty(hHTML, HTMLAPI\_PROP\_BINARYDATA, &bBinary);


                                                     //whatever
the bBinary is TRUE or FALSE, we continue


                                                     if(rslt
= HTMLGetProperty(hHTML, HTMLAPI\_PROP\_TEXTLENGTH, &wTextLength))


                                                     {


                                                            PrintLogInfo("HTML
Get Image Binary Length fail");


                                                            //PrintAPIError(rslt);


                                                            return
rslt;


                                                     }


                                                     


                                                     pszBinaryText
= malloc(wTextLength);


                                                     if(rslt
= HTMLGetText(hHTML, 0, &wTextLength, pszBinaryText))


                                                     {


                                                            PrintLogInfo("HTML
Get Image Binary text fail");


                                                            //PrintAPIError(rslt);


                                                            return
rslt;


                                                     }


                                                     


                                                     rslt
= HTMLDestroyConverter(hHTML);


                                                     //whatever
the converter is destroyed or not, we continue


 


                                                     strcpy(PictureName,
pszItemName);


                                                     strcat(PictureName,
ElemNumber);


                                                     strcat(PictureName,
OffsetNumber);


                                                     strcat(PictureName,
".gif");


                                                     PictureFie
= fopen(PictureName, "wb");


                                                     fwrite(pszBinaryText,
1, wTextLength, PictureFie);


                                                     fclose(PictureFie);


                                                     if(rslt
= HTMLSetReferenceText(cvtr, refi, PictureName)) 


                                                     {


                                                            PrintLogInfo("Error:
HTML Set Reference Text Fail");


                                                            return
rslt;


                                                     }


 


                                                     free(pszBinaryText);


                                             }


                                      }


                              }


                              break;


               }


        }


}


 **See Also :**


**[HTMLConvertImage](HTMLConvertImage.md)**


**[HTMLConvertItem](HTMLConvertItem.md)**


**[HTMLConvertNote](HTMLConvertNote.md)**


**[HTMLCreateConverter](HTMLCreateConverter.md)**


**[HTMLDestroyConverter](HTMLDestroyConverter.md)**


**[HTMLGetProperty](HTMLGetProperty.md)**


**[HTMLGetReference](HTMLGetReference.md)**


**[HTMLGetText](HTMLGetText.md)**



----------------------------------------------------------------------------------------------------------


 





