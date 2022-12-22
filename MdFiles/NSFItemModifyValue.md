




<!--
 /\* Font Definitions \*/
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




 


**Function : Database; Item (Field);
Note**



**NSFItemModifyValue** **- Modify
the value of an item in an opened note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS **NSFItemModifyValue(**  

      DHANDLE  hnote,  

      BLOCKID  bhItem,  

      WORD  ItemFlags,  

      WORD  DataType,  

      const void \*Value,  

      DWORD  ValueLength**);**



**Description :**



Modify the
value of an item in an opened note according to parameters provided as an
argument.


 


**Parameters :**



Input :  

hnote  -  An open Note handle.  

  

bhItem  -  Block ID of item with value to be modified.  

  

ItemFlags  -  New item flags for the item, ITEM\_xxx is the symbol value that
can be used in this argument.  

  

DataType  -  New data type of value that need to be modified in the existing
item value. Refer TYPE\_xxx symbols for possible types.  

  

Value  -  ADDRESS of item new value that modifies existing.  

  

ValueLength  -  Length of new item value.  

  




Output :  

(routine)  -  Return status from the call either success or an error.   

              NOERROR, on success.  

  

  




 **Sample Usage :**


      WORD
m\_wItemflags = ITEM\_SUMMARY; 


            WORD
m\_wItemtype = TYPE\_TEXT; 


            char
m\_szItemname[MAX\_STRING]; 


 
         STATUS error = NOERROR; 


 
         /\* hNote is a NOTEHANDLE for an open document. \*/ 


 


            Cstrcpy(m\_szItemname,"TextItem");



 


            if
(error = NSFItemInfo(hNote, m\_szItemname, Cstrlen(m\_szItemname), &bhItem,
NULL, NULL, NULL)) 


            {



                        printf("Error
returned from NSFItemInfo = %e\n ", error); 


                        return
error; 


            }



            if(error
= NSFItemModifyValue(hNote, bhItem, ITEM\_SUMMARY, m\_wItemtype, m\_szExpValue,
Cstrlen(m\_szExpValue))) 


            {



                        printf("Error
returned from NSFItemModifyValue = %e", error); 


                        return
error; 


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





