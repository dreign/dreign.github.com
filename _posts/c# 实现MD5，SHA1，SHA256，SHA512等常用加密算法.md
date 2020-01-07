---
title: c# 实现MD5，SHA1，SHA256，SHA512等常用加密算法
date: 2007-05-18 01:46:00
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
System.Diagnostics;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security.Cryptography;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)/**//*  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif) *
.Net框架由于拥有CLR提供的丰富库支持，只需很少的代码即可实现先前使用C等旧式语言很难实现的加密算法。本类实现一些常用机密算法，供参考。其中MD5算法返回Int的ToString字串。返回数字字母型结果的算法参见之前Blog文章  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif) */  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace
档案数字化加工  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
类名：HashEncrypt  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
作用：对传入的字符串进行Hash运算，返回通过Hash算法加密过的字串。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
属性：［无］  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
构造函数额参数：  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
IsReturnNum:是否返回为加密后字符的Byte代码  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
IsCaseSensitive：是否区分大小写。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
方法：此类提供MD5，SHA1，SHA256，SHA512等四种算法，加密字串的长度依次增大。  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// </summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    public
class HashEncrypt  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//private string strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private bool isReturnNum;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private bool isCaseSensitive;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
类初始化，此类提供MD5，SHA1，SHA256，SHA512等四种算法，加密字串的长度依次增大。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IsCaseSensitive">是否区分大小写</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <param name="IsReturnNum">是否返回为加密后字符的Byte代码</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public HashEncrypt(bool IsCaseSensitive, bool IsReturnNum)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.isReturnNum = IsReturnNum;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.isCaseSensitive = IsCaseSensitive;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string getstrIN(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (strIN.Length == 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strIN = "~NULL~";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (isCaseSensitive == false)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strIN = strIN.ToUpper();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string MD5Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MD5 md5 = new MD5CryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = md5.ComputeHash(GetKeyByteArray(getstrIN(strIN)));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
md5.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA1Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA1 sha1 = new SHA1CryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha1.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha1.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA256Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA256 sha256 = new SHA256Managed();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha256.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha256.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA512Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA512 sha512 = new SHA512Managed();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha512.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha512.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
使用DES加密（Added by niehl 2005-4-6）  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="originalValue">待加密的字符串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="key">密钥(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IV">初始化向量(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>加密后的字符串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESEncrypt(string originalValue, string key, string IV)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//将key和IV处理成8个字符  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key = key.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = IV.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SymmetricAlgorithm sa;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform ct;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] byt;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa = new DESCryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.Key = Encoding.UTF8.GetBytes(key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.IV = Encoding.UTF8.GetBytes(IV);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ct = sa.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byt = Encoding.UTF8.GetBytes(originalValue);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs = new CryptoStream(ms, ct, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(byt, 0, byt.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Convert.ToBase64String(ms.ToArray());  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESEncrypt(string originalValue, string key)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return DESEncrypt(originalValue, key, key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
使用DES解密（Added by niehl 2005-4-6）  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="encryptedValue">待解密的字符串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="key">密钥(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IV">m初始化向量(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>解密后的字符串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESDecrypt(string encryptedValue, string key, string IV)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//将key和IV处理成8个字符  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key = key.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = IV.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SymmetricAlgorithm sa;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform ct;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] byt;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa = new DESCryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.Key = Encoding.UTF8.GetBytes(key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.IV = Encoding.UTF8.GetBytes(IV);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ct = sa.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byt = Convert.FromBase64String(encryptedValue);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs = new CryptoStream(ms, ct, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(byt, 0, byt.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Encoding.UTF8.GetString(ms.ToArray());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESDecrypt(string encryptedValue, string key)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return DESDecrypt(encryptedValue, key, key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string GetStringValue(byte[] Byte)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string tmpString = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.isReturnNum == false)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ASCIIEncoding Asc = new ASCIIEncoding();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpString = Asc.GetString(Byte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int iCounter;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (iCounter = 0; iCounter < Byte.Length; iCounter++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpString = tmpString + Byte[iCounter].ToString();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return tmpString;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetKeyByteArray(string strKey)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ASCIIEncoding Asc = new ASCIIEncoding();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int tmpStrLen = strKey.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte = new byte[tmpStrLen - 1];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = Asc.GetBytes(strKey);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}

---
title: c# 实现MD5，SHA1，SHA256，SHA512等常用加密算法
date: 2007-05-18 01:46:00
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
System.Diagnostics;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)using
System.Security.Cryptography;  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)/**//*  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif) *
.Net框架由于拥有CLR提供的丰富库支持，只需很少的代码即可实现先前使用C等旧式语言很难实现的加密算法。本类实现一些常用机密算法，供参考。其中MD5算法返回Int的ToString字串。返回数字字母型结果的算法参见之前Blog文章  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif) */  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)namespace
档案数字化加工  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
类名：HashEncrypt  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
作用：对传入的字符串进行Hash运算，返回通过Hash算法加密过的字串。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
属性：［无］  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
构造函数额参数：  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
IsReturnNum:是否返回为加密后字符的Byte代码  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
IsCaseSensitive：是否区分大小写。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    ///
方法：此类提供MD5，SHA1，SHA256，SHA512等四种算法，加密字串的长度依次增大。  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// </summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)    public
class HashEncrypt  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//private string strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private bool isReturnNum;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private bool isCaseSensitive;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
类初始化，此类提供MD5，SHA1，SHA256，SHA512等四种算法，加密字串的长度依次增大。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IsCaseSensitive">是否区分大小写</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <param name="IsReturnNum">是否返回为加密后字符的Byte代码</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public HashEncrypt(bool IsCaseSensitive, bool IsReturnNum)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.isReturnNum = IsReturnNum;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.isCaseSensitive = IsCaseSensitive;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string getstrIN(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (strIN.Length == 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strIN = "~NULL~";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (isCaseSensitive == false)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
strIN = strIN.ToUpper();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return strIN;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string MD5Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MD5 md5 = new MD5CryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = md5.ComputeHash(GetKeyByteArray(getstrIN(strIN)));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
md5.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA1Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA1 sha1 = new SHA1CryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha1.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha1.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA256Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA256 sha256 = new SHA256Managed();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha256.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha256.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string SHA512Encrypt(string strIN)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//string strIN = getstrIN(strIN);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SHA512 sha512 = new SHA512Managed();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = sha512.ComputeHash(GetKeyByteArray(strIN));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sha512.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return GetStringValue(tmpByte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
使用DES加密（Added by niehl 2005-4-6）  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="originalValue">待加密的字符串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="key">密钥(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IV">初始化向量(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>加密后的字符串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESEncrypt(string originalValue, string key, string IV)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//将key和IV处理成8个字符  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key = key.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = IV.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SymmetricAlgorithm sa;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform ct;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] byt;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa = new DESCryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.Key = Encoding.UTF8.GetBytes(key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.IV = Encoding.UTF8.GetBytes(IV);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ct = sa.CreateEncryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byt = Encoding.UTF8.GetBytes(originalValue);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs = new CryptoStream(ms, ct, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(byt, 0, byt.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Convert.ToBase64String(ms.ToArray());  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESEncrypt(string originalValue, string key)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return DESEncrypt(originalValue, key, key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//// <summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
使用DES解密（Added by niehl 2005-4-6）  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="encryptedValue">待解密的字符串</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="key">密钥(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)        ///
<param name="IV">m初始化向量(最大长度8)</param>  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
/// <returns>解密后的字符串</returns>  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESDecrypt(string encryptedValue, string key, string IV)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//将key和IV处理成8个字符  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV += "12345678";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
key = key.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
IV = IV.Substring(0, 8);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
SymmetricAlgorithm sa;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ICryptoTransform ct;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MemoryStream ms;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
CryptoStream cs;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] byt;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa = new DESCryptoServiceProvider();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.Key = Encoding.UTF8.GetBytes(key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
sa.IV = Encoding.UTF8.GetBytes(IV);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ct = sa.CreateDecryptor();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byt = Convert.FromBase64String(encryptedValue);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ms = new MemoryStream();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs = new CryptoStream(ms, ct, CryptoStreamMode.Write);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Write(byt, 0, byt.Length);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.FlushFinalBlock();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
cs.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return Encoding.UTF8.GetString(ms.ToArray());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public string DESDecrypt(string encryptedValue, string key)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return DESDecrypt(encryptedValue, key, key);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private string GetStringValue(byte[] Byte)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string tmpString = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.isReturnNum == false)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ASCIIEncoding Asc = new ASCIIEncoding();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpString = Asc.GetString(Byte);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int iCounter;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (iCounter = 0; iCounter < Byte.Length; iCounter++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpString = tmpString + Byte[iCounter].ToString();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return tmpString;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
private byte[] GetKeyByteArray(string strKey)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
ASCIIEncoding Asc = new ASCIIEncoding();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int tmpStrLen = strKey.Length;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
byte[] tmpByte = new byte[tmpStrLen - 1];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
tmpByte = Asc.GetBytes(strKey);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return tmpByte;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)}

