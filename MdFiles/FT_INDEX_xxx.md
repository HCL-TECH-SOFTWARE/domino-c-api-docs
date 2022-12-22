




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




 


**Symbolic Value : Full Text Search**



**FT\_INDEX\_xxx** **-** Full text
search indexing options.


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**


 **Symbolic Values :**      FT\_INDEX\_REINDEX           -  Forces re-indexing the
database from scratch. This option is useful if the indexing options for the
database are being changed.  

  

      FT\_INDEX\_CASE\_SENS      -  Build case sensitive index.  

  

      FT\_INDEX\_STEM\_INDEX     -  Build an index that includes word variants
(stems). This allows searching to include word variants. A full text search
index built with the Notes user interface, is automatically stemmed.  

  

      FT\_INDEX\_PSW      -  Build index with word, sentence, and paragraph index
break option which allows a search for words within a sentence or paragraph.  

  

      FT\_INDEX\_OPTIMIZE          -  Optimize index (e.g. for CDROM).  

  

      FT\_INDEX\_ATT       -  Index Attachments.  

  

      FT\_INDEX\_ENCRYPTED\_FIELDS    -  Index Encrypted Fields.  

  

      FT\_INDEX\_AUTOOPTIONS             -  Use the index options that are in
database. If the database has never been indexed, use the default indexing
options. Database indexing options include the Stop Word File name, case
sensitivity, the PSW option, reindexing, and the stem index. Note that the stem
index will be set if FT\_INDEX\_AUTOOPTIONS is used.  

  

      FT\_INDEX\_SUMMARY\_ONLY          -  Index summary data only.  

  

      FT\_INDEX\_ATT\_BINARY     -  Index all attachments including BINARY
formats.  

  




**Description :**



These values
define the options used when creating a full text index for a database.  These
options may be combined by bitwise OR-ing them together.  However,
FT\_INDEX\_AUTOOPTIONS will ignore all other indexing options and therefore
should not be OR-ed with any of the other indexing options.


 **See Also :**


**[FTIndex](FTIndex.md)**



----------------------------------------------------------------------------------------------------------


 





