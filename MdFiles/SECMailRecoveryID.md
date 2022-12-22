




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




**Initial Release 8.0**



**Function : Recovery**



**SECMailRecoveryID** **- Mail a
backup ID file based on the recovery information stored in an id file**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECMailRecoveryID(**  

      char \*pIDFileName,  

      KFM\_PASSWORD \*pCurrentPW,  

      char \*pSubjectText,  

      char \*pMailFileName,  

      void \*pReserved,  

      DWORD  ReservedFlags**);**



**Description :**



Given the
name of the ID file,password, subject line material and the mailfile name from
which to mail, mail an id recovery backup copy of the id file to the configured
mail in database.


Routine:  

            1.Create a temp file name to become the ID recovery backup ID file.  

            2.Read all the recovery information out of IDFile.  

            3.Create the ID recovery backup ID file.  

            4.Create a mail note in the pMailFileName database.  

            5.Attach the Id recovery backup ID file.  

            6.Set the from, to, and the composed time/date fields of the mail
message  

            7.Set the subject line to what the caller passes in pSubjectText  

            8.Convert the to field to an address list  

            9.Submit the mail for delivery signed by the currently running ID
file.


 


**Parameters :**



Input :  

pIDFileName  -  pointer to name of the ID file to backed up to the recovery
repository  

  

pCurrentPW  -  KFM\_PASSWORD to pIDFileName  

  

pSubjectText  -  pointer to a string of text to appear in  the subject of the
text message  

  

pMailFileName  -  (Optional) mail file to mail from. Mail.box will be used if
NULL passed in.  

  

pReserved  -  reserved - should be set to NULL  

  

ReservedFlags  -  reserved - should be set to 0  

  




Output :  

(routine)  -  NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  




 **Sample Usage :**


        char                 \*puserIDPath
= "D:\\sectester.id";


            KFM\_PASSWORD        retHashedPassWD;


            char
\*pstrSubjectTitle = "sectesterid backup id file";                    //
mail title


 


            SECKFMCreatePassword(puserIDPass,
&retHashedPassWD);


 


            if
(err = SECMailRecoveryID(puserIDPath, &retHashedPassWD, pstrSubjectTitle,
NULL, NULL, 0))


            {


                        printAPIErr(err);


                        NotesTerm();


                        return
1;                                    


            }


 




----------------------------------------------------------------------------------------------------------


 





