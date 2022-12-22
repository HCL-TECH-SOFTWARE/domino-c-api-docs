




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




 


**Function : Database**



**NSFDbInfoModify** **- Modifies
a specified piece of information in the database information buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



void
LNPUBLIC **NSFDbInfoModify(**  

      char far \*Info,  

      WORD  What,  

      const char far \*Buffer**);**



**Description :**



This
function modifies a specified piece of information in the given database
information buffer.  The database information buffer for a database may be
obtained by a call to NSFDbInfoGet.  This buffer contains the following pieces
of information:  database title, categories, class, and design class.  

  

NSFDbInfoSet must be called after NSFDbInfoModify to store the database
information buffer in the database.  

  

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

  

The database title also appears on the Notes Desktop below each database icon.


 


**Note:**


 


      Anytime
you modify the database information buffer of a database, you also need to
modify this information in the Icon note.  Use NSFNoteOpen with the
NOTE\_ID\_SPECIAL+NOTE\_CLASS\_ICON as the NOTEID to open the Icon note.  Then use
NSFItemSetText and specify  FIELD\_TITLE (defined in stdnames.h)  as the
ItemName parameter and a pointer to the database information buffer as the
ItemText parameter.  Be sure to update and close the note.


 


**Parameters :**



Input :  

Info  -  A pointer to the database information buffer.  

  

What  -  What piece of information is to be modified:  

Use one of the INFOPARSE\_xxx symbolic values to specify whether to modify the
database title, categories, template name (for a design template database), or
inherited template name (for a database that inherited its design from a design
template).  

  

Buffer  -  Pointer to the buffer containing the new information.  The buffer
must be a NULL terminated string.  If the buffer contains multiple categories,
the categories must be separated by commas.  Use NULL to clear the original
information.  If the What argument is set to INFOPARSE\_CLASS or
INFOPARSE\_DESIGN\_CLASS and this pointer is NULL, the corresponding Design
Template option will be disabled (unchecked).  

  




 


 **See Also :**


**[INFOPARSE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00A0009F00E800BD85255E5200656916)**


**[NSFDbInfoGet](NSFDbInfoGet.md)**


**[NSFDbInfoSet](NSFDbInfoSet.md)**



----------------------------------------------------------------------------------------------------------


 





