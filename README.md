# Executing-a-Linux-command-from-a-Windows-machine  
  
  It is possible to execute Linux commands and bash scripts from a Windows machine using a batch file with Putty.  
  The output will be listed in the Window's terminal window.  
  
  1. Download Putty if you do not aready have it.  
     Putty: https://www.chiark.greenend.org.uk/~sgtatham/putty/  
   
  2. It would be best to run you Windows batch files in a program such as free Mobaxterm program.  It will give you a wider terminal window.   https://mobaxterm.mobatek.net/
  
  3. You will use the PLINK.EXE in the Putty folder to execute commands. Double click on the batch file to execute it. Ther are two examples below, the first you use if your server has an SSH key and the second for severs that have just password entry. Your batch file will look something like this:
  
Example 1:  
Batch file name: Display_mailq.bat
```
echo OFF
echo.
echo ===============
echo  Display mailq
echo ===============
echo.

REM nnn.nnn.nnn.nnn = your server IP
REM -i = your server SSH key if it has one
REM -p = your connection port number
REM mailq = display mailq

"C:\Putty\PLINK.EXE" -no-antispoof root@nnn.nnn.nnn.nnn -i "C:\Putty\ED25519key.ppk" -P 22 mailq
"C:\Putty\PLINK.EXE" -no-antispoof root@nnn.nnn.nnn.nnn -P 22 mailq

Pause
```
  
Example 2:  
Batch file name: Run Some_bash_script.bat
```
echo OFF
echo.
echo =========================
echo  Run some_bash_script.sh
echo =========================
echo.

REM nnn.nnn.nnn.nnn = your server IP
REM -i = your server SSH key if it has one
REM -p = your connection port number
REM mailq = display mailq  
REM param1 param2 = any needed input parameters may follow

"C:\Putty\PLINK.EXE" -no-antispoof root@nnn.nnn.nnn.nnn -i "C:\Putty\ED25519key.ppk" -P 22 /etc/some_bash_script.sh param1 param2
"C:\Putty\PLINK.EXE" -no-antispoof root@nnn.nnn.nnn.nnn -P 22 /etc/some_bash_script.sh param1 param2

Pause
```
  
  
Note: If the -no-antispoof parameter causes an error, then take it out. It works in the latest PLINK.EXE.  
Note: There seems to be a bug in the PLINK.EXE program.  Be sure the executable is in capitals and keep  
      a backup of your keys. Executing PLINK.EXE with lower letters has caused the program to auto capitalize  
      itself and then corrupt the keys.  

