---
title: 字节顺序：高位优先(big-endian)和低位优先(little-endian)
date: 2013-12-23 10:59:00
tags: 
categories: 
---
> 网络字节序: MSB 高字节前存法 Most Significant Bit   (Big Edian)

>

> 主机字节序: LSB 低字节前存法 Lest Significant Bit  (Little Edian)  

字节顺序是指占内存多于一个字节类型的数据在内存中的存放顺序，通常有小端、大端两种字节顺序。小端字节序指低字节数据存放在内存低地址处，高字节数据存放在内存高地址处；大端字节序是高字节数据存放在低地址处，低字节数据存放在高地址处。基于X86平台的PC机是小端字节序的（[原文参考](http://www.cppblog.com/aaxron/archive/2011/02/28/140786.html)）。在跨系统处理二进制数据流时，要注意这个问题。我就是在处理++服务端的BML（Binary
Markup Language）二进制标记数据流时碰到了这个问题。

因为现行的计算机都是以八位一个字节为存储单位，那么一个16位的整数，也就是C语言中的short，在内存中可能有两种存储顺序big-endian和litte-
endian。考虑一个short整数0x3132(0x32是低位，0x31是高位)，把它赋值给一个short变量，那么它在内存中的存储可能有两种不同的方式。

对于.net直接用BitConverter的IsLittleEndian属性来判断。Int16可以这样处理：

    
    
    //byte[] buf
    //startIndex 起始位置
    Array.Reverse(buf); //字节序反转
    Int16 i = BitConverter.ToInt16(buf, startIndex);
    

stackoverflow上有人这样处理了（[参考链接](http://stackoverflow.com/questions/14401270/efficient-
way-to-read-big-endian-data-in-c-sharp)），本人未验证：

    
    
    public static int ToInt32BigEndian(byte[] buf, int i)
    {
      return (buf[i]<<24) | (buf[i+1]<<16) | (buf[i+2]<<8) | buf[i+3]`;
    }
    

