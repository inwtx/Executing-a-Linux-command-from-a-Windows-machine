# Executing-a-Linux-command-from-a-Windows-machine  
  
  It is possible to execute Linux commands and a bash scripts from a Windows machine using a batch file with Putty.  
  
  1. Download Putty if you don't aready have it.  
     Putty: https://www.chiark.greenend.org.uk/~sgtatham/putty/  
   
  2. It would be best to run you Windows batch files in a program such as free Mobaxterm program.  It will give you a wider terminal window.  
     https://mobaxterm.mobatek.net/
  
  3. You will use the PLINK.EXE in he Putty folder to execute commands. Your batch file will look something like this:
  
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

"C:\Putty\PLINK.EXE" root@nnn.nnn.nnn.nnn -i "C:\Putty\ED25519key.ppk" -P 22 mailq
"C:\Putty\PLINK.EXE" root@nnn.nnn.nnn.nnn -P 22 mailq

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

"C:\Putty\PLINK.EXE" root@nnn.nnn.nnn.nnn -i "C:\Putty\ED25519key.ppk" -P 22 /etc/some_bash_script.sh any_needed_param1 param2
"C:\Putty\PLINK.EXE" root@nnn.nnn.nnn.nnn -P 22 /etc/some_bash_script.sh any_needed_param1 param2

Pause
```
