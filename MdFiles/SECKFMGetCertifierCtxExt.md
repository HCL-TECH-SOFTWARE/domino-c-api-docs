




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




**Initial Release 8.0.1**



**Function : certifier**



**SECKFMGetCertifierCtxExt** **- Get
certifier context**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMGetCertifierCtxExt(**  

      char far \*pCertFile,  

      KFM\_PASSWORD far \*pKfmPW,  

      char far \*pCAServer,  

      char far \*pCAName,  

      char far \*pLogFile,  

      TIMEDATE far \*pExpDate,  

      char far \*retCertName,  

      HCERTIFIER far \*rethKfmCertCtx,  

      BOOL far \*retfIsHierarchical,  

      WORD far \*retwFileVersion**);**



**Description :**



This
function gets the handle to a certifier context of the given certifier id file.
When done with the certifier context, you are responsible for freeing this
memory by calling SECKFMFreeCertifierCtx(). If an application wants the context
of a Certifier and does not have the id file (possible migrated to CA process)
then they could call this routine with the server name (pCAServer) which the
Certifier (pCAName) is present in its directory. The first two parameters
should be NULL if the pCAServer and pCAName are set to non-NULL.


 


**Parameters :**



Input :  

pCertFile  -  Pathname of the certifier id file.  

  

pKfmPW  -  Optional.  Pointer to KFM\_PASSWORD structure, which contains the 
certifier's encoded password.  Use SECKFMCreatePassword to fill in this
structure with the encoded password, given a non-encoded password.  If NULL is
passed in, and a certifier password is required, you will be prompted to enter
the password.  

  

pCAServer  -  CA server. If pCAServer and pCAName are non NULL, then the CA
context is retrieved from the directory on the pCAServer. If they are NULL the
routine just calls ECKFMGetCertifierCtx.  

  

pCAName  -  CA name. If pCAServer and pCAName are non NULL, then the CA context
is retrieved from the directory on the pCAServer. If they are NULL the routine
just calls SECKFMGetCertifierCtx.  

  

pLogFile  -  Pathname of the certifier's log file.  This parameter is required
for Domino installations that use the Administration Process so that when using
other C API function that require a Certifier Context, the proper entries will
be entered in the Certification Log file (CERTLOG.NSF) .  If your Domino
installation does not include a Certification Log (does not use the
Administration Process), then you should pass in NULL for this parameter.  

  

pExpDate  -  Pointer to the certificate expiration date for the entity that is
being certified.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

  

ERR\_xxx  -  Various OS, and KFM errors.  

  

  

retCertName  -  Returned name of certifier.  

  

rethKfmCertCtx  -  Pointer to returned handle of certifier context.  

  

retfIsHierarchical  -  Contains TRUE if certifier is hierarchical, otherwise
FALSE.  

  

retwFileVersion  -  Pointer to the returned version of the certifier.  

  




 **See Also :**


**[NSFNoteCipherDecrypt](NSFNoteCipherDecrypt.md)**


**[NSFNoteCipherExtractFile](NSFNoteCipherExtractFile.md)**



----------------------------------------------------------------------------------------------------------


 





