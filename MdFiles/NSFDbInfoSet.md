




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




 


**Function : Database**



**NSFDbInfoSet** **- Sets the
database information buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbInfoSet(**  

      DBHANDLE  hDB,  

      char far \*Buffer**);**



**Description :**



This
function sets the database information buffer in a Domino database.  The
information buffer is a character array that is NSF\_INFO\_SIZE bytes and
consists of one or more of the following pieces of information: database title,
categories, class, and design class. You can use NSFDbInfoGet to first get the
database information buffer, then use NSFDbInfoModify to change any one piece
of information in the database information buffer, and then use NSFDbInfoSet to
store the modified database information buffer in the database.      

  

Database information appears in the Notes UI, in the File, Database, Properties
InfoBox.  Clicking the Basics tab displays the Title field with the database
title.  Selecting the Design tab opens the Design tabbed page. The database
class is displayed in the Database is a template/Template Name field and the
database design class is displayed in the Inherit design from template/Template
Name field. The Categories field displays the database categories.  Database
categories are different than view categories.  Database categories are
keywords specified for the database.  Each server's database catalog
(CATALOG.NSF) contains a view, called Databases by Category, which lists only
the categorized databases.


 


**Parameters :**



Input :  

hDB  -  The handle to the database for which you want to set the database
information buffer.  

  

Buffer  -  A pointer to a text buffer of length NSF\_INFO\_SIZE.  The text buffer
consists of one or more of the following pieces of information:  database
title, categories, class, and design class.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is.  The return codes include:  

  

NOERROR  

ERR\_NSF\_INFO\_SIZE  

ERR\_NOACCESS  

  

  




 **Sample Usage :**


  

   /\* Copy the Db tile \*/  

  

   if (error\_status = NSFDbInfoGet(db\_handle\_src, db\_info))  

       goto Exit;  

   if (error\_status = NSFDbInfoSet(db\_handle\_dst, db\_info))  

       goto Exit;  

  




 **See Also :**


**[NSFDbInfoGet](NSFDbInfoGet.md)**


**[NSFDbInfoModify](NSFDbInfoModify.md)**



----------------------------------------------------------------------------------------------------------


 





