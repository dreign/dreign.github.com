---
title: 用dos批处理程序检测是否安装.netframework,并自动安装后运行指定程序(.net自启动光盘的制做)
date: 2007-01-23 03:22:00
tags: 
categories: 
---
.net自启动光盘的制做:  
  
autorun.inf       \---  自启动引导文件  
app.ico            \---   光盘图标文件  
install.bat         \---   检测安装批处理文件  
应用程序.exe ---  要运行的程序  
  
以及dotNetFramework2.0 所需文件  
  
autorun.inf [AutoRun]  
icon=app.ico  
open=install.bat  
  

install.bat@echo off  
@copy LMSoftDogDotNet.dll "%windir%\system32"  
@Regsvr32 /s "%windir%\system32\LMSoftDogDotNet.dll"  
@echo 注册成功！

@if exist "%windir%\Microsoft.NET\Framework\v2.0.50727" goto END  
echo 开始安装系统组件 . . .

:INSTALL  
echo 开始安装:Windows Installer 3.1 (KB893803)  
@.\dotNetFramework2.0\WindowsInstaller-KB893803-v2-x86.exe  
echo 开始安装:dotNetFramework 2.0  
@.\dotNetFramework2.0\dotnetfx.exe  
echo 开始安装:dotNetFramework 2.0 中文语言包  
@.\dotNetFramework2.0\langpack.exe  
echo 开始安装:Microsoft Data Access Components 2.8  
@.\dotNetFramework2.0\MDAC_TYP.EXE  
echo 系统组件安转完成!

:END

@start 应用程序.exe

//注:开头注册控件的不必须

---
title: 用dos批处理程序检测是否安装.netframework,并自动安装后运行指定程序(.net自启动光盘的制做)
date: 2007-01-23 03:22:00
tags: 
categories: 
---
.net自启动光盘的制做:  
  
autorun.inf       \---  自启动引导文件  
app.ico            \---   光盘图标文件  
install.bat         \---   检测安装批处理文件  
应用程序.exe ---  要运行的程序  
  
以及dotNetFramework2.0 所需文件  
  
autorun.inf [AutoRun]  
icon=app.ico  
open=install.bat  
  

install.bat@echo off  
@copy LMSoftDogDotNet.dll "%windir%\system32"  
@Regsvr32 /s "%windir%\system32\LMSoftDogDotNet.dll"  
@echo 注册成功！

@if exist "%windir%\Microsoft.NET\Framework\v2.0.50727" goto END  
echo 开始安装系统组件 . . .

:INSTALL  
echo 开始安装:Windows Installer 3.1 (KB893803)  
@.\dotNetFramework2.0\WindowsInstaller-KB893803-v2-x86.exe  
echo 开始安装:dotNetFramework 2.0  
@.\dotNetFramework2.0\dotnetfx.exe  
echo 开始安装:dotNetFramework 2.0 中文语言包  
@.\dotNetFramework2.0\langpack.exe  
echo 开始安装:Microsoft Data Access Components 2.8  
@.\dotNetFramework2.0\MDAC_TYP.EXE  
echo 系统组件安转完成!

:END

@start 应用程序.exe

//注:开头注册控件的不必须

