What does the script do?
Let me describe it (also if you will use this MD, don't, seriously use the releases instead, this one just tells what the script is doing)
@echo off - turns off the input, like the commands, echo on is to let you know what the script is doing
rem if you want custom name, edit WindowsRE to something else, including the dism stuff and mkdir aswell - this is a note, windows usually ignores this, safe to use.
net session >nul 2>&1 && (goto SUCCESS) || (goto FAIL) - this checks if your administrator or not.
:SUCCESS
echo Have you ran this script as administrator? yes
echo winre will be disabled...
@echo on
reagentc /disable - this disables WinRE so that it can mount
@echo off
echo now i will mount winre for you please wait
@echo on
mkdir C:\WindowsRE - makes a folder called WindowsRE at the root of your C:\ Drive
dism.exe /mount-wim /wimfile:%SYSTEMROOT%\System32\Recovery\WinRE.wim /index:1 /mountdir:C:\WindowsRE - uses dism to mount the OS of winre
@echo off
echo Done! WinRE is at C:\WindowsRE, you can add tools now when your done please press a key
dir C:\WindowsRE - Shows you the directory of WinRE
echo Tip: if you want to edit the Registry, open regedit, load hive and go to C:\WinRE\Windows\system32\config
echo then software, sam or any hive, Enjoy!
pause - Stays frozen on demand, like waits for key
echo Are you really sure?
pause
echo Alright! You asked for it
@echo on
DISM /Unmount-Wim /MountDir:C:\WindowsRE /commit - this will unmount and save changes, /commit tells DISM to save the flag
echo The operation completed successfully
pause
