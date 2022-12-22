




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




 


**Function : Views; Folders**



**NIFFindByName** **- Finds
notes using the collection's primary sort key.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindByName(**  

      HCOLLECTION  hCollection,  

      const char far \*Name,  

      WORD  FindFlags,  

      COLLECTIONPOSITION far \*retIndexPos,  

      DWORD far \*retNumMatches**);**



**Description :**



This
function searches through a collection for notes whose primary sort key matches
a given string. The primary sort key for a given note is the value displayed
for that note in the leftmost sorted column in the view or folder. Use this
function only when the leftmost sorted column of the view or folder is a
string.  

  

This function yields the COLLECTIONPOSITION of the first note in the collection
that matches the string. It also yields a count of the number of notes that
match the string.  With views that are not categorized, all notes with primary
sort keys that match the string appear contiguously in the view or folder. 
This means you may pass the resulting COLLECTIONPOSITION and match count as
inputs to NIFReadEntries to read all the entries in the collection that match
the string.  

  

This routine returns limited results if the view is categorized.  Views that
are categorized do not necessarily list all notes whose sort keys match the
string contiguously; such as in the case where the category note intervenes.
Likewise, this routine cannot be used to locate notes that are categorized
under multiple categories (the resulting position is unpredictable), and also
cannot be used to locate responses.  

  

Use NIFFindByKey if the leftmost sorted column is a number or a time/date.


 


Returning
the number of matches on an inequality search is not supported.  In other
words, if you specify any one of the following for the FindFlags argument:


      FIND\_LESS\_THAN


      FIND\_LESS\_THAN
| FIND\_EQUAL


      FIND\_GREATER\_THAN


      FIND\_GREATER\_THAN
| FIND\_EQUAL


this
function cannot determine the number of notes that match the search condition. 
In this case you may want to specify NULL for the retNumMatches argument.  If
you do not specify NULL for the retNumMatches argument, then \*retNumMatches
will be set to 1.


 


**Parameters :**



Input :  

hCollection  -  The handle of the collection you want to search.  

  

Name  -  A pointer to a null-terminated LMBCS string. The function will look
for notes (within the collection) whose primary sort key matches this string.  

  

FindFlags  -  Flags that control the comparison rules used when Name is
compared to the notes in the collection. The find flags are described in
FIND\_xxx, and may be or'ed together to combine functionailty.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_NOT\_FOUND  

  

  

retIndexPos  -  A pointer to a COLLECTIONPOSITION that receives the place
within the collection where the match is found.  If more than one matching note
was found, the position of the first matching note will be returned.  You can
use retIndexPos with NIFReadEntries to get the notes found by this search.  

  

retNumMatches  -  The address of a DWORD in which the number of matching
entries is returned.  This value is usually passed-on to a subsequent call to
NIFReadEntries().  It can also be used simply to determine if the name has
multiple matches or not (ambiguity).  

  

The number of matching entries is not supported if FIND\_LESS\_THAN,
FIND\_LESS\_THAN | FIND\_EQUAL, FIND\_GREATER\_THAN, or FIND\_GREATER\_THAN |
FIND\_EQUAL is specified in the FindFlags argument.  In this case, you may
specify NULL for the retNumMatches argument.  If you do not specify NULL, then
1 is returned as the number of matching notes.  

  




 **Sample Usage :**


/\* This code fragment
shows how to find only those notes  

in a collection where the left-hand column of the view is "Jones".   

We assume the view is sorted in ascending order on this column. \*/  

  

           error = NIFFindByName (  

                         hCollection,          

                         "JONES",              

                         FIND\_PARTIAL | FIND\_CASE\_INSENSITIVE,   

                         &pCollPosition,               

                         &MatchSize);         

  

           if (ERR(error) == ERR\_NOT\_FOUND) 


                goto
noNotes;  

          if (error) 


              
return(ERR(error));  

  

           if (error = NIFReadEntries(  

                             hCollection,          

                             &pCollPosition,              

                             NAVIGATE\_CURRENT,        

                             0,            

                             NAVIGATE\_NEXT,           

                             MatchSize,              

                             READ\_MASK\_NOTEID,     

                             &hBuffer,       

                             NULL,                 

                             NULL,                 

                             &NumberReturned,        

                             NULL))                

               return(ERR(error));  

  

        if (hBuffer != NULLHANDLE)  

        {  

              IdList = (NOTEID far \*)OSLockObject(hBuffer);  

  

              for (i=0; i<NumberReturned; i++)  

                  printf ("Note ID number %d is: %lu\n", i+1,
IdList[i]);  

  

            OSUnlockObject(hBuffer);  

            OSMemFree(hBuffer);  

        }  

  

        noNotes: ;  

  




 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





