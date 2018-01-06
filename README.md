# DOS_bat
@echo off 
::DateTime 	  2018-1-7
::Author	    Hans
::Version	    v-01.3
::Description	LCMBase TIMCommand Output Report Files
::

set var1=D:\Logs\012_20160525_0901
set var2=%date:~4,2%%date:~7,2%%date:~10,4%
set addr=127.0.0.1
if exist %var1% (cd %var1%) else (echo not exist %var1%,please exit!)
mkdir %var2% && dir 
echo;
echo;

ping -n 6 %addr% >nul
for /R %%i in (*) do (trlist -S %%i -a > %%i.txt)
for /R %%i in (*.txt) do (copy %%i .\%var2%)
if %errorlevel%==0 (echo OK...) else echo Failure...

echo;
echo;

cd %var2% && dir
echo;
echo;

pause
