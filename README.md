ACL-MkDir-Tree
==============
This very very simple ACL project shows how to take advantage of the EXECUTE command to  
create a directory tree at runtime.

Imagine you have a project which generates several daily reports and
you want to have all those reports stored in a directory tree like this:
   

      [ACL_Project_Path]
         \Reports
            \2013\01\01: A.rpt, B.rpt, ...
            \2013\01\02: A.rpt, B.rpt, ...
            \2013\01\31: A.rpt, B.rpt, ...
            \2013\02\01: A.rpt, B.rpt, ...
            \2013\12\01: A.rpt, B.rpt, ...
            \2013\12\31: A.rpt, B.rpt, ...
         
This is what this project does. 

The reusable code of this project are the scripts in MakeDir_Scripts folder.
You just need to assign the full path to a DIRNAME variable and run MakeDir script.
It will create all the directory tree.

* Example 1:

If we have a C:\MyReports directory and we do:

      ASSIGN DIRNAME="C:\MyReports\2013\05"
      DO SCRIPT MakeDir

It will create:

      C:\MyReports\2013
      C:\MyReports\2013\05


* Example 2:

If we have a C:\MyReports directory and we do:

      ASSIGN DIRNAME="C:\MyReports\EntrepriseA\Reports\Sales"
      DO SCRIPT MakeDir
      ASSIGN DIRNAME="C:\MyReports\EntrepriseA\Reports\Purchases"
      DO SCRIPT MakeDir
      ASSIGN DIRNAME="C:\MyReports\EntrepriseB\Reports\Sales"
      DO SCRIPT MakeDir
      ASSIGN DIRNAME="C:\MyReports\EntrepriseB\Reports\Purchases"
      DO SCRIPT MakeDir

It will create:

      C:\MyReports\EnterpriseA
      C:\MyReports\EnterpriseA\Reports
      C:\MyReports\EnterpriseA\Reports\Sales
      C:\MyReports\EnterpriseA\Reports\Purchases
      C:\MyReports\EnterpriseB\Reports
      C:\MyReports\EnterpriseB\Reports\Sales
      C:\MyReports\EnterpriseB\Reports\Purchases


HISTORY:

      20130617 - The semicolon separators have been replaced with spaces. 
                 Now the code will run regardless the ACL user config (Thanks to Keith P.)
