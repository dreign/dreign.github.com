---
title: 生成pdf文件的好东西,itextsharp
date: 2007-01-19 04:34:00
tags: 
categories: 
---
官网:  
<http://sourceforge.net/projects/itextsharp/>  
<http://hardrock.cnblogs.com/>  
<http://www.rubypdf.com/>  
  
现在的版本是3.18版,记得在引用里导入itextsharp.下面的代码是把图象合并到一个多页pdf的例子.

![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)      private
void process(string[] files, string newpdf)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.Document document = new
iTextSharp.text.Document(iTextSharp.text.PageSize.A4, 25, 25, 25, 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.pdf.PdfWriter.GetInstance(document, new FileStream(newpdf,
FileMode.Create, FileAccess.ReadWrite));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Open();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.Image image;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < files.Length; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image = iTextSharp.text.Image.GetInstance(files[i]);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (image.Height > iTextSharp.text.PageSize.A4.Height - 25)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.ScaleToFit(iTextSharp.text.PageSize.A4.Width - 25,
iTextSharp.text.PageSize.A4.Height - 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (image.Width > iTextSharp.text.PageSize.A4.Width - 25)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.ScaleToFit(iTextSharp.text.PageSize.A4.Width - 25,
iTextSharp.text.PageSize.A4.Height - 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.Alignment = iTextSharp.text.Image.ALIGN_MIDDLE;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//image.SetDpi(72, 72);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.NewPage();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Add(image);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Phrase phrase3 = new Phrase("dreign@163.com\n",
FontFactory.GetFont(FontFactory.TIMES, 9, iTextSharp.text.Font.NORMAL, new
iTextSharp.text.Color(192, 192, 192)));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//document.Add(phrase3);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ioe)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show(ioe.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}

---
title: 生成pdf文件的好东西,itextsharp
date: 2007-01-19 04:34:00
tags: 
categories: 
---
官网:  
<http://sourceforge.net/projects/itextsharp/>  
<http://hardrock.cnblogs.com/>  
<http://www.rubypdf.com/>  
  
现在的版本是3.18版,记得在引用里导入itextsharp.下面的代码是把图象合并到一个多页pdf的例子.

![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)      private
void process(string[] files, string newpdf)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.Document document = new
iTextSharp.text.Document(iTextSharp.text.PageSize.A4, 25, 25, 25, 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
try  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.pdf.PdfWriter.GetInstance(document, new FileStream(newpdf,
FileMode.Create, FileAccess.ReadWrite));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Open();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
iTextSharp.text.Image image;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < files.Length; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image = iTextSharp.text.Image.GetInstance(files[i]);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (image.Height > iTextSharp.text.PageSize.A4.Height - 25)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.ScaleToFit(iTextSharp.text.PageSize.A4.Width - 25,
iTextSharp.text.PageSize.A4.Height - 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else if (image.Width > iTextSharp.text.PageSize.A4.Width - 25)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.ScaleToFit(iTextSharp.text.PageSize.A4.Width - 25,
iTextSharp.text.PageSize.A4.Height - 25);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
image.Alignment = iTextSharp.text.Image.ALIGN_MIDDLE;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//image.SetDpi(72, 72);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.NewPage();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Add(image);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Phrase phrase3 = new Phrase("dreign@163.com\n",
FontFactory.GetFont(FontFactory.TIMES, 9, iTextSharp.text.Font.NORMAL, new
iTextSharp.text.Color(192, 192, 192)));  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//document.Add(phrase3);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
catch (Exception ioe)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show(ioe.Message);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
document.Close();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}

