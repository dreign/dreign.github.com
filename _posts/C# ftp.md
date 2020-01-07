---
title: C# ftp
date: 2009-01-06 02:26:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)C#
ftp  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using System;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Configuration;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections.Generic;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Net;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.IO;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace
Wind.Riskfile.Report  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    class
FtpProc  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpServerIP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpUserID;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpPassword;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebRequest reqFTP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private void Connect(String path)//连接ftp  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 根据uri创建FtpWebRequest对象  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP = (FtpWebRequest)FtpWebRequest.Create(new Uri(path));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定数据传输类型  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.UseBinary = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// ftp用户名和密码  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Credentials = new NetworkCredential(ftpUserID, ftpPassword);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public FtpProc()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpServerIP = ConfigurationManager.AppSettings["ReportFTPUrl"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpUserID = ConfigurationManager.AppSettings["ReportUserName"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpPassword = ConfigurationManager.AppSettings["ReportPassWord"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public FtpProc(string ftpServerIP, string ftpUserID, string ftpPassword)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpServerIP = ftpServerIP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpUserID = ftpUserID;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpPassword = ftpPassword;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获取文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string[] GetFileList(string path, string
WRMethods)//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string[] downloadFiles;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StringBuilder result = new StringBuilder();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(path);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WRMethods;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
WebResponse response = reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader reader = new StreamReader(response.GetResponseStream(),
System.Text.Encoding.Default);//中文文件名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string line = reader.ReadLine();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (line != null)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Append(line);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Append(" ");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line = reader.ReadLine();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// to remove the trailing ' '  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Remove(result.ToString().LastIndexOf(' '), 1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reader.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return result.ToString().Split(' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
downloadFiles = null;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return downloadFiles;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFileList(string path)//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList( ftpServerIP + "/" + path,
WebRequestMethods.Ftp.ListDirectory);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFileList()//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList( ftpServerIP + "/", WebRequestMethods.Ftp.ListDirectory);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void Upload(string filename) //上面的代码实现了从ftp服务器上载文件的功能  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfo fileInf = new FileInfo(filename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri =  ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 默认为true，连接不会被关闭  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 在一个命令之后被执行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.KeepAlive = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定执行什么命令  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.UploadFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 上传文件时通知服务器文件的大小  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.ContentLength = fileInf.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 缓冲大小设置为kb  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int buffLength = 2048;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] buff = new byte[buffLength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int contentLen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 打开一个文件流(System.IO.FileStream) 去读上传的文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fs = fileInf.OpenRead();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 把上传的文件写入流  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Stream strm = reqFTP.GetRequestStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 每次读文件流的kb  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
contentLen = fs.Read(buff, 0, buffLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 流内容没有结束  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (contentLen != 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 把内容从file stream 写入upload stream  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strm.Write(buff, 0, contentLen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
contentLen = fs.Read(buff, 0, buffLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 关闭两个流  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strm.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message, "Upload Error");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
public bool Download(string filePath, string fileName, out string
errorinfo)/**//**//**/////上面的代码实现了从ftp服务器下载文件的功能  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
String onlyFileName = Path.GetFileName(fileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string newFileName = filePath + "\\\" + onlyFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (File.Exists(newFileName))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = string.Format("本地文件{0}已存在,无法下载", newFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string url = ftpServerIP + "/" + fileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(url);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Credentials = new NetworkCredential(ftpUserID, ftpPassword);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Stream ftpStream = response.GetResponseStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long cl = response.ContentLength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int bufferSize = 2048;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int readCount;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] buffer = new byte[bufferSize];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
readCount = ftpStream.Read(buffer, 0, bufferSize);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream outputStream = new FileStream(newFileName, FileMode.Create);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (readCount > 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outputStream.Write(buffer, 0, readCount);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
readCount = ftpStream.Read(buffer, 0, bufferSize);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ftpStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outputStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = string.Format("因{0},无法下载", ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
删除文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="ftpUri"></param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns></returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public bool DeleteFile(string ftpUri)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Uri serverUri = new Uri(ftpUri);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (serverUri.Scheme != Uri.UriSchemeFtp)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// Get the object used to communicate with the server.  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
request.Method = WebRequestMethods.Ftp.DeleteFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine("Delete status: {0}", response.StatusDescription);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void DeleteFileName(string fileName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfo fileInf = new FileInfo(fileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 默认为true，连接不会被关闭  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 在一个命令之后被执行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.KeepAlive = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定执行什么命令  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.DeleteFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message, "删除错误");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//创建目录  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void MakeDir(string dirName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + dirName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.MakeDirectory;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除目录  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void delDir(string dirName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + dirName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.RemoveDirectory;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件大小  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public long GetFileSize(string filename)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long fileSize = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.GetFileSize;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fileSize = response.ContentLength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return fileSize;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//文件改名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void Rename(string currentFilename, string newFilename)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FileInfo fileInf = new FileInfo(currentFilename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string uri = "ftp://" + ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + currentFilename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.Rename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.RenameTo = newFilename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Stream ftpStream = response.GetResponseStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//ftpStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件明晰  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFilesDetailList()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList(ftpServerIP + "/",
WebRequestMethods.Ftp.ListDirectoryDetails);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件明晰  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFilesDetailList(string path)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList(ftpServerIP + "/" + path,
WebRequestMethods.Ftp.ListDirectoryDetails);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)

---
title: C# ftp
date: 2009-01-06 02:26:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)C#
ftp  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using System;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Configuration;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections.Generic;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Net;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.IO;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace
Wind.Riskfile.Report  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    class
FtpProc  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpServerIP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpUserID;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string ftpPassword;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebRequest reqFTP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private void Connect(String path)//连接ftp  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 根据uri创建FtpWebRequest对象  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP = (FtpWebRequest)FtpWebRequest.Create(new Uri(path));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定数据传输类型  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.UseBinary = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// ftp用户名和密码  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Credentials = new NetworkCredential(ftpUserID, ftpPassword);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public FtpProc()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpServerIP = ConfigurationManager.AppSettings["ReportFTPUrl"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpUserID = ConfigurationManager.AppSettings["ReportUserName"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpPassword = ConfigurationManager.AppSettings["ReportPassWord"];  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public FtpProc(string ftpServerIP, string ftpUserID, string ftpPassword)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpServerIP = ftpServerIP;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpUserID = ftpUserID;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.ftpPassword = ftpPassword;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获取文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string[] GetFileList(string path, string
WRMethods)//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string[] downloadFiles;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StringBuilder result = new StringBuilder();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(path);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WRMethods;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
WebResponse response = reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader reader = new StreamReader(response.GetResponseStream(),
System.Text.Encoding.Default);//中文文件名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string line = reader.ReadLine();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (line != null)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Append(line);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Append(" ");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line = reader.ReadLine();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// to remove the trailing ' '  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
result.Remove(result.ToString().LastIndexOf(' '), 1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reader.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return result.ToString().Split(' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
downloadFiles = null;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return downloadFiles;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFileList(string path)//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList( ftpServerIP + "/" + path,
WebRequestMethods.Ftp.ListDirectory);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFileList()//上面的代码示例了如何从ftp服务器上获得文件列表  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList( ftpServerIP + "/", WebRequestMethods.Ftp.ListDirectory);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void Upload(string filename) //上面的代码实现了从ftp服务器上载文件的功能  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfo fileInf = new FileInfo(filename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri =  ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 默认为true，连接不会被关闭  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 在一个命令之后被执行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.KeepAlive = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定执行什么命令  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.UploadFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 上传文件时通知服务器文件的大小  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.ContentLength = fileInf.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 缓冲大小设置为kb  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int buffLength = 2048;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] buff = new byte[buffLength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int contentLen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 打开一个文件流(System.IO.FileStream) 去读上传的文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fs = fileInf.OpenRead();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 把上传的文件写入流  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Stream strm = reqFTP.GetRequestStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 每次读文件流的kb  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
contentLen = fs.Read(buff, 0, buffLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 流内容没有结束  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (contentLen != 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 把内容从file stream 写入upload stream  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strm.Write(buff, 0, contentLen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
contentLen = fs.Read(buff, 0, buffLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 关闭两个流  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strm.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message, "Upload Error");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
public bool Download(string filePath, string fileName, out string
errorinfo)/**//**//**/////上面的代码实现了从ftp服务器下载文件的功能  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
String onlyFileName = Path.GetFileName(fileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string newFileName = filePath + "\\\" + onlyFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (File.Exists(newFileName))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = string.Format("本地文件{0}已存在,无法下载", newFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string url = ftpServerIP + "/" + fileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(url);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Credentials = new NetworkCredential(ftpUserID, ftpPassword);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Stream ftpStream = response.GetResponseStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long cl = response.ContentLength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int bufferSize = 2048;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int readCount;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] buffer = new byte[bufferSize];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
readCount = ftpStream.Read(buffer, 0, bufferSize);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream outputStream = new FileStream(newFileName, FileMode.Create);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (readCount > 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outputStream.Write(buffer, 0, readCount);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
readCount = ftpStream.Read(buffer, 0, bufferSize);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ftpStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outputStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
errorinfo = string.Format("因{0},无法下载", ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
删除文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="ftpUri"></param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns></returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public bool DeleteFile(string ftpUri)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Uri serverUri = new Uri(ftpUri);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (serverUri.Scheme != Uri.UriSchemeFtp)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// Get the object used to communicate with the server.  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
request.Method = WebRequestMethods.Ftp.DeleteFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine("Delete status: {0}", response.StatusDescription);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除文件  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void DeleteFileName(string fileName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfo fileInf = new FileInfo(fileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 默认为true，连接不会被关闭  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 在一个命令之后被执行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.KeepAlive = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// 指定执行什么命令  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.DeleteFile;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message, "删除错误");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//创建目录  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void MakeDir(string dirName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + dirName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.MakeDirectory;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除目录  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void delDir(string dirName)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + dirName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.RemoveDirectory;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件大小  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public long GetFileSize(string filename)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long fileSize = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.GetFileSize;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fileSize = response.ContentLength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return fileSize;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//文件改名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void Rename(string currentFilename, string newFilename)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FileInfo fileInf = new FileInfo(currentFilename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string uri = "ftp://" + ftpServerIP + "/" + fileInf.Name;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string uri = ftpServerIP + "/" + currentFilename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Connect(uri);//连接  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.Method = WebRequestMethods.Ftp.Rename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
reqFTP.RenameTo = newFilename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FtpWebResponse response = (FtpWebResponse)reqFTP.GetResponse();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Stream ftpStream = response.GetResponseStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//ftpStream.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
response.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Console.WriteLine(ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件明晰  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFilesDetailList()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList(ftpServerIP + "/",
WebRequestMethods.Ftp.ListDirectoryDetails);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//获得文件明晰  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string[] GetFilesDetailList(string path)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetFileList(ftpServerIP + "/" + path,
WebRequestMethods.Ftp.ListDirectoryDetails);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)

