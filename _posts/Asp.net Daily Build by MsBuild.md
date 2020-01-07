---
title: Asp.net Daily Build by MsBuild
date: 2013-11-15 08:31:00
tags: 
categories: 
---
:: 目录结构  
:: +GW.Point.BLL --dir dll  
:: +GW.Point.IBLL --dir dll  
:: +GW.Point.DAL --dir dll  
:: +GW.Point.IDAL --dir dll  
:: +GW.Point.Model --dir dll  
:: +GW.Point.Manager --dir web  
:: -GW.Point.Web.csproj --file  
:: +GW.Point.Web --dir web  
:: -GW.Point.Web.csproj --file  
:: -GWPoint.sln --file sln

@echo off

::获取文件名  
set WebAppPath=%~n0  
set WebAppName=%WebAppPath%\%~n0.csproj  
::echo %WebAppName%  
::部署路径  
set DeployPath=%CD%\%WebAppPath%_deploy  
::@pause

set path=C:\WINDOWS\Microsoft.NET\Framework\v4.0.30319  
::set path=C:\WINDOWS\Microsoft.NET\Framework\v3.5  
::set path=C:\WINDOWS\Microsoft.NET\Framework\v3.0  
::set path=C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727  
::set path=C:\WINDOWS\Microsoft.NET\Framework\v1.1.4322  
::set path=C:\WINDOWS\Microsoft.NET\Framework\v1.0.3705

::@echo %path%

echo Delete the %WebAppPath%_deploy directory!  
@rd %WebAppPath%_deploy /s/q  
@md %WebAppPath%_deploy

echo Building %WebAppName%, please wait a minute...

"%path%\MsBuild.exe" %WebAppName% /t:rebuild /p:configuration=Release
/t:ResolveReferences;Compile;_CopyWebApplication
/p:OutputPath=%DeployPath%\bin /p:WebProjectOutputDir=%DeployPath%
>%WebAppPath%.log

echo Building %WebAppName% Complete! (%WebAppPath%.log)  
::@pause

