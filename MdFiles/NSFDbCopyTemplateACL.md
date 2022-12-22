




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



**NSFDbCopyTemplateACL** **- Copy
database template's ACL to a new database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCopyTemplateACL(**  

      DBHANDLE  hSrcDB,  

      DBHANDLE  hDstDB,  

      char far \*Manager,  

      WORD  DefaultAccessLevel**);**



**Description :**



This
function copies a database template's Access Control List (ACL) to a newly
created database.  This function copies only the ACL entries of the form *[User
Name]* and converts them to the form *User Name* during the copy.  It
also allows you to add one username to the new database's ACL with manager
access.  


 


The *[-Default-]*
entry from the template is copied to the *-Default-* entry in the
destination ACL.  If the original template does not have a *[-Default-]*
entry,  you can specify the default access level for the new database.


 


 NSFDbCopyTemplateACL
does not copy the LocalDomainServers and OtherDomainServers entries when
copying to a remote database.  This is consistent with what occurs in the Notes
user interface when you copy a template ACL to a remote server.


 


**Parameters :**



Input :  

hSrcDB  -  A DBHANDLE to the database template (NTF) to copy from.  

  

hDstDB  -  A DBHANDLE to the new database to copy to.  

  

Manager  -  A pointer to a null-terminated user name you wish to add to the new
database's ACL with ACL\_LEVEL\_MANAGER.  If NULL is used, the user name from the
workstation or server configuration where this function is executed, will be
added to the ACL. See MAXUSERNAME for the maximum length of a user name.  The
user name must be either in canonical fully-qualified form (ie:  CN=John
Doe/OU=Documentation/O=WorkSavers) or as a common name (ie:  John Doe).  Do not
use abbreviated format.  

  

DefaultAccessLevel  -  If the source template has a [-Default-] entry, then
this entry is copied to the -Default- entry in the destination ACL and this
parameter is ignored.  If the source template does not have a [-Default-]
entry, then this parameter specifies a WORD value containing the ACL\_LEVEL\_xxx
you wish to assign as the new database's -Default- access control level.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully copied Template ACL.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


  

   /\* if New DB from a template \*/  

  

   if (argc == 4 && (copy\_type == 'N'  

       || copy\_type == 'G' || copy\_type == 'H'))  

   {  

       /\* If from template, use replicainfo defaults \*/  

  

       replica\_info\_dst.Flags |= REPLFLG\_IGNORE\_DELETES;  

       replica\_info\_dst.CutoffInterval = 90;  

       OSCurrentTIMEDATE(&replica\_info\_dst.Cutoff);  

       if (TimeDateAdjust(&replica\_info\_dst.Cutoff, 0, 0, 0,  

                    -((int) replica\_info\_dst.CutoffInterval), 0, 0))  

           goto Exit;  

  

       if (error\_status = NSFDbCopy(db\_handle\_src, db\_handle\_dst,  

                              copy\_cutoff\_td, NOTE\_CLASS\_ALLNONDATA))  

           goto Exit;  

       if (error\_status = NSFDbCopyTemplateACL(db\_handle\_src,  

                              db\_handle\_dst, user\_name,  

                              ACL\_LEVEL\_MANAGER))  

           goto Exit;  

    }  

  




 **See Also :**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[NSFDbCopyACL](NSFDbCopyACL.md)**



----------------------------------------------------------------------------------------------------------


 





