---
title: c#实现文件加解密
date: 2007-05-18 01:48:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using System;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.IO;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Data;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Windows.Forms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections.Generic;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security.Cryptography;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Threading;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.ComponentModel;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace aaa  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)     class
En_Dn  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private Hashtable hs = new Hashtable();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private RijndaelManaged myRijndael;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string Key = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string IV =
"~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string 解密(string files, int a)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileName = Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string inFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
inFileName = (string)de.Value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(fin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] infolengthchar = new char[5];//文件的最后五个字符代表加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-5, SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(infolengthchar, 0, 5);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string infolengthstr = new string(infolengthchar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int infolength = Convert.ToInt32(infolengthstr);//加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-(5 + infolength), SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] Filedatachar = new char[infolength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(Filedatachar, 0, infolength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedatastr = new string(Filedatachar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedatastr = this.Decrypt(Filedatastr);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = Convert.ToInt32(Filedatastr.Substring(Filedatastr.Length - 5, 5));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfomation[] FI = new FileInfomation[count];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FI[i] = new FileInfomation();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// FI[i].Filename = Filedatastr.Substring(i * 150, 100).TrimStart(new char[] {
' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Filename = "~" + Filedatastr.Substring(i * 150, 100).TrimStart(new
char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Size = Convert.ToInt32(Filedatastr.Substring(i * 150 + 100,
50).TrimStart(new char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' }));  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//已得到该文件中包括的文件个数、文件名、长度。开始解密。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long start = 0, currentlength = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = CPath + "\\\" + FI[0].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outFileName = CPath + "\\\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(outFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
currentlength = FI[i].Size;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.OpenOrCreate,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.SetLength(0);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(start, SeekOrigin.Begin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int cut = 100000;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[cut];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = currentlength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int report = (int)(((double)rdlen / totlen) * 1000);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (totlen - rdlen < cut)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cut = (int)(totlen - rdlen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = totlen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, cut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return outFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// MessageBox.Show("在文件解密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string 解密(string files)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string pw = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FileName = Path.GetFileNameWithoutExtension(this.files) + "~.tif";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileName = Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Key = pw;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = "~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Directory.CreateDirectory(CPath + "\\\已解密的文件");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string inFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
inFileName = (string)de.Value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(fin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] infolengthchar = new char[5];//文件的最后五个字符代表加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-5, SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(infolengthchar, 0, 5);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string infolengthstr = new string(infolengthchar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int infolength = Convert.ToInt32(infolengthstr);//加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-(5 + infolength), SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] Filedatachar = new char[infolength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(Filedatachar, 0, infolength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedatastr = new string(Filedatachar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedatastr = this.Decrypt(Filedatastr);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = Convert.ToInt32(Filedatastr.Substring(Filedatastr.Length - 5, 5));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfomation[] FI = new FileInfomation[count];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FI[i] = new FileInfomation();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FI[i].Filename = Filedatastr.Substring(i * 150, 100).TrimStart(new char[] {
' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Filename = "~" + Filedatastr.Substring(i * 150, 100).TrimStart(new
char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Size = Convert.ToInt32(Filedatastr.Substring(i * 150 + 100,
50).TrimStart(new char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' }));  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//已得到该文件中包括的文件个数、文件名、长度。开始解密。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long start = 0, currentlength = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string outFileName = CPath + @"\已解密的文件\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outFileName = CPath + "\\\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(outFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
currentlength = FI[i].Size;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.OpenOrCreate,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.SetLength(0);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(start, SeekOrigin.Begin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int cut = 100000;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[cut];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = currentlength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (totlen - rdlen < cut)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cut = (int)(totlen - rdlen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = totlen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, cut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return outFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("在文件解密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private void 加密(string files, string newname)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string pw = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string FileName = "~" + Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Key = pw;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = "~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = newname;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedata = "";//文件名(100字节)长度(50)个数(5)前补空格 加密后 长度(5)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long curlength = -16;//这里是负16,我也不知道是为什么,第一次读fout长度时会少16,以后再读都正常  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.Append,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream((string)de.Value, FileMode.Open,
FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[100000];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = fin.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, 100000);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long foutlenth = fout.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += Path.GetFileName((string)de.Value).PadLeft(100, ' ') + (foutlenth
- curlength).ToString().PadLeft(50, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
curlength = foutlenth;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
count++;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += count.ToString().PadLeft(5, '0');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata = this.Encrypt(Filedata);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += Filedata.Length.ToString().PadLeft(5, '0');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream f = new FileStream(outFileName, FileMode.Append, FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamWriter sw = new StreamWriter(f);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sw.Write(Filedata);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sw.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
f.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("在文件加密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
获得密钥  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>密钥</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetLegalKey()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string sTemp = Key;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.GenerateKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytTemp = myRijndael.Key;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int KeyLength = bytTemp.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (sTemp.Length > KeyLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.Substring(0, KeyLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (sTemp.Length < KeyLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.PadRight(KeyLength, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return System.Text.ASCIIEncoding.ASCII.GetBytes(sTemp);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
获得初始向量IV  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>初试向量IV</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetLegalIV()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string sTemp = IV;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.GenerateIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytTemp = myRijndael.IV;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int IVLength = bytTemp.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (sTemp.Length > IVLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.Substring(0, IVLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (sTemp.Length < IVLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.PadRight(IVLength, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return System.Text.ASCIIEncoding.ASCII.GetBytes(sTemp);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
加密方法  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="Source">待加密的串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>经过加密的串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string Encrypt(string Source)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytIn = System.Text.UTF8Encoding.UTF8.GetBytes(Source);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(ms, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bytIn, 0, bytIn.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytOut = ms.ToArray();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Convert.ToBase64String(bytOut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
throw new Exception("在文件加密的时候出现错误！错误提示： \n" + ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
解密方法  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="Source">待解密的串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>经过解密的串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string Decrypt(string Source)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytIn = Convert.FromBase64String(Source);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms = new MemoryStream(bytIn, 0, bytIn.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(ms, encrypto, CryptoStreamMode.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(cs);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return sr.ReadToEnd();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
throw new Exception("在文件解密的时候出现错误！错误提示： \n" + ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)

---
title: c#实现文件加解密
date: 2007-05-18 01:48:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using System;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.IO;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Data;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Windows.Forms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Collections.Generic;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security.Cryptography;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Threading;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.ComponentModel;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace aaa  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)     class
En_Dn  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private Hashtable hs = new Hashtable();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private RijndaelManaged myRijndael;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string Key = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string IV =
"~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string 解密(string files, int a)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileName = Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string inFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
inFileName = (string)de.Value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(fin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] infolengthchar = new char[5];//文件的最后五个字符代表加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-5, SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(infolengthchar, 0, 5);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string infolengthstr = new string(infolengthchar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int infolength = Convert.ToInt32(infolengthstr);//加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-(5 + infolength), SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] Filedatachar = new char[infolength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(Filedatachar, 0, infolength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedatastr = new string(Filedatachar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedatastr = this.Decrypt(Filedatastr);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = Convert.ToInt32(Filedatastr.Substring(Filedatastr.Length - 5, 5));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfomation[] FI = new FileInfomation[count];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FI[i] = new FileInfomation();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// FI[i].Filename = Filedatastr.Substring(i * 150, 100).TrimStart(new char[] {
' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Filename = "~" + Filedatastr.Substring(i * 150, 100).TrimStart(new
char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Size = Convert.ToInt32(Filedatastr.Substring(i * 150 + 100,
50).TrimStart(new char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' }));  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//已得到该文件中包括的文件个数、文件名、长度。开始解密。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long start = 0, currentlength = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = CPath + "\\\" + FI[0].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outFileName = CPath + "\\\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(outFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
currentlength = FI[i].Size;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.OpenOrCreate,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.SetLength(0);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(start, SeekOrigin.Begin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int cut = 100000;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[cut];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = currentlength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int report = (int)(((double)rdlen / totlen) * 1000);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (totlen - rdlen < cut)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cut = (int)(totlen - rdlen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = totlen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, cut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Dispose();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return outFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// MessageBox.Show("在文件解密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string 解密(string files)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string pw = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FileName = Path.GetFileNameWithoutExtension(this.files) + "~.tif";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileName = Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Key = pw;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = "~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Directory.CreateDirectory(CPath + "\\\已解密的文件");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string inFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
inFileName = (string)de.Value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(fin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] infolengthchar = new char[5];//文件的最后五个字符代表加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-5, SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(infolengthchar, 0, 5);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string infolengthstr = new string(infolengthchar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int infolength = Convert.ToInt32(infolengthstr);//加密后的文件信息长度  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(-(5 + infolength), SeekOrigin.End);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
char[] Filedatachar = new char[infolength];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sr.Read(Filedatachar, 0, infolength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedatastr = new string(Filedatachar);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedatastr = this.Decrypt(Filedatastr);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = Convert.ToInt32(Filedatastr.Substring(Filedatastr.Length - 5, 5));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileInfomation[] FI = new FileInfomation[count];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FI[i] = new FileInfomation();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//FI[i].Filename = Filedatastr.Substring(i * 150, 100).TrimStart(new char[] {
' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Filename = "~" + Filedatastr.Substring(i * 150, 100).TrimStart(new
char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' });  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
FI[i].Size = Convert.ToInt32(Filedatastr.Substring(i * 150 + 100,
50).TrimStart(new char[] ![](http://www.cnblogs.com/Images/dot.gif){ ' ' }));  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//已得到该文件中包括的文件个数、文件名、长度。开始解密。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long start = 0, currentlength = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string outFileName = CPath + @"\已解密的文件\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
outFileName = CPath + "\\\" + FI[i].Filename;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(outFileName);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
currentlength = FI[i].Size;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin = new FileStream(inFileName, FileMode.Open, FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.OpenOrCreate,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.SetLength(0);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Seek(start, SeekOrigin.Begin);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int cut = 100000;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[cut];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = currentlength;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (totlen - rdlen < cut)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cut = (int)(totlen - rdlen);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = totlen;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, cut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return outFileName;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("在文件解密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private void 加密(string files, string newname)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int id = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
hs.Add(id++, files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string pw = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string CPath = Path.GetDirectoryName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string FileName = "~" + Path.GetFileName(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael = new RijndaelManaged();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Key = pw;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = "~!#@$%HGF^&%&^hggk)KJKL989#er345(&*(HBh(u%g6HJ($jhWk7&!hg4ui%$hjk";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string outFileName = newname;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string Filedata = "";//文件名(100字节)长度(50)个数(5)前补空格 加密后 长度(5)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long curlength = -16;//这里是负16,我也不知道是为什么,第一次读fout长度时会少16,以后再读都正常  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
foreach (System.Collections.DictionaryEntry de in this.hs)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fout = new FileStream(outFileName, FileMode.Append,
FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream fin = new FileStream((string)de.Value, FileMode.Open,
FileAccess.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bin = new byte[100000];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long rdlen = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long totlen = fin.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(fout, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
while (rdlen < totlen)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
len = fin.Read(bin, 0, 100000);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bin, 0, len);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
rdlen = rdlen + len;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
long foutlenth = fout.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += Path.GetFileName((string)de.Value).PadLeft(100, ' ') + (foutlenth
- curlength).ToString().PadLeft(50, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
curlength = foutlenth;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
count++;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fout.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
fin.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += count.ToString().PadLeft(5, '0');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata = this.Encrypt(Filedata);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Filedata += Filedata.Length.ToString().PadLeft(5, '0');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FileStream f = new FileStream(outFileName, FileMode.Append, FileAccess.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamWriter sw = new StreamWriter(f);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sw.Write(Filedata);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sw.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
f.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(files);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("在文件加密的时候出现错误！错误提示： \n" + ex.Message, "",
MessageBoxButtons.OK, MessageBoxIcon.Error);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
获得密钥  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>密钥</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetLegalKey()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string sTemp = Key;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.GenerateKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytTemp = myRijndael.Key;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int KeyLength = bytTemp.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (sTemp.Length > KeyLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.Substring(0, KeyLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (sTemp.Length < KeyLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.PadRight(KeyLength, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return System.Text.ASCIIEncoding.ASCII.GetBytes(sTemp);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
获得初始向量IV  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>初试向量IV</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetLegalIV()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string sTemp = IV;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.GenerateIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytTemp = myRijndael.IV;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int IVLength = bytTemp.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (sTemp.Length > IVLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.Substring(0, IVLength);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (sTemp.Length < IVLength)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sTemp = sTemp.PadRight(IVLength, ' ');  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return System.Text.ASCIIEncoding.ASCII.GetBytes(sTemp);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
加密方法  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="Source">待加密的串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>经过加密的串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string Encrypt(string Source)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytIn = System.Text.UTF8Encoding.UTF8.GetBytes(Source);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(ms, encrypto, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(bytIn, 0, bytIn.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytOut = ms.ToArray();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Convert.ToBase64String(bytOut);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
throw new Exception("在文件加密的时候出现错误！错误提示： \n" + ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
解密方法  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="Source">待解密的串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>经过解密的串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string Decrypt(string Source)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] bytIn = Convert.FromBase64String(Source);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms = new MemoryStream(bytIn, 0, bytIn.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.Key = GetLegalKey();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
myRijndael.IV = GetLegalIV();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform encrypto = myRijndael.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs = new CryptoStream(ms, encrypto, CryptoStreamMode.Read);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
StreamReader sr = new StreamReader(cs);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return sr.ReadToEnd();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ex)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
throw new Exception("在文件解密的时候出现错误！错误提示： \n" + ex.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)

