




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




 


**Function : Search**



**NSFQueryDBExt2** **- Run
Domino Query Language (DQL) queries.**


**----------------------------------------------------------------------------------------------------------**



**#include <dbmisc.h>**



STATUS **NSFQueryDBExt2(**  

      DBHANDLE  dbhandle,  

      char \*query,  

      DWORD  Qlen,  

      DWORD  Flags,  

      DWORD  MaxDocsScanned,  

      DWORD  MaxEntriesScanned,  

      DWORD  MaxMsecs,  

      MEMHANDLE \*retResults,  

      MEMHANDLE \*retError,  

      MEMHANDLE \*retExplain,  

      MEMHANDLE  hQArgList**);**



**Description :**



Run DQL
queries. Its inputs are a database handle, the query text, length of query
text, and a set of flags. Returns explanation of output and extra error output.


 


**Parameters :**



Input :  

dbhandle  -  The handle to the database providing context for the DQL query.  

  

query  -  The DQL query to be executed, explained or parsed. The text of the
query must be translated into LMBCS prior to execution using OSTranslate or
OSTranslate32.  

  

Qlen  -  Length of query string. Maximum length is 64K.  

  

Flags  -  Flags passed that govern query processing. Refer to QUEP\_xxx for
allowed flag inputs.  

  

MaxDocsScanned  -  The maximum number of documents scanned to execute or
explain the query.  

  

MaxEntriesScanned  -  The maximum number of view entries scanned to execute or
explain the query.  

  

MaxMsecs  -  The maximum time in milliseconds a query can take to execute or
explain.  

  

hQArgList  -  Values passed to be bound to DQL substitution values. The caller
must free the MEMHANDLE once processing is complete.  Substitution arguments
are supplied through calls to NSFQueryDBAddArgs.  

  




Output :  

(routine)  -  Returns status from the call, either success or an error.   

   The return codes include:   

    NOERROR - On success.   

    ERR\_MISC\_INVALID\_ARGS - Invalid arguments.  

  

  

retResults  -  Returns the results from a DQL execute or explain.  Depending
upon the flags passed in, the results will either be an IDTable or a queue of
data values.  It is the responsibility of the caller to free the DHANDLE once
processing is complete.  

  

retError  -  Returns additional text when DQL processing encounters an error
state.  It is the responsibility of the caller to free the MEMHANDLE once
processing is complete.  

  

retExplain  -  Returns explain text when requested via flag setting. It is the
responsibility of the caller to free the MEMHANDLE once processing is complete.  

  




 **Sample Usage :**


      /\* To
Execute or explain DQL Queries:


 


            hDb
is a DBHANDLE from a previously opened database.


            pQuery
is a LMBCS-translated query using OSTranslate.


            Len
is length of the pQuery in bytes.


            MaxDocsScanned
is maximum number of documents to be scanned.


            MaxEntriesScanned
is maximum number of view entries to be scanned.


            MaxMsecs
is maximum time in milliseconds.


            hQargList
is either NULLMEMHANDLE or the output from a call or calls to
NSFQueryDBAddArgs. \*/


 


            if
(err = NSFQueryDBExt2(hDb, 


                        pQuery,



                        Len,



                        Flags,



                        MaxDocsScanned,



                        MaxEntriesScanned,
    


                        MaxMsecs,



                        &retResults,
    


                        &retError,



                        &retExplain,



                        hQargList))


            {


                        goto
errout;


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





